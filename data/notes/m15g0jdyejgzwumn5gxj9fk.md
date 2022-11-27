
## Target Information

- IP: `46.101.82.173:30227`

## Exploitation

- Enumerated the target with `nmap`:

    ```shell
    nmap 46.101.82.173 -sC -sV -T4 -Pn
    ```

    It only returned that ports 31038 and 31337 were open.

- Attempted to SSH into the given port:

    ```shell
    ssh -p 30227 46.101.82.173
    ```

    Returned the message:

    ```text
    Bad packet length 218766171.
    ssh_dispatch_run_fatal: Connection to 46.101.82.173 port 30227: message authentication code incorrect
    ```

    The same thing when using `anonymous@46.101.82.173`.

    Running in verbose mode returned the following:

    ```log
    OpenSSH_8.2p1 Ubuntu-4ubuntu0.5, OpenSSL 1.1.1f  31 Mar 2020
    debug1: Reading configuration data /etc/ssh/ssh_config
    debug1: /etc/ssh/ssh_config line 19: include /etc/ssh/ssh_config.d/*.conf matched no files
    debug1: /etc/ssh/ssh_config line 21: Applying options for *
    debug1: Connecting to 46.101.82.173 [46.101.82.173] port 30227.
    debug1: Connection established.
    debug1: identity file /home/aaron/.ssh/id_rsa type -1
    debug1: identity file /home/aaron/.ssh/id_rsa-cert type -1
    debug1: identity file /home/aaron/.ssh/id_dsa type -1
    debug1: identity file /home/aaron/.ssh/id_dsa-cert type -1
    debug1: identity file /home/aaron/.ssh/id_ecdsa type -1
    debug1: identity file /home/aaron/.ssh/id_ecdsa-cert type -1
    debug1: identity file /home/aaron/.ssh/id_ecdsa_sk type -1
    debug1: identity file /home/aaron/.ssh/id_ecdsa_sk-cert type -1
    debug1: identity file /home/aaron/.ssh/id_ed25519 type -1
    debug1: identity file /home/aaron/.ssh/id_ed25519-cert type -1
    debug1: identity file /home/aaron/.ssh/id_ed25519_sk type -1
    debug1: identity file /home/aaron/.ssh/id_ed25519_sk-cert type -1
    debug1: identity file /home/aaron/.ssh/id_xmss type -1
    debug1: identity file /home/aaron/.ssh/id_xmss-cert type -1
    debug1: Local version string SSH-2.0-OpenSSH_8.2p1 Ubuntu-4ubuntu0.5
    debug1: Remote protocol version 2.0, remote software version OpenSSH_8.2p1 Ubuntu-4ubuntu0.5
    debug1: match: OpenSSH_8.2p1 Ubuntu-4ubuntu0.5 pat OpenSSH* compat 0x04000000
    debug1: Authenticating to 46.101.82.173:30227 as 'anonymous'
    debug1: SSH2_MSG_KEXINIT sent
    Bad packet length 218766171.
    ssh_dispatch_run_fatal: Connection to 46.101.82.173 port 30227: message authentication code incorrect
    ```

    So we at least know that OpenSSH is running on the target.

    The logs did highlight that at least one of the problems was that my OpenSSH install was trying to authenticate with my local `id_rsa` file, which obviously won't work. After conducting some research, [I determined](https://serverfault.com/q/493213/537331) that the issue could be solved by using a different command:

    ```shell
    ssh -p 30227 anonymous@46.101.82.173 -v -o PreferredAuthentications=password -o PubkeyAuthentication=no
    ```

    This yielded a much more promising set of logs:

    ```log
    debug1: kex_exchange_identification: banner line 0: \033[3mYou knock on the door and a panel slides back\033[0m
    debug1: kex_exchange_identification: banner line 1: |/\360\237\221\201\357\270\217 \360\237\221\201\357\270\217 \\|\033[3m A hooded figure looks out at you\033[0m
    debug1: kex_exchange_identification: banner line 2: "What is the password for this week's meeting?" SSH-2.0-OpenSSH_8.2p1 Ubuntu-4ubuntu0.5
    debug1: kex_exchange_identification: banner line 3:
    debug1: kex_exchange_identification: banner line 4:    \\/
    debug1: kex_exchange_identification: banner line 5: |/\360\237\221\201\357\270\217 \360\237\221\201\357\270\217 \\| "That's not our password - call the guards!"
    kex_exchange_identification: Connection closed by remote host
    ```

- Attempted to brute force the password with `msfconsole`:

    ```shell
    msfconsole
    ```

    ```ruby
    use auxiliary/scanner/ssh/ssh_login
    set RHOSTS 46.101.82.173
    set RPORT 30227
    set PASS_FILE /usr/share/wordlists/rockyou.txt
    set USERNAME anonymous
    set STOP_ON_SUCCESS true
    set VERBOSE true
    run
    ```

    Unfortunately this was sporadically interrupted by the target closing the connection, and there is no setting to force `msfconsole` to keep trying. I opened an issue [here](https://github.com/rapid7/metasploit-framework/issues/17178) to request this feature, but it most certainly won't be implemented in time to help me with this challenge.

- Attempted to brute force the password with `hydra`:

    ```shell
    hydra -l anonymous -P /usr/share/wordlists/rockyou.txt ssh://46.101.82.173 -s 30227 -t 4
    ```

    Gave this error message: `[ERROR] could not connect to ssh://46.101.82.173:30227 - read_packet(): Packet len too high(218766171 d0a1b5b)`

- Running `strings` on the file provided by HTB gave the password `sup3r_s3cr3t_p455w0rd_f0r_u!` thanks to the proximity to the messages displayed by the SSH server. Unfortunately this just SSH's us into our current directory, since it isn't running on the server.

- Attached `edb_debugger` to the SSH password verification binary to determine what the password is being compared to.

    ```shell
    edb --run ./meeting
    ```

    Running a search for the password string shows that `/bin/sh` is ran if the password matches the proper memory address.

- Using `telnet 46.101.82.173 30227` got me the same result as SSH, except this one was interactive and actually allowed me to enter the password.

    Once I did that, the password I uncovered in the local binary (`sup3r_s3cr3t_p455w0rd_f0r_u!`) worked, and I was able to get a shell in the server.

    Running `cat flag.txt` yielded the flag, `HTB{1nf1ltr4t1ng_4_cul7_0f_str1ng5}`.

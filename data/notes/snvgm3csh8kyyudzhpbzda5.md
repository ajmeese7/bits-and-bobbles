
## Target Information

- IP: `167.71.135.137:32184`
-  Nothing related to the challenge is running on any other ports:
    ```shell
    $ nmap 167.71.135.137 -sC -sV -T4 -Pn
    ```
- SSH'ing into the target just runs the binary, it doesn't give a version or anything:
    ```shell
    $ ssh -p 32184 anonymous@167.71.135.137
    ```

## Exploitation

- Tried going into the negative numbers to overflow back to positive, which worked, but it failed when attempting to purchase the laser.

  The overflow happens right above the 32000 mark, which you can get right on the edge of with 24 shovel purchases.

- Figured out that using `telnet 167.71.135.137 32184` connects me to the server and runs the binary there.

  Running anything with letters crashes the program into an endless loop of "You cannot buy less than 1!"

  Running the command in a non-PTY terminal allowed me to use the escape command, which is `^]`. That got me to the telnet prompt, which allowed me to run commands. The `help` command showed me everything I have access to, which is very little.

- Entering `-2` then `-11` a few times got me to the overflow, which allowed me to buy the laser and returned the flag:

  ```text
  HTB{1nt3g3R_0v3rfl0w_101_0r_0v3R_9000!}
  ```

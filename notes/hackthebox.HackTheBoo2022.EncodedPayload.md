---
id: 10kcjswdx90v3sgiv63p36i
title: EncodedPayload
desc: ''
updated: 1666539859716
created: 1666539680143
---

Tried making the binary an executable and executing it:

```shell
chmod +x ./encodedpayload
./encodedpayload
```

But it silently failed. Running it with `strace` showed that it was trying to connect to localhost:

```log
$ strace ./encodedpayload
execve("./encodedpayload", ["./encodedpayload"], 0x7ffd52e05a00 /* 84 vars */) = 0
strace: [ Process PID=479009 runs in 32 bit mode. ]
socket(AF_INET, SOCK_STREAM, IPPROTO_IP) = 3
dup2(3, 2)                              = 2
dup2(3, 1)                              = 1
dup2(3, 0)                              = 0
connect(3, {sa_family=AF_INET, sin_port=htons(1337), sin_addr=inet_addr("127.0.0.1")}, 102) = -1 ECONNREFUSED (Connection refused)
syscall_0xffffffffffffff0b(0xff907188, 0xff907180, 0, 0, 0, 0) = -1 ENOSYS (Function not implemented)
execve("/bin/sh", ["/bin/sh", "-c", "echo HTB{PLz_strace_M333}"], NULL) = 0
strace: [ Process PID=479009 runs in 64 bit mode. ]
brk(NULL)                               = 0x56187162a000
arch_prctl(0x3001 /* ARCH_??? */, 0x7ffe62905c70) = -1 EINVAL (Invalid argument)
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=149062, ...}) = 0
mmap(NULL, 149062, PROT_READ, MAP_PRIVATE, 4, 0) = 0x7f264331a000
close(4)                                = 0
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300A\2\0\0\0\0\0"..., 832) = 832
pread64(4, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784
pread64(4, "\4\0\0\0\20\0\0\0\5\0\0\0GNU\0\2\0\0\300\4\0\0\0\3\0\0\0\0\0\0\0", 32, 848) = 32
pread64(4, "\4\0\0\0\24\0\0\0\3\0\0\0GNU\0\30x\346\264ur\f|Q\226\236i\253-'o"..., 68, 880) = 68
fstat(4, {st_mode=S_IFREG|0755, st_size=2029592, ...}) = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f2643318000
pread64(4, "\6\0\0\0\4\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0@\0\0\0\0\0\0\0"..., 784, 64) = 784
pread64(4, "\4\0\0\0\20\0\0\0\5\0\0\0GNU\0\2\0\0\300\4\0\0\0\3\0\0\0\0\0\0\0", 32, 848) = 32
pread64(4, "\4\0\0\0\24\0\0\0\3\0\0\0GNU\0\30x\346\264ur\f|Q\226\236i\253-'o"..., 68, 880) = 68
mmap(NULL, 2037344, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7f2643126000
mmap(0x7f2643148000, 1540096, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x22000) = 0x7f2643148000
mmap(0x7f26432c0000, 319488, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x19a000) = 0x7f26432c0000
mmap(0x7f264330e000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1e7000) = 0x7f264330e000
mmap(0x7f2643314000, 13920, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f2643314000
close(4)                                = 0
arch_prctl(ARCH_SET_FS, 0x7f2643319580) = 0
mprotect(0x7f264330e000, 16384, PROT_READ) = 0
mprotect(0x56186fc4b000, 8192, PROT_READ) = 0
mprotect(0x7f264336c000, 4096, PROT_READ) = 0
munmap(0x7f264331a000, 149062)          = 0
getuid()                                = 1000
getgid()                                = 1000
getpid()                                = 479009
rt_sigaction(SIGCHLD, {sa_handler=0x56186fc40c30, sa_mask=~[RTMIN RT_1], sa_flags=SA_RESTORER, sa_restorer=0x7f2643169090}, NULL, 8) = 0
geteuid()                               = 1000
getppid()                               = 479006
brk(NULL)                               = 0x56187162a000
brk(0x56187164b000)                     = 0x56187164b000
getcwd("/home/aaron/Downloads/HTB/rev_encodedpayload", 4096) = 45
geteuid()                               = 1000
getegid()                               = 1000
rt_sigaction(SIGINT, NULL, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGINT, {sa_handler=0x56186fc40c30, sa_mask=~[RTMIN RT_1], sa_flags=SA_RESTORER, sa_restorer=0x7f2643169090}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGQUIT, {sa_handler=SIG_DFL, sa_mask=~[RTMIN RT_1], sa_flags=SA_RESTORER, sa_restorer=0x7f2643169090}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGTERM, {sa_handler=SIG_DFL, sa_mask=~[RTMIN RT_1], sa_flags=SA_RESTORER, sa_restorer=0x7f2643169090}, NULL, 8) = 0
write(1, "HTB{PLz_strace_M333}\n", 21)  = -1 EPIPE (Broken pipe)
--- SIGPIPE {si_signo=SIGPIPE, si_code=SI_USER, si_pid=479009, si_uid=1000} ---
+++ killed by SIGPIPE +++
```

And as you can see, the flag was `HTB{PLz_strace_M333}`.

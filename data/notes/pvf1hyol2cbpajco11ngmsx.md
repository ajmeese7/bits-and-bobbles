
Running `./ghost` gives us the following output:

```log
./ghost
|                                       _| I've managed to trap the flag ghost in this box, but it's turned invisible!
Can you figure out how to reveal them?
```

The characters between the pipes are just `0x20`, so there's nothing of interest there.

Running `strings ghost` gives us a lot of output, but the most interesting part is the following, which is right above the string from the prompt:

```log
u/UH
[]A\A]A^A_
[GQh{'f}g wLqjLg{ Lt{#`g&L#uLpgu&Lc'&g2n%s
[4m%*.c
[24m|
```

Running magic on CyberChef with a depth of 5, intensive mode, and extensive language support showed us that the following operation returned the flag:

```text
XOR({'option':'Hex','string':'13'},'Standard',false)

HTB{h4unt3d_by_th3_gh0st5_0f_ctf5_p45t!}
```

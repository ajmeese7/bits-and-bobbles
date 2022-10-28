---
id: j9tuxbmsf7ndkj8z99gtsf8
title: Ouija
desc: ''
updated: 1666785203407
created: 1666738232669
tags:
  - hackthebox
  - reverse-engineering
---

> You've made contact with a spirit from beyond the grave! Unfortunately, they speak in an ancient tongue of flags, so you can't understand a word. You've enlisted a medium who can translate it, but they like to take their time...

## Exploitation

Executing the binary takes a long time and outputs the following:

```log
$ ./ouija
Retrieving key.
     ..... done!
Hmm, I don't like that one. Let's pick a new one.
     ..... done!
Yes, 18 will do nicely.
     ..... done!
Let's get ready to start. This might take a while!
     ..... done!
This one's an uppercase letter!
     ..... done!
Okay, let's write down this letter! This is a pretty complex operation, you might want to check back later.
     ..... done!
H
...
```

And on and on and on, which nobody has time to wait for.

Running `strings ouija` gives us a lot of output, but the most interesting part is the following:

```log
ZLT{Svvafy_kdwwhk_lg_qgmj_ugvw_escwk_al_wskq_lg_ghlaearw_dslwj!}
```

This is obviously the encoded flag, since it follows the same format as the other flags. We can try to use a [Caesar cipher](https://en.wikipedia.org/wiki/Caesar_cipher) to decode it. We can use [CyberChef](https://gchq.github.io/CyberChef/) to do this. We can use the `ROT13` recipe to decode the flag.

After experimenting with the `ROT` recipe, we find the key that decodes the flag to the proper format, 8. That gives us the following flag:

```text
HTB{Adding_sleeps_to_your_code_makes_it_easy_to_optimize_later!}
```

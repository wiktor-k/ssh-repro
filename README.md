# SSH issue

To reproduce:

```
$ ssh-keygen -Y find-principals -f allowed_signers.md -I wiktor@metacode.biz -n file -s rsa-key.txt.sig < rsa-key.txt
allowed_signers.md:3: missing key
wiktor@metacode.biz
```

But empty lines should be allowed per the [documentation for ALLOWED SIGNERS](https://man.archlinux.org/man/ssh-keygen.1#ALLOWED_SIGNERS):

> Empty lines and lines starting with a ‘#’ are ignored as comments.

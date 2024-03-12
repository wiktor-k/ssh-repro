# SSH issue

To reproduce:

```
$ ssh-keygen -Y find-principals -f allowed_signers.md -I wiktor@metacode.biz -n file -s rsa-key.txt.sig < rsa-key.txt
allowed_signers.md:3: missing key
wiktor@metacode.biz
```

But empty lines should be allowed per the [documentation for ALLOWED SIGNERS](https://man.archlinux.org/man/ssh-keygen.1#ALLOWED_SIGNERS):

> Empty lines and lines starting with a ‘#’ are ignored as comments.

Solved in openssh 9.7p1 via https://github.com/openssh/openssh-portable/commit/cd82f7526e0481720567ae41db7849ab1c27e27b

See the relevant message:
  - https://lists.mindrot.org/pipermail/openssh-unix-dev/2024-March/041242.html
  - [`mid:9c94c1f5-b6ac-7210-519b-f6d29bfad4d7@mindrot.org`](mid:9c94c1f5-b6ac-7210-519b-f6d29bfad4d7@mindrot.org)

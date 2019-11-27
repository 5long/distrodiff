---
title: "/bin/sh: a de-facto standard"
slug: bin-sh
layout: post
---

* toc
{:toc}

`/bin/sh` is assumed to exist on Unix systems by many shell scripts.
It is sometimes referred to as "the default shell".

[POSIX] claims that this is not standard. Nevertheless, using
a shebang line of `#!/bin/sh` works well in most popular Unices:

[posix]: https://pubs.opengroup.org/onlinepubs/009695399/utilities/sh.html#tag_04_128_16

| OS | Default `/bin/sh` Implementation |
| --- | --- |
| Alpine | [ash with busybox extensions][busybox-sh] |
| Arch | [bash] |
| Debian | [dash] |
| Fedora / RHEL / CentOS | [bash] |
| FreeBSD | [Bourne shell with Berkerly extensions][freebsd-sh] |
| OpenSUSE | [bash] |
| Ubuntu | [dash] |
| macOS | [bash] |

[dash]: #dash-as-binsh
[bash]: #bash-as-binsh
[busybox-sh]: https://git.busybox.net/busybox/tree/shell
[freebsd-sh]: https://www.freebsd.org/cgi/man.cgi?query=sh&sektion=1&manpath=freebsd-release-ports

## Implementations

### Bash as /bin/sh

Given that [Bash][bash-website] is the GNU project's shell, it's no
surprise that it's installed by default in most‑if‑not‑all GNU/Linux
distributions. When running as `/bin/sh`, Bash enters POSIX mode to
be more compatible with Bourne shell. See
<https://tiswww.case.edu/php/chet/bash/POSIX> for details.

[bash-website]: https://www.gnu.org/software/bash/

#### Beware of bashisms

Some programmers don't quite understand the fact that `/bin/sh`
isn't guaranteed to be bash. Or they simply don't know the
differences. They write shell scripts that use features of bash
(a.k.a [bashism]). But the scripts have `#!/bin/sh` as the shebang
line. This kind of scripts appears to work fine on OSes with [bash
as `/bin/sh`][bash]. But they will fail to work on other OSes.

[bashism]: https://mywiki.wooledge.org/Bashism

### Dash as /bin/sh

[The Debian Almquist Shell (dash)][dash-website] is the default
shell since Debian 6.0 and Ubuntu 6.10. Before that, Debian & Ubuntu
(and their derivatives) use bash as `/bin/sh`.

[dash-website]: http://gondor.apana.org.au/~herbert/dash/

## Take-aways

* `/bin/sh` isn't always `bash`.
* If you want to use bashisms, explicitly use `bash`.
* If you want maximum portability, don't use bashisms.
  - [checkbashisms] can help you detect bashisms from your scripts.

[checkbashisms]: https://linux.die.net/man/1/checkbashisms

## Further Reading

* Ash (Almquist Shell) Variants <https://www.in-ulm.de/~mascheck/various/ash/>

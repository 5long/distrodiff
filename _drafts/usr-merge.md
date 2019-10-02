---
title: /usr merged with /
layout: post
unpublished: true
---

See <https://www.freedesktop.org/wiki/Software/systemd/TheCaseForTheUsrMerge/> for details.

TL;DR - The following directories are to be merged:

```
/bin -> /usr/bin
/sbin -> /usr/sbin
/lib -> /usr/lib
/lib64 -> /usr/lib64
```

... and they will become symlinks, pointing to their respective merge targets (e.g. `/bin` will symlink to `/usr/bin`).

## Implementations

| OS | Merged /usr |
| Ubuntu | 19.04 |
| Debian | 10 |
| Fedora |  |
| RHEL / CentOS |  |
| Arch |  |
| Alpine Linux | ✘ |

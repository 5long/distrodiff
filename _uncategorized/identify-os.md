---
title: Identify Linux Distro and Version
layout: post
---

* toc
{:toc}

If you've just gained access to a machine and you have no one to ask
"what OS does this machine run", you'll have to identify the OS on
your own.

## /etc/os-release

`/etc/os-release` is introduced by systemd. It contains OS
identification data in a [sh]-compatible syntax, allowing users to
`source` it and use the information as shell variables, or use it as
a [dotenv] file, or simply view / parse it as a plain text file.

This file is neither systemd-dependant nor Linux-specific. As the
time of writing, [FreeBSD has adopted this file][freedsd] and it
should be available starting from FreeVSD v13.

## Distro-specific Methods

Many Linux distros have introduced their own method of
identification. See the footnotes in the [os-release annoucement] for
an incomplete list of them.

It's not recommended to use any of those unless you have to support
an end-of-life old Linux distro.

[sh]: bin-sh.html
[dotenv]: https://duckduckgo.com/?q=dotenv
[os-release annoucement]: http://0pointer.de/blog/projects/os-release
[freebsd]: https://svnweb.freebsd.org/base?view=revision&revision=354922

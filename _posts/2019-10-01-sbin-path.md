---
title: "Separated sbin/ Directories"
layout: post
---

* toc
{:toc}

Roughly speaking, there are two types of bin directories: `sbin/`
and others. According to [FHS 3.0]:

> if a normal (not a system administrator) user will ever run it
> directly, then it must be placed in one of the "bin" directories.
> Ordinary users should not have to place any of the `sbin`
> directories in their path.

Some commands should only exist in one of the `sbin` directories:
`/sbin`, `/usr/sbin` and `/usr/local/sbin`. In practice, OSes
implement this differently:

## Implementations

| OS | No separated `sbin/` | Merely separated `sbin/` | Isolate `sbin/` with `$PATH` |
| --- | --- | --- | --- |
| Alpine || ✔ ||
| Arch | ✔ |||
| Debian / Ubuntu ||| ✔ |
| Fedora / RHEL || ✔ ||

### No separated `sbin/`

On Arch Linux, `/sbin/` and `/usr/sbin` are not regular directories.
They are symbolic links to `/usr/bin`.  All executables (that are
installed by package manager) are put in `/usr/bin`. This doesn't
conform to FHS.

### Merely separated `sbin/`

Fedora conforms to FHS: `sbin/` directories are separated.
For normal users, `sbin/` has lower priorities when the shell is
looking up commands in `$PATH`.

### Isolate `sbin/` with `$PATH`

Debian and its derivatives conforms more strictly to FHS: when
setting up `$PATH` with `/etc/profile`, normal users won't see
`sbin/` in their `$PATH`. This means when a normal user runs
`shutdown` command, the shell will print a "command not found"
error.

## Take-aways

* If you run a command but the shell prints "command not found", try
    searching in `/usr/sbin` or `/sbin`.
  - Or try `sudo <command>`. `sudo` looks up commands
      differently than shell.

## Related Post

* [/usr merge](TODO)


[FHS 3.0]: https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch03s16.html#ftn.idm236092603392

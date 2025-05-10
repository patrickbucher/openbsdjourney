+++
date = '2025-05-10T19:27:27+02:00'
title = 'Basic Package Management'
+++

Having installed OpenBSD, I'd like to work with my system. Even though the base system already provides a lot, sooner or later additional software is required, e.g. Vim, the text editor of my choice, or Elixir, a programming language I'd like to discover.

Fortunately, OpenBSD comes with a package system to install additional software provided by the community. I won't get into the details of this system but rather describe its most basic usage.

Entering `pkg_` in the shell and pressing the tab key reveals a list of programs related to package management. Running the `whatis` command for each of those shows the following descriptions (in alphabetic order):

- `pkg_add(1)`: install or update software packages
- `pkg_check(8)`: check consistency of installed packages
- `pkg_create(1)`: create binary software package for distributions
- `pkg_delete(1)`: delete software package distributions
- `pkg_info(1)`: display information on software packages
- `pkg_mklocatedb(1)`: create a locate databaes for packages
- `pkg_sign(1)`: sign a binary package for distribution

Notice that only `pkg_check` is part of section 8 (system maintenance and operation commands), while the other `pkg_`-prefixed programs are part of section 1 (general commands).

I won't bother with `pg_create(1)` and `pkg_sign(1)` in this post, because they are intended for package maintainers, not mere users. The `pkg_mklocatedb(1)` command will be quickly discussed further below.

For the moment, I'll focus on the following use cases, which are relevant on a daily basis for me:

1. Find information about packages,
2. install and updating packages,
3. remove packages, and
4. check consistency of installed packages.

I'll use the `elixir` package as an example, which provides the `iex` program (among others) and depends on the `erlang` package. Commands to be run with super-user rights are prefixed with `#` (even though I prefer `doas` for that purpose); commands that don't require elevated privileges are prefixed with `$`.

## Finding Information: `pkg_info`

List installed packages with a one-line description:

    $ pkg_info -A

Show a one-line comment for a package:

    $ pkg_info -c elixir

Show information about a package:

    $ pkg_info elixir

List the files of an installed package:

    $ pkg_info -L elixir

Figure out which _installed_ package provides a file:

    $ pkg_info -E /usr/local/bin/iex

To figure out which _uninstalled_ package provides a file, see the section about `pkg_locatedb` and `pkg_mklocatedb` further below.

Find a package by providing a substring of their name:

    $ pkg_info -Q elix

## Installing and Updating Packages: `pkg_add`

Install a package with its required dependencies:

    # pkg_add elixir

Install a package, but also update its dependencies:

    # pkg_add -U elixir

Update a package and its dependencies:

    # pkg_add -u elixir

Update all installed packages:

    # pkg_add -u

## Removing Packages: `pkg_delete`

Delete a package:

    # pkg_delete elixir

Remove unused dependencies:

    # pkg_delete -a

To remove a package with all its dependencies, combine the two above commands:

    # pkg_delete elixir && pkg_delete -a

## Checking Consistency: `pkg_check`

Perform a sanity check on the installed packages (files, dependencies):

    # pkg_check

## `pkg_locate` and `pkg_mklocatedb`

Unfortunately, the `pkg_info -E FILE` command, which shows what package provides a given file, only works for packages that are already installed. However, it would be more useful to figure out which package provides a file that is not already on my system.

For example, I'd like to use the `ss` utility as a port scanner, which is not provided by the base system. Fortunately, in the `pkg_info(1)` manpage, the section about the `-E` option points towards the `pkglocatedb` package:

    # pkg_add pkglocatedb

Which provides the following files:

    $ pkg_info -L pkglocatedb
    /usr/local/bin/pkg_locate
    /usr/local/bin/pkglocate
    /usr/local/man/man1/pkg_locate.1
    /usr/local/share/pkglocatedb

Both manpage and binary are reachable via `pkg_locate` and `pkglocate`. I'll use the `pkg_locate` variant for the sake of consistency with the other `pkg_` tools I use.

First, the `pkg_mklocatedb` command has to be run to build the file index for all packages:

    $ pkg_mklocatedb

Once built, the database can be queried using the `pkg_locate` command, which supports the same flags as `locate(1)`.

By default, the `pkg_locate` command queries the entire file path:

    $ pkg_locate iex

To only query the last path component, i.e. the file, use the `-b` option:

    $ pkg_locate -b iex

However, this finds every package/path combination in which `iex` is _part_ of the file name. For exact matches, filter the output using `grep`:

    $ pkg_locate -b iex | grep iex$

## Conclusion

Not only does OpenBSD provide a simple and easy to use package management system with a lot of useful software in recent versions, it also provides great manpages with which you can learn everything that's necessary to cover the most basic use cases.

This system makes a much more streamlined impression to me than the combination of `apt`/`apt-get`/`aptitude` and `dpkg` in Debian GNU/Linux; just like `pacman` in Arch Linux.

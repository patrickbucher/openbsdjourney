# OpenBSD Journey

Personal blog based on Hugo and the [no style,
please!](https://github.com/hanwenguo/hugo-theme-nostyleplease) theme about
getting to know the OpenBSD operating system.

## Setup

Scaffolding:

```sh
hugo new site openbsdjourney.paedubucher.ch
cd openbsdjourney.paedubucher.ch
hugo mod init openbsdjourney.paedubucher.ch
```

Modify and extend `hugo.toml`:

```toml
baseURL = 'https://openbsdjourney.paedubucher.ch'
languageCode = 'en-us'
title = 'OpenBSD Journey'

[module]
[[module.imports]]
path = 'github.com/hanwenguo/hugo-theme-nostyleplease'
```

Install module:

```sh
hugo mod tidy
```

Create files for the footer (`layouts/footer.md`), for the intro content
(`content/_index.md`), and for the navigation (`data/menu.toml` according to
the
[example](https://github.com/hanwenguo/hugo-theme-nostyleplease/blob/main/config.toml))
.

+++
date = '2025-05-11T08:44:27+02:00'
title = 'Tmux Sessions, Windows, and Panes'
+++

In this post, I'm going to summarize the first chapter of [tmux 3. Productive Mouse-Free Development](https://pragprog.com/titles/bhtmux3/tmux-3/) by Brian P. Hogan, published by The Pragmatic Bookshelf. As in yesterday's post, I'm focusing on the commands and their purpose. Since none of the commands require elevated privileges, I'm goint to omit the `$` prompt in front of them.

Command use a _Prefix_, which is `Ctrl`-`b` (press those keys together) by default, and will be displayed as `Prefix`.

Check the tmux version number:

    tmux -V

Start tmux:

    tmux

## Sessions

Create a session with the name `basic`:

    tmux new-session -s basic

The `new-session` command can be abbreviated as `new`:

    tmux new -s basic

Detach from the running session using `Prefix` `d` (i.e. first press the prefix, release, and then press `d`).

List existing tmux sessions (abbreviated):

    tmux list-sessions
    tmux ls

Attach to the last tmux session:

    tmux attach

Attach to a specific tmux session by its name, e.g. `basic`:

    tmux attach -t basic

Create a detached session called `additional` ("in the background"):

    tmux new -s additional -d

End a session, e.g. `basic`:

    tmux kill-session -t basic

## Windows

Start tmux with a named window (`shell`) in a session called `multiwindow`:

    tmux new -s multiwindow -n shell

Create a window in the current session: `Prefix` `c`.

Rename the current window: `Prefix` `,`.

Move to the next window: `Prefix` `n`.

Move to the previous window: `Prefix` `p`.

Move to the nth window (first, second, …): `Prefix` `0`, `Prefix` `1`, …

Display a list of windows in a menu: `Prefix` `w`.

Find a window by its name: `Prefix` `f`.

Close a window: `Prefix` `&`.

## Panes

Split the window (or pane) into a left and a right pane: `Prefix` `%`.

Split the window (or pane) into a top and a bottom pane: `Prefix` `"`.

Cycle through the panes: `Prefix` `o`.

Move to another pane given a direction:

- left: `Prefix` `←`
- right : `Prefix` `→`
- up: `Prefix` `↑`
- down: `Prefix` `↓`

Apply a pre-defined layout: `Prefix` `Space`.

Kill the current pane: `Prefix` `x`.

## Miscellaneous

Enter command mode: `Prefix` `:`.

List key bindings and their commands: `Prefix` `?`.

The next chapter is about configuring tmux, so stay tuned.


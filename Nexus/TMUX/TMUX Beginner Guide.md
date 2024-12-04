
TMUX (Terminal Multiplexer) is a powerful tool for managing multiple terminal sessions from within a single terminal window. It allows you to create, switch between, and manage multiple terminals, windows, and panes, making it easier to work with multiple projects or tasks simultaneously.

With TMUX, you can:

1. **Create multiple sessions**: Launch multiple instances of your favorite shell (e.g., bash, zsh) within a single terminal window.
2. **Switch between sessions**: Quickly switch between multiple sessions using keyboard shortcuts (e.g., C-b).
3. **Manage windows and panes**: Create new windows and panes to organize your sessions, or resize them to suit your needs.
4. **Split screens**: Split your screen into multiple panes to work on different tasks simultaneously.
5. **Share sessions**: Share a session with others over SSH or other protocols.

## How to Install on Mac

use the following command: 

```sh
brew install tmux
```

❖ start `tmux` by opening your shell then type `tmux` and hit enter

❖ The default `prefix` (custom keyboard combination followed by a shortcut) is control `⌃ + b` followed by another key

❖ some useful keyboard shortcuts: 

`CTRL+b then %` → Split the current pane vertically.

`CTRL+b then "` → Split the current pane horizontally.

::`Note`:: just for convenience we can change the `%` and `"` to `h` for horizontal and `v` for vertical. by creating a `tmux.conf` file in your home folder and make it `hidden` by adding the dot `.tmux.conf` but first let's create a file in vs-code: 

```
code ~/.tmux.conf
```

and adding the following lines: 

```
# Remaps the horizontal split to CTRL+b+h.
unbind %
bind h split-window -h


# Remaps the vertical split key to CTRL+b+v.
unbind '"'
bind v split-window -v
```

❖ Save the file by pressing `Command ⌘ + S ` cuz the file is not there by default.

### Activate Mouse Support

❖ To toggle between panes and resize them using the mouse we need to add the following line to the `tmux.conf` 

```
# adding mouse support
set -g mouse on
```

❖ To Reload the configuration without restarting `tmux`:

```shell
tmux source-file ~/.tmux.conf
```

## How to get a terminal output from TMUX to mac os Clipboard?

- First enable mouse support
- Select the text you want to copy with your mouse
- Type the following command: 

```zsh
tmux show-buffer | pbcopy
```

- This will copy the selected text to clipboard but just for convenience we will make an alias for this command in our `.zshrc` file: 

```zsh
alias ~buffer="tmux show-buffer | pbcopy"
```

- Now you just have to select the text and type `~buffer` and hit enter and your text is now ready on your clipboard

## There's also an easier way

- Open `tmux.conf` and add the following lines: 

```
bind-key -T copy-mode-vi y send-keys -X copy-pipe-and-cancel "pbcopy"
bind-key -T copy-mode y send-keys -X copy-pipe-and-cancel "pbcopy"
```

- After reloading TMUX, pressing `y` in copy mode (or when you select with your mouse) will copy the selection directly to your macOS clipboard.


## TMUX Copy Mode

Copy Mode allows users to navigate through the output of a pane and select and copy text. This feature is indispensable in terminal sessions with a lot of output. You can manipulate pane content and transfer it between panes, windows, and sessions much more efficiently.

| Command/Shortcut          | Action                                               |
| ------------------------- | ---------------------------------------------------- |
| **`CTRL+b`** then **`[`** | Enter copy mode.                                     |
| **`CTRL+Space`**          | Start text selection in copy mode (move with arrows) |
| **`CTRL+W`**              | Copy the Selected Text and close copy mode.          |
| **`CTRL+b`** then **`]`** | paste the copied text                                |
:: `Note` :: The paste command won't work outside of `tmux`

## TMUX Windows

Windows are used to separate individual tasks within a session and create a manageable window-based interface. The table lists commands for managing windows within **`tmux`** sessions:

| Command/Shortcut                          | Action                                         |
| ----------------------------------------- | ---------------------------------------------- |
| **`CTRL+b`** then **`c`**                 | Create a new window.                           |
| **`CTRL+b`** then **`,`**                 | Rename the current window.                     |
| **`CTRL+b`** then **`w`**                 | List all windows.                              |
| **`CTRL+b`** then **`&`**                 | Kill the current window.                       |
| **`CTRL+b`** then **`n`**                 | Switch to the next window.                     |
| **`CTRL+b`** then **`p`**                 | Switch to the previous window.                 |
| **`CTRL+b`** then **`l`**                 | Open the last window.                          |
| **`CTRL+b`** then **`0....9`**            | Switch to a specific numbered window.          |
| **`CTRL+b`** then **`d`**                 | Detach from the current session.               |
| **`tmux select-window -t [window_name]`** | Select a specific window by its index or name. |
| **`tmux rename-window [new_name]`**       | Rename the current window.                     |

## TMUX Panes

A pane is a basic element of a tmux window within a session. Managing many panes simultaneously can quickly clutter a window if not organized properly. The following shortcuts help you manage and organize panes efficiently:

| Command/Shortcut                | Action                                    |
| ------------------------------- | ----------------------------------------- |
| **`CTRL+b`** then **`%`**       | Split the current pane vertically.        |
| **`CTRL+b`** then **`"`**       | Split the current pane horizontally.      |
| **`CRTL+b`** then **`x`**       | Close the current pane.                   |
| **`CTRL+b`** then **`o`**       | Switch between panes.                     |
| **`CTRL+b`** then **`z`**       | Toggle pane zoom (make pane full screen). |
| **`CTRL+b`** then **`;`**       | Toggle between the last two active panes. |
| **`CTRL+b`** then **`{`**       | Move the current pane left.               |
| **`CTRL+b`** then **`}`**       | Move the current pane right.              |
| **`CTRL+b`** then **`SPACE`**   | Toggle through different pane layouts.    |
| **`CTRL+b`** then **`!`**       | Convert the current pane into a window.   |
| **`exit`** or  <br>**`CTRL+d`** | Close the selected pane.                  |
| **`CTRL+b`** then **`q`**       | Display pane number.                      |
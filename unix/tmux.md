# `tmux` - terminal multiplexer
> 24/05/2017

#### Helpful links
  - [A tmux crash course](https://robots.thoughtbot.com/a-tmux-crash-course)
  - [A good tmux cheat-sheet](https://gist.github.com/MohamedAlaa/2961058)

### A script to customize `tmux` :
```bash
tmux new -s setup

# downloads tmux-plugin manager
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm

echo "# remap prefix to Control + a
set -g prefix C-a
unbind C-b
bind C-a send-prefix

# mouse mode on
setw -g mouse on

# force a reload of the config file
unbind r
bind r source-file ~/.tmux.conf

# quick pane cycling
unbind ^A
bind ^A select-pane -t :.+


# List of plugins
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'

set -g @plugin 'jimeh/tmux-themepack'

# Other examples:
# set -g @plugin 'github_username/plugin_name'
# set -g @plugin 'git@github.com/user/plugin'
# set -g @plugin 'git@bitbucket.com/user/plugin'

# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'

# set -g @themepack 'powerline/block/blue'
# set -g @themepack 'powerline/double/magenta'
set -g @themepack 'powerline/double/green'" > ~/.tmux.conf

# source the conf file
tmux source-file ~/.tmux.conf
```

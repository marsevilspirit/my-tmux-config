# my-tmux-config

## 简介

这是我的tmux的配置

tmux是一个出色的终端分屏工具，它通常与我使用的编辑器neovim配合，达到了不错的效果

下面是使用我的配置的教程

## 第一步 下载tmux

```shell
sudo pacman -Syu #我的操作系统是arch linux, 其他操作系统请按照各自的方法下载
sudo pcaman -S tmux vim git
```

## 第二步 创建tmux配置文件

```shell
mkdir ~/.tmux.conf
vim ~/.tmux.conf
```

以下是我的tmux配置文件，可以根据自己的喜好进行修改

```
set -g default-terminal screen-256color # 设置终端为256色
set-option -ga terminal-overrides ",*256col*:Tc" # 设置终端为256色
# -- general
setw -g xterm-keys on # 使用xterm风格的快捷键
set -s escape-time 0 # 设置ESC键的响应时间为0
set -sg repeat-time 300 # 设置重复时间为300ms
set -s focus-events on # 开启焦点事件
set -g mouse on # 开启鼠标
set -sg exit-empty on # 关闭最后一个窗口时自动退出

set -q -g status-utf8 on # 设置utf8编码
setw -q -g utf8 on # 设置utf8编码

set -g visual-activity off # 关闭窗口闪烁
setw -g monitor-activity off # 关闭窗口闪烁
setw -g monitor-bell off # 关闭窗口闪烁 

set -g history-limit 10000 # 设置历史记录为10000

#-- prefix
unbind C-b # 解绑默认的前缀
set -g prefix 'C-f' # 设置新的前缀

# window navigation 
unbind n
unbind p
unbind 1
unbind 2
unbind 3 
unbind 4
unbind 5
unbind 6
unbind 7
unbind 8
unbind 9
unbind 0
bind -r C-p previous-window
bind -r C-n next-window

bind -n M-1 select-window -t 1
bind -n M-2 select-window -t 2
bind -n M-3 select-window -t 3
bind -n M-4 select-window -t 4
bind -n M-5 select-window -t 5
bind -n M-6 select-window -t 6
bind -n M-7 select-window -t 7
bind -n M-8 select-window -t 8
bind -n M-9 select-window -t 9
bind -n M-0 select-window -t 0

# 这些 key bindings 用于在不同的窗口之间移动
bind -n M-! join-pane -t :1
bind -n M-@ join-pane -t :2
bind -n 'M-#' join-pane -t :3
bind -n 'M-$' join-pane -t :4
bind -n M-% join-pane -t :5
bind -n M-^ join-pane -t :6
bind -n M-& join-pane -t :7
bind -n M-* join-pane -t :8
bind -n M-( join-pane -t :9
bind -n M-) join-pane -t :0

# 上下左右的分屏
bind k split-window -vb -c "#{pane_current_path}"
bind j split-window -v -c "#{pane_current_path}"
bind h split-window -hb -c "#{pane_current_path}"
bind l split-window -h -c "#{pane_current_path}"

# 小窗口最大化
bind -n M-f resize-pane -Z

# 切屏
bind -n M-h select-pane -L
bind -n M-j select-pane -D
bind -n M-k select-pane -U
bind -n M-l select-pane -R

# 切换布局
bind -n M-Space next-layout

# 插件 
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'erikw/tmux-powerline'

# Initialize TMUX plugin manager (keep this line at the very bottom of tmux.conf)
run '~/.tmux/plugins/tpm/tpm'

```

## 第三步 下载tmux plugin manager

```shell
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

然后进入tmux，下载插件

```shell
tmux
tmux source ~/.tmux.conf
```

完成后按 `prefix `+ `I`下载插件

完成


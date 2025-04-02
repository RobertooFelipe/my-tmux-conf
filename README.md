# That is my tmux config
Tmux is a terminal multiplexer that lets you run multiple programs in a single terminal window on Linux. It's a useful tool for managing remote connections, multitasking, and automating workflows. 

![image](https://github.com/user-attachments/assets/0407c513-c220-4cf9-bce1-a2f8ea45ed17)

### Install tmux
```
sudo apt update
sudo apt install tmux
```

### Now, edit ~/.tmux.conf
```
nano ~/.tmux.conf or touch ~/.tmux.conf
```
And finally, paste this code ->

```
# .tmux.conf

# Atalho para recarregar a configuração
bind r source-file ~/.tmux.conf \; display-message "RELOADING CONFIGURATION FILE…"

# STATUS LINE
set -g status on
set -g status-interval 1
set -g status-justify centre
set -g status-style fg=white,bg=black

# Destacar a janela ativa
setw -g window-status-format "  #I:#W  "
setw -g window-status-current-format "  #[fg=black,bg=colour8]#I:#W  "


# LEFT STATUS
set -g status-left-length 100
set -g status-left-style default
set -g status-left "#[fg=colour39] #(hostname -I | awk '{print $1}') \
#[fg=colour220] #(sensors | awk '/CPU/ {print $2}') \
#[fg=colour82] #(free -m | awk '/Mem/ {printf \"%.2f%%\", $3/$2 * 100}')% \
#[fg=colour208] #(cat /sys/class/power_supply/BAT0/capacity)%"

# RIGHT STATUS
set -g status-right-length 100
set -g status-right-style default
set -g status-right "#[fg=colour220] %F #[fg=colour39]%T "

# Recursos Opcionais
set -g status-left "#[fg=colour39] #(hostname -I | awk '{print $1}') \
#[fg=colour220] #(sensors | awk '/CPU/ {print $2}') \
#[fg=colour82] #(free -m | awk '/Mem/ {printf \"%.2f%%\", $3/$2 * 100}')% \
#[fg=colour202] #(top -bn1 | grep 'Cpu(s)' | awk '{print 100 - $8\"%\"}') \
#[fg=colour208] #(cat /sys/class/power_supply/BAT0/capacity)% \
#[fg=colour111] #(playerctl metadata --format '{{title}} - {{artist}}') \
#[fg=colour196] #(ps -eo %cpu,%mem,comm --sort=-%cpu | head -2 | tail -1)"

```

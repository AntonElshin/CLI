# Вывести текущую директорию пользователя. Расшифровывается Print Work Directory
pwd

# Вывести список папок и файлов в текущей директории (кроме скрытых). Расшифровывается List
ls

# Вывести список папок и файлов в текущей директории (включая скрытые)
ls -a

# Перейти в директорию. Расшифровывается Change Directory
cd <directory_name>

# Перейти в родительскую директорию
cd ..

# Сгенерировать открытый и закрытый ключ ssh
ssh-keygen

# Вывести содержимое файла из другой директории
cat <directory_name>/<file_name>

# Вывести содержимое файла из текущей директории
cat <file_name>

// общая папка для virtual box
sudo usermod -aG vboxsf antonelshin

sudo apt install bzip2

adguardvpn-cli connect -l Stockholm

adguardvpn-cli list-locations

adguardvpn-cli disconnect

curl -fsSL https://raw.githubusercontent.com/AdguardTeam/AdGuardVPNCLI/master/scripts/release/install.sh | sh -s -- -v

sudo apt update && sudo apt install tmux

tmux new -s opencode

tmux kill-server

mkdir -p ~/projects/demo-ai
cd ~/projects/demo-ai

tmux -V

Ctrl+B D detach

Ctrl+B % split вертикально

curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
source ~/.bashrc
nvm install 22
nvm use 22

sudo apt install --reinstall ubuntu-desktop gdm3 -y
sudo dpkg-reconfigure gdm3
sudo reboot

sudo timedatectl set-timezone Europe/Moscow

# Поиск родительского процесса в Linux

#!/bin/bash

# Бесконечный цикл для отслеживания процессов
while true; do
# Ищем все процессы с ключевыми словами
for pid in $(pgrep -f "cron_mailing|don-art|wget"); do
# Проверка, что процесс существует
[ -z "$pid" ] && continue

    echo "🔹 Процесс:"
    ps -o pid,ppid,user,%cpu,%mem,start,time,cmd -p $pid

    echo "🔹 Цепочка родителей:"
    current_pid=$pid
    # Проходим по всем родителям до PID=1
    while [ "$current_pid" -ne 1 ]; do
      ppid=$(ps -o ppid= -p $current_pid | tr -d ' ')
      [ -z "$ppid" ] && break
      ps -o pid,ppid,user,%cpu,%mem,start,time,cmd -p $ppid
      current_pid=$ppid
    done

    echo "----------------------"
done
sleep 1
done
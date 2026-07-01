"# kval" 
sudo apt update && apt upgrade

sudo apt install build-essential dkms linux-headers-$(uname -r)
доп образ гостевой системы -> переход на диск -> run software

sudo apt install libreoffice p7zip-full gimp printer-driver-cups-pdf -y
sudo apt install openssh-server
sudo systemctl enable --now ssh

sudo apt install git git-cola -y

sudo apt install fail2ban
sudo systemctl enable fail2ban
sudo systemctl start fail2ban
sudo systemctl status fail2ban

sudo mkdir -p /var/log/journal
sudo systemd-tmpfiles --create --prefix /var/log/journal
sudo systemctl restart systemd-journald

ssh-keygen -t rsa
ssh-copy-id testuser@localhost

sudo apt install gnome-system-tools
sudo adduser developer
sudo addgroup developers
sudo usermod -aG developers developer
sudo mkdir -p ~/project
sudo chmod 770 ~/project
sudo chown :developers ~/project

# getfacl for view permissionss

sudo ufw status
sudo ufw enable
sudo ufw allow ssh
sudo ufw allow openssh

gsettings set org.gnome.mutter experimental-features "[]" gsettings set org.gnome.desktop.interface enable-animations false

sudo apt install timeshift -y
sudo timeshift --create

apt/snap for install apps

sudo tar cvpzf /backup.tgz --exclude=/proc --exclude=/lost+found --exclude/=backup.tgz --exclude=/mnt --exclude=/sys --exclude=/web --exclude=/media /

# Что такое swappiness – короче и проще говоря это настройка, которая указывает системе, когда начинать «выгружать» неиспользуемые данные из оперативной памяти на жесткий диск.

# Что делает swappiness? (Просто короче, чтобы немного поменять настройки ядра):
Параметр имеет значение от 0 до 100
0 – Системма будет стараться избегать использование swap раздела. Она будет использовать swap только в карйнем случае, когда оператива практически полностью заполнена.

100 – Система будет активно юзать swap, даже когда на оперативе есть место

Изменить парметр swapiness
Временно (до перезагрузки):
sudo sysctl vm.swappiness=20

Постоянно (после перезагрузки):

Нужно отредачить системный файл
/ets/sysctl.conf

Или создать файл в каталоге

sudo nano /etc/sysctl.d/99-my-settings.conf

в этом файле добавить (или поменять) строку
vm.swappiness = 20
сохраняем файл (если вы не пользовались никогда nano, нажмите ctrl + O потом ctrl + X)
Выполняем:

sudo sysctl --system
Эта команда применит все настройки из файло .conf и .d

backup or dot recovery - timeshift
variant copy disk
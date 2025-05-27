# git_commands

sudo apt update
sudo apt install -y wget build-essential git autoconf subversion \
libjansson-dev libxml2-dev libncurses5-dev uuid-dev libsqlite3-dev \
libssl-dev libedit-dev
--------------------------
cd /usr/src
sudo wget http://downloads.asterisk.org/pub/telephony/asterisk/asterisk-20-current.tar.gz
sudo tar -zxvf asterisk-20-current.tar.gz
cd asterisk-20*/
-------------------------------
sudo contrib/scripts/install_prereq install
---
sudo ./configure
sudo make menuselect
----
sudo make
sudo make install
sudo make samples
sudo make config
sudo ldconfig
---
sudo systemctl start asterisk
sudo systemctl enable asterisk
---
sudo asterisk -rvvv
---

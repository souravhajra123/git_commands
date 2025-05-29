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

[6001](!)
type = wizard
transport = transport-udp
endpoint/allow = ulaw
aor/max_contacts = 1
auth/username = 6001
auth/password = 6001pass
endpoint/context = internal

[6002](!)
type = wizard
transport = transport-udp
endpoint/allow = ulaw
aor/max_contacts = 1
auth/username = 6002
auth/password = 6002pass
endpoint/context = internal

[transport-udp]
type = transport
protocol = udp
bind = 0.0.0.0
#include pjsip_wizard.conf

[internal]
exten => 6001,1,Dial(PJSIP/6001,20)
exten => 6002,1,Dial(PJSIP/6002,20)

sudo apt install -y wget build-essential libncurses-dev libssl-dev libxml2-dev uuid-dev libsqlite3-dev

cd /usr/src
sudo wget http://downloads.asterisk.org/pub/telephony/asterisk/asterisk-20-current.tar.gz
sudo tar xvfz asterisk-20-current.tar.gz
cd asterisk-20*/

sudo contrib/scripts/install_prereq install
sudo ./configure
sudo make menuselect
sudo make
sudo make install
sudo make samples
sudo make config
sudo systemctl start asterisk
sudo systemctl enable asterisk


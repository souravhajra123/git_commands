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

[6001](endpoint-basic)
type = wizard
transport = transport-udp
endpoint/context = internal
endpoint/allow = ulaw
aor/max_contacts = 1
auth/username = 6001
auth/password = 6001pass

[6002](endpoint-basic)
type = wizard
transport = transport-udp
endpoint/context = internal
endpoint/allow = ulaw
aor/max_contacts = 1
auth/username = 6002
auth/password = 6002pass

[transport-udp]
type = transport
protocol = udp
bind = 0.0.0.0
#include pjsip_wizard.conf

[internal]
exten => 6001,1,Dial(PJSIP/6001,20)
exten => 6002,1,Dial(PJSIP/6002,20)


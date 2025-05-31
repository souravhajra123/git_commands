# git_commands

Install Asterisk
=================  
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


#pjsip.conf
============
[transport-udp]
type=transport
protocol=udp
bind=0.0.0.0

[6001]
type=endpoint
context=internal
disallow=all
allow=ulaw
auth=6001-auth
aors=6001

[6001-auth]
type=auth
auth_type=userpass
username=6001
password=6001pass

[6001]
type=aor
max_contacts=1

[6002]
type=endpoint
context=internal
disallow=all
allow=ulaw
auth=6002-auth
aors=6002

[6002-auth]
type=auth
auth_type=userpass
username=6002
password=6002pass

[6002]
type=aor
max_contacts=1

#extensions.conf
=================
[internal]
exten => 6001,1,Dial(PJSIP/6001,20)
exten => 6002,1,Dial(PJSIP/6002,20)


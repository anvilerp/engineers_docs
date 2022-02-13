adduser frappe  
usermod -aG sudo frappe  
Then while still logged in as root, update the system to the latest packages…

apt-get update  
apt-get upgrade  
Now, logout as the root user and login with the new user you just created. Perform the following steps:  

export LC_ALL=C.UTF-8  

sudo apt install git libffi-dev python3-minimal build-essential python3-distutils python3-setuptools python3-pip python3-testresources libssl-dev wkhtmltopdf redis  
Nest we need to fix a potential problem in the redis config file:  

sudo nano /etc/redis/redis.conf  

When the editor is open, search for: bind 127.0.0.1 ::1 and edit our the 2 colons and the 1 so it looks like bind 127.0.0.1 then save the file.  

wget https://raw.githubusercontent.com/frappe/bench/develop/install.py  

sudo pip3 uninstall setuptools
sudo pip3 install setuptools==59.6.0
sudo pip3 install -e /home/frappe/.bench/



sudo python3 install.py --verbose --production --user frappe --mariadb-version 10.5 --frappe-branch version-13 --erpnext-branch version-13  

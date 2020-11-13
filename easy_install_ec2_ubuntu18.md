sudo apt-get update
sudo apt install python3-minimal build-essential python3-setuptools -y
# use a complex password for frappe or your user for example anvilerp
sudo adduser anvil
sudo usermod -aG sudo anvil
sudo su anvil
# go to your user directory
cd /home/anvil 
wget https://raw.githubusercontent.com/frappe/bench/develop/install.py
sudo python3 install.py --production --user anvil


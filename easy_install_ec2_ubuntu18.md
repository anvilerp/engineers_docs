sudo apt-get update <br>
sudo apt install python3-minimal build-essential python3-setuptools -y  <br>
# use a complex password for frappe or your user for example anvilerp
sudo adduser anvil  <br>
sudo usermod -aG sudo anvil  <br>
sudo su anvil  <br>
# go to your user directory
cd /home/anvil   <br>
wget https://raw.githubusercontent.com/frappe/bench/develop/install.py <br>
sudo python3 install.py --production --user anvil


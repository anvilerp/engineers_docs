sudo apt-get update <br>
sudo apt install python3-minimal build-essential python3-setuptools -y  <br>
## use a complex password for frappe or your user for example anvilerp
sudo adduser frappe  <br>
sudo usermod -aG sudo frappe  <br>
sudo su frappe  <br>
## go to your user directory
cd /home/frappe   <br>
export LC_ALL=C.UTF-8 <br>
wget https://raw.githubusercontent.com/frappe/bench/develop/install.py <br>
sudo python3 install.py --production --user frappe


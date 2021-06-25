cat /etc/fail2ban/jail.d/nginx-proxy.conf   

## block hosts trying to abuse our server as a forward proxy
[nginx-proxy]  
enabled = true  
filter = nginx-proxy  
logpath = /var/log/nginx/access.log  
action = iptables-multiport[name=NoNginxProxy, port="http,https"]  
maxretry = 6  
bantime  = 600  
findtime = 600  



## how to check if there is a band ip ? 
sudo fail2ban-client status nginx-proxy

## how to uban ip address ?
sudo fail2ban-client set  nginx-proxy unbanip IPADDRESS

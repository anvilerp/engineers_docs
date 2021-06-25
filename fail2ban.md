ERPNext has two type of jails :
1- sshd:
cat /etc/fail2ban/jail.conf 

To use more aggressive sshd modes set filter parameter "mode" in jail.local:
normal (default), ddos, extra or aggressive (combines all).

2- nginx-proxy      
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

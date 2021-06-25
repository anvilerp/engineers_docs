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

## fitler nginx-proxy explained ?
cat /etc/fail2ban/filter.d/nginx-proxy.conf
<pre># Block IPs trying to use server as proxy.
[Definition]
failregex = &lt;HOST&gt;.*\&quot; 400
	&lt;HOST&gt;.*&quot;[A-Z]* /(cms|muieblackcat|db|cpcommerce|cgi-bin|wp-login|joomla|awstatstotals|wp-content|wp-includes|pma|phpmyadmin|myadmin|mysql|mysqladmin|sqladmin|mypma|admin|xampp|mysqldb|pmadb|phpmyadmin1|phpmyadmin2).*&quot; 4[\d][\d]
	&lt;HOST&gt;.*&quot;.*supports_implicit_sdk_logging.*&quot; 4[\d][\d]
	&lt;HOST&gt;.*&quot;.*activities?advertiser_tracking_enabled.*&quot; 4[\d][\d]
	&lt;HOST&gt;.*&quot;.*/picture?type=normal.*&quot; 4[\d][\d]
	&lt;HOST&gt;.*&quot;.*/announce.php?info_hash=.*&quot; 4[\d][\d]

ignoreregex =</pre>

## what 400 stands for ?
The HyperText Transfer Protocol (HTTP) 400 Bad Request response status code indicates that the server cannot or will not process the request due to something that is perceived to be a client error (e.g., malformed request syntax, invalid request message framing, or deceptive request routing).  


## how to check if there is a band ip ? 
sudo fail2ban-client status nginx-proxy

## how to uban ip address ?
sudo fail2ban-client set  nginx-proxy unbanip IPADDRESS

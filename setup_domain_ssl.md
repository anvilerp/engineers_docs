## for domain you need to activate dns_multitenant
bench config dns_multitenant on

## you need also to create a site with your domain name you want to add ssl <br> in fresh installation drop site1.local and create new one with your domain name 
bench drop-site site1.local 
<br>
bench new-site demo.anvilerp.com 
<br>
bench install-app erpnext 

## ssl for ubuntu switch to ubuntu user 
sudo su ubuntu
## Stop the nginx service:
sudo service nginx stop
## Install cerbot: 
sudo snap install --classic certbot
## Generate cert: 
sudo certbot certonly --standalone
<br>
 cd frappe-bench/sites/{{ site_name }}
## Add the following two lines to your site_config.json

"ssl_certificate": "/etc/letsencrypt/live/example.com/fullchain.pem",<br>
"ssl_certificate_key": "/etc/letsencrypt/live/example.com/privkey.pem"


## Re generate nginx config

bench setup nginx

## Start nginx

sudo service nginx start

## Reload nginx

sudo service nginx reload


## Auto renewal (experimental) 
## Login as root or a user with superuser privileges, run 
crontab -e 
## and enter:
# renew letsencrypt certificates on 1st monday of every month and get an email if it gets executed
MAILTO="mail@example.com"
0 0 1-7 * * [ "$(date '+\%a')" = "Mon" ] && sudo service nginx stop && /opt/certbot-auto renew && sudo service nginx start



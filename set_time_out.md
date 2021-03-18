## How to increase nginx time out , you can find this in nginx config as 
```		proxy_read_timeout 6000;
```

bench config http_timeout {time} #time is number in seconds .
bench setup supervisor
bench setup nginx
supervisorctl reload
sudo service nginx reload


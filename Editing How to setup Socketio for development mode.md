1. Set DNS multi-tenant off
```
bench config dns_multitenant off
```
2. remove `sites/currentsite.txt` file
```
rm sites/currentsite.txt
```
3. add site names to /etc/hosts
```
revant@revant-laptop:~/frappe-bench$ cat /etc/hosts
127.0.0.1        localhost
127.0.0.1        test_frappe
127.0.0.1        test_api
127.0.1.1        revant-laptop
```
4. `bench start`
5. Access site from browser e.g. `http://test_api:8000`
6. from console try `publish_realtime()`
```
revant@revant-laptop:~/frappe-bench$ bench --site test_api console
Python 2.7.14 (default, Sep 23 2017, 22:06:14) 
Type "copyright", "credits" or "license" for more information.

IPython 5.5.0 -- An enhanced Interactive Python.
?         -> Introduction and overview of IPython's features.
%quickref -> Quick reference.
help      -> Python's own help system.
object?   -> Details about 'object', use 'object??' for extra details.

In [1]: frappe.publish_realtime(event='msgprint', message='Hello Socketio', user='Administrator')
```

![socketio-develop](https://discuss.frappe.io/uploads/default/original/1X/6c1609020d21d7c0f8a345464d4129ea8368c094.png)

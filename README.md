This is the playbook to configure the datadog to moniter the nginx server.
1.Run the playbook to install datadog .
2.Run the playbook to configure the nginx

Make sure that: 
 
  We have to Enable the mod_status on your Nginx server, 
  
  HttpStubStatusModule is the module that enable the module to read all the metrics, so, you need to know if it is enabled  or not. 

You can check this out using this command:
nginx -V 2>&1 | sed 's,--,n--,g' | grep stub_status</br>

If it is compiled, you should see something like this:</br></br>
--with-http_stub_status_module 

It is enabled by default on most distributions so, in order to enable Nginx status page the next step is editing nginx.conf. Find your nginx.conf file, it may be at one of this locations.
/usr/local/nagios/etc/nginx.conf</br>
/etc/nginx/nginx.conf</br>
/etc/nginx/sites-enabled/default</br>

Edit the configuration file and add the below block of code.
inside the servers block add below code:

location /nginx_status {</br>
stub_status on;</br>
access_log off;</br>
allow 127.0.0.1;</br>
deny all;</br>
}</br>

# nginxCaching
nginx caching server for ubuntu 18.04


# How does it work?

You install 2 packages.
`bind9` a dns server and `nginx` a webserver/proxyserver
If bind gets a request from a windows update domain it will send the request to the proxy server.
Then the server will cache the requested file and send it back to the client.
For this to work you need to set the dns server on your dhcp server to the ip of your caching server.

# How can i install it?

First install `nginx` and `bind9` on your fresh ubuntu 18.04/20.04 vm.
Then remove `/etc/bind/named.conf` and `/etc/nginx/nginx.conf`
After that download the repo and copy over the corrosponding files.

Then create the folder where the cached files are going to be stored.
`mkdir /var/cache/nginx` and `mkdir /var/cache/nginx/cache`

At last change the ipadres in the `/etc/bind/named.conf` file to ipadres you've given your vm.
Then restart all the services with `systemctl restart nginx` and `systemctl restart bind9`.

Check if they are running correctly with `systemctl status nginx` and `systemctl status bind9`.
And if you you've configured your DNS caching server correctly.
If not please check if you followed the manual correctly.

Now set change the default DNS server on your DHCP server/Home router and your done!
 

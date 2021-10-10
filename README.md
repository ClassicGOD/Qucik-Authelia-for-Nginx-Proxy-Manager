# Quick and easy Authelia configuration for Nginx Proxy Manager

All files based on Authelia documentation: https://www.authelia.com/docs/ please refer to it in case of any issues. 
Tutorial provided as is without any warranty.

Tutorial assumes that you are running Nginx Proxy Manager container from jc21/nginx-proxy-manager (but with some modifications will probably work with different configurations) and have few hosts defined. 

1. Create a directory or a volume for authelia configuration.
2. Copy example configuration.yml and users_database.yml from authelia/
3. Edit configuration.yml - I annotated what needs changing in the file. 
4. Edit users_database.yml - I annotated what needs changing in the file. 
5. Spin up an Authelia container - this is not a Docker tutorial and your settings will depend on your Docker configuration so I won’t cover this here. Just remember to map your configuration directory/volume to /config inside of the container.
6. In directory or volume with your Nginx Proxy Manager configuration create ‘authelia’ folder 
7. Copy auth.conf, authelia.conf and proxy.conf files from nginx_proxy_manager/authelia/ into it
8. Edit auth.conf - change last line to match your auth endpoint
9. If your Docker networks are set up in a way that allows the Nginx Proxy Manager container to locate the Authelia container by a name ‘authelia’ you can skip this step. If not, edit the first line of authelia.conf to point to your Authelia container. 
10. In Nginx Proxy Manager create authentication endpoint (for example auth.example.com) with Block Common Exploits and all SSL options enabled and paste nginx_proxy_manager/auth_endpoint contents into it adjusting the annotated line if needed.
11. Check if you can access your auth endpoint and log in with your password.
12. For every host you want to protect, paste the contents of nginx_proxy_manager/protected_endpoint into the Advanced tab in host configuration.

That should be it. Just remember, Authelia remembers your session so don’t be surprised if you don’t see a login page on every endpoint. just go to your auth.example.com equivalent and click LOGOUT to kill the session for testing. 

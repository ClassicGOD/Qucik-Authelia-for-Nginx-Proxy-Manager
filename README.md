# Quick and easy Authelia configuration for Nginx Proxy Manager

All files based on Authelia documentation: https://www.authelia.com/docs/ please refer to it in case of any issues. 
Tutorial provided as is without any warranty.

Tutorial assumes that you are running Nginx Proxy Manager container from jc21/nginx-proxy-manager (but with some modifications will probably work with different configurations) and have few hosts defined. 

1. Create a directory or a volume for authelia configuration.
2. Copy example configuration.yml and users_database.yml from authelia/
3. Edit configuration.yml - I annotated what needs changing in the file. 
4. Edit users_database.yml - I annotated what needs changing in the file. 
5. In directory or volume with your Nginx Proxy Manager configuration create ‘authelia’ folder 
6. Copy auth.conf,authelia.conf and proxy.conf files from nginx_proxy_manager/authelia/ into it
7. Edit auth.conf - change last line to match your auth endpoint
8. If your Docker networks are set up in a way that allows the Nginx Proxy Manager container to locate the Authelia container by a name ‘authelia’ you can skip this step. If not, edit the first line of authelia.conf to point to your Authelia container. 

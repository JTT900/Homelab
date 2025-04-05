# Homelab
Current homelab stacks &amp; templates. * *under constuction* *

![Image](https://github.com/user-attachments/assets/68152526-87da-42fc-990e-55f42e004993)


## Dashboard
**Glance** - https://github.com/glanceapp/glance

Startpage shows overview and stats for the Pi-Hole DNS Server, the Raspberry Pi itself and connection to running services.

Home is a page for media updates through RSS feeds to news-sites, youtube, subreddits etc.


## Proxy Management

**NginxProxyManager** - https://github.com/NginxProxyManager/nginx-proxy-manager

Used to generate SSL certificates via Let's Encrypt 

## DNS Management & Ad blocking
**Pi-hole** - https://github.com/pi-hole

Set up as a DNS-server and network wide ad blocker with integrated block-lists. Local DNS records are added to forward the 
URL of local services to Nginx Proxy Manager, ensuring SSL certificates to these sites. 

## Docker compose Management
**dockge** - https://github.com/louislam/dockge

An easy to use web hosted service for managing and updating the services running through Docker. An agent is set up on my other server
to have the ability to change everything from one site. 


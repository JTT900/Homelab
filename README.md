# Homelab
Current homelab stacks &amp; templates. * *under constuction* *

![Image](https://github.com/user-attachments/assets/68152526-87da-42fc-990e-55f42e004993)

## Hardware
Raspberry Pi 4 4gb running Raspbian OS\
Surface Pro 4 i7/16gb running Ubuntu 24.04.02 LTS\
Ubiquity Unifi Dream Router 7\
TP-Link SG105PE 4-port PoE+ \

## Network Topology


## Dashboard
**Glance** - https://github.com/glanceapp/glance

Startpage shows overview and stats for the Pi-Hole DNS Server, the Raspberry Pi itself and connection to running services.

Home is a page for media updates through RSS feeds to news-sites, youtube, subreddits etc.

<details>
<summary><strong>Preview Docker compose for Glance configuration</strong></summary>
<br>
  
```yaml
  - name: Startpage
    width: slim
    hide-desktop-navigation: false
    center-vertically: true
    columns:

      - size: small
        widgets:
          - type: dns-stats
            service: pihole-v6
            url: http://${SERVER_IP}:${PIHOLE_PORT}
            password: ${PIHOLE_PASSWORD}
            hour-format: 24h

          - type: server-stats
            servers:
              - type: local
                name: Raspberry Pi

      - size: full
        widgets:
          - type: search
            autofocus: true
            search-engine: https://kagi.com/search?q={QUERY}
            new-tab: true
            bangs:
              - title: YouTube
                shortcut: "!yt"
                url: https://www.youtube.com/results?search_query={QUERY}
              - title: Github
                shortcut: "!gh"
                url: https://github.com/search?q={QUERY}&type=repositories

          - type: monitor
            cache: 1m
            title: Services
            sites:
              - title: Pi-Hole
                url: https://pihole${SERVER_URL}/admin/login
                check-url: http://${SERVER_IP}:${PIHOLE_PORT}/admin/
                icon: di:pi-hole

              - title: NGINX Proxy Manager
                url: https://npm${SERVER_URL}/
                check-url: http://${SERVER_IP}:${NPM_PORT}
                icon: di:nginx

              - title: Actual Budget
                url: https://actual${SERVER_URL}/
                check-url: http://${SERVER_IP}:${ACTUAL_BUDGET_PORT}
                icon: di:actual-budget
                
```
</details>
<br>


## Proxy Management

**NginxProxyManager** - https://github.com/NginxProxyManager/nginx-proxy-manager

Used to generate SSL certificates via Let's Encrypt 

## DNS Management & Ad blocking
**Pi-hole** - https://github.com/pi-hole

Set up as a DNS-server and network wide ad blocker with integrated block-lists. Local DNS records are added to forward the 
URL of local services to Nginx Proxy Manager, ensuring SSL certificates to these sites. 

## Docker compose Management
**dockge** - https://github.com/louislam/dockge

An easy to use web hosted service for managing and updating the Docker Compose files within /opt/stacks folder. An agent is set up on my other server
to have the ability to manage both servers files from the same URL instance. 



## Future plans

Ansible roles - Explore ansible and premade roles for a more secure and consistent strategy when configuring current and new servers. 
Kubernetes - Switch from docker to kubernetes for reliability and a self healing setup. 




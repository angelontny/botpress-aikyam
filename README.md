# botpress-aikyam
Botpress V12 OSS deployement at Aikyam

## Guide I'm following
[Botpress AWS deployment](https://v12.botpress.com/going-to-production/deploy/aws)

## TO-DO
- [x] Create an EC2 instance ( Ubuntu 18.04 ) Installed 22.04 as the other options weren't feasible
- [ ] Install Botpress ( configure a systemd unit ) Installting version: v12_30_6
- [x] Configure TLS using certbot [Followed this guide](https://certbot.eff.org/instructions?ws=nginx&os=ubuntufocal)
- [x] Configure Nginx Reverse Proxy
- [ ] Install and configure a postgres instance [github link to dockerfile](https://github.com/botpress/v12/blob/b9589a82f208efd4a14377abde86e974566035a0/examples/docker-compose/docker-compose-community-nginx-https.yaml)
- [ ] Configure botpress config file to include external URL
- [ ] Use pm2 for resilience
- [ ] Install dokku to manage the instance ( recommended by botpress )
- [ ] Configure PostgresSQL server using dokku
- [ ] Write a doc for configuring a telegram bot ( or link to the botpress guide )

## Server Specs
- Documentation recommends 2Gb for botpress and another 4Gb for the PostgresSQL instance.
- Current setup: 2vCPUs ( x86 ), 8Gb memory, 40Gb disk

## To figure Out
- [x] What do i need to cache using nginx? ( all the static contents that don't change across users)
- [x] Why configure a different repository for certbot? ( not required )
- [x] The above results in this error ( use snap )
    ```
    PPA publishes dbgsym, you may need to include 'main/debug' component
    Repository: 'deb https://ppa.launchpadcontent.net/certbot/certbot/ubuntu/ jammy main'
    Description:
    The PPA has been DEPRECATED.
    ```
- [x] The provided configuration results in the following error ( fix: remove the http directive from the sites-enabled file )
    [Stack Overflow](https://stackoverflow.com/questions/43643829/nginx-emerg-http-directive-is-not-allowed-here-in-etc-nginx-sites-enabled)
    Hence, I changed the /etc/nginx/nginx.conf file to include all the security features
    ```
    [emerg] 1591#1591: "http" directive is not allowed here in /etc/nginx/sites-enabled/botpress:1
    ```
- [ ] Why install redis? ( need to check the github repo )

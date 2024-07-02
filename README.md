# botpress-aikyam
Botpress V12 OSS deployement at Aikyam

## Guide I'm following
[Botpress AWS deployment](https://v12.botpress.com/going-to-production/deploy/aws)

## TO-DO
- [x] Create an EC2 instance ( Ubuntu 18.04 ) Installed 22.04 as the other options weren't feasible
- [ ] Install Botpress ( configure a systemd unit ) Installting version: v12_30_6
- [ ] Configure TLS using certbot [Followed this guide](https://certbot.eff.org/instructions?ws=nginx&os=ubuntufocal)
- [ ] Configure Nginx Reverse Proxy
- [ ] Use pm2 for resilience
- [ ] Install dokku to manage the instance ( recommended by botpress )
- [ ] Configure PostgresSQL server using dokku

## Server Specs
- Documentation recommends 2Gb for botpress and another 4Gb for the PostgresSQL instance.
- Current setup: 2vCPUs ( x86 ), 8Gb memory, 40Gb disk

## To figure Out
- [ ] What do i need to cache using nginx?
- [x] Why configure a different repository for certbot? ( not required )
- [x] The above results in this error ( use snap )
    ```
    PPA publishes dbgsym, you may need to include 'main/debug' component
    Repository: 'deb https://ppa.launchpadcontent.net/certbot/certbot/ubuntu/ jammy main'
    Description:
    The PPA has been DEPRECATED.
    ```
- [ ] The provided configuration results in the following error ( fix: remove the http directive from the sites-enabled file )
    [Stack Overflow](https://stackoverflow.com/questions/43643829/nginx-emerg-http-directive-is-not-allowed-here-in-etc-nginx-sites-enabled)
    Hence, I changed the /etc/nginx/nginx.conf file to include all the security features
    ```
    [emerg] 1591#1591: "http" directive is not allowed here in /etc/nginx/sites-enabled/botpress:1
    ```

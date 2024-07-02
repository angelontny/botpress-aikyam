# botpress-aikyam
Botpress V12 OSS deployement at Aikyam

# Guide I'm following
[Botpress AWS deployment](https://v12.botpress.com/going-to-production/deploy/aws)

# TO-DO
- [ ] Create an EC2 instance ( Ubuntu 18.04 )
- [ ] Install Botpress ( configure a systemd unit )
- [ ] Configure TLS using certbot
- [ ] Configure Nginx Reverse Proxy
- [ ] Use pm2 for resilience
- [ ] Install dokku to manage the instance ( recommended by botpress )
- [ ] Configure PostgresSQL server using dokku

# Server Specs
- Documentation recommends 2Gb for botpress and another 4Gb for the PostgresSQL instance.

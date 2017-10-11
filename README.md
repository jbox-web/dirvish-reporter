# Dirvish Reporter

[![GitHub license](https://img.shields.io/github/license/jbox-web/dirvish-reporter.svg)](https://github.com/jbox-web/dirvish-reporter/blob/master/LICENSE)

Dirvish Reporter is a pair or Ruby scripts to generate nice HTML email reports for [Dirvish Backup](http://www.dirvish.org/).

## Installation

You must have at least Ruby 2.x installed on your server with `mail` gem.

To install Ruby and the `mail` gem :

```sh
root@example:~# apt-get install ruby
root@example:~# gem install mail
```

Then copy the content of the `scripts` directory of this repository into `/etc/dirvish/scripts` and configure your vaults to call the [`backup-end` script](http://www.dirvish.org/dirvish.conf.5.html) :

```yaml
post-server: /etc/dirvish/scripts/backup-end
```

Finally change the Dirvish cron task to call our report script :

```sh
# /etc/cron.d/dirvish: crontab fragment for dirvish

# run every night
00 07 * * *     root  /etc/dirvish/dirvish-cronjob 2>&1 | /etc/dirvish/scripts/reporter
```

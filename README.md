# ping-sm
Run this script periodically as a cron job. It will check if [Migros Sanalmarket](https://www.migros.com.tr/) is available for delivery to your neighborhood in the next 4 days.


## How it works
 * Sends you a warning and exits if the cookies are invalid.
 * Exits if delivery isn't available.
 * Sends you a notification if delivery is available.

#### Notifications
You need a [Mailgun domain](https://documentation.mailgun.com/en/latest/api-domains.html) or a [Telegram bot](https://core.telegram.org/bots) in order to enable notifications. You'll have to rely on logs otherwise.

## Installing dependencies
```sh
pip3 install -r requirements.txt
```

## Configuraiton
 1. Copy `.env.example` and name the new file as `.env`
 2. Set each variable in `.env` with your own values. Find out your `SESSION` & `remember-me` cookies using the developer tools of your favorite browser

## Launching
```sh
# launch manually
python3 ./__main__.py

# launch manually with notification emails enabled
python3 ./__main__.py --email

# launch manually with telegram messages enabled
python3 ./__main__.py --telegram

# example cron job
* * * * * /usr/bin/python3 /home/utku/git/ping-sm/__main__.py --email 2>&1 >> /home/utku/git/ping-sm/log.log
```

# bottyTheGoodBot

## Use case
I need a program to always run in my remote server. In case if that program crashes and I am not in front of my screen, this script helps me to restart the program when it stops working. When restart/program failure occurs, I want to be notified if the restart is successful.

This tutorial assumes that you are using Ubuntu. 

## Setting up SMTP Server
Adapted from this [tutorial](https://linuxhint.com/bash_script_send_email/)

Guide:
1. Ensure that you have an email set up to send your notification from
1. Install ssmtp package with `sudo apt install ssmtp`
2. Install mailutils package with `sudo apt install mailutils`
3. Edit your `/etc/ssmtp/ssmtp.conf` file by adding the following:
   `UseSTARTTLS=YES`
   `UseTLS=YES`
   `root=username@gmail.com`
   `mailhub=smtp.gmail.com:587`
   `AuthUser=username@gmail.com`
   `AuthPass=password`

## Modifying botty script
Since I have my program running in a screen session, the script assumes you have screen installed in your linux server. If you haven't, run `sudo apt-get install screen` in your terminal.

Guide:
1. Change all occurences of `./infinityloop` to the program you want to run.
2. Update your mail title, email account to receive notification from, and the mail message.

## Setting up cron
Cron will schedule our script to run at specified time.

Guide:
1. In your command line, type `crontab -e` to edit your crontab file. 
2. Use [crontab.guru](https://crontab.guru/) as guide to create your schedule expression.

## Final words
Let me know if any improvement can be made to the script and have fun with baby botty! :)

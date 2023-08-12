## Web stack debugging #3 incident report
By Thando Siluma

## Issue Summary
From Friday 07:32:16 GMT to 07:11:52 GMT on 24 March 2017, when running the Apache it returns 500 internal Server Error. When Users try to log in Apache does not receive the login or the logs do not provide enough information. The root cause of this outage is that we had bad PHP extensions to PHP in the WordPress file ‘wp-settings.php’.

## Timeline (Greenwich Mean Time)
* 07:30:00 The Command line is being entered
* 07:32:16 Outage begins
* 07:40:17 Pagers alerted teams
* 07:50:28 Used strace to find out what causes the Apache
* 07:55:40 Successful finding the problem and automating it using Puppet
* 07:10:20 Server restart again
* 07:11:52 The Server returns no errors

## Root Causes
At 07:30:00 GMT the user logged into the server using curl. The server returns an internal server error. Checked running processes and found that it was running on the LAMP stack. Login again to find out that it was returning the HTTP/1.0 500 Internal Server Error. As the server was trying to log in it couldn’t pick up what caused the error. So at 07:32:16 GMT, the Outage began.

## Resolution and Recover
Looked at the site to see how the settings of the sites are. Determined that the web server was serving content where it was supposed to serve. Then ran strace on the tmux to find out that what caused the error was incorrect PHP extensions. Then I ran the command 'sed -i s/phpp/php/g /var/www/html/wp-settings.php' to fix the error. Then I used Puppet to automate the changes that have been made. Then curl the server again at 07:11:52 GMT, and it returned ‘200 OK’.

## Corrective and preventative measures
This outage was a web server error that occurred due to a software break to the server's PHP extensions. Next time to avoid such an outage we need to regularly automate our work and ensure that all extensions are tested and automated. We can also use monitors to alert us if there are any possible software breaks.

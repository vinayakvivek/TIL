# Execute a script periodically using cron
> 25/04/2017

To keep track of the sale price of a particular item in Amazon, I wrote a python script for it.
But obviously one cannot execute this in regular intervals. So after some searching, I found out about this `cronjobs`.

(http://www.unixgeeks.org/security/newbie/unix/cron-1.html) <- This is a good read about cron.

## Steps to create a cronjob
- execute the command `crontab -e` in terminal.
- this opens up crontab file in your editor (vim, nano, ..).
- cron file will contain lines which looks similar to `00 01 * * * user /home/user/user-script.sh`.
- to execute a script at every 10 mins, add the following line to the cron file
```bash
*/10 * * * * <path_to_script>
```

--------------------------------------

Note : environment variables for cron are different. So you might need to change `PATH` variable at the start of the script.
```bash
PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin'
```

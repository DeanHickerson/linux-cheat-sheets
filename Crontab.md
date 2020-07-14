# Cron Jobs in Unix Based Systems

1. Open Crontab in Linux:
 - To setup in the context of the current User: `crontab -e`
 - To setup in the context of System: `sudo crontab -e`
2. Adding new Tasks:
 - To add a new task, simply add a new line with the cron syntax followed by the command that you want to run.
 - `minute(0-59) hour(0-23) day(1-31) month(1-12) weekday(0-6) command`
 - `0 0 * * * /myCommand` - would run "myCommand" an every day at 12:00AM
  - Minutes, Hours and Weekdays are zero (0) indexed.
 - `*` indicate any/every of that time/date
 - Use comma-separated values to specify multiple times.
 - Example: `0,14,29,44 * * * * /usr/bin/example` - would run every 15mins.

3. A good resource for checking cron syntax: https://crontab.guru/

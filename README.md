# Linux-Archieving-Logging-Data
This assignment overviews Linux backing up and recovering data while preserving integrity and availability.

I continued  learning system administration fundamentals by working in Linux environments to back up and recover data, preserving integrity and availability.


The Scenario for this assignment was as follows:

For this assignment, you will play the role of a security analyst for Credico Inc., a financial institution that offers checking, savings, and investment banking services.

•	The company collects, processes, and maintains a large database of private financial information for both consumer and business accounts.

•	The data is maintained on a local server.

•	The company must comply with the Federal Trade Commission's Gramm-Leach-Bliley Act (GLBA), which requires that financial institutions explain their information-sharing practices to their customers and protect sensitive data.


In an effort to mitigate network attacks and meet federal compliance, Credico Inc. developed an efficient log management program that performs:

•	Log size management using logrotate.

•	Log auditing with auditd to track events, record the events, detect abuse or unauthorized activity, and create custom reports.


These tools, in addition to archives, backups, scripting, and task automation, contribute to a fully comprehensive log management system.

You will expand and enhance this log management system by learning new tools, adding advanced features, and researching additional concepts.


Steps used to complete task:

1.	I navigated to the ~/Projects directory where I downloaded TarDocs.tar archive file.
2.	I extracted TarDocs.tar.
3.	I created a tar archive called “Javaless_Docs.tar” that excludes the Java directory from the newly extracted TarDocs/Document/ directory.
4.	I verified that this new “Javaless_Docs.tar” archive does not contain the Java subdirectory by using tar to list the contents of “Javaless_Docs.tar” and then piping grep to search for Java.
5.	I used sudo access to create an incremental archive called “logs_backup.tar.gz” that contained only changed files by examining the “snapshot.file” for the /var/log directory.
6.	I created a cron job for backing up “/var/log/auth.log” file to the file “/auth_backup.tgz” every Wednesday at 6 a.m. 
7.	I used brace expansion to create the following directories:
    - ~/backups/freemem, ~/backups/diskuse, ~/backups/openlist and ~/backups/freedisk
8. I edit the “system.sh” script file so that it that does the following:

    •  Prints the amount of free memory on the system and saves it to ~/backups/freemem/free_mem.txt.
    
    •  Prints disk usage and saves it to ~/backups/diskuse/disk_usage.txt.
    
    •  Lists all open files and saves it to ~/backups/openlist/open_list.txt.
    
    •  Prints file system disk space statistics and saves it to ~/backups/freedisk/free_disk.txt.
    
9. I saved the file and modified the “system.sh” file permissions so that it’s executable.
10.	I tested the script with sudo ./system.sh.
11.	I automated the script for  “system.sh” by adding it to the weekly system-wide cron directory.
12.	I ran sudo nano /etc/logrotate.conf to edit the “logrotate config” file.
13.	I configure a log rotation scheme that backs up authentication messages to the /var/log/auth.log directory so that it rotates weekly, rotates only the seven most recent logs, doesn’t rotate empty logs, delays compression and skips error messages for missing logs and continues to next log.
14.	I used systemctl to verify that the auditd service was active and running.
15.	I ran sudo nano /etc/audit/auditd.conf to edit the “auditd config” file using the number of rotated logs as seven and the maximum log file size as 35.
16.	I ran sudo nano /etc/audit/rules.d/audit.rules to edit the rules for auditd. Creating rules that watch the following paths:
	
    •  For /etc/shadow, I set wra for the permissions to monitor and set the keyname for this rule to hashpass_audit.
    
    •  For /etc/passwd, I set wra for the permissions to monitor and set the keyname for this rule to userpass_audit.
    
    •  For /var/log/auth.log, I set wra for the permissions to monitor and set the keyname for this rule to authlog_audit.
    
17. I restarted the auditd daemon
18.	I used sudo to produce an audit report that returns results for all user authentications.
19.	I used auditctl to add another rule that watches the /var/log/cron directory.





I conducted an analysis of suspicious activity on the server and discovered traces of malicious actions. I started by examining the logs (auth.log), where I found that dokuwiki had been installed with elevated privileges. Then, I discovered that a new user, it-admin, was created and later granted sudo privileges.

By checking .bash_history, I found that it-admin had downloaded a script called bomb.sh using curl, edited it, and then deleted it. To understand what happened next, I examined the crontab and found that every day at 08:00 AM, /bin/os-update.sh was executed — which was actually the renamed bomb.sh.

After inspecting the file’s contents, it became clear that it contained malicious code. To prevent execution, I disabled the script, changed its permissions, and removed the entry from crontab. As a result, I successfully neutralized the logic bomb left behind by the former employee.








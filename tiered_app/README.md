## Task: Tiered App
Work with your team to deploy *Question2Answer* as a three-tiered web app,
with a protected database *back-end* in your **secure** zone,
users web browser *clients* in the **outside** zone,
and the web server *middleware* in your **dmz**.
Then clone your web server, so that you have two middleware servers,
and deploy a load balancer in the **dmz** to leverage both web servers.
The web server redundancy will improve your app's availability,
and with both web servers functioning properly,
it should also scale your web app to be able to handle more simultaneous clients.

## Tools
- Use either <a href="https://mariadb.org/" target="_blank" rel="noopener">MariaDB</a> or <a href="https://www.mysql.com/" target="_blank" rel="noopener">MySQL</a> as the back-end database. Very likely,
this will be easy to install using your Linux distribution's package manager.
- Use either <a href="https://httpd.apache.org/" target="_blank" rel="noopener">Apache HTTP Server</a> or <a href="https://nginx.org/" target="_blank" rel="noopener">nginx</a> as your web server. Very likely,
these will be easy to install using your Linux distribution's package manager.
- Download the latest version of <a href="https://www.question2answer.org/" target="_blank" rel="noopener">Question2Answer</a> to your **dmz** web server.

## Requirements
Phase I:
- Install your database server on your **secure** Linux host.
- Find, read, and follow the Question2Answer installation instructions.
(Those instructions anticipate that the database and web servers reside on the same machine,
so be careful to adjust them so that you implement your tiered app archecture instead.)
  - You'll certainly need to configure new firewall policies on your secure-facing firewall to allow
the **dmz** web middleware to communicate with the **secure** database service.
  - Notice that there are some additional pre-requisites that aren't listed above,
such as a <a href="https://www.php.net/" target="_blank" rel="noopener">PHP</a> engine,
that you may need to find and install.
  - For troubleshooting, it may be helpful to install a database client on your **dmz** web host,
and use that to test connectivity through the secure-facing firewall to the **secure** database host.
- After you finish installing Question2Answer and have set up the app's administrator account,
you should be ready to make the app accessible to clients out on the **outside** (untrusted) Internet zone.
  - Just in case, before you allow untrusted clients to connect,
please install a copy of the University's managed security sensor software on your **dmz** web host.
  - Configure your Internet-facing firewall
with static NAT (IP address translation) and security policies (access rules)
that allow untrusted Internet clients connect to your web application via (unencrypted) HTTP protocol.
  - Verify that it works by asking and answering a question;
this will begin to populate your database with application data.

Phase II:
- Clone your web server. Configure this second instance of your web server with its own fixed IP address
in the same subnet as your original web server.
If necessary, re-install the University's security sensor software on the clone.
Change your Internet-facing firewall's NAT configuration
to direct **outside** clients to the clone,
and verify that the web app still works correctly with this new web server.
- Deploy a new load balancing service in the **dmz**, also with its own fixed IP address in the same
subnet as your web servers. Configure the load balancer to be able to direct clients' Question2Answer web
requests to whichever of the two webservers is running and not down.
- Change your Internet-facing firewall's NAT configuration
to direct **outside** clients to the load balancer. Verify that the web app still works correctly
when the original server is running but the clone is stopped,
when the clone is running and the original is stopped,
and when both web servers are running.

## Deliverable
Upload an illustrated tutorial, in which you explain what your team did and how you accomplished it.

- Your document should be clear enough that one of your peers would be able to follow your instructions and accomplish the same tasks.
- Identify any difficult or challenging parts of the project, and clearly explain how you diagnosed and overcame your obstacles.
- Include a few cropped screen captures where appropriate. Also upload your updated and annotated network diagram.

## Scoring Rubric
- If your tutorial satisfies every requirement outlined above, you will earn a passing score (one point).
- If your tutorial does not satisfy any one of the above requirements, you will earn no points. Your team must then address any deficiencies and re-upload corrected documents until you earn the passing score.

## Examples and Hints
Examples:

(Phase I)
- <a href="https://byui-cit.atlassian.net/wiki/spaces/CDI/pages/38273057" target="_blank" ref="noopener">Example deployment of MariaDB database server</a>
- <a href="https://byui-cit.atlassian.net/wiki/spaces/CDI/pages/38567937" target="_blank" ref="noopener">Example deployment of Apache web server and PHP</a>
- <a href="https://byui-cit.atlassian.net/wiki/spaces/CDI/pages/42205185" target="_blank" ref="noopener">Example deployment of Question2Answer</a>

(Phase II)
- Coming soon...

Hints:
- All components for this app can be successfully installed and operated on either Linux or Windows servers;
the hints below assume installation on Linux.
- After your database first starts up, it's considered best practice to execute
the <a href="https://mariadb.com/kb/en/mysql_secure_installation/" target="_blank" rel="noopener">mysql_secure_installation</a> script.
- Record your MariaDB/MySQL root password, your database name, and your database user and password,
and keep them in a secure place shared with your team partner(s)
so that each of you can find and use them.
- Here's an example SQL command for MariaDB that creates a new user
named Lieutenant, with password u_will_Never_guess,
and gives that user privileges to manipulate the tables in the database named "QUE2ANS":
`GRANT ALL PRIVILEGES ON QUE2ANS.* TO "Lieutenant"@"localhost" IDENTIFIED BY "u_will_Never_guess";`
  - This command will only let the user connect from the database server.
To allow connections from a **dmz** web host, re-use the same command syntax,
but replace `"localhost"` with the IP address of that host as a double-quoted string, such as `"10.9.8.7"`.
  - The same command probably won't work in MySQL,
but if you chose to use that for your database software,
a few web searches should help you discover what you need to do.
  - To verify that your database and user is configured correctly, the SQL commands
`SHOW DATABASES;` and `SELECT User,Host,Password FROM mysql.user;` might help you.
- Question2Answer requires the MySQLi extension to your web server's PHP engine.
However, in most Linux distributions, this extension has been deprecated and superseded
by an extension named MySQLnd.
(The "nd" stands for "native driver," which was a marked improvement over the older MySQLi code.)
When you get to that part of the setup, try to find the extension
using shell commands such as `apt search php-mysql` (for Debian/Ubuntu distros)
or `dnf search php-mysql` (for RedHat-style distros).
  - After PHP and the MySQL interface extension are installed, here's a nice way to test it:
    - Create a text file named `470.php` (the name doesn't matter, choose whatever filename you like
as long as it ends with a .php extension) in your web server's *DocumentRoot* folder (usually `/var/www/html`)
and put this one line of code in that file: `<?php phpinfo(); ?>`
Then restart your web server, and use a web browser to visit `http://localhost/470.php` (or whatever
name you chose). If everything's working, you should see a PHP status page, and somewhere on that
page it should show that it's configured to use the MySQLi extension.
  - Some distributions package JSON capabilities separately from the primary PHP package,
and Question2Answer needs this capability. Use shell commands such as `apt search php-json` (Debian/Ubuntu)
or `dnf search php-json` (RedHat), and if you find it, it might not hurt to go ahead and install that too.
- If your distribution implements the mandatory access control features of Security-Enhanced Linux (SELinux),
you will need to do some extra administration on your web servers,
to enable communication between your middleware and back-end tiers.
Search the web for instructions on how to configure the following:
  - Checking security context labels on web-content files with the `ls -Z` command,
  - Repairing security context labels on files and directories with the `restorecon` command,
  - Checking various `httpd_can_network_connect` SELinux flags with the `getsebool` command,
  - Permanently changing SELinux flags using appropriate `semanage boolean` commands.
  - It's tempting to just stop all SELinux controls
by setting the global SELinux mode from `Enforcing` to `Permissive` or even `Disabled`.
For a worthy security professional, that should only be a last resort.
Try to get your web app working within the SELinux control regime.
    - If your supervisor demands that the app start running right now,
and insists that the app's availability is more important than either its confidentiality or integrity,
then of course you would be forced to drop SELinux to `Permissive` mode to get the system up and running.
But after that, keep working on it, perhaps on a separate system, until you figure out how to make it work
properly in `Enforcing` mode. Then show your success to your supervisor, and schedule a change request
to make the appropriate changes and put the web server's SELinux mode back up to `Enforcing`.
- A recommended web protocol load-balancer for Linux is <a href="http://www.haproxy.org/" target="_blank" ref="noopener">HAProxy</a>,
deployed on a separate Linux host.
  - Don't keep the defaults that come with the sample `haproxy.cfg` configuration file.
Instead, create your own `frontend` and `backend` configurations, with the load
balancer "frontend" bound to port 80/tcp, and each web server "backend" also relaying through port 80/tcp.
  - HAProxy's "Round Robin" balancing algorithm is a good choice, and there are a couple of ways to
verify that round-robin is working:
    1. Enable network logging for your load balancer host's rsyslog service,
by activating the `$ModLoad imudp` and `$UDPServerRun 514` directives in rsyslogd's configuration file,
then configure `haproxy.cfg` so that HAProxy sends its syslog messages to `127.0.0.1`. You should
see HAProxy log entries in `/var/log/messages` or `/var/log/syslog`. (You could also
configure a custom rsyslogd logging rule, which corresponds to whatever logging facility and priority
are configured in `haproxy.cfg`. Then your logs would be sequestered to whatever file you specified
in your custom rule.) Generate some web traffic by accessing your Question2Answer web app
from a web browser, and look carefully at the logs HAProxy generates to see evidence that
successive web requests are proxied to different "backend" web servers.
    2. Create distinguishing content on both web servers.
Examples: put a file named `check.html` on both, but which on the first host contains the text "original"
and embeds a bright image, but on the clone contains the text "clone" and embeds a duller-hued image;
also, put different `favicon.ico` icon files on each host.
Then use your web browser to repeatedly reload `check.html`,
and notice that the content changes and/or the site icon changes color with each reload.
- To test your load balancer's ability to keep serving Question2Answer through service outages,
use `systemctl` to start and stop the web service on a web server.

 - (Note: If you chose to deploy Question2Answer using Windows Servers instead of Linux,
your recommended load-balancing solution
is to deploy Microsoft's Network Load Balancing Server Role directly onto both web servers,
which will then share a third "virtual" IP address that identifies a load balancing "cluster."
Be sure to configure multicast communication when you set up the cluster.)

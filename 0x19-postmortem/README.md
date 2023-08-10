Postmortem
An outage happened on an isolated Ubuntu 14.04 container running an Apache web server shortly after the release of ALX's System Engineering & DevOps project 0x19, at 06:00 West African Time (WAT) here in Nigeria. When GET requests were made to the server, they resulted in 500 Internal Server Errors, despite the fact that the intended response was an HTML file defining a simple Holberton WordPress site.

Debugging Procedure
Brennan (BDB... as in my actual initials... made that up on the fly, pretty good, huh?) is a bug debugger. Around 19:20 PST, I experienced the problem after launching the project and being, uh, advised to fix it. He got right to work on rectifying the problem.

Using ps aux, I checked the status of running processes. Two apache2 processes, root and www-data, were operational.

I used Vim pattern matching to go through each file in the /var/www/html/ directory in an effort to find the incorrect.php file extension. the wp-settings.php file is where you may find it. Line 137, require_once(ABSPATH. WPINC. '/class-wp-locale.php') 

Eliminated the line's final p.w
A different curl on the server was tested. 200 A-ok!

I created a puppet manifest to automate the error's correction.

      3. Summation
Simply said, a typo. Have to adore 'em. Specifically, when attempting to load the file class-wp-locale.php, the WordPress app was running into a major problem in wp-settings.php. Class-wp-locale.php was the right file name, and it was located in the wp-content directory of the application folder.The trailing p was simply removed as part of the typo's patch.

 4. Prevention

This outage was caused by an application fault, not a web server error. Please keep the following in mind going ahead to avoid any more outages of this nature.
Test! Try, try, try. Before deploying, test the application. If the programme had been tested, this problem would have occurred and could have been fixed sooner.
status tracking. Enable a website uptime monitoring service, such as UptimeRobot, to send out an immediate alert in the event of a website outage.
Please take note that in reaction to this problem, I created the Puppet manifest 0-strace_is_your_friend.pp to automate the correction of any future instances of this exact error. Any php extensions in the /var/www/html/wp-settings.php file are changed to php by the manifest.Of course, it won't happen again since we're programmers and we don't make mistakes. wink



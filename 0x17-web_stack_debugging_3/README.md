0x17. Web stack debugging #3
In this project I tried to debug a a Wordpress website. This the 4th of the stack in Web Debugging.

Wordpress is a very popular tool, it allows you to run blogs, portfolios, e-commerce and company websites... It actually powers 26% of the web, so there is a fair chance that you will end up working with it at some point in your career.

Wordpress is usually run on LAMP (Linux, Apache, MySQL, and PHP), which is a very widely used set of tools.

The web stack you are debugging today is a Wordpress website running on a LAMP stack.

Tasks
Below is the details.

0. Strace is your friend
mandatory



Using strace, find out why Apache is returning a 500 error. Once you find the issue, fix it and then automate it using Puppet (instead of using Bash as you were previously doing).

Hint:

strace can attach to a current running process
You can use tmux to run strace in one window and curl in another one

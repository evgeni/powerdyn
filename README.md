powerdyn
========

Installation
------------
Clone the git repository, there is no real installation yet.

Configuration
-------------
Edit `powerdyn.conf` and adjust the domain and database credentials to match your environment.

`domain` can have the special value `auto` (or be absent) to trigger autodetection of the domain.
Autodetection is implemented as stripping the first part of the FQDN passed as hostname.

Usage
-----
Add the following to the `~/.ssh/authorized_keys` of the user:

    no-agent-forwarding,no-port-forwarding,no-pty,no-X11-forwarding,no-user-rc,command="/usr/local/bin/powerdyn host.powerdyn.example.com" ssh-rsa <SOMESSHKEY>


Add the following to the crontab on the machine you want the dynamic DNS for:

    */5 * * * * ssh -4 -T -i /home/user/.ssh/powerdyn_rsa powerdyn@server.example.com
    */5 * * * * ssh -6 -T -i /home/user/.ssh/powerdyn_rsa powerdyn@server.example.com

If your IPv6 address does not change, just remove the **-6** line. `powerdyn` won't touch the AAAA record then.

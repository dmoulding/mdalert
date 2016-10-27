# mdalert
Alert / notification program for Linux mdadm monitor

mdalert supports multiple customizable alert methods, with "none", "mail",
"syslog", and "wall" built-in methods. "none" can be used to selectively
suppress certain types of alerts. "mail" sends email alerts, "syslog" logs
them, and "wall" broadcasts them to all users on the local system.
    
The configuration file can define new methods or override the built-in
methods by defining new alert functions.
    
Each type of event can have a configured:
  - Alert method
  - Severity level (for the syslog method)
  - Mail-to list (for the mail method)
    
So, for example, it can be configured to log "NewArray" events (which
are pretty mundane) to syslog only, while syslogging and emailing an
entire team of admins upon a "Fail" event.
    
It also allows setting the severity and method for the "Wrong-Level"
flavor of the "DeviceDisappeared" event (which proabably should have
really been its own event in mdadm).
    
If nothing is configured, the default methods are syslog and wall which
means that all events will be logged to syslog and broadcast on the local
system.
    
The default syslog severity levels have been set to (hopefully) more
appropriate values than the defaults that mdadm uses when the --syslog
option is given to it (for example, mdalert doesn't treat
"Wrong-Level" as a ciritical event as mdadm does). The messages that
are generated are also more descriptive, which means it's preferable
to use mdalert with the syslog method, than to use mdadm's built-in
--syslog option.

# Seafile
## Set up logrotate for server

## How it works

  seaf-server and ccnet-server now (since version 3.1) support reopenning
  logfile by receiving SIGUR1 signal, which feature is familiar to nginx users.

  And this feature is very useful when you need cut logfile while you don't want
  to shutdown the server programs. All you need to do now is cutting the logfile on
  the fly.

  > **NOTE**: signal is not supported by windows, so the feature is not available in windows

## Default logrotate configuration directory

For debian, the default directory for logrotate should be ``/etc/logrotate.d/``

## Sample configuration

Assuming your ccnet-server's logfile is setup to ``/var/log/ccnet-server.log``, and your
ccnet-server's pidfile for ccnet-server is setup to ``/var/run/ccnet-server.pid`` :

- ``ccnet-server  -c where_ccnet_configure_dir_is -P /var/run/ccnet-server.pid -f /var/log/ccnet-server.log``

Assuming your seaf-server's logfile is setup to ``/var/log/seaf-server.log``, and your
seaf-server's pidfile for seaf-server is setup to ``/var/run/seaf-server.pid``:

- ``seaf-server -d where_seafile_data_dir_is -P /var/run/seaf-server.pid -f -l /var/log/seaf-server.log``

The configuration for logroate could be like this:
```
/var/log/seaf-server.log
{
        daily
        missingok
        rotate 52
        compress
        delaycompress
        notifempty
        sharedscripts
        postrotate
                [ ! -f /var/run/seaf-server.pid ] || kill -USR1 `cat /var/run/seaf-server.pid`
        endscript
}

/var/log/ccnet-server.log
{
        daily
        missingok
        rotate 52
        compress
        delaycompress
        notifempty
        sharedscripts
        postrotate
                [ ! -f /var/run/ccnet-server.pid ] || kill -USR1 `cat /var/run/ccnet-server.pid`
        endscript
}
```

You can save this file, for example in debian, to ``/etc/logrotate.d/seafile``

## That's it

   You now gets all the things done, just sit and enjoy your time :-D

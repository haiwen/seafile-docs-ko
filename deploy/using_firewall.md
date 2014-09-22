# Firewall settings

By default, you should open 4 ports in your firewall settings.

     |
     | Seahub
        | 8000
        |-
        | FileServer
        | 8082
        |-
        | Ccnet Daemon
        | 10001
        |-
        | Seafile Daemon
        | 12001
        |

If you run Seafile behind Nginx/Apache with HTTPS, you should open ports

     |
     | HTTPS
        | 443
        |-
        | Ccnet Daemon
        | 10001
        |-
        | Seafile Daemon
        | 12001
        |


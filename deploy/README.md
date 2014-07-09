# Deploying Seafile under Linux

Here we describe how to deploy Seafile from prebuild binary packages.

### Deploy/Upgrade Seafile in Home/Personal Environment

* [Deploying Seafile with SQLite](deploy/using_sqlite.md)

### Deploy/Upgrade Seafile in Production/Enterprise Environment

* [Deploying Seafile with MySQL](deploy/using_mysql.md)
* [Config Seahub with Nginx](deploy/deploy_with_nginx.md)
* [Enabling Https with Nginx](deploy/https_with_nginx.md)
* [Config Seahub with Apache](deploy/deploy_with_apache.md)
* [Enabling Https with Apache](deploy/https_with_apache.md)
* [Configure Seafile to use LDAP](deploy/using_ldap.md)
* [Start Seafile at System Bootup](deploy/start_Seafile_at_system_bootup.md)
* [Firewall settings](deploy/using_firewall.md)
* [Logrotate](deploy/using_logrotate.md)


Other Deployment Issues

* [Add Memcached](deploy/add_memcached.md)
* [Deploy Seafile behind NAT](deploy/deploy_Seafile_behind_NAT.md)
* [Deploy Seahub at Non-root domain](deploy/deploy_Seahub_at_Non-root_domain.md)
* [Migrate From SQLite to MySQL](deploy/migrate_from_sqlite_to_mysql.md)

**Read here** if you have troubles setting up Seafile server

1. Read [Seafile Server Components Overview](../overview/components.md) to understand how Seafile server works. This will save you a lot of time.
2. [Common Problems for Setting up Server](deploy/common_problems_for_setting_up_server.md)
3. Use our google group forum or IRC to get help.

## For those that want to package Seafile server

If you want to package seafile yourself, (e.g. for your favorite Linux distribution), you should always use the correspondent tags:

* When we release a new version of seafile client, say 3.0.1, we will add tags `v3.0.1` to ccnet, seafile and seafile-client.
* Likewise, when we release a new version of seafile server, say 3.0.1, we will add tags `v3.0.1-server` to ccnet, seafile and seahub.
* For libsearpc, we always use tag `v3.0-latest`.

**Note**: The version numbers of each project has nothing to do with the tag name.

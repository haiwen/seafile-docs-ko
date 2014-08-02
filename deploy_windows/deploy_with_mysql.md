# Deploy Seafile With MySQL

## Preparation

- [Download and Setup Seafile Windows Server](download_and_setup_seafile_windows_server.md)
- Stop seafile windows server
  - Right click the seafile server tray icon
  - Choose "Quit and shutdown Seafile Server"
- Make sure your MySQL server is running

### Install MySQL-python Library

- download the windows installer from https://pypi.python.org/pypi/MySQL-python/1.2.4
- install it by double clicking the downloaded exe file

## Create MySQL Databases

You need to create:

- databases for ccnet/seafile/seahub
- a new user to access these databases

Execute these SQL setences on your mysql server:

```
create database `ccnet-db` character set = 'utf8';
create database `seafile-db` character set = 'utf8';
create database `seahub-db` character set = 'utf8';

create user 'seafile'@'localhost' identified by 'seafile';

GRANT ALL PRIVILEGES ON `ccnet-db`.* to `seafile`;
GRANT ALL PRIVILEGES ON `seafile-db`.* to `seafile`;
GRANT ALL PRIVILEGES ON `seahub-db`.* to `seafile`;
```

## Modify Your Seafile Configuations

* Append the following lines to **ccnet/ccnet.conf**:

```
[Database]
ENGINE=mysql
HOST=localhost
USER=seafile
PASSWD=seafile
DB=ccnet-db
```

* Edit the `database` section of **seafile-data/seafile.conf**:

```
[database]
type=mysql
host=localhost
user=seafile
password=seafile
db_name=seafile-db
```

* Append following lines to **seahub_settings.py**

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME' : 'seahub-db',
        'USER' : 'seafile',
        'PASSWORD' : 'seafile',
        'HOST' : 'localhost',
    }
}
```

* Edit the `DATABASE` section of **seafile-server/pro-data/seafevents.conf**

```
[DATABASE]
type=mysql
username=seafile
password=seafile
name=seahub-db
host=127.0.0.1
port=3306
```

### Create Database Tables for Seahub

Now we create the database tables for seahub.

Open a window command line prompt, and execute the following commands:

Assume you have uncompressed seafile server to `C:/SeafileProgram/seafile-pro-server-2.1.4`,
and you have choosed `D:/seafile-server` during seafile server initialization.

```
set INSTALL_PATH=C:/SeafileProgram/seafile-pro-server-2.1.4
set SEAFSERV_DIR=D:/seafile-server
```

```
set CCNET_CONF_DIR=%SEAFSERV_DIR%/ccnet
set SEAFILE_CONF_DIR=%SEAFSERV_DIR%/seafile-data
set PYTHONPATH=%PYTHONPATH%;%INSTALL_PATH%/seahub/thirdpart;%INSTALL_PATH%/pro/python;%INSTALL_PATH%/seahub-extra
python %INSTALL_PATH%/seahub/manage.py syncdb
```

## Done

Now you can start your seafile server.

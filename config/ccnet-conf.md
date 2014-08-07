# Seafile Network Configurations (ccnet.conf)

You may change Seafile's network options by modifying `ccnet/ccnet.conf` file. Let's walk through the options by an example.

<pre>
[General]

# This option is not used by Seafile server
USER_NAME=example

# Please don't change this ID.
ID=eb812fd276432eff33bcdde7506f896eb4769da0

# This is the name of this Seafile server. Currenlty it is only used in Seafile client's log.
NAME=example

# This is outside URL for Seahub(Seafile Web). 
# The domain part (i.e., www.example.com) will be used in generating share links and download/upload file via web.
# Note: Outside URL means "if you use Nginx, it should be the Nginx's address"
SERVICE_URL=http://www.example.com:8000


[Network]

# Ccnet waits for client connections on this port. If it's used by other services, please change it.
# This is only useful for the seafile server.
PORT=10001

[Client]
# Start from version 3.1.2, this option is not used in Linux server and client. Unix socket is used instead.
# Ccnet listens to this port on localhost for internal RPC calls.
# If it's been used by other services, ccnet and seafile would not be able to run.
# If you want to run seafile client and server on the same machine, change this port for the client.
PORT=13419

</pre>

**Note**: You should restart seafile so that your changes take effect.

<pre>
cd seafile-server
./seafile.sh restart
</pre>

# Accessing CivicDuty Services

## Prefect Admin Dashboard

Note that as of this current time, the web-based Admin Dashboard does not have any authentication mechanism or SSL/TLS connection encryption, so it must be protected from public access by other means.

The simplest and most secure method of accessing the prefect dashboard is by creating an SSH Tunnel from your workstation to the host running the CiviDuty stack. This should be fine for most purposes as the prefect Dashboard is a developer/sysadmin tool and shouldn't need to be accessed by the majority of your used base.

If there is a need to access the Prefect Admin from the public internet, then there are a number of options. Our preferred method is to front the Prefect Dashboard by a NGINX proxy such as our [Praxis NGINX Proxy Component](https://hub.docker.com/repository/docker/encircle/nginx-proxy/general). Adding SSL/TLS Certificates from Lets Encrypt for an encrypted connection. The NGINX Proxy can then be configured with basic auth to protect the dashboard from unauthorised access. A more elegant solution would be to put Cloudflare in front of the NGINX Proxy and use Cloudflare Access to provide the authentication. Note that if this topology is used, Cloudflare Authenticated Origin Pulls must be enabled so that potential attackers cannot circumvent cloudflare by connecting directly to the host running the CiviCDuty Stack. If you would like further assistance with this, please drop us a line at [https://www.encircle.co.uk/contact/](https://www.encircle.co.uk/contact/)

### Connecting via SSH Tunnel

The Prefect Admin Dashboard is configure to listen on TCP port 4200 on the CivicDuty host server.

If you are accessing the dashboard from the host within the host server itself. then you can simply go to the url: [http://localhost:4200](http://localhost:4200)

If you are connecting to the dashboard from another machine via SSH you will need to set up SSH local port forwarding so that port 4200 on your localhost tunnels this port to the CivicDuty host server.

In Linux/Bash this can be done on the command line as follows:

```bash
ssh myusernameonthehost@civicduty-host.somedomain.com -L 4200:localhost:4200
```

For convenience, you can set up an alias in your `~\.ssh\config` file so that the port forwarding is automatically set up every time you connect to the CivicDuty host server via ssh

```Properties
Host civicduty-host
  Hostname civicduty-host.somedomain.com
  User myusernameonthehost 
  LocalForward 4200 localhost:4200
```

Then you can connect via ssh as follows:

```Properties
ssh civicduty-host
```

Once you have SSH tunnel to port 4200 up and running, leave the ssh connection open in the terminal. Then simply go to the url: [http://localhost:4200](http://localhost:4200)

## Postgres Database

By default the CivicDuty Docker stack publishes the Postgres port to the local host on tcp port 5433

The password for the Postgres primarary database user 'prefect' is set in the file `./versions.env` as follows:

```
POSTGRES_PASSWORD=postgres-test
```

## MiniIO Storage container

TBC

# Basic Usage
The appserver will automatically start after your intstallation wizard (or package manager) finishes the setup. You can use it without limitations from now on.

Below you can find basic instructions on how to make use of the appserver.
After the installation you might want to have a look and some of the bundled apps.
Two of are interesting in particular:

* **Example** shows basic usage of services. You can reach it at `http://127.0.0.1:9080/example`

* **Admin** appserver and app management `http://127.0.0.1:9080/admin`

Start your favorite browser and have a look at what we can do. :)
You will see that we provide basic frontend implementations of services the appserver runtime provides.
If you want to use these services yourself you should have a look into the code of our apps and read about [app development](#app-development)

You might be curious about the different port we use.
Per default the appserver will open several ports at which it's services are available. As we do not want to block (or be blocked by) other services we use ports of a higher range.

As a default we use the following ports:

* WebContainer
	- Http-Server: `9080`
	- Https-Server: `9443`
	- WebSocketServer: `8589`  
* Persistence-MQ-Container
	- PersistenceServer: `8585`
	- PersistenceServer: `8587`
* LemCacheContainer
	- MemcacheServer: `11210`

You can change this default port mapping by using the [configuration file](<#appserver.xml-the-configuration>).
If you are interested in our naming, you can see our container->server pattern, you might want to have a deeper look into our [architecture](<#technical-background-&-architecture>)

## Start and Stop Scripts

Together with the appserver we deliver several standalone processes which we need for proper functioning of different features.

For these processes we provide start and stop scripts for all *nix like operating systems.
These work the way they normally would on the regarding system.
They are:

* `appserver`: The main process which will start the appserver itself

* `appserver-php5-fpm`: php-fpm + appserver configuration. Our default FastCGI backend. Others might be added the same way

* `appserver-watcher`: A watchdog which monitors filesystem changes and manages appserver restarts

On a normal system all three of these processes should run to enable the full feature set.
To ultimately run the appserver only the appserver process is needed but you will miss simple on-the-fly deployment (`appserver-watcher`) and might have problems with legacy applications.
Depending on the FastCGI Backend you want to use you might ditch `appserver-php5-fpm` for other processes e.g. supplying you with a hhvm backend.

Currently we support three different types of init scripts which support the commands `start`, `stop`, `status` and `restart` (additional commands migth be available on other systems).

**Mac OS X (LAUNCHD)**
The LAUNCHD launch daemons are located within the appserver installation at `/opt/appserver/sbin`.
They can be used with the schema `/opt/appserver/sbin/<DAEMON> <COMMAND>`

**Debian, Raspbian, CentOS, ...(SystemV)**
Commonly known and located in `/etc/init.d/` they too support the commands mentioned above  provided in the form `/etc/init.d/<DAEMON> <COMMAND>`.

**Fedora, ... (systemd)**
systemd init scripts can be used using the `systemctl` command with the syntax `systemctl <COMMAND> <DAEMON>`.

**Windows**

On Windows we sadly do not offer any of these scripts.
After the installation you can start the Application Server with the ``server.bat`` file located within the root directory of your installation.
Best thing to do would be starting a command prompt as an administrator and run the following commands (assuming default installation path):

```
C:\Windows\system32>cd "C:\Program Files\appserver"
C:\Program Files\appserver>server.bat
```

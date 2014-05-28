# Uninstall

Before uninstalling you might stop all services which are still running, otherwise there might be probpems with existing pid-files on Linux for the next time you install it.

To uninstall the appserver on Linux you might rely on your package management system. 
On Windows you can use the normal uninstall process provided by the operating system.

Under Mac OS X you can simply delete the `/opt/appserver` folder and delete the configuration
files for the launch deameons. These are files are located in folder `/Library/LaunchDaemons` and named `io.appserver.<DAEMON>.plist`.
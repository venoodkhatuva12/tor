Install Tor
Contrary to the weirdly outdated install instructions on Tor’s website (hey, remember Macports?), installing Tor on macOS is super simple with Homebrew.
In your Terminal execute:

brew install tor

Set network proxy settings via System Preferences
You can do this under System Preferences > Network by creating a specific Tor network location for it:

From Location dropdown at the top, select Edit Locations…
Create a new location by hitting the plus button and name it Tor. Hitting Done will select the new location which is now ready to be configured
Go to Advanced > Proxies and activate SOCKS Proxy and add those values:
SOCKS proxy server: localhost
Port: 9050

Thankfully macOS provides a way to programmatically set those proxy values via the networksetup utility. I’ve found a nice script for this but running it opened multiple admin password prompts. So I extended it a bit to make it more user friendly.

In a nutshell, this shell script asks you for your admin password upfront, starts up Tor, and sets all required proxy network settings automatically

Save this script under something like tor.sh in one of your sourced bin folders, make it executable with chmod + x and use it as a replacement for the general tor command. So you can just run


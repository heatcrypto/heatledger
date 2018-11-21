# heatledger

Latest version is 2.5.3

Heatledger cryptocurrency server.

To install and run heatledger you need Java JDK 1.8 or higher installed, note that JDK is different from standard java distributions.

On ubuntu use `sudo apt-get install default-jdk` package. For other platforms please look here http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

For configuration settings see the conf/heat-default.properties files in the installation folder.

# testnet

In order to connect to the heat testnet (this is used by developers mostly) please add these properties to `conf/heat.properties` file.

```
heat.wellKnownPeersTest=176.9.102.212;95.85.4.150;146.185.154.55
heat.isTestnet=true
```

## Recent Server updates:

The HEAT 2.5.3 Server is an optional update with improvements and some bug fixes.

Fixed errors on public name duplication in database at blockchain scanning. This improves blockchain scanning speed.

The server initialization is reorganized for embedded usage. Also implemented more robust (in different OS) server shutdown for desktop Heatwallet application using file signaling.

Eliminated extra console output about balances hash equality on blockchain scan and download.

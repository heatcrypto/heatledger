# Heatledger

Latest version is 4.0.0

# Preffered installation

Please use our official Docker images to run your HEAT server

https://hub.docker.com/r/heatcrypto/heatledger

# About

Heatledger cryptocurrency server.

To install and run heatledger you need Java JDK 1.8 or higher installed, note that JDK is different from standard java distributions.

On ubuntu use `sudo apt-get install default-jdk` package. For other platforms please look here http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

For configuration settings see the conf/heat-default.properties files in the installation folder.

# Testnet

In order to connect to the heat testnet (this is used by developers mostly) please add these properties to `conf/heat.properties` file.

```
heat.wellKnownPeersTest=176.9.102.212;95.85.4.150;146.185.154.55
heat.isTestnet=true
heat.numberOfForkConfirmations=0
```

*For mainnet the parameter heat.numberOfForkConfirmations should be reverted to the default value 2*

## Recent Server updates:

- to be updated shortly

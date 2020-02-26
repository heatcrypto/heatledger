# heatledger

Latest version is 3.1.0

Heatledger cryptocurrency server.

To install and run heatledger you need Java JDK 1.8 or higher installed, note that JDK is different from standard java distributions.

On ubuntu use `sudo apt-get install default-jdk` package. For other platforms please look here http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

For configuration settings see the conf/heat-default.properties files in the installation folder.

# testnet

In order to connect to the heat testnet (this is used by developers mostly) please add these properties to `conf/heat.properties` file.

```
heat.wellKnownPeersTest=176.9.102.212;95.85.4.150;146.185.154.55
heat.isTestnet=true
heat.numberOfForkConfirmations=0
```

*For mainnet the parameter heat.numberOfForkConfirmations should be reverted to the default value 2*

## Recent Server updates:

1. Implemented compatibility in addition to Java 1.8 with Java 9, 10, 11, 12
2. Upgraded 3rd party java librares
3. Added POP POS Rewards history storage to have ability to get account and amount of rewards at any height
4. Scanning optimization: disabling storage map versioning on scanning before 1440 blocks until blockchain end
5. Improved embeddability: make Genesis class embeddable
6. Fixed erroneously persisting peer blacklisting due to old version
7. Fixed bug: on scanning storing genesis account at wrong version height
8. Fixed API bug: getting Last Price for market
9. Fixed minor bugs

# heatledger

Latest version is 3.0.0

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
Notable server changes

Added signaling server to provide peer-to-peer messaging via WebRTC technology. The basic version of the signaling server supports central signaling host with the following features:

- Off-chain messaging, data transtmitted and stored encrypted on local device (sender & receiver) only
- P2P direct connect from client to client after signaling channel creation
- prevent MITM attacks via encryption signaling data (on client side) by users public/private keys. Server cannot recognize any client WebRTC data after signaling channel creation
- Online trigger with accept / decline confirmation for incoming connect requests
Other updates:
- discard chart and market updates when blockchain is downloading and height is far from peers height;
- fix sql select transactions


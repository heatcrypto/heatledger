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
**Note that this is a mandatory update. All nodes on the network must update to version 3.0.0 before block 2 700 000**

1. Enabled 18 million terabytes decentralized blockchain storage engine, in preparation for decentralized block slice hosting.
2. New transaction type for registration of a node’s IP address or domain name to become Masternode. Only registered masternodes are eligible for POP rewards when forging a block. Masternode registration is valid for 311,040  blocks (~90 days) with a single registration transaction. Masternode registration fee (goes to next block finder) is 100 HEAT, and the minimum guaranteed balance checked at every block creation time is 1,000 HEAT. Masternode feature will be enabled at hard fork block height 2,700,000 (approx. August 10th).
3. In preparation to the decentralized POP network where nodes are rewarded for archiving and distributing historic blockchain data, we are beginning to move to nodes being required to register as Masternodes. The first phase will start with the coming fork after which POP rewards are rewarded only to registered valid Masternodes. Registration is simple and is performed through the HEAT wallet user interface or API.
4. New transaction type for sending multiple payments in one transaction - Atomic Multiple Transfer. This feature is for now accessible through the Heatwallet API only, not User Interface. Intended for use in external integrations and for the automation of processes on the HEAT network like microservices sending automated payments. Atomic Multiple Transfer feature will be enabled at hard fork height 2,700,000.
5. P2P protocol update. Starting from block 2700000 all nodes will communicate with the newer, more efficient binary protocol instead of text based JSON. This will save bandwidth and makes things faster and more stable. CPU and memory usage of a node go down considerably especially when communicating larger pieces of data.
6. Configurable webrtc signaling server for local secure chat setup independent from 3rd party services. Create your own private messaging network by turn on signaling service in your server heat.properties using “heat.signalingServerEnabled=true” and specifying your signaling host in the client application fail-over config (failover-config.json). Ask your users to do the same in their client apps, and VOILA! There you have the world’s most secure messaging service where the encrypted messages are transmitted directly from sender ip address to receiver ip. Initiation of communication channel coordination goes through single “central” server only - your own!


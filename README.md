# heatledger

Latest version is 2.5.2.

Heatledger cryptocurrency server.

To install and run heatledger you need Java JDK 1.8 or higher installed, note that JDK is different from standard java distributions.

On ubuntu we use `sudo apt-get install default-jdk` package. For other platforms please look here http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

For configuration settings see the conf/heat-default.properties files in the installation folder.

# testnet

In order to connect to the heat testnet (this is used by developers mostly) please add these properties to `conf/heat.properties` file.

```
heat.wellKnownPeersTest=176.9.102.212;95.85.4.150;146.185.154.55
heat.isTestnet=true
```

## Recent Server updates:

The HEAT 2.5.2 Server is an optional update, it mostly aggregates completed improvements and a number of bug fixes.

An improvement deserving special mention - we’ve added a new dialect to the peer 2 peer communication protocol (how servers talk amongst each other). Only new servers using the 2.5.2 version are capable of using this more advanced protocol. When your server talks to older servers the old dialect will be used.

The new communication protocol is based on https://avro.apache.org/ instead of https://www.json.org/. HEAT has added full fledged AVRO encoding and decoding support to both the core HEAT server as well as the SDK https://github.com/Heat-Ledger-Ltd/heat-sdk (sdk = native browser + nodejs libs).

With AVRO enabled you can expect a ~3-5 times network traffic reduction. 

The biggest boost however is its CPU usage. Especially on high loads the amount of memory used and CPU power needed drops from significant to almost non existent. Both encoding and decoding happens up to 100s of times faster than before.

Other notable updates to the server code:

- Fixed a bug in reporting of the total coin supply. While not important in any way from a p2p or technical aspect, with this fix there now are 25,776 more HEAT than was thought before, an increase of 0,07%! Thanks to the sharp community members for pointing this out! You know how you are. 
- Support for WebRTC decentralized signaling server was added which plays a role in our future decentralized messaging network plans
- All external dependencies have been upgraded to their latest versions
- Support for use of OS environment variables in config files (heat.properties), use this syntax heat.name=ENV[NAME_OF_ENV_VAR_GOES_HERE]
- Some new API methods and improvements
    - https://heatwallet.com/api/#!/Transactions/checkApplicability 
    - https://heatwallet.com/api/#!/Accounts/payments now returns transaction id
- New p2p/network health/node monitoring system with build in email reporter

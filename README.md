# Heatledger

Latest version is 4.1.1 is available here https://github.com/heatcrypto/heatledger/releases

# Preferred installation

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

# Recent Server updates:

## Private Asset feature:

- Issue asset of type Standard or Private;
- Specify whitelist of accounts available to use the private asset;
- Specify the fee on order creation, the fee on trade, the recipient of these fees;
- Define default network fee payer for private asset on whitelisting market;
- Calculate and charge the fees on order creation, on trading;
- API functions to support private assets;

## Asset expiration feature:

- Asset trading available until asset expiration time;
- New transaction type to assign the expiration;

## Supervisory Account feature:

- New transaction type (type 4 subtype 2) to assign one account under the control of another account;

## Limited Amount of Account Asset in interval feature:

- New transaction type (type 4 subtype 3) to limit the account by supervisory account how much max amount of the asset the account can send in the interval;

## Microservice engine:
- Implement listeners “onConfirmed”, “onComplete”;
- Fix minor bugs;

## API additions

- To get the Multi Atomic Transfers.
- Added field height for API function /account/payments.
- To get the list of actual masternodes.
- To get messages by transaction type (e.g. get messages of order placements).
- Ability to attach messages to transactions of types Ask order, Bid order, Cancel order, Issue Asset, Set Fee for private asset.

## Changes

- New ways to set server properties (on command line)
- Support encrypted messaging through server when direct WebRTC is not allowed for endpoints.

## Bug fixes and optimisations

- Optimised performance of processing block with big number of transactions.
- Fixed getting highest transaction for benchmarking: compare longs as unsigned values. Prevent bloating cache of the highest transactions.
- Fixed processing broadcast request with multiple transactions if one of transactions is failed.
- Fixed applying unconfirmed transactions for atomic multi transfers to guarantee all transfers or nothing (truly atomic).
- Fixed description of API function. Update Swagger UI.
- Fixed several minor bugs.


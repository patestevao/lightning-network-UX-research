# Objective one: Current state of development

The first part of the research followed the available scenario of usage \(as of mid-February 2018\) of the Lightning Network. It was composed by the installation of the necessary software and performance of an economic transaction using a Lightning payment channel. The implementation used was the [c-lightning](https://github.com/ElementsProject/lightning), as it was, at the time, easier to use as a mainnet client than the other well-known alternative \([lnd](https://github.com/lightningnetwork/lnd)\). As for the transaction itself, it would be a payment to the [Blockstream store](https://store.blockstream.com/). Once an order had been successfully placed, the objective would be accomplished.

During the exploration of this scenario, it was clear that, at this point, the only user who would be able to perform the necessary operations was John, leading to the perhaps obvious conclusion that the technology is not usable for less technical users, even if they are willing to go through some risk.

Even though a [tutorial](https://medium.com/@dougvk/run-your-own-mainnet-lightning-node-2d2eab628a8b) was partially followed for the whole task, there were a few problems encountered along the way that required extra effort and previous experience to overcome them. Apart from navigating the website for the purchase, all the actions were direct commands in the CLI. The requirement for specific knowledge was considered by the evaluators as a natural constraint of the development process that, in fact, avoids that unprepared users are exposed to the risk of financial loss. In other words, those who can't perform the operation shouldn't be using the technology yet.

Nevertheless, the task was successfully carried out through these steps:

1. Set up Bitcoin Core \(bitcoind\), have it synchronized with the mainnet and running.
2. Install and configure c-lightning \(lightningd\):
   1. Create wallet
   2. Run it connected to bitcoind
3. Get `newaddr` and fund the lightningd wallet.
4. Wait for confirmations of the funding.
5. Connect to another node.
6. Set a transaction fee for the Bitcoin node.
7. Open and fund a Lightning Network channel with a well-connected peer.
8. Go to Blockstream's store, add items to basket and proceed to checkout, where you get a Lightning payment request.
9. Decode payment request, find a route and send the transaction.

The process is not particularly complex for users who know how to use the wallet through the CLI, but all the others \(Luke and Jennifer\) will have to wait until they are able to use it. In addition, the moment now is essentially for tests and development of new solutions and structures. Even for technically-able users, the system is still too risky to be considered ready for use.


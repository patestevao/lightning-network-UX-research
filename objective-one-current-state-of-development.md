# Objective one: Current state of development

The first part of the research followed the available scenario of usage \(as of mid-February 2018\) of the Lightning Network. It consisted in the installation of the necessary software and performance of an economic transaction using a Lightning payment channel. The implementation used was the [c-lightning](https://github.com/ElementsProject/lightning), as it was, at the time, easier to use as a mainnet client than the other main alternative \([lnd](https://github.com/lightningnetwork/lnd)\). As for the transaction, it would be a payment to the [Blockstream store](https://store.blockstream.com/). Once an order had been successfully placed, the objective would be accomplished.

During the exploration of this scenario, it was clear that, at this point, the only user who would be able to perform the necessary operations was John, leading to the perhaps obvious conclusion that the technology is not usable for less technical users, even if they are willing to go through some risk.

Even though a tutorial was follwed for the installation of c-lightning, there were a few problems encountered along the way that required extra effort and previous experience to overcome them. Apart from navigating the website for the purchase, all the actions were direct commands in the CLI. The requirement for specific knowledge was considered by the evaluators as a natural constraint of the development process that, in fact, avoids that unprepared users are exposed to the risk of financial loss. In other words, those who can't perform the operation shouldn't be using the technology yet.

Nevertheless, the task was successfully carried out in these general steps:

1. Setting up CLI wallet.
2. Connecting with Blockstream's peer addres to directly open a channel with them.
3. Getting the payment code from the store during checkout.
4. Sending a Lightning Network transaction.




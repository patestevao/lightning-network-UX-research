Objective two: Visualizing the user interface

The stage of restricted use and high risk described in Objective 1 is expected to end in its due time when the development reaches a more mature state and the Lightning Network will evolve to be part of regular user interfaces, as it is the case with common Bitcoin wallets. The mental exploration of what those interfaces should look like is the second objective of this study.



Phase 1 wallets



Let's call the stage with no user interface available the Phase 0 of the Lightning Network development. Phase 1 would be, then, the following stage, where the first interfaces are already functional and compatible with the abilities of the 3 described users.

This is a period when all the operations that were done throough the CLI in the first part of this research are properly integrated in a graphic interface. On the other hand, there might be quite a few structures for the Lightning Network there were not yet build or are not completely mature \(e.g. automated network discovery systems\) and the integration of these systems with the regular wallet's APIs and functions might result in delaying the launching of usable Lightning wallets. Also, it will take time for the Lightning enabled wallets to be considered really tested in dayly use and, during this period, a series of bugs and unexpected behavior might come to light. As a consequence of those two aspects, it makes sense that the first wallets to be made available are specially dedicated to Lightning operations and not "all-purpose" wallets. That is both because of timing, so that Lightning wallets can start to be used and tested as soon as they are sufficiently secure and functionable, and because of the security risk of adding new features with unkown effect in the wallets holding the users main funds. The ideal and "all-purpose" wallets will be described further in the Phase 2 wallets section.

The general consequence in terms of User Experience is that, even though all 3 typical users will be able to use the wallet, the extra learning effort of having a specialized wallet for the Lightning Network might alienate the third user, Jennifer, until the next phase. Also, this will mean that actually two blockchain transactions will be required to open the first Lightning channel \(and subsequent channels in case the wallet runs out of funds\), since the user will need to send a regular Bitcoin transaction to fund the wallet and then a second transaction will be made to open a channel. However, this is considered a minor problem given the above stated reasons for adopting this type of wallet while the Lightning development matures.

What will not be left for Phase 2 is the ability of wallets of bootstrapping themselves and automatically managing channels without the requirement for user input. The importance of this aspect lies upon the fact that, when the user doesn't need to manage his channels manually, the main break on his mental model of how a Bitcoin wallet should work gets out of the way. Or, in case of a completely new user to cryptocurrency, such as Jennifer, the learning needed to get the first transaction going is smaller and more intuitive \(send and receive transactions\). With time, the user can get curious and understand what the channels section is about and how to operate it, but it doesn't get frustatingly in the way of regular payments.

In order to imagine what the wallet should look like, we are going to do a task analysis of three main flows of action that need to be contemplated:

1. Wallet Setting

2. Sending payment

3. Requesting payment



The guidelines and wireframe sketches on this section are limited to specific operations and situations that were prioritized in this explanation, but this doesn't mean a real implementation of a Lightning wallet should limit itself to them. Also, they are purposefully low fidelity drawings, in order to focus on the elements and the general architecture instead of aesthetic aspects of design.

The first flow is common to all Bitcoin wallets, not only the ones for the Lightning Network. Nevertheless, it's such a crucial part of the interface that it will be included here anyway, with the following sketches and items being used to hightlight usability concerns of this implementation.



1. Setting up the wallet for the first time \(same as to regular Bitcoin wallet\)

- Choice for creating a new wallet or recovering an existing one.

- Chooses create new wallet and mnemonic code is displayed.

- Mnemonic code is verified.

- Other security setups \(passphrase, 2FA, etc\).

- Wallet is ready.



- First screen should be a simple choice of creating or recovering a wallet. With the "Creating new wallet" button more prominent since that's what "clueless" users will likely want to do and they should be indicated that that's the most common choice.



- Wallet backup should come next and work an interlock, i.e., the user should be constrained to begin using the wallet without going through the backup steps.

- The seed \(BIP39\) scheme is the more user friendly form of backup.

- Clear but short instructions about what to do with the mnemonic code and its importance should be given. It could be organized in bullet points or other short structure, aided by the use of bold or differentiated characters to highlight important parts. A link to a more detailed explanation of how to make a safe backup is a good call and should be more prominent than the text, but less than the list of words. That way it gets user attention but doesn't distract the person when she's writing down the words.

- Mnemonic code should be organized in a clear way, with no ambiguity in the order of words and, preferencially, numbered \(so the user can see more quickly if he's missed a word\).

- The software should avoid triggering mobile behavior of capitalizing first words, as it will make a otherwise valid word appear as invalid, causing user confusion.



- The verification of words is important to make sure the user didn't make a mistake in the copying process. All words can be requested one at a time, or an incomplete list can be shown for them to complete the missing ones. The latter will be more effective in the verification, although it will require more time and effort from the user.

- Wrong words should be hightlighted readly after the user writes them and not only when he tries to verify the whole list \(specially valid if the interface is not asking one word at a time\).

- A list of suggested words based on the partial user input can accelerate the verification process and give a quicker feedback if he has the correct words.

- A option to generate a new seed should be available in case the user realizes he's made great mistakes in the copying process \(or maybe skip the copying altogether because he thought he could get away with it\).



- Other security setups might be prompted to the user, such as password settings and 2FAs, but they should be able to go through without completing it \(given that the proper warning is displayed\) and he should be able to set those up at any time in the settings section inside the app.



The second flow consists on sending a transaction in the Lightning Network. This scenario counts on the user having external access to the address he wants to send money to.

2. Wants to send a transaction via Lightning Network

- Opens payment section.

- Pastes/writes/scans payment code/address.

- Writes amount to be sent \(in case it wasn't specified in the payment code\).

- Optionally, writes a label for that transaction.

- Hits "PAY".



- The option of writing, scaning a QR code or simply copy/pasting the address that should receive the money is already widely adopted in Bitcoin applications, but it's important to mention it as a best practice, anyway.

- When the user inputs the address or lightning payment code, the wallet should promptly give the feedback of what type of address is that \(Lightning or blockchain\).

- The idea of a self-bootstrapped wallet is that it will connect itself to a number of relevant peers in a way that, in most cases, there will already be a route for any payment the user might want to make. Nevertheless, it might come a time, specially in these early stages of the network, that a path can't be found and the wallet will need to open a channel before doing the Lightning transaction. In that case, the best option is to warn the user that the transaction will take longer and require an extra fee, because it will need to make a blockchain transaction to open a channel.

- As it was already stated, the process of opening new channels should be automated by the wallet's backend, removing any burden from the user having to perform this operation manually. Nevertheless, the user should be able to add peers manually if he specifically desires so. The possiblities of how this should be implemented will be discussed further.

- The fee estimation for the route chosen by the wallet's backend should be displayed, as well, with a warning if the fee seems too high. The definition of a high fee could be a market stablished one that is used by default, with the possibility of the user setting his own threshold in the settings section.

- Alternatively, if the fee threshold is available in a Settings section, the development team might choose not to display the fee every time to avoid excessive information. In this case, it should be displayed only when the fee is considered too high.

- Amount can be written in the Bitcoin field or in the fiat currency field, with one autocompleting the other using the current Bitcoin price. Both the fiat currency and the unit of Bitcoin should be available for personal setup in the settings section.



The third basic flow to be covered is the request of a payment. The publication of the payment information will be handled outside the wallet client \(e.g. sending by e-mail\), unless the payer is phisically present so he's able to scan the QR code information.

3. Wants to receive a transaction via Lightning Network

- Opens request section.

- Optionally writes amount to be requested.

- Optionally writes label for the request.

- Click "REQUEST" button.

- Send/publish payment request.

- Wait for payment to be completed by other party.



- Like the PAY section, it should be possible to add the amount in fiat currency or BTC. The one provided will be used by the wallet to autocomplete the equivalent amount in the other currency based on updated price.

- The top of this section should present an easily perceivable option of "Lightning payment" or "Funding wallet" in case the user wants to see a blockchain address to add funds to the wallet. The default, however, should have the Lightning payment selected, since it's the main use of this wallet.

- When the "Funding wallet" option is selected, the screen should show a regular Bitcoin request, with a blockchain address available to receive transactions.

- When the "Lightning payment" is selected, a link to show the "network address" should be available, in case the user wants to give a way for others to open a channel directly with his client.

- When clicking the "REQUEST" button, the payment code should be displayed on the same screen so that the user can check if the information he provided was correct. But the information should not be editable anymore, to make it clear that he will have to generate a new code in case any input changes.

- A link to "generate new request" should be provided in case the user does want to change any inputs. By clicking it, the input information should become editable again \(preferencially not being erased\) and the previously generated code should be erased.

- The payment code should be selectable \(for copying\).

- It would improve usability to also have the buttons for directly copying the code and to show its representation as a QR code.



Now that the most basic flows were covered, let's take a look at other relevant pages, starting with how the dashboard page \(the main page the user sees when he enters the wallet\) could look like.



- The PAY and REQUEST button should be the more prominent elements of the screen, since they are the main actions a user would need.

- In the case of desktop or browser wallets, it would be best to make the PAY and REQUEST button available in all screens. This might not be optimal in mobile wallets because of limited space and clutter.

- A summarized display of the wallets funds should be seen, with the separation of total funds, available funds and funds commited to Lightning channels.

- The main items to show on the navigation are: dashboard page, Wallet page \(where all transactions can be seen\), Channels page \(where channels can be seen and managed\) and Settings page. These items should be visible for an easy discovery, while other necessary items can be less visible if there isn't much available space for displaying or if there are too many items and a visual hierarchy has to be applied. For example, if building a mobile application, the four main items could be in a tab-style navigation, while the others could be in a hidden menu.

- This page is also where general warnings and messages should be prompted to the user, such as that a new version is available or that some setting should be reviewed, etc.

- The current exchange price of Bitcoin might also be displayed in a more subtle manner, while this is considered a relevant information by most users.



As for the "wallet" page, where transactions will be shown, the main issue is to make a differentiation between lightning and blockchain transactions. Other options such as beign able to filter transactions by type \(blockchain, Lightning Payment, Lightning request, all Lightning\) are also nice to have. Apart from that, the already stablished best practices for displaying transactions should be applied, such as ordering from most to less recent, showing number of confirmations, displaying the chosen label \(when there is one\), giving a link to a blockexplorer service, color coding the receipt and send of money, etc.

In this particular sketch of a mobile wallet, the transaction rows are links to the expanded transaction information, due to the lack of space for directly displaying everything.

The last page to be analyzed will be the Lightning channels section. The most important elements to be considered:

- List of channels with information about the peer, amount commited and the current status of the channel.

- Possibility of manually opening a channel with a specific peer.

- Filter for channels based on their status would be a nice to have.



Phase 2 wallets



Phase 2 wallets will be the clients developed in a future state of the network, when the technology is more mature and tested. In that scenario, the proper interface will not put any burden of performing different operations for Lightning transaction or regular Bitcoin transactions on the user. The same wallet will be used for any type of transaction and the software will be responsible for recognizing and act accordingly to the type of transaction that is expected.

Let's explore the same three activities we analyzed on Phase 1 wallets.

1. Wallet setting: will be based on the same principles, so no further analysis is necessary.

2. Sending payment and 3. Requesting payment: the basic flow should be exactly the same, only, now, the wallet will have both blockchain and lightning transactions with the same degree of importance to the user. The following items and sketches will highlight the differences that should be expected in this type of wallet.



- On the REQUEST page, a more advanced option of for blockchain transactions should be implemented, giving the user the possibility of creating a more complete request \(with the amount already filled in\). In order to avoid unnecessary clutter, since it's very common for users to just want the address, this should be hidden under a "advanced options" link.

- The page for Lightning channels will be less important in the general wallet hierarchy, because the opening and closing of channels should be even more seamless for the user. At the same time, it has to continue existing so users can manually open channels if they have that need. The solution is to remove this section from the main navigation elements and put it in a hidden or contextual menu \(in case there's reason for a Lighting submenu\).



The conclusion we can take from the Phase 2 analysis is that the main differences will occur in the wallet's backend and in the conceptual model passed to the user that this is now an "all-purpose" wallet. The interface itself will need very few modifications. Nevertheless, the usage simplification of only needing one wallet, together with the fact that more standards and best practices will be stablished by then is the necessary evolution that will fully integrate Jennifer, our third persona, as a user of the Lightning Network.


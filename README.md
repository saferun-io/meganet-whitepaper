# MegaWise Network WhiteBook

## Abstract

The Hybrid Proof-of-Work/Proof-of-Service system of MegaWise provides a unique way to incentivize actions by all nodes. MegaWise utilizes these incentivized nodes to create an auxiliary private shared network routing layer. Monitoring and execution of the lowest node functionality in the second layer is achieved through a new method called swarm flagging. MegaWise is based on a modified version of the Monero/Loki source code to ensure high levels of metadata obfuscation for all transactions. This whitepaper provides an overview of the adopted/innovative technologies in MegaWise. We anticipate that these technologies may undergo changes as development of MegaWise continues. When any significant future changes and updates occur, a new version of this whitepaper will be published to reflect these changes.

## 1. Introduction

The demand for privacy in digital communication and transactions is increasing day by day. Users' data is being collected, processed, and traded more than ever before. From browsing data and email content to credit ratings and consumer habits, this data is being collected and sold by some of the largest corporations and state-level institutions in the world. The goal of MegaWise and its subsequent product line is to provide a decentralized anti-censorship tool and privacy network that utilizes decentralized distributed computing mining and AI's intelligent logical judgment, allowing users to transact and communicate privately, thereby achieving a decentralized knowledge text/video sharing, a decentralized full-chain wallet, and a multi-layered decentralized indexing space.

Bitcoin came with a promise of privacy, but it is actually more traceable than ever before. Companies like Chainalysis and BlockSeer have already been using Bitcoin's transparent blockchain architecture to track and monitor specific transactions. MegaWise is built on top of Monero/Loki, the latter of which has established one of the most secure and private transaction networks to date. However, we recognize that Monero does have inherent flaws. Monero transactions are much larger in size compared to Bitcoin transactions, requiring large bandwidth, processing, and disk space. As the network grows, this creates a significant burden on Monero node operators, with no incentives or rewards for contributing to the network. This makes running nodes an expensive and often unappreciated task. MegaWise will adopt Loki's introduced node incentive program: Service Nodes, which alleviates the above challenges and provides substantial economic incentives to node operators.

Service Nodes can also be utilized to provide a range of other privacy-centric functions if given appropriate incentives. First, the Service Node network will allow users to transmit and receive data packets anonymously. This private communication is facilitated by having each Service Node act as a relay in the mixer network, with similar properties to Tor and I2P. Additionally, this emerging communication network will be used as a backbone for the decentralized and end-to-end encrypted messaging service MegaWise Messenger, which will allow users to communicate directly without relying on any trusted third parties or requiring both parties to be online simultaneously.

MegaWise is not only a flexible private exchange medium, but also a platform for decentralized and metadata-free internet services.

## 2. Basic Parameters

  MegaWise Difficulty Target (Block Time): 120 seconds
    Difficulty Algorithm: Zawy LWMA
    Hash Algorithm: CryptoNight Heavy
    Elliptic Curve: Curve25519
  
## 3 CryptoNote Features

Although the full node incentive plan can be implemented on any cryptocurrency, MegaWise uses the Monero/Loki source code because it offers a high level of transaction privacy. Monero/Loki is an evolution of the CryptoNote protocol, which uses ring signatures, stealth addresses, and RingCT, allowing users to sign transactions and obscure amounts while maintaining deniability.

To maintain privacy in the MegaWise ecosystem, it is important to provide not only a medium of exchange that supports internal economies but also to minimize the time analysis risk when interacting across independent layers of MegaWise. MegaWise incorporates the following technologies from Loki while adding some innovations.

### 3.1 Ring Signatures

Ring signatures hide the actual output data of a transaction by creating possible signer rings, with only one signer being the actual sender. MegaWise enforces the use of ring signatures for all MegaWise transactions (excluding block reward transactions), and each input will spend from ten possible outputs (including the true output) (see 6.3).

### 3.2 Stealth Addresses

MegaWise uses stealth addresses to ensure that the recipient's true public key is never linked to their transactions. Each time a MegaWise transaction is sent, a one-time stealth address is created, and funds are sent to that address. Using Diffie-Hellman key exchange, the transaction recipient can compute a private spending key for that stealth address, allowing them to take control of the funds without revealing their true public address. Stealth addresses provide protection for the transaction recipient and are a core privacy feature of MegaWise.

### 3.3 RingCT

RingCT was first proposed by the Monero Research Lab as a method to obscure transaction amounts. The current deployment of RingCT uses range proofs, which utilize Pedersen commitments to prove that the amount sent in the transaction is between 0 and 2^64. This range ensures that only non-negative amounts of currency are sent and does not reveal the actual amount sent in the transaction. Recently, many cryptocurrencies have proposed using simplified proofs to replace the traditional range proofs in RingCT, as it significantly reduces transaction size. MegaWise will utilize simplified proofs to reduce the information that nodes need to store and relay, thereby improving scalability.

## 4 Service Nodes

Although MegaWise/Loki has made some new modifications on the basis of the CryptoNote protocol (see 7), most of the MegaWise network functions and scalability are implemented by a group of incentive nodes called Service Nodes. To operate a Service Node, the operator needs to lock a certain amount of MegaWise and provide the minimum bandwidth and storage to the network. As a reward for their service, MegaWise Service Node operators can receive a portion of the block rewards from each block.

This design gives the network the ability to resist Sybil attacks based on markets, solving a series of problems faced by existing mixed networks and privacy center services. This resistance is based on the interaction of supply and demand, which helps prevent a single participant from having a significant negative impact on MegaWise that provides second-layer privacy services. DASH first proposed a method derived from cryptoeconomics to resist Sybil attacks on networks. As attackers accumulate MegaWise, the circulating supply decreases, putting pressure on demand and driving up the price of MegaWise. As this trend continues, the cost of buying more MegaWise continues to increase, making the attack costly and difficult.

### 4.1 Block rewards

To achieve this economic protection, appropriate issuance curves and collateral requirements must be designed to ensure sufficient circulating supply is locked while providing reasonable returns to operators to ensure that they can resist Sybil attacks.

MegaWise's block rewards are distributed through POS/POW AI Proof, a robust and extensively researched system for block creation and transaction ordering. Miners collect and write transactions into blocks and are paid for doing so. As a consensus rule for MegaWise, each block contains multiple reward outputs, of which only one reward is given to the miner.

#### POW AI Mining Reward:

Decentralized distributed AI nodes will account for 9.2125% (22,118,000) of ecological tokens, and 100% of the block rewards will be given to the miner who constructs the block.

#### Service node POS reward:

16.17% (40 million) of ecological tokens belong to Service Nodes. The service node's reward is based on the time since it last received a reward (or registered). It prioritizes nodes that have been waiting longer. Each time a service node registers with the network, it occupies the last position in the queue. If the service node maintains good service and is not marked and expelled from the queue, it will slowly move to a higher position in the queue. Nodes near or at the front of the queue are eligible for rewards. Once a reward is obtained, the node drops back to the last position of the queue and slowly starts working its way back to the front again.

#### LP liquidity pool reward:

3% (7.2 million cross-chain tokens) of ecological tokens belong to the LP liquidity pool.

### 4.2 Verifiable Collateralisation

Service nodes must prove to the network that they hold the required collateral. This is difficult with MegaWise's inherent privacy features, particularly as public address balances cannot be audited or output transactions viewed with viewkeys.

MegaWise uses time-locked outputs in a novel way that allows MegaWise coins to be time-locked on the blockchain before a defined block height is reached. Before this defined height, the MegaWise network makes spending these time-locked outputs invalid. MegaWise uses this process to prove the specific amount held by a particular service node and prevent collateral transfers.
To register as a service node, the operator needs to create the required amount of time-locked outputs that unlock after at least 10,800 blocks (approximately 15 days). In the additional field of the transaction, the service node operator includes the MegaWise address that can receive service node rewards. This address will also be used as the public key for service node operations, such as group voting. Wallets can avoid using these service node registration transactions in mixes as they reveal the true amount and destination of the transaction, thus providing no additional anonymity for the transaction.

Before each node joins the Service Node network, other nodes must individually verify that the node's collateral expenditure matches the gradually decreasing collateral requirements.

## 5 MegaWiseNet

The Onion Routing protocol allows users to form tunnels or paths through a decentralized network, using multiple nodes as relay points to obfuscate the source and destination of packets. The service nodes on the MegaWise network will implement the Low Latency Onion Routing (LLOR) /Loki protocol to form a fully decentralized overlay network known as MegaWiseNet. This network does not rely on trusted authorities and its state is entirely derived from the blockchain. Users can connect to individual service nodes and establish bidirectional paths for packets. The network can be used to access internally hosted services called SNApps. If used correctly, users can utilize the egress capabilities of the service nodes to browse the external Internet without exposing their IP addresses.

### 5.1 Low Latency Anonymous Routing Protocol (LLARP)

All applications behind the service nodes are anonymous routing protocols. The protocol defines the way each service node communicates with its peer nodes. MegaWise adopts a new routing protocol called LLARP, which is a hybrid of Tor and I2P, offering additional desirable properties that existing routing protocols lack. LLARP is specifically designed to run on top of the MegaWise service node network, and all LLARP optimizations take this architecture into account. To understand the goals of LLARP, it is best to analyze existing routing protocols and consider how LLARP improves upon them.

#### The Onion Router (Tor)

Tor has been the most popular anonymous mix network in recent years. The Tor network has a high capacity to resist censorship and has proven to be a valuable tool for protecting Internet privacy. However, Tor is not a decentralized network; it is more like a hierarchical network. Tor relies on a set of directory authorities, which are centralized servers operated by a group of volunteers near the Tor Foundation. These directory authorities serve two main functions. First, they act as trusted reporters of node statuses in the network. When users (or relays) initially connect to the network, they can connect to one of the ten hardcoded directory authorities. These directory authorities provide a document called a consensus, which lists all the relays, guard nodes, and exit nodes (excluding bridge nodes) running in the Tor network. Second, the directory authorities also measure the bandwidth each relay can provide to the network. They use this information to categorize the relays and determine if a node can serve as a relay, a guard node, or an exit node.

This high level of centralization creates single points of failure and makes Tor vulnerable to attacks. In 2014, there were reliable reports of threats to shut down the directory authority servers. If the directory authorities in the US and Germany or the Netherlands were shut down, it would be enough to shut down half of the directory authority servers. This would make the Tor network highly unstable and significantly reduce the ability for new relays to interact with the network.

The communication in Tor is also limited as it only allows communication using TCP. While it is feasible to go through Tor with IP, it does not support UDP-based protocols like VoIP.

### Invisible Internet Project (I2P)

I2P uses a hybrid network architecture system different from Tor, which determines network status by referring to decentralized hash tables (DHT) rather than trusted directory authorities. I2P also allows TCP and UDP traffic, supporting a wider range of protocol interactions. However, I2P has no stable development process and has accumulated technical debt, particularly in encryption usage. I2P uses 2048-bit ElGamal encryption, which is slower in encryption and decryption speed than elliptic curve operations. Although there are plans to gradually phase out ElGamal in the I2P roadmap, progress has been slow.

In addition, I2P lacks formal support for exit nodes, meaning that most traffic on the network is directed towards internally hosted sites called Eepsites. This greatly reduces I2P's ability to attract users whose primary purpose is to access the wider internet.

Furthermore, the way I2P is constructed means that most users connecting to the network also become routers, which is problematic because the resulting network often lacks sufficient bandwidth to construct fast paths. The network speed in a hybrid network is limited by the least capable node in each circuit, and since low-performance users become relays in I2P, the overall performance is reduced.

Finally, I2P is different from Tor in that it provides a packet switching (rather than circuit switching) network. Rather than setting up a single, longer-lasting tunnel through which all traffic passes, I2P sets up multiple paths, each of which can take different routes through the network for each communicating packet. This allows I2P to transparently bypass network congestion and node failures.

Both Tor and I2P have not completely mitigated Sybil attacks. A motivated attacker with enough time and capital to purchase a large number of relays can execute time analysis, which breaks user privacy. The effectiveness of such analysis is higher the more exit nodes, relays, and guard nodes an attacker operates. Tor and I2P are both run entirely by volunteers who donate their time and money to operate nodes. We speculate that a network built by financial incentives instead of altruism can achieve greater resistance to attacks and provide more reliable services.

### LLARP

LLARP does not require the use of directory authorities but relies on a DHT built by staked mining transactions, allowing service nodes to act as routers in the network. Bandwidth measurement and classification are obtained from a group that assesses each node's capacity and provides adequate network bandwidth.

LLARP only attempts to provide an anonymous network layer in the Open Systems Interconnection (OSI) model. This means that it supports a wider range of internet protocols and can minimize the overhead of storing file descriptors if exit nodes pass traffic through UDP. In addition, LLARP chooses packet-switched routing over tunnel-based routing, which allows the network to achieve better load balancing and redundancy.
It is not expected (or even allowed) for end-users of MegaWiseNet to route data packets, which means that MegaWiseNet is much less exposed to Sybil attacks because the capital expenditure required to operate a service node reduces the attack surface.

## 6 MegaWise Services

Similar to a miner's investment in hardware, each service node operator must freeze MegaWise network tokens when starting to operate a service node. This frozen capital has two purposes:

1. Each service node operator has a large enough stake to participate in the network's success. If any service node operator provides poor performance or improper behavior, they will risk damaging the network and reducing their investment value in the network.

2. It provides an opportunity to enforce more aggressive enforcement. If the network can effectively limit dishonest nodes from receiving rewards, those dishonest nodes must bear the opportunity cost of reward loss and occupying mortgage time.

If we believe that the above points are correct and we can actively punish poorly performing nodes, we can build a service node group that can query the blockchain state or implement special offline node behavior to achieve consensus.

In MegaWise, this behavior is related to network and storage activity. These offline activities are combined with applications that leverage these ideal characteristics, called MegaWise Services.

### 6.1 MegaWise Messenger

The first MegaWise service to be developed and deployed on the MegaWise network is a decentralized end-to-end encrypted messaging application similar to Session, called MegaWise Messenger.

End-to-end encrypted messaging applications already exist and provide users with a platform to send messages without revealing their content, but they rely on centralized servers that can be targeted, blocked, or shut down. These centralized service models pose a high risk to the anonymity of communication parties, as they often require users to register their phone numbers or other identifying information and connect directly through users' IP addresses. This information can be extracted from servers through data breaches or legal processes and used against users. By leveraging the service node architecture on the MegaWise network, we can offer a service similar to popular centralized encrypted messaging applications like Signal, but with a higher degree of privacy and resistance to censorship.

#### 6.1.1 Messenger Routing

Message routing on the MegaWise network depends on whether the receiving user is online or not. When both users are online simultaneously, higher bandwidth communication can take place as messages don't need to be stored on service nodes.

In MegaWise, public keys serve as both long-term encryption keys and routing addresses. In the simplest case, this key should be exchanged offline to ensure protection against man-in-the-middle attacks. This exchange should be done in person or through another secure means of exchange.

##### Online Messaging

Once Lily knows Bob's public key, she assumes he is online and attempts to establish a path to him. Lily accomplishes this by querying any service node's DHT and retrieving any introduction set associated with Bob's public key. In LLARP, an introduction set lists the introducers each user maintains, and it is through these introducers that a path can be established. Through Bob's introducers, Lily now selects three random service nodes to act as intermediary hops between her source and Bob's destination (i.e., Bob's introducers). A path has now been established, and Lily and Bob can transmit messages through this path. If properly authenticated and using OTR, Lily and Bob can now communicate while maintaining a high level of privacy.

##### Offline Messaging

If Lily doesn't receive a response from Bob, she can initiate the offline messaging process. Offline routing utilizes a modified version of Swarm Services over Swarm (PSS). Swarms are service nodes grouped based on the logic of their public keys and the hash of the block where their deposit transaction first appeared. Each swarm has a swarm ID consisting of nine nodes. To send a message to Bob, Lily can calculate which swarm Bob belongs to using his public key. With this information, Lily can anonymously route the message to a random service node in that swarm. When a service node receives a unique message for a target user swarm, it must distribute that message to the other eight nodes in the swarm. All nodes also need to store the message with an assigned time to live (TTL). When Bob comes online, he can query any two nodes in his swarm to retrieve messages that he can decrypt. A small proof-of-work attached to each message is used to prevent spam.

#### 6.1.2 Messenger Encryption and Authentication

Once the messaging link is established, MegaWise Messenger enforces Perfect Forward Secrecy (PFS) and Deniable Authentication (DA). PFS and DA are key concepts of the Off-The-Record (OTR) messaging protocol. Centralized services like Signal and WhatsApp use encryption to maintain OTR protection. Loki simulates its OTR implementation based on the existing Tox protocol, which is a distributed peer-to-peer instant messaging protocol that uses the highly scrutinized NaCl library.

PFS supports resistance to attacks on long-term key exposure. Each conversation uses a new shared encryption key, so if a single conversation key is compromised, the entire messaging link remains unaffected. If a third party wants to decipher the encryption of the messaging link, they need to obtain the keys for each individual conversation. PFS ensures that compared to existing methods like PGP encryption, breaking into MegaWise Messenger is very difficult, as the latter only requires a pair of long-term keys to decrypt the entire messaging link.

DA refers to both parties being able to prove themselves as the sender of each new message. However, third parties cannot determine the true sender of any message. When using DA, a Message Authentication Code (MAC) is published after each conversation, allowing third parties to securely create messages that appear to come from the sender's public address. If implemented correctly, any third party cannot prove the actual sender of a specific message.

##### User Authentication

Authentication of user identity is crucial to prevent man-in-the-middle attacks. For example, if Bob expects messages from Lily but does not yet know her public key, a third party (Eve) can send messages to Bob pretending to be Lily. This is why users should authenticate each other before sharing personal information.

Similar to Session/Pidgin and other OTR messaging services, MegaWise Messenger uses pre-shared key (PSK) authentication for user identity. Users can establish PSK in multiple ways. They can establish keys offline or achieve agreement on PSK through MegaWise Messenger by asking each other a question that a third party would not know the answer to. MegaWise Messenger will implement PSK authentication based on a modified version of the Loki/Pidgin encrypted identity authentication plugin.

### 6.2 SNApps (Service Node Applications)

SNApps function similarly to Tor's so-called hidden services, and they have seen significant development. They provide users with a way to interact entirely within the hybrid environment and offer a higher level of anonymity without accessing externally hosted content. SNApps allow users to set up and host various internet applications such as marketplaces, forums, insider websites, social media, etc., on their own machines or servers while maintaining complete server and client anonymity. This greatly expands the scope of the network and allows users to build meaningful communities within MegaWise Net.

SNApp operators use the traditional server-client model, with the key difference being that the service node acts as an intermediary for users to establish connections through MegaWise Net. When an SNApp wishes to register on the network, it must update the Distributed Hash Table (DHT) with its descriptor. This descriptor contains various introducers that can be contacted by users to form paths with specific service nodes in order to connect with the SNApp. Once these paths are established, users can connect to the SNApp without any party knowing the location of others in the network.

### 6.3 Exit Nodes

Exit nodes allow users to make requests to the broader internet and have them returned through the mix network. When used correctly, exit nodes can enable users to browse the internet privately without revealing their IP address to servers. However, mandating that all service nodes also act as exit nodes may be detrimental because it could expose operators to legal risks if users engage in malicious activity while using the node as a proxy. Since exit nodes simply relay traffic from the internet to end users, they often receive Digital Millennium Copyright Act (DMCA) requests or are often blamed as the source of attempted hacks. While in most jurisdictions, safe harbor laws can protect exit node operators, internet service providers carrying the flow of service node traffic may be wary of legal risks and frequently throttle exit node services.

Upon activation, service nodes are assigned a relay flag and are restricted to routing packets internally within the MegaWise net, and never make requests to the broader internet. If an operator wishes to become an exit node, they must elect to do so, indicating that they understand the additional risks while accepting extra community testing.

Operators who choose to act as exit nodes can customize the reward criteria when block rewards are distributed. This incentivization mechanism is designed to ensure that exit node operators have sufficient economic incentives to operate exit nodes and help prevent Sybil attacks aimed at taking over the exit node network. This is a vulnerability that Tor has experienced due to a lower ratio of exit nodes to relays.

### 6.4 Remote Nodes

For most users, storing a full copy of the blockchain is impossible or impractical on any given cryptocurrency network. In Bitcoin or Ethereum, users can choose to connect to public full nodes holding copies of the chain and can query and submit transactions to the network. This is feasible because Bitcoin and Ethereum's full nodes can efficiently search the blockchain to find transactions targeting a user's public key.

Due to the structure of CryptoNote currencies, public full nodes (referred to as remote nodes) bear much greater pressure. When users connect to remote nodes, they must temporarily download every block to their local machine (since wallet creation or last checkpoint), and check every transaction to look for public transaction keys that can be generated from the user's private view key. This process can significantly impact the performance of remote nodes. Given no additional reward for this service, it could discourage lightweight client sync services from running. CryptoNote mobile wallets are often unreliable, sometimes requiring multiple switches of remote nodes to establish a reliable connection before submitting a transaction or scanning the blockchain.

Furthermore, malicious remote node operators running some popular nodes can record a user's IP address when broadcasting specific transactions. Although this attack does not reveal any information about the actual transaction, it can be linked to a specific IP address and then used to establish a connection with the real identity, compromising user privacy.

MegaWise circumvents these problems by requiring every service node to also act as a remote node available to users. Service nodes are naturally suited for this task since they already hold full copies of the blockchain and form a widely distributed high-bandwidth node network. By using service nodes as remote nodes, any interested party can have financial restrictions on the remote node network, thus limiting any data that malicious node operators can collect.

### 6.5 Blink

In typical blockchain systems, the confirmation time for any given transaction is the time it takes to include the transaction in a block. Due to competing miners, withheld blocks, and Finney attacks, the recipient usually needs to create additional blocks on top of the block containing the transaction before considering the transaction complete. Depending on various factors that affect each blockchain, this process typically takes 10-60 minutes, which is highly inconvenient for merchants and customers who must wait for confirmation before releasing the goods or starting the service.
With the adoption of Loki's service node architecture, nearly instantaneous transactions are possible in MegaWise. Blink allows the same transactions occurring on the main chain to be confirmed before being included in a block, ensuring the validity of the transaction and preventing double-spending for senders and receivers.
Blink works similarly to DASH's InstantSend. Each block, a deterministic group of service nodes is selected to act as witnesses, confirm the validity of the transaction, and lock the transaction to prevent double-spending. Unlike the locking of unused outputs in DASH, the locking in MegaWise is done at the key image level. Key images are unique keys attached to each unused output in a ring signature. To provide instant confirmation, Blink authorizes the selected group to signal the network to lock the key images associated with the output until the transaction is included in a block. If an attempt to double-spend the same unused output occurs, the same key image will be produced, which will be rejected by the group and thus rejected by the entire network.
Users will be able to pay higher fees to send Blink transactions that require only a few seconds to confirm instead of several minutes. This opens up a range of new use cases for MegaWise, where face-to-face payments become increasingly practical, and online payment integration becomes easier. Throughout the process, all of MegaWise's inherent privacy features remain uncompromised.

### 6.6 MegaWise Integration

The MegaWise project is an innovation based on the Loki and Oxen blockchains. It integrates the current Session into the MegaWiseNet client, creating a privacy-protected SNApps platform. In the existing Oxen ecosystem, Session and the Loki client are separate, and there is no unified entry point to display SNApps content. This leads to poor user experience, limited SNApps development, and an underutilized value of MegaWiseNet. To address these issues, MegaWise's improvements are as follows:

MegaWise will prioritize Session as the main interface, enabling users to achieve private communications, browse SNApps, and manage (full-chain) wallets within one application. MegaWise will be an end-to-end encrypted messaging application based on the Oxen blockchain that protects the privacy and security of users, allowing them to freely communicate information and files. MegaWise is also an SNApps display platform that allows users to discover and use various interesting and practical SNApps, such as social, entertainment, education, and business, all within one application. Consuming services within MegaWiseNet will earn users ecosystem tokens, creating a virtuous economic cycle.

We will add the MegaWise Net GUI Client as a Session submodule, enabling users to access SNApps services through the MegaWise Net network and enjoy a fast, secure, and decentralized network experience. MegaWise Net is an anonymous network based on the Loki blockchain that allows users to access any website and service without exposing their true IP addresses and locations. Additionally, MegaWise is an SNApps runtime environment that enables developers to create and deploy their own SNApps on MegaWise Net without any centralized servers or domain names. Our project allows users to easily switch on and off MegaWiseNet availability within MegaWise, as well as view and manage the status and settings of MegaWise Net.

Our specific methods are as follows:
1. Build a new WEB3 entry point, enabling users to achieve private communications, browse SNApps, and manage wallets within one application.
2. Include MegaWise Net GUI Client as a submodule, allowing users to enjoy a fast, secure, and decentralized private network experience.
3. Implement a community voting mechanism to audit and recommend SNApps, incentivizing more developers to join the SNApps ecosystem and enriching MegaWise's application scenarios.
4. Integrate a full-chain wallet, enabling convenient acquisition and consumption of ecosystem tokens to support SNApps' development and operation, achieving a virtuous economic cycle.

#### 6.6.1 Innovative Application: AI Distributed Training

##### Background and Objectives

Distributed training for artificial intelligence (AI) is a method of using multiple graphics processing units on multiple machines to accelerate the training of large models. It can improve training speed and scalability but also requires efficient communication and synchronization mechanisms, as well as considerations for data partitioning and load balancing. Additionally, AI distributed training faces security and privacy concerns regarding data and model protection, such as preventing data leakage, model stealing, and adversarial attacks.

Our innovation is based on the decentralized anonymous network of Loki/LLARP, allowing users to visit the internet through service nodes' tunnels and hide their real IP addresses and network traffic. Additionally, we will use anonymous domain names that are only resolvable on their network, such as .snode.

Our goal is to explore how to combine AI distributed training with Loki/LLARP to create a more efficient, secure, and private AI training platform.

##### Design and Solution

Our design relies on Loki/LLARP's anonymous domain names and tunnels to set up a decentralized AI training network where each participant can act as a training node, providing their own data and computational resources while obtaining data and models from other nodes. The steps are as follows:

First, we need to register a dedicated anonymous domain name on the network, such as ai-train.loki, as the entry and identifier for our training network. We also need to assign a subdomain for each training node, such as node1.ai-train.loki, node2.ai-train.loki, etc. This will facilitate communication and identification between nodes.

Secondly, we need to install the Loki client on each training node and configure the corresponding tunnel and routing rules to enable each node to access the ai-train.loki domain name and its subdomains through Loki/LLARP.

Once the setup is complete, we can start the distributed training process, where each training node provides its own data and computational resources, and algorithms are used to combine the results. By using an anonymous network, we can ensure data privacy and model protection for all participants.

## 7 CryptoNote Changes

As a cryptocurrency, MegaWise is functionally similar to other CryptoNote coins, but there are key differences beyond service nodes and related functions.

### 7.1 ASIC Resistance

Application-Specific Integrated Circuits (ASICs) are computer chips specifically built for a single function. In mining, ASICs are used to calculate specific hashing algorithms. They present a risk to decentralization as their speed exceeds all other mining methods, they are manufactured by specific companies, have limited distribution channels due to the specialized nature of the hardware, and require a large capital cost to develop and profitably operate. ASICs do have the potential benefits that miners must bear the capital cost of investing in specific algorithm hardware which makes it less likely for them to act maliciously to undermine their own investment. However, the production and distribution of mature hashing algorithm ASIC chips are still concentrated in the hands of a few large companies. These companies can refuse to ship to certain areas, decide which regions and customers may receive the best-performing ASICs, and can plan for limited runs and manipulate prices.

To prevent ASIC miners from monopolizing network hash power, several alternative Proof of Work algorithms have been proposed such as Memory-hard Hashing Algorithms (MHHA) like Argon2, Balloon Hashing, and Polymorphic Hashing Algorithms (PHA) such as ProgPoW and RandProg. MegaWise will use a version of CryptoNight integrated into Loki team's Loki called CryptoNight Heavy. It has several differences from CryptoNight V7: It provides a 4MB scratchpad size increase and changes the way implodes and explodes are handled. These changes differentiate it from Monero's CryptoNight V7, the largest target of ASIC miners, and provide stronger ASIC development protection until more permanent solutions are proposed.

### 7.2 Dynamic Block Size

Like other Oxen/CryptoNote coins, MegaWise has no fixed block size. Instead, the block size will change over time and grow as the network achieves higher transaction throughput to include more transactions. MegaWise's block size is slowly adjusted to a threshold for any new block by observing the median block size of the past 100 blocks.

A longstanding concern for other cryptocurrencies is that large block sizes impose a heavy burden on nodes that store and verify transactions. As the block size grows, nodes running on lower-spec hardware will be unable to handle and propagate new blocks, leading to node network centralization around those who have a business interest in maintaining nodes. This could be worrying because distributing blockchains between many nodes allows multiple parties to confirm the state of the chain, increasing its efficacy and resilience against censorship.

In MegaWise, a portion of the block reward is granted to service nodes that process and propagate blocks as full nodes. Since service nodes that do not provide enough bandwidth and performance are removed from the service node network, the reward pool self-enforces a minimum performance requirement. This incentive structure not only ensures high node counts, but also ensures that said nodes have a sufficient performance level to successfully share blockchain data across the network, regardless of how large the blockchain grows or what bandwidth requirements are imposed. Nonetheless, transaction size optimizations remain necessary to ensure network efficiency scalability, keeping service node operational costs low so that high node counts can be maintained long-term.

### 7.3 Size of a Circular Signature

The size of a ring signature refers to the number of mixins used to construct the ring, which hides the true output in a given transaction. Currently, Monero implements a minimum ring signature size of 7, with six mixins used in conjunction with the actual unused outputs in the transaction. There is limited research on the effects of different ring sizes. However, a study in Monero Research Lab's 0001 document analyzed the impact of different ring sizes on attackers who have a large number of outputs on the blockchain. The study found that higher ring sizes can reduce the time frame in which a malicious attacker with a large number of unused outputs can effectively analyze them. Enforcing larger ring sizes can also prevent a theoretical EABE/Knacc attack, where a third party, such as an exchange, can perform limited time analysis on transactions between two users. 

Furthermore, the Monero network consensus rules do not enforce a maximum ring size. Many wallets, such as Monero GUI, limit the ring size to 26. However, users can manually create transactions with any ring size greater than seven. This is a problem because most wallets have a default ring size of seven. Increasing the ring size of a transaction to anything higher than 7 makes it stand out. Additionally, if an individual's Monero transactions always use a non-standard ring size, such as ten, a passive third party can analyze the blockchain and deduce patterns through time analysis. 

MegaWise improves both of these issues by statically enforcing a ring size of ten. Setting the maximum ring size protects users who utilize over nine mixins, and setting the minimum ring size to ten prevents attackers with a large number of outputs from differentiating the actual output used in the ring signature. Larger ring sizes also increase the effectiveness of default obfuscation in a non-linear way, with greater effects as ring size increases. 

In the current transaction scheme, increasing the ring size to ten results in a 2.6% increase in transaction size. However, implementing Simplified proof, it will account for an increase of around 8-13% in transaction size. This is due to the overall reduction in transaction size caused by Simplified proof. Increasing the minimum ring size may be problematic on networks that do not support larger transaction sizes without structural support. However, MegaWise can bear this burden by incentivizing service nodes that provide sufficient bandwidth and performance.

## 8 Attack Prevention

### 8.1 IP and Packet Blocking

Despite the lack of a single point of failure in the service node network, the network faces two major censorship threats: harvesting attacks and deep packet inspection (DPI). Harvesting attacks will attempt to collect the IP addresses of all operational service nodes on the network and use ISP-level firewalls to block connections to these specific addresses. This type of censorship is commonly carried out on the Tor network in China. Deep packet inspection (DPI) aims to investigate the structure of each individual data packet passing through the firewall and selectively delete or block packets that appear to be related to specific services. Once again, DPI is extensively used by nation-state actors.

Significant efforts have been made to design systems that can bypass DPI. Users can utilize pluggable transport types that change the signature of each data packet to make it appear as normal unblocked traffic. IP blocking is avoided by encrypting the traffic as HTTPS requests to unblocked services such as Azure or Cloudflare. Once they reach the unblocked service, the bridge will forward the requests to the desired location. In the case of domain fronting, it becomes challenging for nation-state actors to prevent traffic from flowing to popular bridges without causing significant disruption to widespread internet usage.

The governance mechanisms in MegaWise (see Chapter 9) can be used to operate domain fronting bridges so that users can access MegaWise services in countries/regions implementing large-scale internet censorship policies. Additionally, the OBFS4 pluggable transport support can be bundled with the service node version of the MegaWise wallet to further protect against DPI.

### 8.2 Denial of Service Attacks

Decentralized blockchains do not require users to provide digital or physical identifiers. This can be beneficial for users who lack identification and therefore face persecution. However, systems that do not require identity make themselves vulnerable to Sybil attacks, where malicious actors generate many fake identities (in MegaWise's case, many public-private key pairs) and use these identities to send a large number of requests to the network.

Many cryptocurrencies are combating this issue and are forced to implement service fee models or proof-of-work models. In service fee models like Siacoin, users pay for the services they use. In the case of Siacoin, the cost is determined based on storage space per terabyte per month. Service fee models effectively reduce Sybil attacks, but they also discourage many users from using the system, especially when similar services are available for free (e.g., Google Drive and OneDrive in the case of Siacoin). Proof-of-work systems like Hashcash and Nano require users to compute a small proof-of-work before sending messages or transactions. These lightweight proof-of-work systems provide some level of fairness compared to service fee models but can be preyed upon by attackers with significant computational power.

MegaWise adopts a modified proof-of-work scheme, based on loki, to address the two most significant Sybil attack vectors in the MegaWise system: offline messaging and path creation. Offline messaging is a potential target as each message needs to be stored by nine nodes. The potential for abuse exists when malicious users overload specific groups and store a large number of messages. In path creation attacks, attackers attempt to participate in the path creation process with as many nodes as possible, occupying bandwidth resources and denying service to users creating paths through the network for legitimate purposes.

To prevent both of these attacks, the MegaWise network requires a short proof-of-work to be attached when creating messages and paths. For messages, the proof-of-work calculation is done based on the Blake2b hash of the message. For path creation, the proof-of-work is sent along with the node request to join the path building process. To ensure scalability and accessibility for mobile users, the difficulty of the proof-of-work is fixed based on the message or path's time-to-live (TTL), rather than global network activity.

### 8.3 Swarm Flagging

Operating in a trust environment without a central leader to enforce global rules makes it difficult to maintain proper node behavior on the network. Although service nodes in MegaWise must hold the correct collateral requirements, they can choose to not forward traffic or store data in their memory pool. Since this choice is financially advantageous (using less bandwidth/CPU cycles/storage), a decentralized tagging system must be proposed to remove underperforming nodes.

Implementing such a decentralized tagging system poses significant challenges for MegaWise. Fundamentally, each service node has an incentive to tag every other service node as a bad actor for financial gain. This is because when a service node is tagged, it will face removal from the stake pool, increasing the odds for the tagger to gain rewards. One potential decentralized tagging approach is to provide evidence when a tagging event occurs, but this solution is vulnerable to node forgery of favorable evidence. On the other hand, unrestricted tagging allows an individual node or a collaborative group of nodes to intentionally tag honest nodes to improve their own chances of winning block rewards. To circumvent these issues, MegaWise proposes Swarm Flagging.

Swarm Flagging works by utilizing existing groups (see 6.1.1) to select members participating in each round of testing. Each service node holds a copy of the blockchain, and each block created by a miner will deterministically choose some testing groups to participate. For each block, 1% of the network groups are selected to participate in the testing groups. To compute the participating groups, a Mersenne Twister is seeded with the hashes of the previous five blocks, and the groups are selected based on their order in the deterministic list.

When a group is selected to participate, each node in that group conducts a series of tests on every other node in the group. These are not active tests; instead, each node stores historical information about interactions with every other node in the group. Information is collected and retained over time regarding bandwidth, message storage, blockchain requests, and the node's functionality as an exit node. New group members who haven't collected this information can query service nodes outside the group to gather data about each service node being tested.

Each service node decides how to vote on other members. Once it makes a decision based on the aforementioned tests, it collects and broadcasts its vote to all members. Now, each node in the group can inspect the votes of all members. If over 50% of the nodes in the group vote against a particular node, any group member has the necessary information to construct a deregistration transaction. Once this transaction is verified and included in a block, all service nodes update their DHT, removing any nodes that were voted out.

#### 8.3.1 Testing Suite

In order for the network to be self-executing performance standards, service nodes must be equipped with the necessary tools to test other service nodes. These tests should cover the full range of functionalities offered by service nodes to prevent delayed primary node attacks. In this initial design, four basic tests are proposed. As service node functionalities expand, additional tests may be added to the Testing Suite.

When an operator runs the service node software for the first time, a pre-allocated file with a predetermined size is assigned on the hard drive to ensure space is reserved for tasks requiring storage. Next, a simple bandwidth test is performed between the service node and a set of test servers geographically distributed, operated by the trusted community. These checks are optional, allowing service nodes to skip, ignore, or fail and join an untrusted pool of service nodes. However, running and passing these tests provides a good indication for any potential service node operators as to whether they should take the risk of locking their stake on a node that may not meet the minimum requirements. Once a service node joins an untrusted service node pool, its stake is locked, and it is tested by the next selected group. Group testing is mandatory and new nodes joining the service node network cannot bypass these tests. If a node passes all group tests, it will be granted a trusted node flag and may begin routing packets. Otherwise, they will be removed from the network, and their stake will remain locked for 30 days.

##### Bandwidth Test

The bandwidth test constitutes the backbone of the MegaWise network testing Suite. If a node passes this test, it is assumed it is routing packets honestly at a speed above the minimum threshold.

Each time a node interacts with another service node, it logs and retains a record of incoming bandwidth. Over time, the node will be included in thousands of paths and route millions of messages. These interactions will form the basis of the node bandwidth table. From this table, a node can respond to bandwidth queries from the service nodes in its group.

All nodes should also respond to queries from other nodes regarding their own bandwidth table. This means even nodes that recently joined the network can query the broader network to gain information about any specific node in their group.

##### Message Storage Test

Message storage is crucial to MegaWise Messenger's offline message functionality. Service nodes must be tested to demonstrate their capability to cache messages and serve users within the message's lifetime.

Users sending offline messages randomly select a service node in the target user's group. That node must distribute copies of the message to the rest of the group. Based on the proof-of-work attached to the message header, receiving service nodes store the data for the TTL. When the TTL of the original message approaches its end, the distributing node sends a nonce to all other members of the group. The group uses the nonce to add to the message and then hash the result, sending it back to the distributing node. This test ensures that service nodes hold the message until the TTL expires, and if they are unable to produce the correct message digest, they will face eviction. As the sampling of distributing nodes is random, over time, each service node will be able to collect performance data on the peers in its group.

##### Blockchain Storage Test

It is planned that service nodes will hold a complete copy of the MegaWise blockchain. By holding a complete copy of the blockchain, service nodes can perform important tasks for network users, including acting as remote nodes, validating transactions, and locking transactions in Blink.
Since honest nodes also hold a copy of the blockchain, dishonest nodes can avoid holding a complete copy by only requesting blocks from honest nodes during testing. To avoid this scenario, the blockchain storage test is designed in such a way that honest nodes can pass the test while dishonest nodes cannot.
To achieve this, the testing node requests each tested node to select K random transactions from the blockchain's transaction history, then connects and hashes these transactions. The hash is then returned to the testing node. By measuring the delay of this request, the testing node can compare the delay to the expected return time T. The value of T is accurately set to a delay between the expected delays of loading blocks from disk and downloading blocks from the network. Downloading and hashing K blocks within T is not feasible for any attacker, making sybil attacks difficult.

##### Exit Node Test

Service nodes chosen as exit nodes receive additional rewards when selected for block rewards, so functional testing is required to ensure the abuse of these additional rewards.
To perform exit node functional testing, service nodes must be able to simulate human-like natural search behavior. If the service nodes can detect that they are being tested, they can only respond to the test and discard legitimate user requests. Simulating natural page request behavior is challenging, but exit testing can be designed in such a way that the cost of distinguishing legitimate requests from tests is sufficiently difficult, making the bandwidth cost difference between running legitimate nodes and malicious nodes negligible.
Service nodes use a locally stored list of search engines combined with a dictionary to construct pseudo-random natural search terms. These search terms are then fed into the search engines, and a webpage is randomly selected from the results. Now, the service node can establish a path using random nodes as relays and use the tested node as an exit node. From this exit node, the service node requests web pages generated by its pseudo-random searches. If the results returned by the exit node match the results generated by the service node, the exit node is considered to have passed the test.

## 9 Governance, Funding, and Voting

Governance is an essential component of cryptocurrency design and should be supported at the protocol level. Weak and informally defined governance risks have been extensively studied in the history of blockchain technology. Bitcoin and Ethereum have experienced controversial hard forks that have diverted the focus and efforts of their respective communities. While hard forks can be used as a governance strategy, they should always be seen as a last resort for resolving contentious issues, rather than as a solution for every dispute. The design of the MegaWise governance system is aimed at addressing potential issues without relying on external influences or altruism by providing a structured environment for discussion and representation, as well as a source of funding for the development of MegaWise.

In addition to preventing hard forks, governance structures should also create means to provide funding for new projects that improve the MegaWise ecosystem internally. Internal funding projects can prevent the formation of special interest groups whose motivations may not align with those of users, miners, or service nodes. We have seen this in Bitcoin as well as various Bitcoin forks, where for-profit companies like Blockstream, Bitcoin ABC, and Bitcoin Unlimited have been accused of hiring developers to make protocol changes for their business goals or following their specific ideological alignment with Bitcoin and Bitcoin Cash.

Therefore, in each MegaWise block, a specific 18.33% reward is allocated for network governance. This provides a stable flow of MegaWise to distribute among community projects, software developers, and integration teams.

### 9.1 MegaWise Community

The MegaWise community is a non-profit organization aimed at promoting the MegaWise blockchain.
X official Twitter account: @MegaWise_Net
The MegaWise community can advance its goals through fundraising, executing plans and projects, providing support and guidance, and others, but every stage's aims will be confirmed by member votes to address increasingly complex organizational management and fully transparent decision-making needs.

Regarding goal decisions, the MegaWise governance community will return decision-making power to community members. For example, MegaWise will promote community member voting to ensure that MegaWise blockchain goal decisions align with the majority of community member goals.
In summary, to further enhance the efficiency and precision of the MegaWise community decision-making process, the following suggested solutions can be considered:

Introduce Core OG Opinions - Core OGs can be invited to participate in discussions and provide suggestions during important decision-making processes. For example, blockchain and related fields' core OGs can be invited to participate in MegaWise community discussions and decision-making processes to better evaluate and choose the course of action to take.
Establish Voting Mechanisms - The MegaWise community can establish a more comprehensive and user-friendly voting mechanism to enable more community members to participate in voting and reduce errors and confusion during the voting process. For example, completely decentralized voting systems can be established using existing blockchain technology.

Increase Discussion Transparency - The MegaWise community can increase discussion process transparency through public discussion and information sharing. For example, issues, opinions, and suggestions can be discussed publicly in community discussion areas, enabling more community members to participate and supervise the decision-making process, resulting in higher transparency and trust.

Establish Risk Management Mechanisms-The MegaWise community can establish a comprehensive risk management mechanism to address unpredictable situations. For example, emergency decision-making procedures can be considered to ensure that decisions can be made quickly in case of emergencies, reducing unnecessary losses.

In conclusion, by introducing core OG opinions, establishing voting mechanisms, increasing discussion transparency, and establishing risk management mechanisms, the MegaWise community can further optimize its decision-making process, improve organizational management efficiency and accuracy, and achieve greater social and industry benefits.

### 9.2 MegaWise Funding System

The total amount of ecological tokens required for approved proposals will either exceed the total accumulated amount during the 30-day period, or be lower than that amount. If the total sum of approved proposals exceeds the available funds in the funding block, miners will build the funding block based on the order in which they were submitted to the blockchain, giving priority to earlier proposals. The remaining approved proposals will be kept on the blockchain until the next funding block.

### 10 Conclusion

MegaWise proposes an anonymous transaction and decentralized communication model built by incentivizing nodes through economics. MegaWise utilizes the foundation of the CryptoNote protocol to ensure privacy and implements a staking node system to enhance network resilience and functionality.
Additionally, MegaWise improves on previous research and open-source projects proposed by the Loki project and adopts a new anonymous routing protocol proposed by Loki. The unique architecture and protocol design of MegaWise combined to create a network with market resistance to Sybil attacks, reducing the effectiveness of time analysis and providing users with a highly digital de-monetized data process.

---
title: A Beginner’s Guide to Blockchain
date: 2018-07-11  19:30:35
tags: Blockchain
---
  
  ![Blockchain](https://i.loli.net/2018/07/11/5b45ea9c1ef9e.jpeg)
  
  I don’t get why people find it difficult to understand Blockchain. I wonder why I myself didn’t. It was in 2013 I first heard about Bitcoin (yea, too late). I was poor to purchase one, so tried mining it. If I had been successful, you wouldn’t be reading this. Later, I thought of studying its underlying technology, the Blockchain. But, I was too busy with my startup (that didn’t work out either).

![161907_UhxM_2896879.png](https://i.loli.net/2018/07/11/5b45eb4509f1c.png)

###So what is this “Blockchain”?

There are two things. A block and a chain. At a very high level, it is just a chain of blocks. Since it’s inside computers, we can rule out the physical stuff. Here digital information is divided into blocks and linked together. For example consider the following blocks, each represent a country. Each of them contains the city names of the respective country.

![1_rujLcCpQ7tvNhGm57nv-jA.png](https://i.loli.net/2018/07/11/5b45eb95e2353.png)


Wait, there is something more. Each of these blocks has something called a hash. A hash is a set of characters (eg. “1hi515AHA5H” ). Hash is derived from the information contained in the block. The block of U.S.A has cities New York, Los Angeles, and Chicago. So the hash would be something like “NYLAC” (Technically that’s not the case, but you get the idea).

![1_G-k0X7mDVanUf9wz8dMpSQ.png](https://i.loli.net/2018/07/11/5b45ebd2496cc.png)


Every successive block will contain the previous block’s hash. This is what binds them together (The force). If someone tampers the first block to add the city Boston. The new hash becomes “NYLACB”. However, the succeeding block of India has already stored the hash as “NYLAC”. This mismatch will break the chain. So the purpose of hash is to make sure no one tampers it.

**What if someone changes the contents of a block and update the hash of successive blocks?** This is possible but there is one thing I didn’t tell you. The data of the blockchain doesn’t lie in one computer. It is replicated in the computers of every user in the network. If you join a blockchain network, your computer will download these blocks. If someone tampers his version, the network will consider what majority say is correct.

One more thing, in a Blockchain network, not only data but the program is also replicated. Computers collectively execute the program. Most internet apps are centralised. Consider Facebook, its data and program lies on its servers. Your computer requests information from Facebook’s server on a need to know basis. In case of blockchain, there is no central thing. It relies on its user’s computer to host its program. Yes, this means if every computer in the blockchain network switches off, it’s dead.

###Public Blockchains

![1_wCoFI8Ohp3M1ZWbtsqFWgA.png](https://i.loli.net/2018/07/11/5b45ec5ce4096.png)

**Does this mean Blockchain is formed by a group of people who keeps their computers running for goodwill? What is the use of these tamper-proof blocks?**

Blockchain networks have one or more functionalities. Bitcoin is a digital currency and a payment system. Its tamper-proof blocks hold ledger of all transactions. The people who sacrifice their computers are called miners. They get rewarded in bitcoins .

Ethereum has an additional functionality. It can host your code. Developing a blockchain from scratch and building your own community would be very difficult (Remember people has to sacrifice their computers for you?) . Ethereum takes care of the heavy lifting. You need to pay a fee depending on the computational costs.

Blockchain apps don’t have to be just payments systems or cryptocurrencies. It could be anything, like a social network, a learning platform like LiveEdu, etc.

###Private Blockchains

![1_UpfvatIr0iTcZv4BrYA4Qg.png](https://i.loli.net/2018/07/11/5b45ec9663b28.png)

**Bitcoin, Ethereum, etc are examples of the public blockchain. Anyone can be a part of it. What if we want to make a private blockchain network? Why would someone need a private blockchain for? Have a look at these stories.**

**Mark and Sara**

Mark hasn’t paid his rent for five months. When Sara questions he promise to pay later. She is helpless. She can’t afford a lawyer. Courts take eight months to almost a year to enforce action. The only option is to persuade Mark.

**Joe’s business**

Joe is a businessman. He does business with different corporates on a frequent basis. A few months ago he signed a contract with a retailer. Though the conditions of the contract were met. The retailer refused to pay. These people take advantage of the legal system and persuade Joe to settle for less pay. Joe had such experiences before. In some cases, he went to court. The time and money he spent there cost him his profits.

**How do we help Sara and Joe?**

Have we solved this problem elsewhere? In Sara’s case, we need to make Mark pay the rent every month. A time-based trigger. Your calendar app uses such trigger to give you notifications of predefined events.

In Joe’s case, once terms of the agreement is met the party needs to pay. It’s a condition based trigger. Consider the last time you purchased an ebook from Amazon. Amazon will only deliver it once the payment is confirmed.

The point is computer programs execute such instructions consistently. It did when you clicked on this article, scrolled down, etc . In order to help Sara, we need to convert the agreements of the contract into code.

**Pseudo code of the smart contract between Sara and Mark**

```
If today’s date is 30th and rent is not paid then
Transfer $500 from Mark’s account to Sara’s account
```

But where do we deploy this code? It should be deployed on computers of all parties involved. Sara’s and Mark’s bank will be part of a private Blockchain network. Joe and Sara will sign a coded contract(a.k.a smart contract). Then it’s deployed on the network. Both Mark’s and Sara’s bank will have a copy. On 30th of every month when the clock ticks 12.00. The agreed amount gets transferred from Mark’s account to Sara’s account. Joe started using smart contracts to enforce his clients to pay the agreed amount.

Sara is happy because she doesn’t have to trust Mark’s consent to transfer rent. Joe’s glad because he doesn’t have to go to a court for justice. Instead, he can spend those efforts to grow his business.
Private blockchain will be restricted to the parties involved in the business. Joe won’t be a part of the Sara’s and Mark’s Blockchain network.

###The Way Ahead

![1_jErKGSY4dEY5N7F0G8Vmuw.png](https://i.loli.net/2018/07/11/5b45ed27b1f3d.png)

Now that you have some idea, you should take this course on edX(It’s free). It will teach you to build apps on Blockchain.


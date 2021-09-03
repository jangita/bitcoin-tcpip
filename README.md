# bitcoin-tcpip
Connect to the bitcoin network and retrieve one transaction information
## Introduction
There is all this talk about bitcoin and blockchain with the structure, how mining works etc, but very few documents or information on how the tcp/ip protocol actually works. This is my attempt on low level connection onto the bitcoin blockchain network

Blockchain technology is built around consensus algorithms which allow distributed nodes to share a common ledger. A fundamental dependency of these algorithms is a common network protocol to enable communication between participating nodes. Today, let's write a Python program from scratch to interact with a real Bitcoin node. This post will assume you're familiar with the fundamentals of blockchain technology. If you aren't, I would recommend checking out the [Bitcoin White Paper](https://bitcoin.org/bitcoin.pdf "Bitcoin White Paper") by [Satoshi Nakamoto](https://en.wikipedia.org/wiki/Satoshi_Nakamoto "Satoshi Nakamoto").

Bitcoin nodes communicate with each other using the TCP protocol. Nodes will typically listen on port number 8333. For a detailed description of the bitcoin network protocol [check out this resource](https://en.bitcoin.it/wiki/Protocol_documentation "check out this resource").

Today, we are going to write a Python program to connect to a Bitcoin node and fetch the details of a specific transaction. Here is a diagram of the message flow that will be developed.

![Data flow](https://github.com/jangita/bitcoin-tcpip/blob/main/4b8fg9fpn3iyq871rxa1.png "Data flow")

Before we start coding our program, we must make one point clear. Interacting with a Bitcoin node using raw TCP sockets is reinventing the wheel. This has already been done by python packages such as [python-bitcoinlib](https://github.com/petertodd/python-bitcoinlib "python-bitcoinlib").

If you want to write sophisticated applications you should definitely use the correct tool for the job. With that said though, programming with TCP sockets is a great way to improve your low level understanding of a network protocol.
## Show me the code!
Well, check out run.py some things to look out for

The struct module is used for packing binary data. The [hashlib](https://docs.python.org/3/library/hashlib.html "hashlib") module is used for generating message checksums. For a full understanding of the code, you'll need to cross reference the data encoding with the [protocol documentation](https://en.bitcoin.it/wiki/Protocol_documentation "protocol documentation").

Please note that not all nodes will be able to return arbitrary transaction data; some will prune their history to save disk space.

To find an IP address of node on the network I used [Bitnodes](https://bitnodes.earn.com/nodes/ "Bitnodes"). Details of the transaction we elected to query can be found on a [block explorer](https://www.blockchain.com/btc/tx/fc57704eff327aecfadb2cf3774edc919ba69aba624b836461ce2be9c00a0c20 "block explorer").
# And that is it! Enjoy!
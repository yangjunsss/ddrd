# Background
Working docker registry and studying block chain technology bring me the idea.

# What's ddr
DDR is a Decentralized Docker Registry based on P2P technology to supply high concurrency, fast transfer, low cost for docker images distribution and storage.It does not requires any centralized service but docker users can push and pull the docker images from the system as usual.As pure P2P network structure model, each node is producer and consumer.

# What's ddrd
Decentralized Docker Registry Daemon(ddrd) is one component of Decentralized Docker Registry system. a daemon running on each P2P node to supply node location, key location, value storage, etc. It uses standard HTTP interface to communicate with other server nodes and client nodes.

More technical detail see my  [blog](http://yangjunsss.github.io/2018-07-05/DDR-%E5%8E%BB%E4%B8%AD%E5%BF%83%E5%8C%96-Decentralized-Docker-Registry-%E9%95%9C%E5%83%8F%E4%BB%93%E5%BA%93%E8%AE%BE%E8%AE%A1/).

# Why
1. High concurrency, 100,000+
2. Reduce network traffic
3. High availability
4. Low cost
5. Long distance transfer
6. Open source

# Reinventing the wheel?
1. Alibaba Dragonfly

  Not a pure distribution service and base on BT protocol, use CDN as storage node.

2. Tencent FID

  Use BT protocol, simulate with Dragonfly but not open source.

3. DID,Quay and Docket

  Make torrent for the whole image,not for layer.



# Design Goal
1. Zero invading
2. High configurable
3. Decoupled with Registry, be independent
4. Full supported API

# Network
The network uses Kademlia/SKademlia protocol to communicate. The main idea of Kademlia/SKademlia is every node organized by fixed bit ID and the distance of node is defined by XOR operation.The distance metric can guide you get close to the destination by ask repeatedly.

![img](http://yangjunsss.github.io/images/kademlia.png)

# Arch
Each node is local registry service server and registry client to push and pull image from other registry service by ddrd. Local registry service supplies image management stuff things to interact with docker client. And we need develop ddr backend driver to handle all necessary request such as getting manifest or blobs.If the driver can't find any message local, it should ask ddrd to find message from remote node.So the ddrd has only one responsibility for finding the message in the P2P network but not for storage.

![ddr](http://yangjunsss.github.io/images/ddr_arch.png)

# Plan
1. August, September, core technical problems finish
2. October, ddrd alpha release
3. November, ddr driver alpha release
4. December, bug fix and beta release

# License

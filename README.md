# What's ddrd
Decentralized Docker Registry Daemon(ddrd) is a daemon process running on each server node for the decentralized docker registry in a P2P system.It supplies HTTP service to interact with other P2P server nodes or client.

More detail see this  [blog](http://yangjunsss.github.io/2018-07-05/DDR-%E5%8E%BB%E4%B8%AD%E5%BF%83%E5%8C%96-Decentralized-Docker-Registry-%E9%95%9C%E5%83%8F%E4%BB%93%E5%BA%93%E8%AE%BE%E8%AE%A1/).

# Motivation

1. High concurrency, 100,000+
2. Reduce network traffic
3. High availability
4. Low cost
5. Long distance transfer

# Design Goal

1. Zero invading
2. High configurable
3. Decoupled with Registry, be independent

# Arch

![ddr](http://yangjunsss.github.io/images/ddr_arch.png)

# Plan

# Contributors
yangjunsss:cj.yangjun@gmail.com

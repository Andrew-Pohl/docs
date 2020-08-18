---
description: A technical guide on how to run you own node.
---

# How to run a node?

## Run Local Node

This guide will walk you trough running your own validator node using a docker image. Please make sure you have access to a continuously running machine, if you like to participate as a network validator.

### Pre-Requisites

A complete [Docker](https://docs.docker.com/) environment is needed to be installed on your system, as well as [Docker-Compose](https://docs.docker.com/compose/)

Make sure that your user is added to the `docker` user-group on _Unix_ systems, if you can't access root permissions to run containers.

*note if using the quickstart this will correctly configure your node and the enviroment.

### Node Definitions:

* Bootnodes - Are required to support the inital syncing of all other node types. They are nodes with known addresses.
* Node - Nodes in the network are used to "peak" into the block chain. They can be used to query the network and send transactions.
* Explorer Node - An explorer node is an "archive" node it holds all the block chains informations for other nodes in the network to access.
* Validator Nodes - These nodes are responsible for validating transactions and maintaining the bridge between Fuse Network and Main Etherum Network.
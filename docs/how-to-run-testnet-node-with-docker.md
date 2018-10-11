# Running testnet node with Docker

There are two types of nodes in DEIP blockchain: **low-memory node** and **full node**.

Low-memory node only stores blockchain important data and is suitable for:
 - seed nodes
 - block producer nodes
 - exchanges, etc.

Full node stores *all* the data (including data for supporting content web site) and has all plugins and APIs enabled.

There is separate Docker image for each type of node, and separate config file in **testnet** repository.

#### Initial setup
No matter what type of node you want to run, there are some common preparation steps we need to perform.

1. Install Docker and Docker Compose
Instructions for ubuntu 16-04 [here](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04) and [here](https://docs.docker.com/compose/install/#prerequisites), don't skip optional step 2 to run docker without sudo

2. To get the latest docker-compose.yml file, clone the repository
```
git clone https://github.com/DEIPworld/deip-testnet
cd deip-testnet
```

3. Pull the latest docker image
```
docker-compose pull
```

Now after we setup everything, we are ready to start the node.

#### Low-memory node
To make it easier to run a witness node, there is `node-config.env` that allows you easily set witness account name and private key.

`DEIPD_WITNESS_NAME` - name of your witness account who will run the node \
`DEIPD_PRIVATE_KEY` - your witness account private key

You can also set `DEIPD_SEED_NODES` parameter if you want your node to connect to already running nodes. Whitespace delimited list of seed nodes (with port).

5. Launch the node
```
docker-compose up node
```

To launch in detached mode 
```
docker-compose up -d node
```

If your account is already selected to active witnesses list, your node will start producing blocks. If not, follow [this instructions](https://github.com/DEIPworld/deip-testnet/blob/master/docs/how-to-become-a-witness.md) to become a witness.

#### Full node
To run a full node no special configuration required. If you want to set seed nodes for full node, you can do it in `fullnode-config.env`.

Launch the full node 
```
docker-compose up full_node
```

To launch in detached mode 
```
docker-compose up -d full_node
```

#### Attach to running node
To see the output of node running in detached mode use `docker attach` command. Ypu need to know container id or name to connect to it. 

Get list of running containers: 
```
docker ps
```

You will see id, name and some other properties of all running containers. Once you have the id (for example purpose we will use `f92768f1dd89`):
```
docker attach f92768f1dd89
```

#### Resync node
[See here](https://github.com/DEIPworld/deip-testnet/blob/master/docs/resync-node.md)
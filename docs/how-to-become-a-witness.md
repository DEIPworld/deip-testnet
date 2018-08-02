# Becoming a witness

1. Сreate an account using wallet [see this tutorial]() and remember the private active key

2. Pull the last docker build from hub.docker.com
([see this tutorial](https://github.com/DEIPworld/deip-testnet/docs/blob/master/how-to-run-testnet-node-with-docker.md))

3. Run the docker package in detached mode
```
docker-compose up -d
```
You can always look at its latest logs
```
docker-compose logs --tail 100
```
And stop it, if needed
```
docker-compose stop
```

4. **To be completed** Run the command line wallet connected to your node to create a witness








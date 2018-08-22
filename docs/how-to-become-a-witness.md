# Becoming a witness

1. Сreate an account using wallet [see this tutorial](https://github.com/DEIPworld/deip-testnet/blob/master/docs/create-account-using-wallet.md) and remember the private active key
2. Import your account key to wallet
3. To become a witness execute `update_witness` command with following parameters: account name, your witness url, your block signing key (public key), your proposed chain properties (account creation fee & maximum block size), boolean showing whether or not you want to broadcast this transaction.
Chain properties object can be empty (default account creation fee & maximum block size values will be used), or user defined in form `{"account_creation_fee":"1.000 TESTS","maximum_block_size":65536}`
```
update_witness "yourAccountName" "yourAccountUrl" DEIP6ioSfo5gbaP3YJ3G7ivXATXSLbFLURsB4Y1MmgBFjfepW9qm6u {} true
```
4. Once your transaction submitted and included in block, you can verify your account is in witnesses list now. To gel a list of all witnesses run `list_witnesses` command with parameters: lower bound witness name (leave empty if you want to list all witnesses), limit of witnesses to show
```
list_witnesses "" 1000
```
As result you should see your account name in the list.
5. To become an active block signing witness you should be selected into active witnesses list.
To do it, you must vote for yourself. You can use any of [shared accounts](https://github.com/DEIPworld/deip-testnet/blob/master/testnet-shared-accounts.txt).
```
vote_for_witness "alice" "yourAccountName" true true
```
Now you can verify your account received votes by running `get_witness` command
```
get_witness "yourAccountName"
```

When your witness gets enough votes, you can start a witness node by providing DEIPD_WITNESS_NAME and DEIPD_PRIVATE_KEY parameters in `fullnode-config.env` and it will start producing blocks



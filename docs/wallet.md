# Wallet

## How to start a wallet

1. Install Docker and Docker Compose
Instructions for ubuntu 16-04 [here](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04) and [here](https://docs.docker.com/compose/install/#prerequisites), don't skip optional step 2 to run docker without sudo

2. To get the latest docker-compose.yml file, clone the repository
```
git clone https://github.com/DEIPworld/deip-testnet
cd deip-testnet
```

3. Pull the latest docker images
```
docker-compose pull
```

4. Execute command
```
docker-compose run wallet -w /var/lib/wallet/wallet.json -s ws://82.196.2.5:8090
```
After this wallet will start and connect to node at 82.196.2.5 (Full-Node supported by DEIP). You can specify different address if you want to connect to different node.
Wallet file is saved to `data` folder.

To stop the wallet, press `Ctrl + P`, `Ctrl + Q`.

To get list of all available arguments execute:
```
docker-compose run wallet --help
```

## Further actions

[How to create account using wallet](https://github.com/DEIPworld/deip-testnet/blob/master/docs/create-account-using-wallet.md)

[How to become a witness](https://github.com/DEIPworld/deip-testnet/blob/master/docs/how-to-become-a-witness.md)

## Available commands
To get full list of all commands supported by wallet, execute `help` command while running wallet.

To get detailed information about command and all parameters, execute `gethelp command_name`, i.e. `gethelp create_account`

### create_account
This method will genrate new owner, active, and memo keys for the new
account which will be controlable by this wallet. There is a fee associated
with account creation that is paid by the creator. The current account
creation fee can be found with the 'info' wallet command.

Parameters:
- creator: The account creating the new account (type: const std::string&)
- newname: The name of the new account (type: const std::string &)
- json_meta: JSON Metadata associated with the new account (type: const	std::string &)
- fee: The fee to be paid for account creation. It is converted to Common tokens for new account (type: const asset &)
- broadcast: true if you wish to broadcast the transaction (type: bool)

### create_account_with_keys
This method is used by faucets to create new accounts for other users which
must provide their desired keys. The resulting account may not be
controllable by this wallet. There is a fee associated with account
creation that is paid by the creator. The current account creation fee can
be found with the 'info' wallet command.

Parameters:
-    creator: The account creating the new account (type: const std::string&)
-    newname: The name of the new account (type: const std::string&)
-    json_meta: JSON Metadata associated with the new account (type: const std::string&)
-    owner: public owner key of the new account (type: const public_key_type&)
-    active: public active key of the new account (type: const public_key_type&)
-    posting: public posting key of the new account (type: const public_key_type&)
-    memo: public memo key of the new account (type: const public_key_type&)
-    fee: The fee to paid for account creation. It is converted to Common tokens for new account (type: const asset&)
-    broadcast: true if you wish to broadcast the transaction (type: bool)

### update_witness
Update a witness object owned by the given account.

Parameters:
- witness_name: The name of the witness account. (type: const std::string&)
- url: A URL containing some information about the witness. The empty string makes it remain the same. (type: const std::string &)
- block_signing_key: The new block signing public key. The empty string disables block production. (type: const public_key_type &)
- props: The chain properties the witness is voting on. (type: const chain_properties &)
- broadcast: true if you wish to broadcast the transaction. (type: bool)

### vote_for_witness
Vote for a witness to become a block producer. By default an account has
not voted positively or negatively for a witness. The account can either
vote for with positively votes or against with negative votes. The vote
will remain until updated with another vote. Vote strength is determined by
the accounts vesting shares.

Parameters:
- account_to_vote_with: The account voting for a witness (type: const std::string&)
- witness_to_vote_for: The witness that is being voted for (type: const std::string&)
- approve: true if the account is voting for the account to be able to be a block produce (type: bool)
- broadcast: true if you wish to broadcast the transaction (type: bool)

### transfer
Transfer funds from one account to another. DEIP and SBD can be
transferred.

Parameters:
- from: The account the funds are coming from (type: const std::string&)
- to: The account the funds are going to (type: const std::string&)
- amount: The funds being transferred. i.e. "100.000 TESTS" (type: const asset&)
- memo: A memo for the transactionm, encrypted with the to account's public memo key (type: const std::string&)
- broadcast: true if you wish to broadcast the transaction (type: bool)

### transfer_to_common_tokens
Transfer DEIP into a vesting fund represented by vesting shares (VESTS).
VESTS are required to vesting for a minimum of one coin year and can be
withdrawn once a week over a two year withdraw period. VESTS are protected
against dilution up until 90% of DEIP is vesting.

Parameters:
- from: The account the DEIP is coming from (type: const std::string&)
- to: The account getting the VESTS (type: const std::string&)
- amount: The amount of DEIP to vest i.e. "100.00 TESTS" (type: const asset&)
- broadcast: true if you wish to broadcast the transaction (type: bool)

### create_vesting_contract
Create new vesting contract

Parameters:
- creator: The account who creates vesting contract (type: const std::string&)
- owner: The account who owns tokens from contract (type: const	std::string&)
- balance: Amount to vest (i.e. "1.000 TESTS") (type: const asset&)
- vesting_duration_seconds: Duration of vesting in seconds (type: const	uint32_t&)
- vesting_cliff_seconds: Duration of vesting cliff in seconds (type: const uint32_t&)
- period_duration_seconds: Duration of withdraw period in seconds (funds will be available every period, i.e. every 3 months) (type: const uint32_t&)
- broadcast: (type: const bool)

### withdraw_vesting_balance
Withdraw from vesting contract. Only withdraws the amount available for
withdrawal

Parameters:
- vesting_balance_id: The account who created vesting contract (type: const int64_t&)
- owner: The account who owns tokens from contract (type: const std::string&)
- amount: Amount to withdraw (i.e. "1.000 TESTS") (type: const asset&)
- broadcast: (type: const bool)

### get_active_witnesses
Returns the list of witnesses producing blocks in the current round (21
Blocks)


# Create account using wallet

In order to create an account, any other user should issue a transaction for account creation.
Account who will issue this transaction will also pay account creation fee, which will be credited to new accounts Common tokens balance.\
For testnet users we prepared [shared accounts](https://github.com/DEIPworld/deip-testnet/blob/master/testnet-shared-accounts.txt) that you can use for testing and creation of new accounts

## Create account with keys

1. Start wallet [see this tutorial](https://github.com/DEIPworld/deip-testnet/blob/master/docs/wallet.md)
2. Set password for wallet file
```
set_password yourSecretPassword
```
3. Unlock the wallet
```
unlock yourSecretPassword
```
4. Import private key of one of the [shared accounts](https://github.com/DEIPworld/deip-testnet/blob/master/testnet-shared-accounts.txt)\
Let's take 'alice' for this example
```
import_key 5JGoCjh27sfuCzp7kQme5yMipaQtgdVLPiZPr9zaCwJVrSrbGYx
```
5. Generate new keys. You can use up to 4 keys for owner, active, posting authorities and memo; or you can use single key and update them later
```
suggest_brain_key
```
**Make sure you saved the keys!**\
For this example, let's say following keys were generated
```
{
  "brain_priv_key": "CHOLANE MORTIER MIZZLY ELBOW ADAYS SUNKET SUBBASS SHIMMER FLEWS KRAL EXPORT PELTATE UNBUSH CRUCIFY SULK ANNUAL",
  "wif_priv_key": "5JEHAET62qWq1Mep3qZhWe2QhTDzF2uzWwgg6DGCify56VBrUkR",
  "pub_key": "DEIP6ioSfo5gbaP3YJ3G7ivXATXSLbFLURsB4Y1MmgBFjfepW9qm6u"
}
```
6. Create account. This method takes following parameters: creator name, new account name, json metadata (can leave empty), owner key, active key, posting key, memo, and boolean showing whether or not you want to broadcast this transaction
```
create_account_with_keys "alice" "yourAccountName" "" DEIP6ioSfo5gbaP3YJ3G7ivXATXSLbFLURsB4Y1MmgBFjfepW9qm6u \
 DEIP6ioSfo5gbaP3YJ3G7ivXATXSLbFLURsB4Y1MmgBFjfepW9qm6u DEIP6ioSfo5gbaP3YJ3G7ivXATXSLbFLURsB4Y1MmgBFjfepW9qm6u \
 DEIP6ioSfo5gbaP3YJ3G7ivXATXSLbFLURsB4Y1MmgBFjfepW9qm6u true
```

After transaction was included in block, your account should be created. To verify your account exists run following command:
```
get_account "yourAccountName"
```
As result you should see info about your newly created account.

7. Now you can import key of your new account to wallet (see step 4) and use it





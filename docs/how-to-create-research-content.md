# Create a research content using wallet

**IMPORTANT NOTICE:** To create a research content you have to supply content hash (hash of your document).
This way in testnet you can timestamp your data, but you will be responsible for storing the original content file.
DEIP will later provide decentralized storage solution that will store your data and supply hash to DEIP blockchain automatically.\
To calculate hash of your data you can use online hash calculation services.

1. Start wallet [see this tutorial](https://github.com/DEIPworld/deip-testnet/blob/master/docs/wallet.md)
2. [Create a research ](https://github.com/DEIPworld/deip-testnet/blob/master/docs/how-to-create-a-research.md)
3. To propose creation of research content run `propose_create_research_content` command, which takes following parameters:
- creator name
- id of research group
- id of research
- type of content (announcement = 1, milestone = 2, final_result = 3)
- title
- hash of content
- permlink
- list of author accounts (i.e. `[alice, bob, charlie]`)
- list of ids of referenced contents (i.e. `[1, 10, 20]`)
- list of external references (URL of referenced papers) (i.e. `["google.com", "bing.com"]`)
- broadcast: boolean showing whether or not you want to broadcast this transaction
```
propose_create_research_content "yourAccountName" 0 10 2 "content title" "content_hash" "content-permlink" ["alice", "bob"] [10] ["google.com"] true
```
After transaction was included in block, proposal to add a research content will be created.
4. To list proposals in research group use following method and provide desired research group id:
```
list_research_group_proposals id_of_research_group
```
As result you should see a list of all proposals in research group.
5. To vote for specific proposal use `vote_proposal` method:
```
vote_proposal "yourAccountName" id_of_proposal id_of_research_group true
```
When enough accounts vote for proposal and quorum percent is achieved - proposal will be accepted and content is created.





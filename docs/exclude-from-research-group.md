# Exclude member from research group

1. To propose exclude member from research group run `propose_exclude_member` command, which takes following parameters:
- proposal creator name
- account to exclude
- id of research group
- broadcast: boolean showing whether or not you want to broadcast this transaction
```
propose_exclude_member "yourAccountName" "AccountNameToExclude" 0 true
```
After transaction was included in block, proposal to exclude a member from research group will be created.
2. To list proposals in research group use following method and provide desired research group id:
```
list_research_group_proposals id_of_research_group
```
As result you should see a list of all proposals in research group.
3. To vote for specific proposal use `vote_proposal` method:
```
vote_proposal "yourAccountName" id_of_proposal id_of_research_group true
```
When enough accounts vote for proposal and quorum percent is achieved - proposal will be accepted and specified account will be excluded from research group.


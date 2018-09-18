# Invite member to research group

1. [Create a research group](https://github.com/DEIPworld/deip-testnet/blob/master/docs/how-to-create-a-research-group.md)
2. To propose invite member to research group run `propose_invite_member` command, which takes following parameters:
- proposal creator name
- account to invite
- id of research group
- percent of research group tokens invited account will receive (0 to 10000)
- message for invited account
- broadcast: boolean showing whether or not you want to broadcast this transaction
```
propose_invite_member "yourAccountName" "invitedAccountName" 0 3000 "motivation to join my research group" true
```
After transaction was included in block, proposal to invite a member to research group will be created.
4. To list proposals in research group use following method and provide desired research group id:
```
list_research_group_proposals id_of_research_group
```
As result you should see a list of all proposals in research group.
5. To vote for specific proposal use `vote_proposal` method:
```
vote_proposal "yourAccountName" id_of_proposal id_of_research_group true
```
When enough accounts vote for proposal and quorum percent is achieved - proposal will be accepted and invite is sent to specified account.

# Accept or reject invite to research group
As a member who was invited to research group you can accept or reject the invitation.

1. To list your invites, use `list_my_research_group_invites`
2. To **accept** invite use `approve_research_group_invite` command; to **reject** invite use `reject_research_group_invite` command. Parameters:
- id of invite
- account who is invited
- broadcast
```
approve_research_group_invite 0 alice true
```
```
reject_research_group_invite 0 alice true
```

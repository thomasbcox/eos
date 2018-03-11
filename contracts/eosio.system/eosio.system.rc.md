# Ricardian Contract

This Ricardian Contract is legally binding and can be used in the event of a dispute. Disputes shall be settled through this system's adopted arbitration process.

## Description

The `eosio.system` contract provides basic system commands for the blockchain.

## Action(s), Input(s) and Input Type(s)

The table below contains the `action(s)`, `input(s)` and `input type(s)` for the `eosio.system` contract.

| Action | Input | Input Type |
|:--|:--|:--|
| `transfer` | `from`<br/>`to`<br/>`quantity`<br/>`memo`<br/> | `account_name`<br/>`account_name`<br/>`asset`<br/>`string`<br/> |
| `issue` | `to`<br/>`quantity`<br/> | `account_name`<br/>`asset`<br/> |
| `nonce` | `value` | `string` |
| `regproducer` | `producer`<br/>`producer_key`<br/> | `account_name`<br/>`bytes`<br/> |
| `cfgproducer` | `producer`<br/>`config`<br/> | `account_name`<br/>`???`<br/> |
| `okproducer` | `producer`<br/>`vote`<br/> | `account_name`<br/>`boolean`<br/> |
| `setproxy` | `account`<br/>`proxy`<br/> | `account_name`<br/>`account_name`<br/> |
| `stakevote` | `voter`<br/>`amount`<br/> | `account_name`<br/>`asset`<br/> |
| `unstake` | `voter`<br/>`amount`<br/> | `account_name`<br/>`asset`<br/> |
| `freeze` | `producer`<br/>`account`<br/>`truefalse`<br/> | `account_name`<br/>`account_name`<br/>`boolean`<br/> |
| `paystandby` | `producer`<br/> | `account_name`<br/>|


### Transfer
As an authorized person, I ${from} hereby transfer to ${to}, a party

1. whose identity is known to me,
2. who has consented to receive this transfer from me,

the amount of ${quantity}. I further wish to memorialize this transaction by including in it the text ${memo}.
### Issue
As an authorized person, I hereby issue to ${to}, a party

1. whose identity is known to me,
2. who has consented to receive this issuance from me,

the amount of ${quantity}. 

### Nonce
As an authorized user of this system I request a nonce return based on the input ${value}.
### RegProducer
As a self proclaimed candidate for block producer, I hereby register myself with the ID ${producer} and the producer key ${producer_key}, which I stipulate are mine. I further stipulate that I am authorized to do this.
### CfgProducer
As a self proclaimed candidate for block producer, I ${producer} stipulate that my block producer configuration settings shall now be ${config}, which I further stipulate are accurate and I invite others to make decisions relying on my statement.
### OKProducer
As an authorized person I wish to register on behalf of ${account} a vote ${vote} regarding Producer ${producer} equal to all my current vote-staked tokens. By passing in TRUE I wish to vote in favor, and by passing in FALSE I wish to remove a prior vote in favor. I agree not to accept payment of any kind in exchange for my vote, on penalty of confiscation of my tokens and freezing of my account.
### SetProxy
As an authorized person I hereby empower ${proxy} to cast all votes of vote-staked tokens owned by ${account}.
### Stakevote
As an owner of EOS Tokens, I ${voter} wish to stake ${amount} of tokens for purposes of voting on this blockchain. 

* I am aware of the current rules regarding token staking, including token lockups. 
* I agree not to accept payment of any kind in exchange for my vote, on penalty of confiscation of my tokens and freezing of my account. 
* I understand that if I already have votes registered, increasing my staked-for-voting amount via 'stakevote' immediately increases those existing votes by ${amount}.
 
### Unstake
As an owner of EOS Tokens, I ${voter} wish to unstake ${amount} of tokens from voting on this blockchain. I am aware of the current rules regarding token staking, including token lockups. I am aware that this action will remove all my votes immediately. I am aware that my voting-unstaked tokens will return from lockup to their liquid state on a schedule established in the rules of this system.
### Withdraw
*command is called by unstake and has no Ricardian contract*

System Intention: To move the correct amount of unstaked tokens from the unstaking state to the liquid state.

### OnBlock
*command is called by unstake and has no Ricardian contract*

System Intention: To issue the correct number of new tokens appropriate for the creation of a new block, and to place those tokens into the correct locations, i.e. half into the account of the block producer, and half into the standby pay bucket.
### Freeze
As an authorized block producer, I ${producer} agree that, based on evidence presented to me, the account ${account} should be [ if TRUE: frozen || if FALSE: unfrozen ] immediately. 

*When 15 producers agree the @producers permission is invoked and this commmand takes effect.*
### PayStandby
As an authorized active or standby block producer, I ${producer} hereby request my account be credited with the 'standby pay' for which I am eligible.

*Callable once per day per producer; each "eligible producer" is eligible for (their total votes / allvotes) worth of the currently available standby pay. A producer is "eligible" if they rank in the top 121*

## Signatures

**Provider:** `EOS123abc`

**User:** `EOSdef456`

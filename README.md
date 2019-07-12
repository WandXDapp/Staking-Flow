# Staking Flow
This page will allow users to stake their spare tokens on platform such as Livepeer, Tezos etc and earn rewards.

# 1. Livepeer Staking
Users can ‘bond’/’stake’ their Livepeer Tokens (LPT) to transcoders (validators), which perform the task of transcoding (i.e. converting video streams from some bit rates to required bit rates). Rewards need to be claimed. Once claimed, the rewards will be added to their total staked tokens. Now if the users wish to receive this reward, along with the principal, they can ‘unbond’ their tokens, and after a cooling (unbonding) period of approximately 7 days, they can withdraw their (principal + reward) into their wallets.  
Basic flow for *Livepeer Staking* is explained below.

## Welcome Screen
*Account Information* (Ethereum Address, Eth Balance and LPT Balance), *Bonding Information* (Status, Bonded Amount, Last Claimed Round, Deleagted Address), *Round Information* (Current Round, Block Count Before Next Round, Round Status) will be displayed after successful page loading.

## Step - 1 (Initialize Round)
- *Round Status* must be **Initialized** before user performs any staking related action. Otherwise error message will be displayed.
- Although for Mainnet *Round Status* generally remains as **Initialized**.

Under ***Round Information*** option user click **Initialize Round** button.

### Response
If transaction is successful, *Round Status* will be updated, otherwise error message will be displayed.

## Step - 2 (Set Allowance)
- User need to set allowance so that while bonding, the proxy contract can spend LPT token on behalf of user.
- Setting relatively higher allowance will save subsequent transaction fees.

Under ***Allowance Information*** option user need to enter amount (in LPT) and click **Submit** button.

### Response
If transaction is successful, *Remaining Allowance* will be updated to new value, otherwise error message will be displayed.

## Step - 3 (Bond Tokens)
- At any given instance tokens can be bonded towards at most *1 Transcoder* only.
- User can select different *Transcoders* from the dropdown and choose one of them based on *Fee Share*, *Reward Cut* and *Total Stake* parameters.
- If user select different transcoder (than the address user currently delegated to) and do bonding then delegated address will be updated. Previously bonded amount will now be bonded towards new transcoder.
- User can also increase bonded amount by selecting same transcoder.

Under ***Bond Tokens*** option user need to select one transcoder, enter amount to bond (in LPT) and click **Submit** button.

### Response
**Case 1**: If *Round Status* is not **Initialized** or *Entered Amount* is more than *Remaining Allowance* or *Entered Amount* is more than *LPT Balance* then error message will be displayed.  
**Case 2**: Otherwise transaction will be submitted to blockchain, and on confirmation details will be updated.

## Step - 4 (Claim Earnings)
- After each round transcoder shares a portion of their earning with the delegators. User need to manually *Claim Earning* to add the amount to already bonded amount.
- User can also claim earnings collectively for multiple rounds (at max 100 rounds).
- When user do **Bond Token** or **Unbond Token** then automatically unclaimed earnings will gets claimed.

Under ***Earning information*** option user need to click **Claim Earnings** button.

### Response
**Case 1**: If *Round Status* is not **Initialized** then error message will be displayed.  
**Case 2**: Otherwise all earnings till maximum possible round will be claimed and the earning will be added to already bonded amount.

## Step - 5 (Unbond Tokens)
- Unbonded token can be withdrawn after a cooling period of 7 rounds (7 days approx.)

Under ***Unbond Tokens*** option user need to enter *Amount to Unbond* and click **Submit** button.

### Response
**Case 1**: If *Round Status* is not **Initialized** or *Entered Amount* is more than *Bonded Amount* then error message will be displayed.  
**Case 2**: Otherwise on successful transaction the amount will be added to **Withdraw Stake** table.

## Step - 6 (Withdraw Stake)
User need to click **Withdraw Stake** corresponding to any row under *Withdraw Stake* table.

### Response
**Case 1**: If *Round Status* is not **Initialized** or **Cooling Period** is not finished then error message will be displayed.  
**Case 2**: On successful transaction the amount will be added to *LPT Balance*, which can later be used as desired by user.

# 2. Tezos Staking
Users have to perform staking from inside their wallets itself. They will stake their XTZ to entities known as ‘delegates’ which run the tezos blockchain. The rewards will start being deposited directly into their wallets after an approximate span of 20 days. Meanwhile their staked tokens will be stored in another account (KT1…) inside their wallets, which they have complete access to.  
Basic flow for *Tezos Staking* is explained below.

## Welcome Screen
*Tezos Address*, current *XTZ Balance* will be displayed. Also list of all *KT1...* addresses generated from this account along with details specific to *KT1...* address will be shown.

## Step - 1 (Originate Account)
- User requires *KT1...* address to start delegate XTZ.
- Creating new *KT1...* will require a fee of *0.257 XTZ*.

Under ***New Origination*** option user need to enter amount (this amount will be balance of the *KT1...* account) and click **Submit** button.

### Response
If *Available Balance* is greater than equal to *Entered Amount* + *Account Creation Fee (0.257 XTZ)* + *Gas Fee* then transaction will be submitted to blockchain. Once it is included in a block then *New KT1...* address will appear on the table. If transaction fails error message will be displayed.

## Step - 2 (Set Delegation)
- Already created *KT1...* address can be used to set delegation.
- Gas fee will be deducted from the balance of corresponding *KT1...* address itself.
- Rewards will start getting credited automatically 20 days (approx.) onward.
- User can also change baker any time. But each time user has to bear the gas fee.

Under ***Set Delegation*** option user new to enter *Serial No* of *KT1... address* and *TZ... address* of a baker and click **Submit** button. User can find list of bakers on *tzscan.io*.

### Response
On success the details corresponding to *KT1... address* will be updated on table, otherwise error message will be displayed.

## Step - 3 (Transfer Tezos) [Optional]
- Users can transfer XTZ from their *tz... or KT1... address* to any other address.
- Gas fee will be deducted from corresponding account only.
- Any amount added to *KT1...* address will be eligible for reward only after 7 cycles (20 days approx.).

Under ***Transfer Tezos*** option user need to enter *From Account*, *To Account*, *Amount* and click **Submit** button.

### Response
On successful transfer, page will load updated details, otherwise error message will be displayed.

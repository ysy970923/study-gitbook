# Decentralized Finance

### Anchor Protocol ([website](https://www.anchorprotocol.com))

* where: Terra
* Earn (deposit):
  * deposit UST to earn yield
  * fixed constant (almost) yield of 20%
  * aTerra (aUST):
    * receipt for the deposit
    * price rises (APY)
* Borrow:
  * bAsset (bLuna, bEth):
    * bonded asset
    * used as collateral
    * burning back to Asset takes time (\~ 21days)
  * provide collateral and borrow UST
  * ANC tokens are distributed to borrowers (until planned)
  * Borrow APR: interest to pay in return
  * Distributed APR: ANC rewards
  * net APR: Distributed APR - Borrow APR
    * if (+), rewards are higher than interest
* ANC token:
  * ANC tokens generate a buying pressure that increases proportionally with Anchor's AUM. Protocol fees are used to purchase ANC tokens from Terraswap, which are then distributed as staking rewards to ANC stakers.
  * Protocol fees:
    * ANC captures protocol fees generated from Anchor, where 10% of the value flowing into the yield reserve is used for the value accrual of ANC tokens. Anchor's protocol fees are sourced from bAsset rewards, excess yield, and collateral liquidation fees.
  * Governance Fees:
    * ANC token deposits of Anchor governance polls that have failed to reach the required quorum are redistributed to ANC stakers as staking rewards.
* how to get profit:
  * both Borrowing and Earning earns profit
  * if want fixed profit: deposit UST
  * long position on luna: borrow UST for luna as collateral
* is it sustainable?:
  * ANC rewards until year 4
  * Borrower and Lender both profits, how?
    * Asset (luna, eth) staking
    * ANC rewards (growing yield reserve)
  * if ANC rewards go down, borrowers goes down, less collateral, less staking rewards

### Prism Protocol ([website](https://prismprotocol.app))

* where: Terra
* what is it?
  * refract(split) Luna into yield & principal tokens
  * yLuna can be staked just like Luna staking
  * pLuna can be sold
  * to redeem Luna, need pLuna & yLuna pair
* how to use:
  * split Luna -> (pLuna & yLuna)
  * stake yLuna
  * sell pLuna
  * if you want to redeem Luna, buy pLuna then merge back to cLuna -> Luna (takes time from cLuna -> Luna)

### Mirror Protocol ([website](https://www.mirror.finance))

* where: Terra
* what is it?
  * mirrors(follows) off chain asset prices
* how to use:
  * mint mirror assets with collaterals
  * writing...

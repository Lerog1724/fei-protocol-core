---
description: An ETH specific FEI bonding curve
---

# EthBondingCurve

## Contract

[EthBondingCurve.sol](https://github.com/fei-protocol/fei-protocol-core/blob/master/contracts/bondingcurve/EthBondingCurve.sol) implements [BondingCurve](https://github.com/fei-protocol/fei-protocol-core/blob/master/contracts/bondingcurve/BondingCurve.sol)

## Description

A bonding curve implementation for purchasing FEI with ETH.

Let _x_ be the current amount of FEI issued from the bonding curve, _S_ be the Scale target and _O_ be the oracle price reported as underlying per FEI. The price function used is:

![Price function for FEI/ETH bonding curve](../../.gitbook/assets/screen-shot-2021-02-14-at-4.11.48-pm.png)

The "k" shift is an additional feature since the white paper release. It helps shift the starting price upward so the protocol can retain more [PCV](../protocol-controlled-value/). K is initially set to `S/3` which makes the starting price $0.50 per FEI.

The amount of FEI out for a given quantity of ETH input _Q_ is equal to the following:

![](../../.gitbook/assets/bonding-curve-integral-with-shift.png)

The Scale target is 100,000,000 FEI.

The oracle used is the [UniswapOracle](https://github.com/fei-protocol/fei-protocol-core/wiki/UniswapOracle).

## [Access Control](../access-control/) 

* Minter💰

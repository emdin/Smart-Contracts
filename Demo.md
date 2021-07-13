Loan Wolf Demo API Outline
========================

# Motivation

We're building a LW demo for the customizable over-collateralized lending with the flexible type of collateral. Idea is to promote in into the MVP of the protocol if demo gets traction.

Following list of proposed changes and additions (TBC = to be changed, TBI = to be implemented):

## Create Pool

Create a new lending pool (in terms of contract, Pool == Loan).  
Will be called with hardcoded values for demo

TBC
* Remove borrower check, so anyone can create Pool
* Add param address _creator to keep info about Pool creator

```Solidity
function ERC20PaymentStandard.configureNew()
```

## Get list of Pools

Return full list of Pools which exists in the protocol for the given contract

TBI

```Solidity
function ERC20PaymentStandard.getPools() returns loans[]
```

## Deposit to the pool

Lender can deposit any token to the pool, which later can be borrowed by the Borrower.
For the demo we only support DAI.

TBI

```Solidity
function ERC20PaymentStandard.deposit(address depositor, address erc20, uint256 amount) returns boolean
```

## Withdrawal

Lender can withdraw non-locked deposit from the pool

```Solidity
function ERC20PaymentStandard.withdrawDeposit(address erc20, uint256 amount) returns boolean
```

## Add collateral to the pool

Borrower should add collateral before borrowing.

```Solidity
function ERC20CollateralPayment.addCollateral(address _ERC20Contract, uint256 _ammount, uint256 _loanId)
```

## Borrow from the pool

Borrower can borrow from the pool for which he/she added collateral.
For the demo we only support DAI.

TBI

```Solidity
function ERC20PaymentStandard.borrow(address erc20, uint256 amount, uint256 loanId) returns boolean
```

## List of Loans

Borrower can see list of pools he/she added collateral and/or borrowed from with specific information about borrrowed amound and payment properties.
Returns list of pools where sender added collateral or borrowed money

TBI

```Solidity
function ERC20PaymentStandard.getLoans(uint256 amount, uint256 id) returns loans[]
```

## Loan repayment

Borrower can repay loan partially or in full by sending DAI to the contract.

```Solidity
function ERC20PaymentStandard.payment(uint256 _id, uint256 _erc20Ammount) returns boolean
```

## Collateral withdrawal

Borrower can withdraw its collateral, partially or in full, depending on the repayment status.  

```Solidity
function ERC20CollateralPayment.returnCollateral(uint256 _loanId)
```

## Collateral liquidation

When borrower misses the payment, protocol or 3rd party can liquidate its delinquent loan.  

TBC
* Add support for the exchange protocol for liquidating the collateral

```Solidity
function ERC20CollateralPayment.withdrawl(uint256 _id, uint256 _amm)
```

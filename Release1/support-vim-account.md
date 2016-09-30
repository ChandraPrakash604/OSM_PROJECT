# Support for VIM account and RO account #

## Proposer ##
Rajesh Velandy (RIFT.io)

## Type ##
**Feature** (do not modify)

## Target MDG/TF ##
UI, SO, RO

## Description ##
Release 0 account management  has some flaws in how it  treats RO and  VCA  accounts,
* The RO account is added as a cloud account which is incorrect - RO account is a different account
  than "cloud" which is  more a  "VIM" account.
* The use of term "cloud account" can be confusing.
* The VCA account is limited to a single account per launchpad.

The feature proposes the following changes,
1. Add support for a new account type -  RO accounts.
2. Change the  term "cloud account" to "vim account" in the UI.
3. Change the  VCA account to a single account per launchpad.

## Demo or definition of done ##
Should demonstrate the following:
1. A user should be able to configure openMANO as an  RO account in launchapd.
2. A user should be able to configure one or more  VIM accounts in launchpad.
2. When a VIM account is provisioned in the system, the UI/SO should pass the account details to
   the RO.
3. The VCA account should be limited to a single account per launchpad.


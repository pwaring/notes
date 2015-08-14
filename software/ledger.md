# Ledger

Aim to help out small businesses and charities but also update my Java skills.

## Data storage

One SQLite 3 database for each set of accounts.

## Features

Everything will be based around a simple ledger system with the five types (Assets, Liabilities, Capital, Income and Expenses). Some extra features will be added to allow processing of common transactions (e.g. receipt and cashing of cheques) without needing to understand the ledger entries.

 * Production of invoices
 * List of incoming payments

## Bookkeeping notes

Balance of an account is the total of all debits/credits on that account and all sub-accounts. Probably easiest to calculate balances recursively, by going all the way down to the leaf accounts and then back up again, i.e. treating the network of accounts as a tree structure.

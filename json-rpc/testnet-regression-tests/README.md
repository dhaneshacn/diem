# Testnet Regression Testsuite

This testsuite executes regression test cases against the testnet.

## Overview

* This testsuite act as safetynet for new version deployment on testnet and also checks regression due to infra changes.
* This testsuite is derived from JSONRPC integeration testcases, but it uses Rust SDK and targets Testnet.
* All stable JSONRPC integeration testcases are ported here. If new test case is added in Integration test, then same test should be implemented in this testsuite.

## Test Coverage
    This test case covers all JSON RPC apis, along with following functionalites
    1. designated dealer account creation and preburn funtionality.
    2. Offchain APIs :- multiagent dual attestation.
    3. Rotating parent vasp account compliance key.
    4. Treasury Compliance account.
    5. create parent and child vasp account
## Implementation Details

* This testsuite uses environment variables to set treseaury account address and its private key, to avoid security risk.
* These test cases must be run in sequence, in a single execution thread. So these testsuite should be ignored for the CI test execution.
* Dual attestation limit must be set for testnet before executing this testcases.

## Execution
```
TC_ACCT_ADDR="<treasury account address>" TC_ACCT_PRIV_KEY="<treasury account 64 byte private key>" JSON_RPC_URL="<testnet json rpc url>" FAUCET_URL="<mint url>" cargo x test --package testnet-regression-tests -- --test-threads 1 --exact --nocapture --ignored
```
Both JSON_RPC_URL & FAUCET_URL environment variables are optional.

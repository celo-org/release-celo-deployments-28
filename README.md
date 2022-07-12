# Release Celo Deployments Wave 28

This repository contains the `ReleaseCelo` configurations that will be deployed in the wave 28 deploy on or around 7/15/22.

Please take this chance to verify your grant's inclusion and the relevant information.

## Verification

In order to verify your grant, first reference the json file within `deployment_jsons` to which you have been assigned.

Then, search for your submitted address using cmd+f (mac) or cntrl-f (windows);
* Multiply "amountReleasedPerPeriod" by "numReleasePeriods"and verify that the total matches your expectations for each respective address.
* Verify the "releaseStartTime" is the same as your purchase date. A start date value of "MAINNET" indicates that the start date will be dynamically assigned to the current time at deployment.
* Verify the "numReleasePeriod" times "releasePeriod" (in seconds) is consistent with your grant length(in months). For example, a 4 year grant will be have a `releasePeriod` of `2,628,000` and `numReleasePeriods` of `48` for a total of `126,144,000` seconds.
* Verify the "releaseCliffTime" (in seconds) is consistent with your expectation. Note 31536000 seconds is equivalent to 1 year.

We also strongly recommend that you do a small test transaction on the Alfajores Testnet to double check that you indeed have access to the address that you are checking. Feel free to follow the [instructions here](https://docs.celo.org/operations-manual/summary/ledger#performing-a-test-transaction).

## Deployment

Around 7/15/22, we will be deploying these configs (with any necessary changes). This deployment is done using a script available in the [celo monorepo](https://github.com/celo-org/celo-monorepo/blob/master/packages/protocol/scripts/bash/deploy_release_contracts.sh). This script is run from the `celo-monorepo/packages/protocol` directory like this:

```
# In `celo-monorepo/packages/protocol`
./scripts/bash/deploy_release_contracts.sh -n rc1 -f 0x5409ED021D9299bf6814279A6A1411A7e866A631 -g deployment_jsons/deployment_0.json
```

Once this is done, we will be publishing a mapping:

```
{
  {YOUR_ADDRESS}: {YOUR_CONTRACT_ADDRESS}
}
```

For you to reference to perform actions on your contract. You can find more information on `ReleaseCelo` (previously `ReleaseGold` [here](https://docs.celo.org/celo-gold-holder-guide/release-gold).

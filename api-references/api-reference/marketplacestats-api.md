# MarketplaceStats API

{% hint style="info" %}
The MarketplaceStats API retrieves aggregated information for a particular NFT marketplace.
{% endhint %}

{% hint style="success" %}
Timeframe filter details (all times are in UTC) for when the sale transactions are captured for the aggregation:

Daily - starts from 00:00 am to 11:59 pm every day

Weekly - starts from 00:00 am on Monday to 11:59 pm on the same week Sunday

Monthly - 00:00 am on the first calendar day of the month to 11:59 pm on the last calendar day of the month. If querying the current month, the aggregation would be from the first calendar day to the most recent daily aggregation.

Yearly - 00:00 am on the first day of the year to 11:59 pm on the last day of the year. If querying the current year, the aggregation would be from the first calendar day to the most recent daily aggregation.

Lifetime - from the first recorded sale to the most recent daily aggregation.&#x20;
{% endhint %}

### Inputs & Filters

```graphql
input MarketplaceStatFilter {
averageSalePriceInUSDC: 
dappName: # Marketplace DApp name
dappSlug: # Marketplace DApp slug (contract version)
firstTransactionBlockTimestamp: 
highestSalePriceInUSDC: 
lastTransactionBlockTimestamp: 
lowestSalePriceInUSDC: 
totalSalesCount: 
totalSaleVolumeInUSDC: 
timeframe: DAILY / WEEKLY / MONTHLY / YEARLY / LIFETIME
}
```

### Outputs

```graphql
type MarketplaceStat {
averageSalePriceInNativeToken: Float
averageSalePriceInUSDC: Float
blockchain: Blockchain # Blockchain where the NFT sale transaction took place
chainId: String # Unique blockchain identifier
dappName: # Marketplace DApp name
dappSlug: # Marketplace DApp slug (contract version)
dappVersion: String # Airstack unique dapp version number
firstTransactionBlockTimestamp: Time
highestSalePriceInNativeToken: Float
highestSalePriceInUSDC: Float
highestSaleTransactionId: String
id: ID! # Airstack unique identifier for this particular element
lastTransactionBlockTimestamp: Time
lowestSalePriceInNativeToken: Float
lowestSalePriceInUSDC: Float
lowestSaleTransactionId: String
timeFrame: TimeFrames # DAILY / WEEKLY / MONTHLY / YEARLY / LIFETIME
totalFeeVolumeInNativeToken: Float
totalFeeVolumeInUSDC: Float
totalRoyaltyFeeVolumeInNativeToken: Float
totalRoyaltyFeeVolumeInUSDC: Float
totalSalesCount: Int
totalSaleVolumeInNativeToken: Float
totalSaleVolumeInUSDC: Float
}
```

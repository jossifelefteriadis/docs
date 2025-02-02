# CollectionStats API

{% hint style="info" %}
The CollectionStats API offers aggregated data for NFT collections (ERC721 and ERC1155) at the collection level.
{% endhint %}

{% hint style="success" %}
Timeframe filter details (all times are in UTC) for when the sale transactions are captured for the aggregation:

Daily - starts from 00:00 am to 11:59 pm every day

Weekly - starts from 00:00 am on Monday to 11:59 pm on the same week Sunday

Monthly - 00:00 am on the first calendar day of the month to 11:59 pm on the last calendar day of the month. If querying the current month, the aggregation would be from the first calendar day to the most recent daily aggregation.

Yearly - 00:00 am on the first day of the year to 11:59 pm on the last day of the year. If querying the current year, the aggregation would be from the first calendar day to the most recent daily aggregation.

Lifetime - from the first recorded sale of the NFT inside a collection to the most recent daily aggregation.&#x20;
{% endhint %}

### API Inputs & Filters

```graphql
input CollectionStatFilter {
averageSalePriceInUSDC: 
dappName: # Marketplace DApp name
dappSlug: # Marketplace DApp slug (contract version)
firstTransactionBlockTimestamp: 
highestSalePriceInUSDC: 
lastTransactionBlockTimestamp: 
lowestSalePriceInUSDC: 
tokenAddress: # NFT contract address on the blockchain
totalSalesCount: 
totalSaleVolumeInUSDC: 
timeframe: DAILY / WEEKLY / MONTHLY / YEARLY / LIFETIME
}
```

### Outputs

```graphql
type CollectionStat {
averageSalePriceInNativeToken: Float
averageSalePriceInUSDC: Float
blockchain: Blockchain # Blockchain where the NFT contract is deployed
chainId: String # Unique blockchain identifier
dappName: # Marketplace DApp name
dappSlug: # Marketplace DApp slug (contract version)
dappVersion: String # Airstack unique dappVersion number
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
token: # **Nested query** allowing to query contract level data
tokenAddress: Address! # NFT contract address on the blockchain
totalFeeVolumeInNativeToken: Float
totalFeeVolumeInUSDC: Float
totalRoyaltyFeeVolumeInNativeToken: Float
totalRoyaltyFeeVolumeInUSDC: Float
totalSalesCount: Int
totalSaleVolumeInNativeToken: Float
totalSaleVolumeInUSDC: Float
}
```

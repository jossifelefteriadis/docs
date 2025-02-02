# NFTSaleTransactions API

{% hint style="info" %}
The NFTSaleTransactions API retrieves ERC721 and ERC1155 token sale transactions that have occurred on NFT marketplaces.
{% endhint %}

### Inputs & Filters

```graphql
input NFTSaleTransactionFilter {
blockTimestamp: # Allows entering blockTimestamp to filter transactions which happened in specific periods
dappName: # Marketplace DApp name
dappSlug: # Marketplace DApp slug (contract version)
from: # Identity: blockchain address, domain name, social identity
to: # Identity: blockchain address, domain name, social identity
nfts: # ** Nested query ** input token contract address and/or NFT token ID
transactionHash: # Allows filtering to a specific transaction
}
```

### Outputs

```graphql
type NFTSaleTransaction {
blockchain: Blockchain # Blockchain where the NFT sale transaction took place
blockNumber: Int #Block number of the NFT sale transaction
blockTimestamp: Time #Timestamp of the NFT sale transaction
chainId: String # Unique blockchain identifier
collection: Token # **Nested query** to get NFT contract level data
dappName: # Marketplace DApp name
dappSlug: # Marketplace DApp slug (contract version)
dappVersion: String # Airstack unique dappVersion number
feeAmount: String # Fee amount for the NFT sale transaction
feeAmountInNativeToken: String # Fee amount in blockchain native token for the NFT sale transaction
feeAmountInUSDC: String # Fee amount in USDC for the NFT sale transaction
feeBeneficiary: # **Nested query** - wallet-related information, including address, domains, social profile, other token balances, and transfer history.
formattedFeeAmount: Float # Formatted fee amount for the NFT sale transaction
formattedFeeAmountInNativeToken: Float # Formatted fee amount in blockchain native token
formattedFeeAmountInUSDC: Float # Formatted fee amount in USDC
formattedPaymentAmount: Float # Formatted payment amount for the NFT sale transaction
formattedPaymentAmountInNativeToken: Float # Formatted payment amount in the native token
formattedPaymentAmountInUSDC: Float # Formatted payment amount in USDC
from: # **Nested query** - wallet-related information, including address, domains, social profile, other token balances, and transfer history.
id: ID # Airstack unique identifier for the NFT sale transaction
nfts: TokenNft # **Nested query** - individual NFT token level data, such as an address, amount, ID, metadata
paymentAmount: String # Payment amount
paymentAmountInNativeToken: String # Payment amount in blockchain native token
paymentAmountInUSDC: String # Payment amount in USDC
paymentToken: Token # **Nested query** to get token contract level data
paymentTokenPriceInNativeToken: Float # Price of the payment token in blockchain native token
paymentTokenPriceInUSDC: Float # Price of the payment token in USDC
royalties: [Royalty] # Information on sale royalties: amount, beneficiary address
to:  # **Nested query** - wallet-related information, including address, domains, social profile, other token balances, and transfer history.
transactionHash: String # Transaction hash of the NFT sale transaction
transactionType: String # Type of the NFT transaction (e.g., "sale")
}
```

{% hint style="warning" %}
Airstack currently includes sales on OpenSea and Rarible. More marketplaces are being added.
{% endhint %}

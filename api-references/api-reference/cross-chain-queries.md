# Cross-chain Queries

If you would like to run a query which fetches information from multiple blockchains, you can simply pass multiple inputs inside a single query:

```graphql
query Wallet {
# first query on Polygon
  polygon: Wallet(input: {blockchain: polygon, identity: "vitalik.eth"}) {
    addresses
    tokenTransfers {
      transactionHash
    }
    tokenBalances {
      amount
      tokenType
      tokenAddress
    }
  }
# second query on Ethereum
  ethereum: Wallet(input: {blockchain: ethereum, identity: "vitalik.eth"}) {
    addresses
    tokenTransfers {
      transactionHash
    }
    tokenBalances {
      amount
      tokenType
      tokenAddress
    }
  }
}

```

{% hint style="info" %}
Make sure to use aliases before the queries to differentiate between chains. IN the above query the aliases are "polygon:" and "ethereum".&#x20;
{% endhint %}

# Explore Magento's GraphQL with GraphiQL

1. If you're not familiar with GraphQL or GraphiQL read this short [article on medium].
1. Install the ChromeiQL browser extension.
1. Set it to use a public Magento GraphQL endpoint.      
https://release-dev-231-npzdaky-zddsyhrdimyra.us-4.magentosite.cloud/graphql
1. Explore the docs section to see what [queries and mutations] are currently available in Magento's GraphQL API.
1. Run the following query:
  ```graphql
  {
    category(
      id: 10
    ) {
      url_key
      products{
        items {
          name
        }
      }
    }
  }
  ```
6. Compare Magento's GraphiQL docs to their [Swagger REST docs].
1. Check to see what GraphQL queries the [venia storefront demo] is using by looking at the chrome network tab.
![chrome network tab](./graphql-network-screenshot.png)
1. Try using one of these queries in GraphiQL.


---
- [> see other topics](../../README.md#Topics)

[article on medium]: https://medium.com/the-graphqlhub/graphiql-graphql-s-killer-app-9896242b2125
[ChromeiQL]: https://chrome.google.com/webstore/detail/chromeiql/fkkiamalmpiidkljmicmjfbieiclmeij
[queries and mutations]: https://graphql.org/learn/queries/
[Swagger REST docs]: https://devdocs.magento.com/swagger/
[venia storefront demo]: https://veniapwa.com/
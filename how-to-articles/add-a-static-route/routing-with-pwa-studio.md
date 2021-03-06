# Routing in PWA Studio
Routing in PWA studio is complex, it needs to consider all the different types of routes from Magento (category, product, CMS, customer, sales etc) as well as all the URL rewrites which Magento offers. This article aims to walk through how routing works in PWA Studio to help you gain a better understanding of it.

First lets look in the entry point of the venia-concept package in [packages/venia-concept/src/index.js].
What React component is it rendering? [`<App>`].
Check at the top of the file to see where this component is coming from from, [at line 9].

Note the use of the `<Adapter />` [HOC] wrapped around the the `<App />` component. This is where Venia sets the ApolloProvider, the ReduxStore, and the [Router configuration].  See [src/drivers/adapter.js#L75].  Install the [react-developer-tools] extension for chrome and use it to inspect the React front end of veniapwa.com.

![magento router screenshot](./magento-router-screenshot.png)

The [APP component] is responsible for rendering the components for the [application shell].
The [`<Main>`] component here is using the **renderRoutes()** function from [renderRoutes.js].

In [renderRoutes.js] we see how pwa-studio is using [react-router] for rendering static routes like _/search.html_ and _/create-account_. It's using the `<Page>` component from PWA Studio's Peregrine library to render Magento's Category & Product routes.

If we look a little closer we can see that the [Page component] in turn uses the [MagentoRouteHandler component] to resolve the route by querying Magento 2 API, it then receives the page type in the response. Currently, those page types are: **CMS_PAGE**, **CATEGORY** and **PRODUCT**.

If the URL doesn’t exist, Magento 2 will send out a 404 error (temporary until proper 404 page type has been implemented). If the URL exists, MagentoRouter will render a **RootComponent** which is assigned to the received page type.

All Root Component folders must be placed in the `rootComponentsDirs` path defined in [webpack.config.js#L25], **src/RootComponents/**.

In this directory you will find it's components each have an _index.js_ entry point.  These files are important as webpack uses the commented section to define the pageType for a specific page type. See [src/RootComponents/Category/index.js]

> As you can see, the commented section in index.js defines the RootComponent for a specific page type. If we change pageTypes variable value to PRODUCT (webpack restart is required to perform code-splitting again), this component will be used for Product page, and not for CMS page as specified previously.
>
> ref: https://inchoo.net/magento-2/magento-pwa-studio-routing-root-components/

Since Magento's GraphQL is still in development, page types are limited to the three types , CMS, Category and Product. You can find them defined in:
- [CatalogUrlRewriteGraphQl schema]
- [CmsUrlRewriteGraphQl schema]

#### References
- [Routing with PWA Studio]
- [Magento PWA Studio: Routing and Root Components]

---
- [> see other topics](../../README.md#Topics)

[packages/venia-concept/src/index.js]: https://github.com/magento-research/pwa-studio/blob/v2.1.0/packages/venia-concept/src/index.js
[`<App>`]: https://github.com/magento-research/pwa-studio/blob/v2.1.0/packages/venia-concept/src/index.js#L41
[at line 9]: https://github.com/magento-research/pwa-studio/blob/v2.1.0/packages/venia-concept/src/index.js#L9: 
[HOC]: https://reactjs.org/docs/higher-order-components.html
[Router configuration]: https://magento-research.github.io/pwa-studio/peregrine/routing/#magentorouter
[src/drivers/adapter.js#L75]: https://github.com/magento-research/pwa-studio/blob/v2.1.0/packages/venia-concept/src/drivers/adapter.js#L75
[react-developer-tools]: https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi
[APP component]: https://github.com/magento-research/pwa-studio/blob/v2.1.0/packages/venia-concept/src/components/App/app.js
[application shell]: https://magento-research.github.io/pwa-studio/technologies/basic-concepts/app-shell/
[`<Main>`]: https://github.com/magento-research/pwa-studio/blob/v2.1.0/packages/venia-concept/src/components/App/app.js#L93-L96
[renderRoutes.js]: https://github.com/magento-research/pwa-studio/blob/v2.1.0/packages/venia-concept/src/components/App/renderRoutes.js
[react-router]: https://reacttraining.com/react-router/web/guides/quick-start
[Page component]: https://github.com/magento-research/pwa-studio/blob/v2.1.0/packages/peregrine/src/Page/Page.js
[MagentoRouteHandler component]: https://github.com/magento-research/pwa-studio/blob/v2.1.0/packages/peregrine/src/Router/MagentoRouteHandler.js
[webpack.config.js#L25]: https://github.com/magento-research/pwa-studio/blob/v2.1.0/packages/venia-concept/webpack.config.js#L25
[src/RootComponents/Category/index.js]: https://github.com/magento-research/pwa-studio/blob/v2.1.0/packages/venia-concept/src/RootComponents/Category/index.js#L4
[CatalogUrlRewriteGraphQl schema]: https://github.com/magento/magento2/blob/2.3-develop/app/code/Magento/CatalogUrlRewriteGraphQl/etc/schema.graphqls#L21-L22
[CmsUrlRewriteGraphQl schema]: https://github.com/magento/magento2/blob/2.3-develop/app/code/Magento/CmsUrlRewriteGraphQl/etc/schema.graphqls#L5
[Routing with PWA Studio]: https://magento-research.github.io/pwa-studio/peregrine/routing/
[Magento PWA Studio: Routing and Root Components]: https://inchoo.net/magento-2/magento-pwa-studio-routing-root-components/
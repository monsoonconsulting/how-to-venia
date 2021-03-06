# How to Venia (**work in progress**)
## What?
This is a Magento 2.3.1 PWA Storefront which is a simple copy of [PWA Studio's venia-concept] v2.1.0 package.    
Why [re-invent the wheel]?  

More than that, it's a collection of **[how-to-articles]** which can be followed to give you a basic understanding of how the venia-concept package was built 
and to demonstrate one method in which it could be used to create your own PWA Storefront for Magento.

⚠️ **CAVEAT**     
Do your own research before using this in a production environment.  
It's not clear to me which are the recommended approaches from Magento to use [PWA Studio], and this may not be one. 
In-fact, while I believe a lot has been accomplished in PWA Studio, a lot is yet to be done, which will bring about change. 
Read [what magento says].   
There are other approaches out there too, for example see [fallback-studio], [ScandiPWA] and [DEITY Falcon].   
**I created this repository to share what I've learnt from exploring PWA Studio.
There are aspects of PWA Studio which I may not fully appreciate.**   
See [TODO]

## Why?
As I started to explore [PWA Studio] I kept notes to help me understand how it worked. 
As a Magento front-end developer there are new skills to master :smile:
I thought that these notes may be helpful to others who were in a similar position.

Also, it was unclear to me how PWA Studio could be quickly bootstrapped to create a PWA Storefront for Magento.
After following the [Venia storefront setup] documentation I had a project which was part of a [monorepo] that is used to develop and publish NPM packages for [@magento].  

While this works very well to demonstrate, publish and help people to contribute to the work of [PWA Studio], it does not seem like the best place to begin a project from.

I wanted a stand-alone PWA Storefront for a Magento 2 backend, not something which was part of a monorepo that managed dependencies with [Yarn Workspaces].
So rather than create something from scratch I have copied the base configuration, tooling & setup from the venia-concept package.
Magento and their community contributors have done an excellent job in providing these. 
And I believe this gives an excellent starting for a project by providing:
- [PWADevServer](https://magento-research.github.io/pwa-studio/pwa-buildpack/reference/pwa-dev-server/)
- [Routing](https://magento-research.github.io/pwa-studio/peregrine/routing/)
- [Redux setup](https://magento-research.github.io/pwa-studio/technologies/tools-libraries/)
- Magento API Integration
    - [GraphQL](https://magento-research.github.io/pwa-studio/technologies/basic-concepts/graphql/)
    - Apollo Client Setup
    - [REST API Client](https://magento-research.github.io/pwa-studio/peregrine/reference/rest-api-client/)
- [ServiceWorkerPlugin](https://magento-research.github.io/pwa-studio/pwa-buildpack/reference/serviceworker-plugin/)
- [CSS Modules](https://magento-research.github.io/pwa-studio/technologies/basic-concepts/css-modules/)
- [Modular components from PWA Studio](https://magento-research.github.io/pwa-studio/venia-pwa-concept/features/modular-components/)
    - [Category page](https://magento-research.github.io/pwa-studio/venia-pwa-concept/design/category-page/)
    - [Product Page](https://magento-research.github.io/pwa-studio/venia-pwa-concept/design/product-page/)
    - [Checkout](https://magento-research.github.io/pwa-studio/venia-pwa-concept/features/checkout/)
    - **and more...**
- **and more...**

## How?

### How-to-Articles
Notes have been kept in markdown format in the [./how-to-articles/] directory.  
They cover basic [React] & [PWA Studio] concepts which I think may be useful to front-end developers with limited React & PWA experience.

#### Topics
1. [Project Setup](./how-to-articles/project-setup/index.md)
    - [Copy Venia Storefront](./how-to-articles/project-setup/copy-venia-storefront.md)
    - [Set Venia as Project Dependency](./how-to-articles/project-setup/set-venia-as-project-dependency.md) *Optional*
1. [Add a static route](./how-to-articles/add-a-static-route/index.md)
    - [Routing with PWA Studio](./how-to-articles/add-a-static-route/routing-with-pwa-studio.md)
1. [Props & propTypes](./how-to-articles/props-proptypes/index.md)
1. [Add a Link to the Footer](./how-to-articles/add-link-to-footer/index.md)
1. [CSS Modules](./how-to-articles/css-modules/index.md)
1. [Configure CSS modules to use SCSS](./how-to-articles/css-modules-for-scss/index.md) (TODO)
1. [Replace the CSS for the Header](./how-to-articles/replace-header-css/index.md)
1. [Component State](./how-to-articles/component-state/index.md)
1. [Reuse a PWA Studio component](./how-to-articles/reuse-a-venia-component/index.md)
1. [Explore Magento's GraphQL API in GraphiQL](./how-to-articles/explore-graphql-with-graphiql/index.md)
1. [Use Magento's GraphQL API with Apollo](./how-to-articles/use-magentos-graphql-api/index.md)
1. [Manage State with Redux](./how-to-articles/manage-state-with-redux/index.md)
1. [Redux with Apollo Client](./how-to-articles/redux-with-apollo-client/index.md) (TODO)
1. [Use Magento's REST API](./how-to-articles/use-magentos-rest-api/index.md) (TODO)
1. [Use a another GraphQL API](./how-to-articles/use-another-graphql-api/index.md) (TODO)
1. [Use a another REST API](./how-to-articles/use-another-rest-api/index.md) (TODO)

### Quick Setup
#### Prerequisites
* [NodeJS >=10.14.1 LTS](https://nodejs.org/en/)
* [Yarn >=1.13.0](https://yarnpkg.com)
* Python 2.7 and build tools, [see the Installation instructions on `node-gyp`](https://github.com/nodejs/node-gyp#installation) for your platform.
* A unix based OS for example MacOS or Linux

```bash
git clone git@github.com:rossmc/how-to-venia.git
cd how-to-venia

# install dependencies
yarn install

# set default environment variables
cp .env.dist .env

# start the app with development environment which includes hot-reloading
yarn watch

# OR run the staging environment which will more closely reflect production
yarn build:prod
yarn start
```

## Credits
Magento for creating [PWA Studio].

## TODO
- The npm/yarn build:esm script is not working, look into fixing this.
- Experiment more with VeniaAdapter to make venia components work more reliably.    
i.e. [Set Venia as Project Dependency](./how-to-articles/project-setup/set-venia-as-project-dependency.md)

[PWA Studio's venia-concept]: https://magento-research.github.io/pwa-studio/venia-pwa-concept/
[@magento/venia-concept]: https://www.npmjs.com/package/@magento/venia-concept
[re-invent the wheel]: https://en.wikipedia.org/wiki/Reinventing_the_wheel
[what magento says]: https://community.magento.com/t5/Magento-DevBlog/PWA-Studio-2-1-0-has-been-released/ba-p/127492
[@magento/peregrine]: https://www.npmjs.com/package/@magento/peregrine
[how-to-articles]: #How-to-Articles
[TODO]: #TODO
[Venia storefront setup]: https://magento-research.github.io/pwa-studio/venia-pwa-concept/setup/
[monorepo]: https://github.com/magento-research/pwa-studio#about-this-repository
[@magento]: https://www.npmjs.com/org/magento
[Yarn Workspaces]: https://yarnpkg.com/en/docs/workspaces/
[fallback-studio]: https://github.com/Jordaneisenburger/fallback-studio
[ScandiPWA]: https://scandipwa.com/
[DEITY Falcon]: https://github.com/deity-io/falcon
[./how-to-articles/]: ./how-to-articles/
[PWA Studio]: https://github.com/magento-research/pwa-studio
[React]: https://reactjs.org/

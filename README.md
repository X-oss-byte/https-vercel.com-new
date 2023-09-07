[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fvercel%2Fcommerce&project-name=commerce&repo-name=commerce&demo-title=Next.js%20Commerce&demo-url=https%3A%2F%2Fdemo.vercel.store&demo-image=https%3A%2F%2Fbigcommerce-demo-asset-ksvtgfvnd.vercel.app%2Fbigcommerce.png&env=COMPANY_NAME,SHOPIFY_REVALIDATION_SECRET,SHOPIFY_STORE_DOMAIN,SHOPIFY_STOREFRONT_ACCESS_TOKEN,SITE_NAME,TWITTER_CREATOR,TWITTER_SITE)

# Next.js Commerce

A Next.js 13 and App Router-ready ecommerce template featuring:

- Next.js App Router
- Optimized for SEO using Next.js's Metadata
- React Server Components (RSCs) and Suspense
- Server Actions for mutations
- Edge Runtime
- New fetching and caching paradigms
- Dynamic OG images
- Styling with Tailwind CSS
- Checkout and payments with Shopify
- Automatic light/dark mode based on system settings

<h3 id="v1-note"></h3>

> Note: Looking for Next.js Commerce v1? View the [code](https://github.com/vercel/commerce/tree/v1), [demo](https://commerce-v1.vercel.store), and [release notes](https://github.com/vercel/commerce/releases/tag/v1).

## Providers

Vercel will only be actively maintaining a Shopify version [as outlined in our vision and strategy for Next.js Commerce](https://github.com/vercel/commerce/pull/966).

Vercel is happy to partner and work with any commerce provider to help them get a similar template up and running and listed below. Alternative providers should be able to fork this repository and swap out the `lib/shopify` file with their own implementation while leaving the rest of the template mostly unchanged.

- Shopify (this repository)
- [BigCommerce](https://github.com/bigcommerce/nextjs-commerce) ([Demo](https://next-commerce-v2.vercel.app/))
- [Medusa](https://github.com/medusajs/vercel-commerce) ([Demo](https://medusa-nextjs-commerce.vercel.app/))
- [Saleor](https://github.com/saleor/nextjs-commerce) ([Demo](https://saleor-commerce.vercel.app/))
- [Shopware](https://github.com/shopwareLabs/vercel-commerce) ([Demo](https://shopware-vercel-commerce-react.vercel.app/))
- [Swell](https://github.com/swellstores/verswell-commerce) ([Demo](https://verswell-commerce.vercel.app/))
- [Umbraco](https://github.com/umbraco/Umbraco.VercelCommerce.Demo) ([Demo](https://vercel-commerce-demo.umbraco.com/))

> Note: Providers, if you are looking to use similar products for your demo, you can [download these assets](https://drive.google.com/file/d/1q_bKerjrwZgHwCw0ovfUMW6He9VtepO_/view?usp=sharing).

## Running locally

You will need to use the environment variables [defined in `.env.example`](.env.example) to run Next.js Commerce. It's recommended you use [Vercel Environment Variables](https://vercel.com/docs/concepts/projects/environment-variables) for this, but a `.env` file is all that is necessary.

> Note: You should not commit your `.env` file or it will expose secrets that will allow others to control your Shopify store.

1. Install Vercel CLI: `npm i -g vercel`
2. Link local instance with Vercel and GitHub accounts (creates `.vercel` directory): `vercel link`
3. Download your environment variables: `vercel env pull`

```bash
pnpm install
pnpm dev
```

Your app should now be running on [localhost:3000](http://localhost:3000/).

<details>
  <summary>Expand if you work at Vercel and want to run locally and / or contribute</summary>

1. Run `vc link`.
1. Select the `Vercel Solutions` scope.
1. Connect to the existing `commerce-shopify` project.
1. Run `vc env pull` to get environment variables.
1. Run `pmpm dev` to ensure everything is working correctly.
</details>

## Vercel, Next.js Commerce, and Shopify Integration Guide

You can use this comprehensive [integration guide](http://vercel.com/docs/integrations/shopify) with step-by-step instructions on how to configure Shopify as a headless CMS using Next.js Commerce as your headless Shopify storefront on Vercel.



Next.js Commerce

The all-in-one starter kit for high-performance e-commerce sites. With a few clicks, Next.js developers can clone, deploy and fully customize their own store. Start right now at nextjs.org/commerce

Demo live at: demo.vercel.store

Shopify Demo: https://shopify.vercel.store/
Swell Demo: https://swell.vercel.store/
BigCommerce Demo: https://bigcommerce.vercel.store/
Vendure Demo: https://vendure.vercel.store
Saleor Demo: https://saleor.vercel.store/
Ordercloud Demo: https://ordercloud.vercel.store/
Spree Demo: https://spree.vercel.store/
Kibo Commerce Demo: https://kibocommerce.vercel.store/
Commerce.js Demo: https://commercejs.vercel.store/
SalesForce Cloud Commerce Demo: https://salesforce-cloud-commerce.vercel.store/
Run minimal version locally

To run a minimal version of Next.js Commerce you can start with the default local provider @vercel/commerce-local that has all features disabled (cart, auth) and uses static files for the backend
pnpm install & pnpm build # run these commands in the root folder of the mono repo
pnpm dev # run this command in the site folder
If you encounter any problems while installing and running for the first time, please see the Troubleshoot section
Features

Performant by default
SEO Ready
Internationalization
Responsive
UI Components
Theming
Standardized Data Hooks
Integrations - Integrate seamlessly with the most common ecommerce platforms.
Dark Mode Support
Integrations

Next.js Commerce integrates out-of-the-box with BigCommerce, Shopify, Swell, Saleor, Vendure, Spree and Commerce.js. We plan to support all major ecommerce backends.

Considerations

packages/commerce contains all types, helpers and functions to be used as a base to build a new provider.
Providers live under packages's root folder and they will extend Next.js Commerce types and functionality (packages/commerce).
We have a Features API to ensure feature parity between the UI and the Provider. The UI should update accordingly and no extra code should be bundled. All extra configuration for features will live under features in commerce.config.json and if needed it can also be accessed programmatically.
Each provider should add its corresponding next.config.js and commerce.config.json adding specific data related to the provider. For example in the case of BigCommerce, the images CDN and additional API routes.
Configuration

How to change providers

Open site/.env.local and change the value of COMMERCE_PROVIDER to the provider you would like to use, then set the environment variables for that provider (use site/.env.template as the base).

The setup for Shopify would look like this for example:

COMMERCE_PROVIDER=@vercel/commerce-shopify
NEXT_PUBLIC_SHOPIFY_STOREFRONT_ACCESS_TOKEN=xxxxxxxxxxxxxxxxxxxxxxxxxxxx
NEXT_PUBLIC_SHOPIFY_STORE_DOMAIN=xxxxxxx.myshopify.com
Features

Every provider defines the features that it supports under packages/{provider}/src/commerce.config.json

Features Available

The following features can be enabled or disabled. This means that the UI will remove all code related to the feature. For example: turning cart off will disable Cart capabilities.

cart
search
wishlist
customerAuth
customCheckout
How to turn Features on and off

NOTE: The selected provider should support the feature that you are toggling. (This means that you can't turn wishlist on if the provider doesn't support this functionality out of the box)
Open site/commerce.config.json
You'll see a config file like this:
{
  "features": {
    "wishlist": false,
    "customCheckout": true
  }
}
Turn wishlist on by setting wishlist to true.
Run the app and the wishlist functionality should be back on.
How to create a new provider

Follow our docs for Adding a new Commerce Provider.

If you succeeded building a provider, submit a PR with a valid demo and we'll review it asap.

Contribute

Our commitment to Open Source can be found here.

Fork this repository to your own GitHub account and then clone it to your local device.
Create a new branch git checkout -b MY_BRANCH_NAME
Install the dependencies: pnpm install
Build the packages: pnpm build
Duplicate site/.env.template and rename it to site/.env.local
Add proper store values to site/.env.local
Run cd site & pnpm dev to watch for code changes
Run pnpm turbo run build to check the build after your changes
Work in progress

We're using Github Projects to keep track of issues in progress and todo's. Here is our Board

People actively working on this project: @okbel, @lfades, @dominiksipowicz, @gbibeaul.

Troubleshoot

I don't  own a BigCommerce store. What should I do?
BigCommerce shows a Coming Soon page and requests a Preview Code
When run locally I get `Error: Cannot find module '...@vercel/commerce/dist/config'`>

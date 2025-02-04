# @nestjs-shopify/auth

## 3.1.0

### Minor Changes

- c9a89c6: Add and use `@InjectShopify()` and `@InjectShopifySessionStorage()` decorators.

## 3.0.0

### Major Changes

- bd636c5: Removed `ShopifyAuthGuard.register()`. Before you had to import the `ShopifyAuthGuard` as followingbe to be able to use `@UseShopifyAuth()`:

  ```ts
  @Module({
    imports: [ShopifyAuthGuard.register()],
    controllers: [MyControllerUsingShopifyAuth],
  })
  class MyModule {}
  ```

  This call is now not required anymore. All you have to do is ensure is that `ShopifyAuthGuard.forRootOnline` or `ShopifyAuthGuard.forRootOffline` is imported your root module (usually called `AppModule`).

  That means that you should remove any references to to `ShopifyAuthGuard.register()`:

  ```diff
  @Module({
  - imports: [ShopifyAuthGuard.register()],
    controllers: [MyControllerUsingShopifyAuth],
  })
  class MyModule {}
  ```

## 2.0.3

### Patch Changes

- 71ec7c8: Fix offline auth always being invalid due to not having an expires in session (issue #110)

## 2.0.2

- Fix deployment issue in npmjs.com

## 2.0.1

### Patch Changes

- 34f4133: Add missing `jsonwebtoken` dependency

## 2.0.0

### Patch Changes

- Updated dependencies [8782b25]
  - @nestjs-shopify/core@2.0.0

## 1.0.0

### Major Changes

- e6a3891: GraphQL proxy moved to own package.

  Install `@nestjs-shopify/graphql` and use it as following:

  ```ts
  import { ShopifyCoreModule } from '@nestjs-shopify/core';
  import { ShopifyAuthModule } from '@nestjs-shopify/auth';
  import { ShopifyGraphqlProxyModule } from '@nestjs-shopify/graphql';

  @Module({
    imports: [
      // ...
      ShopifyCoreModule.forRoot(/* ... */),
      ShopifyAuthModule.forRootOnline(/* ... */),
      ShopifyGraphqlProxyModule,
      // ...
    ],
  })
  export class AppModule {}
  ```

- e6a3891: Upgrade to v6.0.0 of `@shopify/shopify-api`.

  See the upgrade guide of [`@shopify/shopify-api`](https://github.com/Shopify/shopify-api-js/blob/main/docs/migrating-to-v6.md)

  Run `npm install @shopify/shopify-api@6.0.0` or `yarn add @shopify/shopify-api@6.0.0` together with the upgrade of all `@nestjs-shopify/*` packages.

### Patch Changes

- Updated dependencies [e6a3891]
- Updated dependencies [e6a3891]
  - @nestjs-shopify/core@1.0.0

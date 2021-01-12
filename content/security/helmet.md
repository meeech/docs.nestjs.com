### Helmet

[Helmet](https://github.com/helmetjs/helmet) can help protect your app from some well-known web vulnerabilities by setting HTTP headers appropriately. Generally, Helmet is just a collection of 14 smaller middleware functions that set security-related HTTP headers (read [more](https://github.com/helmetjs/helmet#how-it-works)).

> info **Hint** Note that applying `helmet` as global or registering it must come before other calls to `app.use()` or setup functions that may call `app.use()`). This is due to the way the underlying platform (i.e., Express or Fastify) works, where the order that middleware/routes are defined matters. If you use middleware like `helmet` or `cors` after you define a route, then that middleware will not apply to that route, it will only apply to routes defined after the middleware is initialized with `app.use()`.

#### Use with Express (default)

Start by installing the required package.

```bash
$ npm i --save helmet
```

Once the installation is complete, apply it as a global middleware.

```typescript
import * as helmet from 'helmet';
// somewhere in your initialization file
app.use(helmet());
```

> info **Hint** If you are getting the `This expression is not callable` error while trying to import `Helmet`, you very likely have the `allowSyntheticDefaultImports` and `esModuleInterop` options set to `true` in your project's `tsconfig.json` file. If that's the case, change the import statement to: `import helmet from 'helmet'` instead.

#### Use with Fastify

If you are using the `FastifyAdapter`, install the [fastify-helmet](https://github.com/fastify/fastify-helmet) package:

```bash
$ npm i --save fastify-helmet
```

[fastify-helmet](https://github.com/fastify/fastify-helmet) should not be used as a middleware, but as a [Fastify plugin](https://www.fastify.io/docs/latest/Plugins/), i.e., by using `app.register()`:

```typescript
import * as helmet from 'fastify-helmet';
// somewhere in your initialization file
app.register(helmet);
```

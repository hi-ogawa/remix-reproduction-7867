remix vite https (http2) reproduction

- https://github.com/remix-run/remix/issues/7867
- https://github.com/remix-run/remix/discussions/8046

Use https://github.com/FiloSottile/mkcert to manage local certificates

```sh
mkcert -install

# generate localhost.pem and localhost-key.pem
mkcert localhost

# start dev server
pnpm dev
```

Accessing https://localhost:5173/test (route with loader) fails by:

```
TypeError: Header name must be a valid HTTP token [":authority"]
    at /home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+web-fetch@4.4.1/node_modules/@remix-run/web-fetch/dist/lib.node.cjs:1000:6
    at Array.map (<anonymous>)
    at new Headers (/home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+web-fetch@4.4.1/node_modules/@remix-run/web-fetch/dist/lib.node.cjs:999:12)
    at new Request (/home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+web-fetch@4.4.1/node_modules/@remix-run/web-fetch/dist/lib.node.cjs:1471:5)
    at stripIndexParam (/home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+server-runtime@2.3.0_typescript@5.2.2/node_modules/@remix-run/server-runtime/dist/data.js:96:10)
    at Object.callRouteLoaderRR (/home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+server-runtime@2.3.0_typescript@5.2.2/node_modules/@remix-run/server-runtime/dist/data.js:53:29)
    at commonRoute.loader (/home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+server-runtime@2.3.0_typescript@5.2.2/node_modules/@remix-run/server-runtime/dist/routes.js:54:20)
    at runHandler (/home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+router@1.12.0/node_modules/@remix-run/router/dist/router.cjs.js:4022:26)
    at callLoaderOrAction (/home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+router@1.12.0/node_modules/@remix-run/router/dist/router.cjs.js:4078:22)
    at /home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+router@1.12.0/node_modules/@remix-run/router/dist/router.cjs.js:3571:68
    at Array.map (<anonymous>)
    at loadRouteData (/home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+router@1.12.0/node_modules/@remix-run/router/dist/router.cjs.js:3571:55)
    at queryImpl (/home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+router@1.12.0/node_modules/@remix-run/router/dist/router.cjs.js:3413:26)
    at Object.query (/home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+router@1.12.0/node_modules/@remix-run/router/dist/router.cjs.js:3313:24)
    at handleDocumentRequestRR (/home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+server-runtime@2.3.0_typescript@5.2.2/node_modules/@remix-run/server-runtime/dist/server.js:168:35)
    at requestHandler (/home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+server-runtime@2.3.0_typescript@5.2.2/node_modules/@remix-run/server-runtime/dist/server.js:93:24)
    at /home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+dev@2.3.0_@remix-run+serve@2.3.0_typescript@5.2.2_vite@5.0.0/node_modules/@remix-run/dev/dist/vite/node/adapter.js:191:26
    at /home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+dev@2.3.0_@remix-run+serve@2.3.0_typescript@5.2.2_vite@5.0.0/node_modules/@remix-run/dev/dist/vite/plugin.js:546:21
    at call (file:///home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/vite@5.0.0/node_modules/vite/dist/node/chunks/dep-T98iZFpD.js:42848:7)
    at next (file:///home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/vite@5.0.0/node_modules/vite/dist/node/chunks/dep-T98iZFpD.js:42792:5)
    at /home/hiroshi/code/tmp/remix-vite-http2/node_modules/.pnpm/@remix-run+dev@2.3.0_@remix-run+serve@2.3.0_typescript@5.2.2_vite@5.0.0/node_modules/@remix-run/dev/dist/vite/plugin.js:525:13
```

---

# templates/unstable-vite

⚠️ Remix support for Vite is unstable and not recommended for production.

📖 See the [Remix Vite docs][remix-vite-docs] for details on supported features.

## Setup

```shellscript
npx create-remix@latest --template remix-run/remix/templates/unstable-vite
```

## Run

Spin up the Vite dev server:

```shellscript
npm run dev
```

Or build your app for production and run it:

```shellscript
npm run build
npm run start
```

[remix-vite-docs]: https://remix.run/docs/en/main/future/vite

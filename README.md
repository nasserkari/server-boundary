# server-boundary

Keep server code out of client bundles

## Install

```bash
npm install server-boundary
```

## Usage

Add the import at the top of any module that must only run on the server.

```ts
import "server-boundary";

export const db = createClient(process.env.SECRET_KEY!);
```

If a Client Component imports this module, the build fails with a clear error.

## How it works

The package uses the `react-server` export condition, which Next.js sets only when bundling Server Components.

| Environment       | Resolves to      | Result                |
| ----------------- | ---------------- | --------------------- |
| Server Component  | `src/error.js`   | No-op                 |
| Client Component  | `src/index.js`   | Throws a build error  |

## Notes

- Zero dependencies
- Works with Next.js and any bundler that supports the `react-server` condition
- Pair it with [client-boundary](https://www.npmjs.com/package/client-boundary) for the opposite direction

## License

MIT

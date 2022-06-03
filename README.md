# Reproduction steps:

1. Run install on monorepo with circular dependency
2. Run install --prod in one package
3. Notice other package's dependencies are removed from store

At this point symlinks are broken other package's to its dependency

```
$ pnpm --version                                           13:09:37
7.1.7
$ pnpm i
$ ls node_modules/.pnpm | grep chalk
chalk@5.0.1
$ cd pkg-b
$ pnpm i --prod --filter='.'
$ ls ../node_modules/.pnpm | grep chalk
$
```
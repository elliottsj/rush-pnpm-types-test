# rush-pnpm-types-test
Reproduction of a bug involving rush + pnpm + @types/webpack + @types/tapable.

To repro the bug:

```
npm install
./node_modules/.bin/rush install
cd packages/bar-webpack-plugin/
npm test
```

And observe the TypeScript error output:

```
> bar-webpack-plugin@1.0.0 test /Users/spencerelliott/Dev/elliottsj/rush-pnpm-types-test/packages/bar-webpack-plugin
> tsc --project .

../../common/temp/node_modules/.registry.npmjs.org/@types/webpack/4.4.7/node_modules/@types/webpack/index.d.ts:21:10 - error TS2305: Module '"/Users/spencerelliott/Dev/elliottsj/rush-pnpm-types-test/common/temp/node_modules/.registry.npmjs.org/@types/tapable/0.2.5/node_modules/@types/tapable/index"' has no exported member 'Tapable'.

21 import { Tapable, HookMap,
            ~~~~~~~


../../common/temp/node_modules/.registry.npmjs.org/@types/webpack/4.4.7/node_modules/@types/webpack/index.d.ts:21:19 - error TS2305: Module '"/Users/spencerelliott/Dev/elliottsj/rush-pnpm-types-test/common/temp/node_modules/.registry.npmjs.org/@types/tapable/0.2.5/node_modules/@types/tapable/index"' has no exported member 'HookMap'.

21 import { Tapable, HookMap,
                     ~~~~~~~

...
```

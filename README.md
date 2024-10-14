# dnt-repro
dnt reproduction.

## Issue
Deno dependencies are not copied to package json when directory is created.

## Steps

```bash
deno run -A build_npm.ts 0.1.0
```

You should then see the following output:
```
[dnt] Transforming...
[dnt] Running npm install...

added 7 packages, and audited 8 packages in 2s

found 0 vulnerabilities
[dnt] Building project...
[dnt] Type checking ESM...
src/main.ts:2:19 - error TS2307: Cannot find module 'chalk' or its corresponding type declarations.

2 import color from "chalk";
                    ~~~~~~~
src/main_test.ts:2:30 - error TS2307: Cannot find module '@std/assert' or its corresponding type declarations.       

2 import { assertEquals } from "@std/assert";
                               ~~~~~~~~~~~~~

error: Uncaught (in promise) Error: Had 2 diagnostics.
          throw new Error(`Had ${diagnostics.length} diagnostics.`);
                ^
    at getProgramAndMaybeTypeCheck (https://jsr.io/@deno/dnt/0.41.3/mod.ts:468:17)
    at build (https://jsr.io/@deno/dnt/0.41.3/mod.ts:354:17)
    at eventLoopTick (ext:core/01_core.js:175:7)
    at async file:///C:/Users/ablesea/Documents/GitHub/dnt-repro/build_npm.ts:6:1
```

If you look at the generated package.json in `npm/package.json` you will see that the chalk package was not copied.



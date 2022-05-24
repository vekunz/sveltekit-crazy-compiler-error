# Crazy SvelteKit compiler error

This repository demonstrates a very weird compiler error in SvelteKit.

## Setup

To reproduce the error, you need four things to exist in your SvelteKit application.

1. In the `svelte.config.js` set the key `kit.vite.build.target` to `esnext`.
2. Have a Svelte component with some styling (in this case `SomeComponent.svelte`)
3. Have a `__layout.svelte` and any `some-route.svelte`, which both use the component from step 2.
4. Put the component in either the `__layout.svelte` or the `some-route.svelte` (or in both) inside an `{#if ...}` statement

## The error

If you now run the build command (`npm run build`), you will get this error message.

```
Error [ERR_MODULE_NOT_FOUND]: Cannot find module 'C:\somePath\sveltekit-crazy-compile-error\.svelte-kit\output\server\chunks\SomeComponent.svelte_svelte_type_style_lang-6fa38ce4.js' imported from C:\somePath\sveltekit-crazy-compile-error\.svelte-kit\output\server\entries\pages\__layout.svelte.js
    at new NodeError (node:internal/errors:371:5)
    at finalizeResolution (node:internal/modules/esm/resolve:418:11)
    at moduleResolve (node:internal/modules/esm/resolve:981:10)
    at defaultResolve (node:internal/modules/esm/resolve:1078:11)
    at ESMLoader.resolve (node:internal/modules/esm/loader:530:30)
    at ESMLoader.getModuleJob (node:internal/modules/esm/loader:251:18)
    at ModuleWrap.<anonymous> (node:internal/modules/esm/module_job:79:40)
    at link (node:internal/modules/esm/module_job:78:36)
Error [ERR_MODULE_NOT_FOUND]: Cannot find module 'C:\somePath\sveltekit-crazy-compile-error\.svelte-kit\output\server\chunks\SomeComponent.svelte_svelte_type_style_lang-6fa38ce4.js' imported from C:\somePath\sveltekit-crazy-compile-error\.svelte-kit\output\server\entries\pages\__layout.svelte.js
> 500 /
    at file:///C:/somePath/sveltekit-crazy-compile-error/node_modules/@sveltejs/kit/dist/chunks/index2.js:1037:11
    at save (file:///C:/somePath/sveltekit-crazy-compile-error/node_modules/@sveltejs/kit/dist/chunks/index2.js:1257:4)
    at visit (file:///C:/somePath/sveltekit-crazy-compile-error/node_modules/@sveltejs/kit/dist/chunks/index2.js:1148:3)
    at processTicksAndRejections (node:internal/process/task_queues:96:5)
```

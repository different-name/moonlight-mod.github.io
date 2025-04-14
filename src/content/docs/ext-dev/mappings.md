---
title: Mappings
description: moonlight comes with mappings that automatically rename Webpack modules for you.
sidebar:
  order: 8
---

moonlight comes with [mappings](https://github.com/moonlight-mod/mappings) that automatically rename Discord's Webpack modules for you. You can import and use these modules in your extensions.

mappings automatically detects unknown modules and remaps them to have consistent module IDs and export names.

## Browsing mappings

There is no search system for mappings yet, but you can browse [the source repository](https://github.com/moonlight-mod/mappings) instead. Press `/` on your keyboard to search in the GitHub web UI.

## Notable modules

- `react`: React
- `discord/packages/flux`: Discord's fork of Flux
- `discord/Dispatcher`: Discord's Flux dispatcher
- `discord/components/common/index`: A lot of components reused in the client

## Using mappings in an extension

Inside of a Webpack module, you can import/require mappings just like any other module:

```ts
import Dispatcher from "@moonlight-mod/wp/discord/Dispatcher";
// or
const Dispatcher = require("discord/Dispatcher").default;
```

Remember to [add the module as a dependency](/ext-dev/webpack#webpack-module-dependencies) to your Webpack module.

## Mappings stability

The mappings repository only proxies existing Discord modules and exports. As such, if Discord removes a module or export, or a module is not properly remapped, the mapping will fail and your extension may break.

You should structure your code with the expectation that imported modules or exports may randomly fail. Use the [ErrorBoundary](/ext-dev/api#common) component provided by moonlight to safely catch errors in your UI code.

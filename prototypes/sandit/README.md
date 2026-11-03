# Sandit prototype

Paste an article, highlight a section, and annotate it. The selected model, ChatGPT or Claude, rewrites that section and the reply replaces it in place.

This is a static page with no server. You add your own API keys, and the browser sends your key, article and note straight to OpenAI or Anthropic. Keys stay in memory unless you choose to remember them on your device. Use keys with a spending limit, because a saved key can be read by other pages on the same GitHub Pages address.

`vendor/preact.min.js` is [Preact](https://preactjs.com) 10.24.3 under the MIT license.

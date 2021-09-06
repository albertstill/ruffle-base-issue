## Running

Any tool for hosting a web server in this folder, for example:

`npx serve .`

Load up the root localhost to see index.html.

## Issue

ruffle loads `base.swf` fine, you'll see the green background, but it requests `screen.swf`
and is not respecting the [base param](https://helpx.adobe.com/flash/kb/flash-object-embed-tag-attributes.html)
of `/public/game/`.

The base param is set up by SWFObject, and I can see it going through to ruffle [here](https://github.com/ruffle-rs/ruffle/blob/3982f3af9811cfc32c6f7eaf06aa3c8c81b91226/web/packages/core/src/ruffle-player.ts#L417).

This causes a request to `http://localhost:5000/screen.swf`, not `http://localhost:5000/public/game/screen.swf`,
causing a 404.

This repo uses the polyfill approach with SWFObject, but I've also had no luck using the ruffle API either.

Thanks for help.
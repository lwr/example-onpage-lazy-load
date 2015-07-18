

# RequireJs example for lazy loading

A simple example requirejs-base project that shows how to match these goals:
- One page or multipage application that have some modules that could be load lazily. That is, they are not depended by the application directly.
- The js files should be combined to reduce the request count.
- The built target should split into some smaller files instead of a large one, that helps for speeding up the startup time.


RequireJs / r.js is an excellent open source project, and it has some good examples that helps us to understand the basic concepts, such as this one: <https://github.com/requirejs/example-multipage>

But I didn't find a simple enough runnable example that match my requirement. I thought it should be a very common case, so I wrote this simple example and I hope it helps.


## Project notes

The project layout is simple.
- **`build`**: The optimizer (`r.js`) config, `option.js`
- **`www`**: All static resources are here, it is almost standalone except that it depends on `require.js`, you could copy it from `node_modules` or any where to the project to make it really standalone.
- **`www-built`**: The built target files generated by optimizer (`r.js`)


Setup
- Please run `npm install` to download `requirejs` before any tasks.
  ```bash
  npm install

  ```


To run the application by source (development mode), just open `www/index.html` in browser

To run the optimizer, just type
```bash
./build.sh
```

Please check [options.js](build/options.js) for details of how to config `r.js` to match our goals.

Then optimizer will generate the web to `www-built`

All modules will be packaged to three
- `index.js`: the entry point and basic
- `m12.js`: combined of module1 and module2
- `m34.js`: combined of module3 and module4

Only minimum files are built into each bundle, no module is duplicated packaged, you can check `www-built/build.txt` to make sure of this.

After the built, just open `www-built/index.html` in browser to check if all things go well.


## More info

For more information on the optimizer: http://requirejs.org/docs/optimization.html

For more information on using RequireJs: http://requirejs.org/docs/api.html

RequireJs git repos / examples: https://github.com/requirejs

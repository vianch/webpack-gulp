# Webpack Task
Use webpack to transpile and bundle your source files.

You will need to provide a `webpack.config.js` file in your project root. For more information on webpack configuration, see https://webpack.github.io/docs/configuration.html.

## API

### webpackBuild([options])

Returns a Promise that resolves when the build is finished if there are no errors, and rejects if there are build errors. Use the `failOnWarning` option to also reject when there are build warnings.

#### Available options:
- **watch** (boolean) Whether to watch for changes or not. Default: `false`.
- **watchOptions** (Object) [Watch options](https://webpack.github.io/docs/node.js-api.html#compiler) for webpack. Default: `null`.
- **config** (Object) [Configuration](https://webpack.github.io/docs/configuration.html) for webpack. Default: uses `webpack.config.js` from your project root.
- **failOnWarning** (boolean) Whether to reject on warning or not. Default: `false`.
- **statsOptions** (Object) [Stats options](https://webpack.github.io/docs/node.js-api.html#stats-tostring) for webpack. Default:
```
{
  'colors': true,
  'modules': false,
  'chunks': false,
  'exclude': ['node_modules']
}
```

## Example

```
var webpackBuild = require('webpack-gulp');

gulp.task('build', webpackBuild);

gulp.task('watch', function(){
  return webpackBuild({
    watch: true,
    statsOptions: {
      'colors': false,
      'errorDetails': true
    }  
  })
});
```

## Example 2

```
var webpackBuild = require('webpack-gulp');
var webpackConfig = require('webpack.production.js');

gulp.task('build', webpackBuild);

gulp.task('watch', function(){
  return webpackBuild({
    config: webpackConfig  
  })
});
```
[Full Example](https://github.com/vianch/angular2-gulp-webpack)





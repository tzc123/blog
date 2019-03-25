前天花了半个下午的时间，写了一套gulp的配置文件用于快速开发用于嵌入webview的h5。
主要做了几点：
1、最主要的样式方面，使用vw布局，直接采用了vue-cli的兼容方式，引入了postcss
```javascript
gulp.task('css', function(){
  return gulp.src('./src/css/*.css')
  .pipe(plugins.postcss())
  .pipe(gulp.dest('./dist/static/css'));
})
```
```javascript
// .postcssrc.js
module.exports = {
  "plugins": {
      "postcss-import": {},
      "postcss-url": {},
      "postcss-aspect-ratio-mini": {}, 
      "postcss-write-svg": {
          utf8: false
      },
      "postcss-cssnext": {},
      "postcss-px-to-viewport": {
          viewportWidth: 750,     // (Number) The width of the viewport.
          viewportHeight: 1334,    // (Number) The height of the viewport.
          unitPrecision: 3,       // (Number) The decimal numbers to allow the REM units to grow to.
          viewportUnit: 'vw',     // (String) Expected units.
          selectorBlackList: ['.ignore', '.hairlines'],  // (Array) The selectors to ignore and leave as px.
          minPixelValue: 1,       // (Number) Set the minimum pixel value to replace.
          mediaQuery: false       // (Boolean) Allow px to be converted in media queries.
      }, 
      "postcss-viewport-units":{},
      "cssnano": {
          preset: "advanced",
          autoprefixer: {
            "browserslist": [
                "Android >= 4.0"
              ]
          },
          "postcss-zindex": false
      }
  }
}
```
2、

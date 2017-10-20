# gulp

## 使用 gulp 创建项目流程

参考 jianan-front 项目

/static/img/food-1.da308f69.png

无法对css内的图片进行压缩



gulp.task('img-min', function () {
    return gulp.src(TARGET_IMG + '/*.{png,jpg,gif,ico}')
        .pipe($.imagemin())
        .pipe(gulp.dest(TARGET_IMG))
})


没有即使更新


"gulp-rev": "^8.0.0",
    "gulp-rev-collector": "^1.2.2",
gulp-cachebust


"babel-eslint": "^7.2.3",
"babel-preset-es2015": "^6.5.0",
"browser-sync": "^2.18.12",
"eslint": "^3.19.0",
"eslint": "3."
"eslint-config-standard": "^6.2.1",
"eslint-friendly-formatter": "^3.0.0",
"eslint-loader": "^1.7.1",
"eslint-plugin-html": "^3.0.0",
"eslint-plugin-promise": "^3.4.0",
"eslint-plugin-standard": "^2.0.1",


* gulp
* gulp-autoprefixer
* gulp-babel
* gulp-clean
* gulp-load-plugins
* gulp-sync

HTML

* gulp-file-include
* gulp-html-i18n
* gulp-minify-html

CSS 

* gulp-sourcemaps
* gulp-sass
* gulp-minify-css

JS

* gulp-eslint
* gulp-uglify

IMG

* gulp-imagemin


"gulp-base64": "^0.1.3",
"gulp-cachebust": "0.0.6",
"gulp-plumber": "^1.0.1",
"gulp-postcss": "^7.0.0",
"gulp-sync": "^0.1.4",

"i18next-parser": "^0.12.0"
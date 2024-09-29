# Ход сборки  
### Инициализация нового проекта:  
`npm init`
### Установка Gulp на диск (глобально):  
`npm i gulp-cli -g`
### Установка Gulp в проект (app/srs):  
`npm i gulp -D`
### Создаем рабочие папки с файлами:  
`app, dist, css > style.scss, js > main.js`
### Подключаем в index.html файлы css и js:  
`<link rel="stylesheet" href="css/style.min.css">`  
`<script src="js/main.min.js"></script>`
### Создаем переменную с названием {src, dest} и подключаем возможности 'gulp':  
`const {src, dest} = require('gulp');`
### Подключаем плагин (препроцессор) Sass в сборку:  
`npm i gulp-sass sass -D`
### Создаем переменную для подключения Sass:  
`const scss = require('gulp-sass')(require('sass'));`
### Пишем функцию для работы с стилями:
>`function styles() {`  
`return src('app/css/style.scss')`  
`.pipe(scss())`  
`.pipe(dest('app/css'))`  
`}`
### Экспортируем функцию `styles` для её использования в терминале:  
`exports.styles = styles;`
### Обновляем функцию `styles` добавив сжатие кода `css`:
>`function styles() {`  
`return src('app/css/style.scss')`  
`.pipe(scss(`***{outputStyle: 'compressed'}***  `))`  
`.pipe(dest('app/css'))`  
`}`
### Проверяем написанную функцию:  
`gulp style`
### Подключаем плагин Concat:  
`npm i gulp-concat -D`
### Создаем переменную для плагина Concat:  
`const concat = require('gulp-concat');`
### Обновляем функцию `styles` с использованием плагина Concat:
>`function styles() {`  
`return src('app/css/style.scss')`  
***.pipe(concat('style.min.css'))***  
`.pipe(scss({outputStyle: 'compressed'}))`  
`.pipe(dest('app/css'))`  
`}`
### Устанавливаем плагин для сжатия кода JS:  
`npm i gulp-uglify-es -D`
### Создаем переменную для плагина Uglify:  
`const uglify = require('gulp-uglify-es').default;`
### Пишем функцию для работы с Javascript:
>`function scripts() {`  
`return src('app/js/main.js')`  
`.pipe(concat('main.min.js'))`  
`.pipe(uglify())`  
`.pipe(dest('app/js'))`  
`}`
### Экспортируем функцию `scripts` для её использования в терминале:  
`exports.scripts = scripts;`
### Проверяем написанную функцию:  
`gulp scripts`
### Добавляем функцию Watch:  
`const {src, dest, `***watch***`} = require('gulp');`  
>`function watching() {`  
  `watch(['app/css/style.scss'], styles)`  
  `watch(['app/js/main.js'], scripts)`  
`}`  

`exports.watching = watching;`
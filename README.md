# Ход сборки  
### Инициализация нового проекта: `npm init`
### Установка Gulp на диск (глобально): `npm i gulp-cli -g`
### Установка Gulp в проект (app/srs): `npm i gulp -D`
### Создаем рабочие папки с файлами: `app, dist, css > style.scss, js > main.js`
### Подключаем в index.html файлы css и js
### Создаем переменную с названием {src, dest} и подключаем возможности 'gulp': `const {src, dest} = require('gulp');`
### Подключаем плагин (препроцессор) Sass в сборку: `npm i gulp-sass sass -D`
### Создаем переменную для подключения Sass: `const scss = require('gulp-sass')(require('sass'));`
### Пишем функцию для работы с стилями:
>`function styles() {`  
`return src('app/css/style.scss')`  
`.pipe(scss())`  
`.pipe(dest('app/css'))`  
`}`
---
### Экспортируем функцию `styles` для её использования в терминале: `exports.styles = styles;`
### Обновляем функцию `styles` добавив сжатие кода `css`:
>`function styles() {`  
`return src('app/css/style.scss')`  
`.pipe(scss(`**{outputStyle: 'compressed'}**`))`  
`.pipe(dest('app/css'))`  
`}`
---
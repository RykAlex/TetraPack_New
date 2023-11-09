## Структура проекта
-  src - исхдные файлы проекта
   -  assets
      - ejs - компоненты html-препроцессора
      -  styles - стили
         -  *.scss собираемые файлы стилей, будут в билде 1 к 1
         -  _*.scss - несобираемые стили (для импорта)
      - script - скрипты
         -  *.js - собираемые файлы скриптов, будут в билде 1 к 1
         -  _*.js - несобираемые скрипты (для импорта)
      -  static - копируется без обработки в build
         -  img - картинки ужатые (только для чтения)
         -  img-raw - картинки сырые
         -  font - шрифты
         -  что угодно еще
   - *.ejs самостоятельные страницы
-  node_modules - пакеты
-  build - готовая сборка, повторяет структуру src но содержит уже готовые файлы
-  package.json - информация о проекте
   - dependences - список установленных пакетов
   - scripts - готовые команды сборки

- Для работы сборки требуется node.js, все команды пишутся из корня проекта - там где package.json и gulpfile.js
- "npm run init" - устанавливается всё, можно работать
- Если установлена gulp-cli то команды можно запускать через "gulp [task] [keys]". Также готовые команды записаны в файле /package.json в поле scripts и могут быть запущены через "npm run SCRIPTNAME"

- ## Задачи
   - Сборка. [task] == 'default' || ''
      - [keys]:
         - --ram - собирает в оперативку
         - --min - минифицирует стили и скрипты
         - --watch - следит за изменениями файлов, пересобирая/копируя при изменении (Процесс в терминале будет бесконечным) и поднимает локальный сервер. При обработке файлов изменения будут отображены на странице автоматически
         - --port - определяет порт для локального сервера, иначе по умолчанию 3000
   - Оптимизация картинок. [task] == 'imagemin'. Картинки из папки ./src/assets/static/img-raw ужимаются и копируются в папку ./src/assets/static/img
   - Рекомпил шрифтов в woff. [task] == 'ttfToWoff' - новые заменяют старые в src
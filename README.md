# form-html

## Разработка

1. Устанавливаем пакеты командой `npm i` (_рабочая версия ноды `v6.7.0`_)
2. Запускаем сборщика и сервер командой `npm run dev`
3. Сервер запустится по адресу http://localhost:8080

## Сборка
1. Устанавливаем пакеты командой `npm i`
2. Запускаем сборку командой `npm run build`

## Создание нового стиля

1. Создать одноименные директории в `src\styles` и `src\templates`
    Например: `src\styles\example` и `src\templates\example`
2. В созданной директории со стилями создать основной файл стиля `index.styl`
    _Структура компонентов стилей внутри данной директории - на усмотрение разработчиков._
3. В созданной директории с шаблонами создать файл шаблона `index.pug`
    Пример:
    
    ```
    extends ../layout.pug
    include ../form.pug
    
    block form
        +form
            +cardNumber
            +expiryDate
            +cardHolder
            +cardCvv
            +cpf
            +dni
            +personalId
            +address
            +city
            +zipCode

    ```
    
    **Важно: необходимо строго соблюдать порядок очередности подключаемых миксинов элементов (полей) формы, как в примере!**
4. Для просмотра результата запустить сервер `npm run dev` и открыть в браузере URL по имени созданных директорий `http://localhost:8080/example.html`

## Ошибки
Если при выполнении команды `npm run dev` возникает ошибка наподобие:
  ```
 npm ERR! Darwin 18.0.0
 npm ERR! argv "/usr/local/bin/node" "/usr/local/bin/npm" "run" "dev"
 npm ERR! node v6.7.0
 npm ERR! npm  v3.10.3
 npm ERR! code ELIFECYCLE
 npm ERR! signed-pay@1.0.0 dev: `cross-env NODE_ENV=development webpack-dev-server -d --inline --hot --port 8089`
 npm ERR! Exit status 1
 npm ERR! 
 npm ERR! Failed at the signed-pay@1.0.0 dev script 'cross-env NODE_ENV=development webpack-dev-server -d --inline --hot --port 8089'.
 npm ERR! Make sure you have the latest version of node.js and npm installed.
 npm ERR! If you do, this is most likely a problem with the signed-pay package,
 npm ERR! not with npm itself.
 npm ERR! Tell the author that this fails on your system:
 npm ERR!     cross-env NODE_ENV=development webpack-dev-server -d --inline --hot --port 8089
 npm ERR! You can get information on how to open an issue for this project with:
 npm ERR!     npm bugs signed-pay
 npm ERR! Or if that isn't available, you can get their info via:
 npm ERR!     npm owner ls signed-pay
 npm ERR! There is likely additional logging output above.>
   ```
то нужно поменять номер порта в файле **package.json**:
  ```
"dev": "cross-env NODE_ENV=development webpack-dev-server -d --inline --hot --port 8093",
  ```
Либо для предотвращения этой проблемы при закрытии порта использовать комбинацию клавиш `ctrl + c`.
[Полная версия задания](https://github.com/netology-code/ajs-homeworks/tree/ajs8/workspace)

# Домашнее задание к лекции «Рабочее окружение»

**Важно**: каждая задача выполняется в виде отдельного проекта с собственным GitHub репозиторием.

В личном кабинете на сайте [netology.ru](http://netology.ru/) в поле комментария к домашней работе вставьте ссылки на ваш GitHub-проекты.

---

## ESLint (задача со звёздочкой)

**Важно**: данная задача не является обязательной 

### Легенда

Очень важно следить за качеством кода в вашем проекте и следовать единым принципам кодирования в команде. В этом нам поможет ещё один инструмент - ESLint.

### Описание

Ваша задача «прикрутить» ESLint к проекту и настроить работу с его использованием.

Установка:
```shell
npm install --save-dev eslint
npx eslint --init
```

При инициализации конфиг-файла выберите те же опции, что указаны в лекции:
* How would you like to use ESLint? *To check syntax, find problems, and enforce code style*
* What type of modules does your project use? *JavaScript modules (import/export)*
* Which framework does your project use? *None of this*
* Where does your code run? *Browser*
* How would you like to define a style for your project? *Use a popular style guide*
* Which style guide do you want to follow? *Airbnb*
* What format do you want your config file to be in? *JSON*
* Would you like to install them now with npm? *Y*

Настройте скрипт запуска `lint` для `npm`. Для этого в секции `scripts` файла `package.json` пропишите:
```json
{
    ...
    "scripts": {
        ...
        "lint": "eslint ."
        ...
    }
}
```

Создайте файл `src/app.js` со следующим содержимым:
```javascript
const characters = [
  {name: 'мечник', health: 10},
  {name: 'маг', health: 100},
  {name: 'маг', health: 0},
  {name: 'лучник', health: 0}
];

const alive = characters.filter(item => item.health > 0);
```

Содержимое `.eslintignore`:
```
dist
```

Содержимое `.eslintrc.json`:
```json
{
    "extends": "airbnb-base",
    "env": {
        "es6": true,
        "browser": true
    },
    "rules": {
        "no-restricted-syntax": [
            "error",
            "LabeledStatement",
            "WithStatement"
        ]
   }
}
```

Запустите ESLint и удостоверьтесь, что вам показываются ошибки стиля. Исправьте их, затем снова запустите ESLint и удостоверьтесь, что исправлены все ошибки проверки стиля.
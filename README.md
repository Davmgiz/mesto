# Mesto

> Одностраничное приложение для обмена фотографиями, созданное в учебных целях.
> Позволяет регистрироваться, редактировать профиль, публиковать «карточки» с изображениями, лайкать и удалять их.
> Фронтенд написан на чистом JavaScript с Webpack‑сборкой и развёртывается в GitHub Pages.

## Демо

▶ [Живая версия](https://davmgiz.github.io/mesto/)


## Основные возможности

* Авторизация по JWT‑токену (передаётся в `API_TOKEN`).
* Просмотр и редактирование данных профиля, замена аватара.
* Создание карточек с фотографиями и подписью.
* Лайк/дизлайк карточек, подсчёт лайков в реальном времени.
* Удаление карточки владельцем.
* Просмотр изображения в полноэкранном модальном окне.
* Валидация всех форм на клиенте.


## Технологический стек

| Слой                    | Технологии / инструменты                           |
| ----------------------- | -------------------------------------------------- |
| **Язык**                | JavaScript ES2022 (модульный)                      |
| **Сборка**              | Webpack 5, Babel, PostCSS (Autoprefixer), CSS‑nano |
| **Структура CSS**       | БЭМ (Nested‑folders)                               |
| **Запросы к API**       | Fetch + собственная обёртка                        |
| **Деплой статики**      | [gh‑pages](https://github.com/tschaub/gh-pages)    |
| **CI/CD (опционально)** | GitHub Actions                                     |

---

## Быстрый старт

### 1. Клонировать репозиторий

```bash
git clone https://github.com/<USERNAME>/<REPO>.git
cd <REPO>
```

### 2. Установить зависимости

```bash
npm install
```

### 3. Настроить переменные окружения

Создайте файл `.env` по образцу и укажите токен и базовый URL вашего REST‑API:

```env
API_TOKEN=<your_api_token>
API_BASE=https://nomoreparties.co/v1/apf-cohort-999
```

### 4. Запустить локальный сервер

```bash
npm run dev     # http://localhost:8080
```

### 5. Сборка production‑версии

```bash
npm run build   # результат в dist/
```

### 6. Публикация в GitHub Pages

```bash
npm run deploy  # создаст / обновит ветку gh-pages
```

> В Settings → Pages репозитория укажите `Branch → gh-pages / root`.


## Структура проекта (основное)

```
├── src
│   ├── blocks/          # стили БЭМ‑блоков (SCSS/PostCSS)
│   ├── images/          # статические изображения
│   ├── scripts/
│   │   ├── api.js       # работа с REST‑API
│   │   ├── card.js      # класс Card
│   │   ├── modal.js     # управление модальными окнами
│   │   └── ...
│   └── index.html       # точка входа
├── webpack.config.js
├── .env.example
└── package.json
```


## Сценарии npm

| Скрипт           | Назначение                             |
| ---------------- | -------------------------------------- |
| `npm run dev`    | Dev‑сервер с hot‑reload                |
| `npm run build`  | Production‑сборка в `dist/`            |
| `npm run deploy` | Сборка + публикация в ветку `gh-pages` |
| `npm run lint`   | (опция) ESLint + Prettier              |


## API‑интерфейс

> Подробная документация в `docs/api.md` (добавьте при интеграции собственного бэкенда).

Основные эндпоинты (REST):

* `GET    /users/me`          — данные профиля
* `PATCH  /users/me`          — изменить профиль
* `PATCH  /users/me/avatar`   — новый аватар
* `GET    /cards`             — все карточки
* `POST   /cards`             — создать карточку
* `PUT    /cards/:cardId/likes` — лайк
* `DELETE /cards/:cardId/likes` — убрать лайк
* `DELETE /cards/:cardId`       — удалить карточку


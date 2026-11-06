# Сайт TANYA BALYNSKA beauty studio

Статичний сайт: `index.html` (головна) і `shop.html` (косметика). Нічого збирати не треба.

## Публікація на Netlify з GitHub
1. Netlify → **Add new site → Import an existing project → GitHub** → репозиторій `cosmetology`.
2. Build settings лишити порожніми (усе вже є в `netlify.toml`) → **Deploy**.
3. Після цього кожна зміна в гілці `main` автоматично оновлює сайт.

## Заявки в Telegram (через Make.com)
Сайт → Make.com → бот у Telegram. Ключ бота зберігається в Make, а не в коді сайту.

### Крок 1. Бот
1. У Telegram знайдіть **@BotFather** → `/newbot` → назва та юзернейм, що закінчується на `bot`.
2. Збережіть **токен** (`123456789:AA...`) і нікому його не пересилайте.
3. З акаунта, куди мають приходити заявки, напишіть боту `/start`.

### Крок 2. Make.com
1. https://www.make.com → Create a new scenario → **Webhooks → Custom webhook** → Add → Save.
2. Скопіюйте адресу вебхука (`https://hook.eu1.make.com/...`).
3. В `index.html` знайдіть `const TELEGRAM_WEBHOOK_URL = "";` і вставте адресу між лапками.
4. У Make натисніть **Run once** і відправте тестову заявку з сайту.
5. Додайте модуль **Telegram Bot → Send a Text Message or a Reply**:
   - Connection: токен від BotFather;
   - **Chat ID**: відкрийте `https://api.telegram.org/bot<ТОКЕН>/getUpdates` і візьміть число з `"chat":{"id":...`;
   - **Text**: поле `message` з вебхука.
6. Збережіть сценарій і увімкніть **ON**.

Поки `TELEGRAM_WEBHOOK_URL` порожній, форма працює в тестовому режимі й нічого не надсилає.

## Фото «до/після»
Зараз у блоці «Результати» заглушки з логотипом. Щоб додати роботу, покладіть фото в `img/results/`
і в `index.html` у блоці `const R={` допишіть до пункту `before:"img/results/назва-до.jpg", after:"img/results/назва-після.jpg"`.

## Косметика
Сторінка `shop.html`: 8 порожніх карток з логотипом, які чекають на товари.

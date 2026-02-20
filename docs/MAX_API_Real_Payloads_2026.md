# Real World MAX API Payloads (2026)
# Reverse engineered JSON payloads for MAX Messenger API (Feb 2026). Real-world examples for developers./
---
# MAX Messenger API & SubCheckerBot Architecture

> **CRITICAL REFERENCE:** This document contains REAL payloads captured from the MAX API on Feb 10, 2026.
> AI coding assistants must use these structures, NOT generic Telegram schemas.

## 1. Bot Identity (`/me`)
*Source: `bot_info_me.json`*
```json

{
  "user_id": 12345,
  "first_name": "Bot_Name",
  "username": "example_bot",
  "is_bot": true,
  "last_activity_time": 1739184000000,
  "description": "🚀 Автовыдача бонусов за подписку! Бот проверяет подписку на ваш канал и мгновенно выдает лид-магнит (файл или ссылку). 📈 Расти аудиторию на автомате. ⚙️ Настройка поста за 1 минуту.",
  "avatar_url": "https://i.oneme.ru/i?r=BTFjO43w8Yr1OSJ4tcurq5HiGFXTgmcNFCqWsL5eFLaBsq_WO3gNo_PCmzpboct_jy8",
  "full_avatar_url": "https://i.oneme.ru/i?r=BTFjO43w8Yr1OSJ4tcurq5HiHBeIhpWE6pyKskhnmJMdXK_WO3gNo_PCmzpboct_jy8",
  "commands": [
    {
      "name": "start",
      "description": "Главное меню"
    },
    {
      "name": "menu",
      "description": "Главное меню"
    },
    {
      "name": "help",
      "description": "Помощь"
    }
  ],
  "name": "Bot_Name"
}

2. Real API Events (Webhooks)
2.1 Message Event: Text (message_created)
Triggered when a user sends text. Source: event_message_created_xxxx.json (Text variant)
JSON
{
  "timestamp": 1739184000000,
  "message": {
    "recipient": {
      "chat_id": -100000000,
      "chat_type": "dialog",
      "user_id": 12345
    },
    "timestamp": 1739184000000,
    "body": {
      "mid": "mid.REDACTED_ID",
      "seq": 0,
      "text": "Привет"
    },
    "sender": {
      "user_id": 54321,
      "first_name": "User_Name",
      "last_name": "",
      "is_bot": false,
      "last_activity_time": 1739184000000,
      "name": "User_Name"
    }
  },
  "user_locale": "ru",
  "update_type": "message_created"
}


2.2 Message Event: Image/Media (message_created)
Triggered when a user uploads an image. Source: event_message_created_xxxx.json (Image variant)
JSON
{
  "callback": {
    "timestamp": 1739184000000,
    "callback_id": "CALLBACK_ID_REDACTED",
    "user": {
      "user_id": 54321,
      "first_name": "User_Name",
      "last_name": "",
      "is_bot": false,
      "last_activity_time": 1739184000000,
      "name": "User_Name"
    },
    "payload": "new_campaign"
  },
  "message": {
    "recipient": {
      "chat_id": -100000000,
      "chat_type": "dialog",
      "user_id": 54321
    },
    "timestamp": 1739184000000,
    "body": {
      "mid": "mid.REDACTED_ID",
      "seq": 0,
      "text": "Описание бота",
      "attachments": [
        {
          "callback_id": "CALLBACK_ID_REDACTED",
          "payload": {
            "buttons": [
              [
                {
                  "payload": "new_campaign",
                  "text": "➕ Создать новую проверку",
                  "intent": "default",
                  "type": "callback"
                }
              ],
              [
                {
                  "payload": "menu_my_campaigns",
                  "text": "📂 Мои проверки",
                  "intent": "default",
                  "type": "callback"
                }
              ],
              [
                {
                  "payload": "menu_statistics",
                  "text": "📊 Статистика",
                  "intent": "default",
                  "type": "callback"
                }
              ],
              [
                {
                  "payload": "menu_settings",
                  "text": "⚙️ Настройки",
                  "intent": "default",
                  "type": "callback"
                }
              ],
              [
                {
                  "payload": "menu_help",
                  "text": "🆘 Помощь",
                  "intent": "default",
                  "type": "callback"
                }
              ],
              [
                {
                  "payload": "menu_what",
                  "text": "😏 Чё это за бот ваще?",
                  "intent": "default",
                  "type": "callback"
                }
              ]
            ]
          },
          "type": "inline_keyboard"
        },
        {
          "payload": {
            "photo_id": 0,
            "token": "MEDIA_TOKEN_REDACTED",
            "url": "https://example.com/image.png"
          },
          "type": "image"
        }
      ]
    },
    "sender": {
      "user_id": 12345,
      "first_name": "Bot_Name",
      "username": "example_bot",
      "is_bot": true,
      "last_activity_time": 1739184000000,
      "name": "Bot_Name"
    }
  },
  "timestamp": 1739184000000,
  "user_locale": "ru",
  "update_type": "message_callback"
}

2.3 Callback Event (message_callback)
Triggered when an inline button is pressed. Source: event_message_callback_xxxx.json
JSON
{
  "callback": {
    "timestamp": 1739184000000,
    "callback_id": "CALLBACK_ID_REDACTED",
    "user": {
      "user_id": 54321,
      "first_name": "User_Name",
      "last_name": "",
      "is_bot": false,
      "last_activity_time": 1739184000000,
      "name": "User_Name"
    },
    "payload": "utm_view_6"
  },
  "message": {
    "recipient": {
      "chat_id": -100000000,
      "chat_type": "dialog",
      "user_id": 54321
    },
    "timestamp": 1739184000000,
    "body": {
      "mid": "mid.REDACTED_ID",
      "seq": 0,
      "text": "🔗 UTM-ссылки\n\nКампания 1 — 0 получивших бонус, 0 пытались забрать бонус, 0 просмотров поста\nКампания 2 — 0 получивших бонус, 0 пытались забрать бонус, 0 просмотров поста",
      "attachments": [
        {
          "callback_id": "CALLBACK_ID_REDACTED",
          "payload": {
            "buttons": [
              [
                {
                  "payload": "utm_view_2",
                  "text": "🔗 Кампания 1",
                  "intent": "default",
                  "type": "callback"
                }
              ],
              [
                {
                  "payload": "utm_view_1",
                  "text": "🔗 Кампания 2",
                  "intent": "default",
                  "type": "callback"
                }
              ],
              [
                {
                  "payload": "utm_create",
                  "text": "➕ Создать UTM-ссылку",
                  "intent": "default",
                  "type": "callback"
                }
              ],
              [
                {
                  "payload": "view_campaign",
                  "text": "🔙 К проверке",
                  "intent": "default",
                  "type": "callback"
                }
              ]
            ]
          },
          "type": "inline_keyboard"
        }
      ],
      "markup": [
        {
          "from": 0,
          "length": 12,
          "type": "strong"
        }
      ]
    },
    "sender": {
      "user_id": 12345,
      "first_name": "Bot_Name",
      "username": "example_bot",
      "is_bot": true,
      "last_activity_time": 1739184000000,
      "name": "Bot_Name"
    }
  },
  "timestamp": 1739184000000,
  "user_locale": "ru",
  "update_type": "message_callback"
}

2.4 User Added (user_added)
Triggered when a user opens the chat or unblocks the bot. Source: event_user_added_xxxx.json
JSON
{
  "chat_id": -100000000,
  "user": {
    "user_id": 55555,
    "first_name": "User_Name",
    "last_name": "",
    "is_bot": false,
    "last_activity_time": 1739184000000,
    "name": "User_Name"
  },
  "is_channel": true,
  "timestamp": 1739184000000,
  "update_type": "user_added"
}


## 2.5 Анализ несоответствий: Docs vs Real Payloads

Здесь и далее:
**DOCS**: Как это описано в объектах Message, User на dev.max.ru.
**REAL**: Что на самом деле прилетает в вебхуке (твой файл).

### 1. Структура обновления (Update Wrapper)
Критичное отличие: Документация описывает объект Message. Но вебхук присылает объект Update, внутри которого лежит message.

**DOCS**: Описывает чистый Message:
```json
{ "sender": {...}, "body": {...} }
```

**REAL**: Оборачивает всё в контейнер с метаданными:
```json
{
  "update_type": "message_created",  // <--- Этого нет в описании Message
  "user_locale": "ru",               // <--- Важно для локализации
  "timestamp": 1739184000000,        // <--- Дублируется на верхнем уровне
  "message": { ... }                 // <--- Сам объект Message тут
}
```
> **Вывод**: Твой `main.py` должен парсить корень JSON, смотреть `update_type`, и только потом лезть в `['message']`.

### 2. Таймстемпы (Timestamp)
Мелкая, но фатальная деталь:

**DOCS**: "**Unix-time**" (обычно подразумеваются секунды, 1739184000).
**REAL**: **Milliseconds** (1739184000000).

> **Вывод**: Если парсить как секунды, получишь 57000-й год. Дели на 1000.

### 3. Объект Sender (Отправитель)
**DOCS**: Часто ссылаются на User объект.
**REAL**: Поле называется **sender**, а не `from` (как в Telegram) или `user`.

Нюанс: В Telegram API это `message.from`. В MAX API это `message.sender`.
Нюанс 2: В реальном пейлоаде у бота (`is_bot: true`) есть поле `username`, а у юзера его может не быть (или пустое), зато есть `name`.

### 4. Текст сообщения (Body)
Самая частая ошибка новичков в MAX.

Telegram Style / Ожидание: `message.text`
**DOCS**: `body.text`
**REAL**: `message.body.text`

```json
"body": {
  "mid": "mid.REDACTED",
  "seq": 0,
  "text": "Привет"
}
```
> **Вывод**: Текст лежит глубоко: `payload['message']['body']['text']`.

### 5. Callback (Нажатие кнопок)
Здесь архитектура MAX сильно отличается от Telegram.

**REAL**: При нажатии кнопки приходит `update_type: "message_callback"`.
В этом объекте `callback` и `message` — братья (siblings).

```json
{
  "callback": { "payload": "utm_view_6", ... }, // <--- Данные кнопки тут
  "message": { ... }                            // <--- Сообщение, к которому кнопка привязана
}
```
> **Вывод**: ID пользователя, нажавшего кнопку, лежит в `callback.user.user_id`, а не в `message.sender.user_id` (sender там — это сам бот, отправивший сообщение).

### 6. Вложения (Attachments)
**DOCS**: MessageBody может содержать `attachments`.

**REAL**:
```json
"body": {
  "text": "Описание...",
  "attachments": [
    { "type": "inline_keyboard", "payload": { ... } }, // Клавиатура — это тоже attachment!
    { "type": "image", "payload": { "url": "..." } }
  ]
}
```
> **Вывод**: Кнопки (`inline_keyboard`) приходят как вложение, а не отдельным полем `reply_markup` (как в Telegram).


3. The Internal Normalization Layer

IMPORTANT FOR DEVELOPERS: The SubCheckerBot transforms the Raw Data (above) into a Normalized Object in main.py before passing it to Handlers.
- If editing main.py / api.py: Use the **Raw JSON structures** above.
- If editing handlers/.py: Use the **Normalized keys** below.

| Normalized Field (In Handlers) | Mapped From Raw MAX JSON |
|-------------------------------|--------------------------|
| message.text | message.body.text |
| message.from.id / from_user.id | message.sender (MAX has no "from"; we build it from sender) |
| message.chat.id | message.recipient.chat_id; for dialog → recipient.user_id or sender.user_id |
| callback_query.id | callback.callback_id |
| callback_query.data | **callback.payload** (string, e.g. "check_system_sub", "utm_view_6") | 

4. API Quirks & Limits
Images: External URLs are forbidden. Flow: POST /uploads -> Get Token -> POST /messages with token.

Deep Links: Parsed from message.body.text (e.g., /start c42) or specific payload fields if available.

>**Original Source & Updates:**
> This document is a snapshot of the collection maintained in [this GitHub Gist](https://gist.github.com/Danya2904/4280c88912090e7440fb7bfc54abdea3).
> Please check the Gist for the most recent updates or to leave comments/stars.

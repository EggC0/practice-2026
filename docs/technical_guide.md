# Техническое руководство для начинающих

## Пошаговая инструкция

### Шаг 1. Создание бота
Создайте бота в Telegram через `@BotFather` и получите токен.

### Шаг 2. Установка Python и библиотек
Установите необходимые библиотеки:

```bash
pip install pyTelegramBotAPI python-dotenv
```

### Шаг 3. Создание файлов
Создайте файлы:

- `bot.py`
- `.env` — для хранения токена

### Шаг 4. Код бота

Основные блоки программы:

- импорты библиотек;
- загрузка токена;
- словарь предсказаний;
- создание клавиатур;
- обработчики команд;
- callback-обработчик;
- логирование.

#### Пример кода

```python
def sign_keyboard():
    keyboard = telebot.types.InlineKeyboardMarkup(row_width=3)

    signs = [
        'Aries', 'Taurus', 'Gemini',
        'Cancer', 'Leo', 'Virgo',
        'Libra', 'Scorpio', 'Sagittarius',
        'Capricorn', 'Aquarius', 'Pisces'
    ]

    buttons = [
        telebot.types.InlineKeyboardButton(
            s,
            callback_data=f'sign_{s.lower()}'
        )
        for s in signs
    ]

    keyboard.add(*buttons)
    return keyboard
```

### Шаг 5. Логирование
Действия пользователей записываются в файл `bot_log.txt`.

### Шаг 6. Запуск бота

```bash
py bot.py
```

## Диаграмма последовательности (UML)

```text
Пользователь → /horoscope → бот → выбор знака
→ выбор даты → бот → поиск в словаре
→ отправка предсказания
```

## Таблица команд

| Команда | Действие |
|---|---|
| `/start` | Приветствие |
| `/horoscope` | Выбор знака и даты |
| `/help` | Справка |

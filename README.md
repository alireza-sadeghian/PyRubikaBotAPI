# PyRubikaBotAPI Python Package
A Python library for developing Rubika bots, from the simplest to the most advanced.

## Instalation
You need Python version 3.10 or higher to install this library.
```bash
python -m pip install PyRubikaBotAPI
```

To update pip, you can use the following command:
```bash
python -m pip install --upgrade pip
```

## Get Started
To get started, go to @BotFother on Rubika, create a new bot, and obtain a token.
```python
from Rubibot import Rubibot
```
Now, paste the received token in this field."
```python
bot = RubiBot('your_token')
```
Defining a simple handler
```python
@bot.message_handler()
def start(message):
  bot.reply_to(message.chat_id, message.text)
```
Now we have created a handler that can reply to all user messages with the same message.
To run the bot locally for testing, we use this method. Place this method at the end of your Python file.
```python
bot.polling(t=1)
```

## Features

PyRubikaBotAPI provides a variety of methods to easily build Rubika bots, from simple echo bots to advanced interactive bots. Below is an overview of the most important methods:

---

### 1. `message_handler`
Handles all incoming messages and updates from users. You can filter by commands or content types such as text, sticker, file, location, contact, and poll. Handlers are executed in the order they are defined.

**Example:**
```python
bot = RubiBot('TOKEN')

# Handle /start command
@bot.message_handler(commands=['start'])
def start(message):
    bot.send_message(message.chat_id, "Hello from RubiBot!")

# Handle all sticker messages
@bot.message_handler(content_types=['sticker'])
def sticker_handler(message):
    bot.send_file(message.chat_id, message.sticker.file.id, "Here is your sticker")

# Handle all text messages
@bot.message_handler()
def echo(message):
    bot.reply_to(message, message.text)
```

### 2. `send_message`
Send a text message to a specific chat. You can also attach a chat keypad, inline buttons, or disable notification.

**Example:**
```python
bot.send_message(
    chat_id="123456",
    text="Hello, this is a test message!"
)
```

### 3. `reply_to`
Reply to a specific message conveniently with text.

**Example:**
```python
@bot.message_handler()
def greet(message):
    bot.reply_to(message, "Thanks for your message!")
```

### 4. `get_me`
Retrieve information about your bot, including username, avatar, description, and share URL.

**Example:**
```python
bot_info = bot.get_me()
print(bot_info.username, bot_info.description)
```

### 5. `send_poll`
Send a poll to a specific chat.

**Example:**
```python
poll = ChatPoll("Favorite color?", ["Red", "Blue", "Green"])
bot.send_poll(chat_id="123456", poll=poll)
```

### 6. `send_contact`
Send a contact to a chat.

**Example:**
```python
bot.send_contact(
    chat_id="123456",
    first_name="John",
    last_name="Doe",
    phone_number="+123456789"
)
```

### 7. `get_chat`
Retrieve information about a chat, such as its type, title, and username.

**Example:**
```python
chat_info = bot.get_chat("123456")
print(chat_info.title, chat_info.username)
```

### 8. `forward`
Forward a message from one chat to another.

**Example:**
```python
bot.forward(from_chat_id="123", to_chat_id="456", message_id="789")
```

### 9. `edit_message`
Edit the text or inline buttons of a sent message.

**Example:**
```python
bot.edit_message(chat_id="123", message_id="456", new_text="Updated text")
```

### 10. `delete_message`
Delete a specific message.

**Example:**
```python
bot.delete_message(chat_id="123", message_id="456")
```

### 11. `set_commands`
Set commands that appear for new users in the bot interface.

**Example:**
```python
bot.set_commands(
    BotCommand("/start", "Start the bot"),
    BotCommand("/help", "Show help")
)
```

### 12. `edit_chat_keypad`
Update or remove the chat keypad for a specific chat.

**Example:**
```python
bot.edit_chat_keypad(chat_id="123", chat_keypad=my_keypad)
```

### 13. `set_webhook`
Set a webhook to receive updates from Rubika.

**Example:**
```python
bot.set_webhook("https://myserver.com/webhook")
```

### 14. `get_file` & `download_file`
Get a file download URL and download the file sent by users.

**Example:**
```python
file_url = bot.get_file("file_id")
file_data = bot.download_file(file_url)
with open("file.png", "wb") as f:
    f.write(file_data)
```

💡 **Tip:** PyRubikaBotAPI allows you to build bots ranging from **simple echo bots** to **full-featured interactive bots** with polls, contacts, keyboards, and more.

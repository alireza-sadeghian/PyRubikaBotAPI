# PyRubikaBotAPI Python Package
A Python library for developing Rubika bots, from the simplest to the most advanced.

## Instalation
You need Python version 3.10 or higher to install this library.
```bash
python -m pip install PyRubikaBotAPI

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



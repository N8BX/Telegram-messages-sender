# Telegram Message Sender

A Python script that sends messages to all Telegram contacts using the **Telethon** library.

## Features
- Logs into Telegram via Telethon.
- Sends a message to all non-bot contacts.

## Installation
1. **Clone the repository**:
   ```bash
   git clone https://github.com/YOUR_USERNAME/telegram-message-sender.git
   cd telegram-message-sender
   ```

2. **Install dependencies**:
   ```bash
   pip install telethon
   ```

## Usage
Run the script:
```python
from telethon import TelegramClient
import asyncio
 
api_id = 'YOUR_API_ID'
api_hash = 'YOUR_API_HASH'

client = TelegramClient('session_name', api_id, api_hash)

async def send_messages_to_all():
    try:
        print("Logging in...")
        await client.start()
        print("Login successful.")
        message = input('Enter Your Message: ')
        dialogs = await client.get_dialogs()
        if not dialogs:
            print("No conversations found.")
        else:
            print(f"Found {len(dialogs)} conversations.")

        for dialog in dialogs:
            if dialog.is_user and not dialog.entity.bot:
                try:
                    await client.send_message(dialog.id, message)
                    print(f"Message sent to {dialog.name}")
                except Exception as e:
                    print(f"Error sending message to {dialog.name}: {e}")
    except Exception as e:
        print(f"Script error: {e}")

with client:
    client.loop.run_until_complete(send_messages_to_all())
```

## Connect with Me
- **GitHub**: [YOUR_GITHUB](https://github.com/N8BX)
- **Telegram**: [YOUR_TELEGRAM](https://t.me/SY_BROTHER)
- **Twitter/X**: [YOUR_TWITTER](https://twitter.com/SY_GRX)

## ⭐ Star This Repository
If you like this project, don't forget to **star** ⭐ it on GitHub!

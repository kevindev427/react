# ChatGPT Bot for Telegram

![](/docs/dialog.png)

## News

- **DALL·E, the OpenAI Image Generation Model**, is now supported! Send a short prompt to the Bot and get your own painting!
- **Whisper, the OpenAI Intelligent Speech Recognizer**, is now supported! Now chat with the Bot with audio messages!
- **Important privacy protection stategy** is deployed! The Bot is unable to collect any message in group chat except user prompts.

## Introduction

ChatGPT Bot for Telegram is implemented with [OpenAI ChatGPT API](https://platform.openai.com/docs/guides/chat) released on March 1, 2023. The Telegram integration framework is based on [python-telegram-bot](https://python-telegram-bot.org).

ChatGPT Bot can act as your Telegram contact. You can chat with it personally, share with a contact, and collabrate in a group chat. We attach great importance to privacy protection and make sure the Bot can't acquire any unrelated messages in group chats.

The Bot shares knowledge and inspires exciting new ideas. Many interesting features, such as **DALL·E** and **Whisper** are integrated together to make our Bot smarter and more usable.

We hope you enjoy it!

## Features

The Telegram Bot features the following functions:

- An AI consultant, based on OpenAI ChatGPT, interacts in a conversational way.
- A flexible speech recognizer which supports audio interaction.
- A AI painter reponses to user's requirement prompt.

Additonal functions are also implemented:

- (Beta) _Telegram inline mode_ is supported to invoke the Bot in a private chat with a contact.
- Set the daily limitation of requirements to **DALL·E**.
- Grant more resources to _Super Users_.

## Commands

- `/start`: Start the bot.
- `/clear`: Clear the conversation context.
- `/chat` : Invoke the Bot in group chat.
- `/getid`: Get your Telegram user ID.
- `/dalle <prompt>`: Ask DALL·E for a painting based on your prompt.

## Sample Usage

The Bot works in both personal and group chat of Telegram.

In a personal chat, simply send a message to the Bot and it will reply to you.

In a group chat, use the `/chat` to invoke the Bot. It will not collect any other message except the prompts after the command.

**(Beta)** In a personal chat with a contact, use `@your_bot_name <your messages>` to invoke the Bot with Telegram inline mode. Both you and your contact can see the Bot's reply in the chat. This function is Beta because it currently can't record the chat context.

### Preparation

1. Create a Telegram bot by [@BotFather](https://t.me/BotFather) and get the token.
2. Create an OpenAI account and get the API key.
3. A Linux VM or a server with Python 3 is needed to run the bot.
4. A practical Internet environment is required.
5. (Optional) [FFmpeg](https://ffmpeg.org) is required for the Bot to handle voice messages with Whisper. If you are not interested in using voice messages, you don't need to install it and **must set `enable_voice` in the config file to False**.

> **Note**: You should disable the privacy mode of the bot. Otherwise the bot will not receive the messages from the group chat. You can do this by sending `/setprivacy` to [@BotFather](https://t.me/BotFather).

### Deployment

Git clone from main branch or download the latest release [Source code](https://github.com/flynnoct/chatgpt-telegram-bot/releases/latest) and install the dependencies.

```bash
git clone https://github.com/flynnoct/chatgpt-telegram-bot.git
cd chatgpt-telegram-bot
pip install -r requirements.txt
```

Then, you need to create a config file to manage the Bot. The config file includes sensitive information, such as telegram_token and openai_api_key, and we only release the corresponding template `config.json.template`. Therefore, you need to create a new `config.json` file and replace the relative fields with your own.

```bash
cp config.json.template config.json
```

Follow below procedures to modify your `config.json`:

1. Replace the `telegram_token` and `openai_api_key` with your own.
2. Add allowed users to the `allowed_users` list. You can get your user id by sending `/start` to [@userinfobot](https://t.me/userinfobot) or send `/getid` to the Bot (after you start it).

> Note: the user ID is a series of numbers, you should add it to the `allowed_users` list as a string (add quotation marks around it).

Now, you can run the Bot with `start_bot.sh` and try talk to it. Also, you can invite it to group chats and share with your friends!

```bash
# First, make sure you are in the root directory of the project,
# aka <your_download_location>/chatgpt-telegram-bot
bash ./bin/start_bot.sh # start the bot
```

To clear ChatGPT conversation context and restart the Bot, run shell script `restart_bot.sh`. To shut down the Bot, run `stop_bot.sh`.

```bash
bash ./bin/restart_bot.sh # restart the bot
bash ./bin/stop_bot.sh # stop the bot
```

## Release version and notes

The latest released version can be found [here](https://github.com/flynnoct/chatgpt-telegram-bot/releases/latest). More interesting new features are comming soon!

The release notes are [here](/docs/release_notes.md).

## License

[MIT](LICENSE.md)

## Buy Me a Coffee

If you like this project, you can buy me a coffee ❤️ or give this repository a free star ⭐️.

Click [Alipay](docs/donate_code/alipay.jpg) to open QR code.

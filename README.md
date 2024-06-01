<h1 align="center">Node.js Telegram Bot API</h1>

<div align="center">

Node.js module to interact with the official [Telegram Bot API](https://core.telegram.org/bots/api).

</div>

## 📦 Install

```sh
npm i node-telegram-bot-api
```

<br/>

> ✍️ **Note:** If you use Typescript you can install this package that contains type definitions for this library
>```sh
>npm install --save-dev @types/node-telegram-bot-api
>```

## 🚀 Usage

```js
const TelegramBot = require('node-telegram-bot-api');

// replace the value below with the Telegram token you receive from @BotFather
const token = 'YOUR_TELEGRAM_BOT_TOKEN';

// Create a bot that uses 'polling' to fetch new updates
const bot = new TelegramBot(token, {polling: true});

// Matches "/echo [whatever]"
bot.onText(/\/echo (.+)/, (msg, match) => {
  // 'msg' is the received Message from Telegram
  // 'match' is the result of executing the regexp above on the text content
  // of the message

  const chatId = msg.chat.id;
  const resp = match[1]; // the captured "whatever"

  // send back the matched "whatever" to the chat
  bot.sendMessage(chatId, resp);
});

// Listen for any kind of message. There are different kinds of
// messages.
bot.on('message', (msg) => {
  const chatId = msg.chat.id;

  // send a message to the chat acknowledging receipt of their message
  bot.sendMessage(chatId, 'Received your message');
});
```


# rexz-imagine-ai

## Description
`rexz-imagine-ai` is an AI-powered image generation package that allows users to create stunning visuals based on text prompts. It simplifies the process of generating AI-driven artwork and is easy to integrate into your JavaScript or Node.js projects.

## Installation
Install the package using npm:

```sh
npm install rexz-imagine-ai
```

## Usage
Below is a simple example demonstrating how to use `rexz-imagine-ai` to generate an image from a text prompt.

```javascript
const rexzimagine = require("rexz-imagine-ai");

async function main() {
  const prompt = "A futuristic cyberpunk cityscape with neon lights and flying cars.";
  const result = await rexzimagine.response(prompt);
  console.log(result);
}

main();
```

## Discord Usage
Below is a simple example demonstrating how to use `rexz-imagine-ai` in discord bot to generate an image from a text prompt with the help of `MongoDB` (you can use any other DB or send it directly).

```javascript
const { Client, GatewayIntentBits } = require('discord.js');
const mongoose = require('mongoose');
const fs = require('fs');
const rexzimagine = require('rexz-imagine-ai');
const { GridFSBucket } = require('mongodb');

const client = new Client({ intents: [GatewayIntentBits.Guilds, GatewayIntentBits.GuildMessages, GatewayIntentBits.MessageContent] });
token = 'your bot token'
mongoose.connect('Your Mongo DB ', { useNewUrlParser: true, useUnifiedTopology: true })
  .then(() => console.log('Connected to MongoDB'))
  .catch(err => console.error(err));

const db = mongoose.connection;
let bucket;
db.once('open', () => {
  bucket = new GridFSBucket(db.db, { bucketName: 'images' });
});

client.on('messageCreate', async (message) => {

    if (!message.content.startsWith('-imagine')) return;

    const prompt = message.content.replace('-imagine ', '').trim();
    if (!prompt) return message.reply('Please provide a prompt!');

    try {
     
        const result = await rexzimagine.response(prompt);

  
        const imagePath = './image.png';

     
        const imageStream = fs.createReadStream(imagePath);
        const uploadStream = bucket.openUploadStream('image.png');
        imageStream.pipe(uploadStream);

     
        uploadStream.on('finish', async () => {
          
            await message.channel.send({
                content: `${message.author.toString()}, here is your imagination:`,
                files: [imagePath]
            });
        });
    } catch (error) {
      
        console.error(error);
        message.reply('Failed to generate image. Please try again.');
    }
});
client.login(token); 
```

## Example Output
![Generated Image 1](https://github.com/ExE-Venom/rexz-imagine-ai/blob/main/cropped_image.png)
![Generated Image 2](https://github.com/ExE-Venom/rexz-imagine-ai/blob/main/cropped_image-1.png) 
![Generated Image 3](https://github.com/ExE-Venom/rexz-imagine-ai/blob/main/cropped_image-2.png) 

## API
### `rexzimagine.response(prompt: string) => Promise<string>`
Generates an image URL based on the given text prompt.

#### Parameters
- `prompt` (string): A description of the image you want to generate.

#### Returns
- A `Promise<string>` containing the URL of the generated image.

## Features
- Simple API for generating AI-based images.
- Fast and reliable response times.
- Easily integrates with Node.js applications.

## License
This project is licensed under the MIT License.

## Contributing
Contributions are welcome! Feel free to submit issues and pull requests to improve the package.

## Support
If you encounter any issues or have questions, please open an issue on the GitHub repository.

For further assistance:
Discord: [RexZ Development](https://discord.gg/AjH5wHWU4M)

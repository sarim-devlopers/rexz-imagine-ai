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

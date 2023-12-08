# c11-chatgpt
An introduction to the ChatGPT API. Use this repository as a tutorial!

## Setup

### Creating an Account
In order to use the ChatGPT API, you will need an openai account.

Navigate to the [OpenAI API page](https://openai.com/product) and Click on Get Started. Create an account.

### Getting an API Key
After creating your account, navigate to the API keys section.

Create your own key, or use the one provided to you.

### Saving your API Key
On the root directory of your project, create an `.env` file. Add the following contents:

```
export OPENAI_API_KEY=<your api key here>
```

replacing `<your api key here>` with your key.

### Initialize and Install OpenAI
Run:
```
npm init -y
npm install openai
npm install dotenv # allows your api key to be read
```

Add the following line within `package.json`:
```
{
    ...
    "type": "module"
}
```

### Using the import
Import the openai package using the following lines on a js file.
```
import OpenAI from "openai"

const openai = new OpenAI()
```


## Exercise 1
Complete the setup and create the following file:
```
import dotenv from "dotenv"
import OpenAI from "openai"

dotenv.config()

const openai = new OpenAI({
    apiKey: process.env.OPENAI_API_KEY
})

async function main() {
  const completion = await openai.chat.completions.create({
    messages: [{ role: "system", content: "You are a helpful assistant." }],
    model: "gpt-3.5-turbo",
  })

  console.log(completion)
}

main()
```

Run the file using the following command:
```
node openai-test.js
```

## Exercise 2

### Refining output
Edit the console log such that the output is only the response like so:
```
GPT: How can I assist you today?
```
Make sure to add `GPT: ` before the response.

### Implementing user input
We will be implementing user input using the cli.
Edit the code to add `process.argv[2]`, which is the first input on the command line, as a message to send to ChatGPT.

Read the [Chat Completions API](https://platform.openai.com/docs/guides/text-generation/chat-completions-api) to determine how to add a new message to your current completion.

#### Solution Hint
```
{"role": "user", "content": process.argv[2]}
```

#### Example usage:
```
c11-chatgpt % node chat.js "Can you give me the history of the Turing Test?"
GPT: The Turing Test, proposed by the British mathematician and computer scientist Alan Turing in 1950, ...
```

## Exercise 3
Train your model to provide sarcastic responses. Learn more on the [Fine Tuning API](https://platform.openai.com/docs/guides/fine-tuning) document. Have fun!
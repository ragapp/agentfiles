# agentfiles

Run AI agents with a single file. 

Using a simple file format to define AI agents (for single and multi-agent systems). 
Each agent is defined by its name, backstory, goal, role, and the tools that it uses.

The agentfile is a YAML file that is a superset of [crewai's agent config](https://docs.crewai.com/concepts/agents#yaml-configuration-recommended).

## Examples

You can find a number of example agentfiles in the [`examples`](examples) directory. 

For running each of the examples, call the `agentfile` script with the path to the example agentfile. The examples use [ragapp](https://github.com/ragapp/ragapp) to run the agent.

To run the examples, make sure your environment has the following configured:

- [Docker](https://www.docker.com/)
- An [OpenAI API key](https://platform.openai.com/account/api-keys) set as `OPENAI_API_KEY` environment variable

### News Reporter

```bash
./agentfile ./examples/news.yaml
```

Go to http://localhost:8000 and try it out by typing "Generate a report about The Hughes Fire"

### Financial Analyst

For this, you'll need a [Stability AI API key](https://platform.stability.ai/account/keys) and set it in the `tools.ImageGenerator.config.api_key` property of the agentfile.

```bash
./agentfile ./examples/finance.yaml
```

Go to http://localhost:8000 and try it out by typing "Write an article about the upcoming tariffs on Canada in 2025"

## Create your own agentfile

Just call `agentfile` with no arguments to create an `agents.yaml` file:

```bash
./agentfile
```

Then go to http://localhost:8000/admin/ to configure the agentfile. On the right side, you can test the agentfile by typing by chatting with the agent.

## Tools 

The list of supported tools can be found in the [`tools`](https://github.com/ragapp/ragapp/tree/main/src/ragapp/backend/models/tools) directory. The best way to create a tool configuration is to configure the agentfile via UI as described in the previous section.

## Changing the model

The `agentfile` script supports the following optional parameters to change the model used:

### `--model`

Specify which model to use. Defaults to `gpt-4o-mini` if not specified.

```bash
./agentfile --model gpt-4o ./examples/news.yaml
```

### `--model-provider`

Specify the model provider to use. Defaults to `openai` if not specified. When using `--model-provider`, you must also specify the `--model` parameter.

```bash
./agentfile --model-provider gemini --model gemini-1.5-pro-latest ./examples/news.yaml
```

The following providers are supported: `openai`, `gemini`, `ollama`, `azure-openai`, `t-systems`, `mistral`, `groq`.

Changing the model provider, you need to set the necessary environment variables. For example, to use `gemini`, you need to set `GOOGLE_API_KEY` to your API key.

## Contributing

Please fork this repo and submit pull requests adding new examples or improving the existing ones.
# agentfiles

A simple file format to define AI agents (for single and multi-agent systems). 
Each agent is defined by its name, backstory, goal, role, and the tools that it uses.

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
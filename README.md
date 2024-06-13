# Gnosis Labs ZuBerlin 2024

Welcome to the Gnosis AI dAGI Hackathon repo! Here you will find all you need to build an AI agent that can autonomously complete actions (including onchain).

[Presentation available here.](https://docs.google.com/presentation/d/1aOLmKrRkkNktWOh3BwLqtG9AmQeiht9Gc1ONB5fH7RQ/edit?usp=sharing)

Follow the instructions below to get started.

## Running the autonomous agent

``````

## Support

Contact us on Discord (channel #gnosis-ai on the Gnosis Discord).

## Setup

Install the project dependencies with `poetry`, using Python 3.10 (you can use [pyenv](https://github.com/pyenv/pyenv) to manage multiple Python versions):

```bash
python3.10 -m pip install poetry
python3.10 -m poetry install
python3.10 -m poetry shell
```

Copy `.env.example` to `.env` and fill in the values:

### OpenAI API key

We will provide you with OpenAI key that's allowed to use gpt-3.5-turbo and embedding models, contact us.

However, everyone is welcome to use any arbitrary LLM you like (for example, open-source Ollama models).

### Tavily API key

Create a free acount on https://tavily.com and get the key there.

Again, everyone is welcome to use arbitrary search engines, combine them, or even do a totally different approaches!

### Private key on Gnosis Chain

We recommend you create a fresh new developer key for the project to avoid losing your funds. 

You can create a new set of private and public keys by running
```python
from eth_account import Account
acc = Account.create()
print (acc.key.hex(), acc.address)
```

By default the script will do only very tiny bets (0.00001 xDai per market).

## Task

Your task is to add new functions to the general agent. Be creative!

-> Feel free to get inspiration from the tools we already built (https://github.com/gnosis/prediction-market-agent/blob/main/prediction_market_agent/agents/microchain_agent/microchain_agent.py#L30)

You can play with the prompts, different approaches, different LLMs, search engines, or anything you can think of.

A few ideas:

- Interact with protocolos on Gnosis Chain (Aave, CowSwap, Omen, etc.)

## Deployment

We suggest using [Modal](https://modal.com) for the deployment of agents.
If you installed the dependencies using Poetry, Modal should already be available in your environment.
You need to create an account and generate api keys. Then, add the keys MODAL_TOKEN_ID and MODAL_TOKEN_SECRET to your .env file.

For creating a cron job that triggers the general agent, deploy it with
```
poetry run modal deploy --name <YOUR_APP_NAME> general_agent/remote_runner.py  
```
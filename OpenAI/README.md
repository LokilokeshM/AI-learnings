# OpenAI Agents — Companion Code

Three small, self-contained scripts that go from a single API call to a
multi-agent customer support system, using the OpenAI Responses API and the
OpenAI Agents SDK.

## Setup

### 1. Install Python 3.10+
Make sure you have Python 3.10 or newer installed.

### 2. Create a virtual environment
```bash
python -m venv .venv
source .venv/bin/activate        # Mac/Linux
# .venv\Scripts\activate         # Windows
```

### 3. Install dependencies
```bash
pip install openai openai-agents pydantic python-dotenv
```

### 4. Set your API key
Get an API key from https://platform.openai.com/api-keys

Every script calls `load_dotenv()`, so the simplest option is a `.env` file in
this folder:

```
OPENAI_API_KEY=sk-...
```

`.env` is already covered by the repo's `.gitignore`, so your key won't be
committed. An exported environment variable works too:

```bash
export OPENAI_API_KEY="sk-..."   # Mac/Linux
# set OPENAI_API_KEY=sk-...      # Windows
```

## Code Files (Run in Order)

| File | What You'll Learn |
|------|-------------------|
| [hello_response.py](hello_response.py) | Your first Responses API call — a bare string input, then `instructions` plus a messages array |
| [first_agent.py](first_agent.py) | Your first agent with the Agents SDK — `Agent` + `Runner.run_sync()` |
| [customer_support.py](customer_support.py) | Full project: triage agent with handoffs, custom function tools, an input guardrail, hosted web search, and Pydantic structured output |

## Running the Code
```bash
python hello_response.py
python first_agent.py
python customer_support.py
```

## Notes
- Each file is self-contained — you can run them independently.
- Files build on each other conceptually, so run them in order for best learning.
- All three use the `gpt-5.5` model; change the `model=` argument to try others.
- `customer_support.py` is async (`asyncio.run(main())`) and runs four demo
  conversations, including one the guardrail blocks on purpose.
- Modify the code! Change instructions, add tools, experiment.
- Check your traces at: https://platform.openai.com → Dashboard → Traces

## Related folders
- [LangChain/](../LangChain/) — the same first-agent idea in LangChain
- [MCP/](../MCP/) — an agent that talks to an MCP tool server

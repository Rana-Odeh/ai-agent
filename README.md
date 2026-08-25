# AI Coding Agent (CLI)

A command-line AI agent that takes a natural-language coding task and autonomously works through a codebase to complete it — reading files, writing changes, and running code until the task is done.

## 🧠 What It Does

You give the agent a task in plain English, and it figures out how to complete it by calling a set of predefined functions:

- Scan the files in a directory
- Read a file's contents
- Overwrite a file's contents
- Execute the Python interpreter on a file

The agent loops through these actions — reasoning, calling functions, evaluating results — until the task is complete.

### Example

```bash
uv run main.py "fix my calculator app, it's not starting correctly"

# Calling function: get_files_info
# Calling function: get_file_content
# Calling function: write_file
# Calling function: run_python_file
# Calling function: write_file
# Calling function: run_python_file
# Final response:
# Great! The calculator app now seems to be working correctly. The output
# shows the expression and the result in a formatted way.
```

## 🛠️ Tech Stack

- **Python 3.10+**
- **OpenRouter API** — LLM access for reasoning and function selection
- **uv** — project and package management
- Function-calling / tool-use pattern for agent decision-making

## 📂 Project Structure

```
ai-agent/
├── functions/     # Predefined functions the agent can call
├── calculator/    # Sample buggy app used to demo/test the agent
├── main.py        # Entry point — accepts the task via CLI
├── call_function.py
├── config.py
├── prompts.py
└── test_*.py      # Unit tests for core functions
```

## ⚙️ How It Works

1. The user provides a task as a CLI argument
2. The agent sends the task + available function definitions to the LLM via OpenRouter
3. The LLM decides which function to call next based on the current state
4. The agent executes that function and feeds the result back to the LLM
5. This repeats until the LLM determines the task is complete and returns a final response

## 🚀 Getting Started

### Prerequisites
- Python 3.10+
- [uv](https://github.com/astral-sh/uv) package manager
- An OpenRouter API key
- Unix-like shell (bash/zsh)

### Setup

```bash
# Clone the repository
git clone https://github.com/Rana-Odeh/ai-agent.git
cd ai-agent

# Install dependencies
uv sync

# Add your OpenRouter API key to your environment / config
```

### Usage

```bash
uv run main.py "your coding task here"
```

## ✅ Testing

The project includes unit tests for the core agent functions:

```bash
uv run test_get_files_info.py
uv run test_get_file_content.py
uv run test_write_file.py
uv run test_run_python_file.py
```

## 💡 Why This Project

Built to understand how LLM-powered coding agents actually work under the hood — going beyond using AI tools to implementing the function-calling loop that drives them, using a pre-trained LLM rather than building one from scratch.

## 👩‍💻 Author

**Rana Odeh**
[GitHub](https://github.com/Rana-Odeh)

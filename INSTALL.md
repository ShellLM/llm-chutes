# Installation Guide for llm-chutes

## Prerequisites

1. Make sure you have Python 3.9+ installed
2. Install the LLM CLI tool if you haven't already:
   ```bash
   pip install llm
   ```

## Installation

### Option 1: Install from source (recommended for development)

1. Clone or download this repository
2. Navigate to the project directory
3. Install in development mode:
   ```bash
   pip install -e .
   ```

### Option 2: Install using pip (when published)

```bash
pip install llm-chutes
```

## Configuration

1. Get your API key from Chutes AI
2. Set it as an environment variable:
   ```bash
   export CHUTES_API_KEY="your-api-key-here"
   ```
   
   Or add it to your shell profile (`.bashrc`, `.zshrc`, etc.):
   ```bash
   echo 'export CHUTES_API_KEY="your-api-key-here"' >> ~/.zshrc
   source ~/.zshrc
   ```

   Alternatively, you can use the LLM keys system:
   ```bash
   llm keys set chutes
   ```

## Verification

1. Test the installation:
   ```bash
   python3 test_basic.py
   ```

2. List available models:
   ```bash
   llm chutes models
   ```

3. Try a simple prompt:
   ```bash
   llm -m chutes/deepseek-ai/DeepSeek-R1 "Hello, how are you?"
   ```

## Troubleshooting

### "No models found" error
- Make sure your `CHUTES_API_KEY` is set correctly
- Try refreshing models: `llm chutes refresh`
- Check your internet connection

### Plugin not recognized
- Make sure you installed in the same Python environment as LLM
- Try reinstalling: `pip uninstall llm-chutes && pip install -e .`

### API errors
- Verify your API key is valid
- Check if the Chutes AI service is accessible
- Try the test script: `python3 test_basic.py`

## Usage Examples

```bash
# List all models
llm chutes models

# List models in JSON format
llm chutes models --json

# Refresh model cache
llm chutes refresh

# Use a model with caching
llm -m chutes/deepseek-ai/DeepSeek-R1 -o cache 1 "Explain quantum computing"

# Set up an alias for easier use
llm aliases set deepseek chutes/deepseek-ai/DeepSeek-R1
llm -m deepseek "What is machine learning?"
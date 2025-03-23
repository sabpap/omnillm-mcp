# OmniLLM: Universal LLM Bridge for Claude

OmniLLM is an MCP server that allows Claude to query and integrate responses from other large language models (LLMs) like ChatGPT, Azure OpenAI, and Google Gemini, creating a unified access point for all your AI needs.

## Features

- Query OpenAI's ChatGPT models
- Query Azure OpenAI services
- Query Google's Gemini models
- Get responses from all LLMs for comparison
- Check which LLM services are configured and available

## Setup Instructions

### 1. Prerequisites

- Python 3.10+
- Claude Desktop application
- API keys for the LLMs you want to use

### 2. Installation

```bash
# Clone or download this repository
git clone https://github.com/yourusername/omnillm-mcp.git
cd omnillm-mcp

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install mcp[cli] httpx python-dotenv
```

### 3. Configuration

Create a `.env` file in the project root with your API keys:

```
OPENAI_API_KEY=your_openai_key_here
AZURE_OPENAI_API_KEY=your_azure_key_here
AZURE_OPENAI_ENDPOINT=your_azure_endpoint_here
GOOGLE_API_KEY=your_google_api_key_here
```

You only need to add the keys for the services you want to use.

### 4. Integrating with Claude Desktop

1. Open Claude Desktop
2. Navigate to Settings > Developer > Edit Config
3. Add the server to your `claude_desktop_config.json` file:

```json
{
  "mcpServers": {
    "omnillm": {
      "command": "python",
      "args": [
        "path/to/server.py"
      ],
      "env": {
        "PYTHONPATH": "path/to/omnillm-mcp"
      }
    }
  }
}
```

Replace "path/to/server.py" with the actual path to your server.py file.

4. Save the config file and restart Claude Desktop

## Usage Examples

Once connected to Claude Desktop, you can use phrases like:

- "What would be the top places to visit if you're looking for an adventurous hiking trip? Consult ChatGPT"
- "What's the best way to learn programming? Ask Gemini for their opinion."
- "Compare different frameworks for building web applications, and then get input from both ChatGPT and Azure OpenAI"

Claude will automatically detect when to use the Multi-LLM Proxy tools to enhance its responses.

## Available Tools

1. `query_chatgpt` - Query OpenAI's ChatGPT with a custom prompt
2. `query_azure_chatgpt` - Query Azure OpenAI's ChatGPT with a custom prompt
3. `query_gemini` - Query Google's Gemini with a custom prompt
4. `query_all_llms` - Query all available LLMs and get all responses together
5. `check_available_models` - Check which LLM APIs are properly configured

## Troubleshooting

- Check that your API keys are correctly set in the `.env` file
- Ensure Claude Desktop is properly configured with the server path
- Verify that all dependencies are installed in your virtual environment
- Check Claude's logs for any connection or execution errors

## License

[MIT License](LICENSE)


# OSINT Assistant

An AI-enhanced OSINT (Open Source Intelligence) tool for gathering, analyzing, and reporting on information from various web sources. This tool leverages the power of Perplexity AI to provide deeper insights and more accurate analysis.

This project includes both a command-line interface and a full-featured web application for easier interaction.

## Features

- 🔍 **Web Search:** Collect information from multiple sources based on specific queries
- 🧠 **AI-Powered Analysis:** Use Perplexity AI for enhanced content analysis
- 📊 **Entity Recognition:** Identify key people, organizations, and concepts from collected data
- 🔗 **Connection Analysis:** Map relationships between identified entities
- 📈 **Pattern Recognition:** Identify trends and patterns in the collected data
- 📝 **Comprehensive Reporting:** Generate structured reports with visualizations and actionable insights
- 📤 **Data Export:** Save results in JSON format with proper serialization using Pydantic

## Installation

### Prerequisites

- Python 3.11+
- pip package manager
- Node.js 14+ and npm (for web application)

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/AXRoux/OSINT-Assistant.git
   cd OSINT-Assistant
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Set up your environment variables:
   ```bash
   cp .env.example .env
   ```
   
4. Edit the `.env` file and add your Perplexity API key:
   ```
   PERPLEXITY_API_KEY=your_api_key_here
   ```

## Usage

### Command Line Interface

Run a search query:
```bash
python osint_assistant.py --query "quantum computing advances"
```

### Web Application

Start the web application:

#### Linux/Mac
```bash
bash run.sh
```
or make it executable first:
```bash
chmod +x run.sh
./run.sh
```

#### Windows
```
run_windows.bat
```

The web application will automatically:
1. Install required dependencies
2. Set up the environment file if not present
3. Build the React frontend if needed
4. Start the Flask server

On Windows, the script will automatically open your browser to http://localhost:5000.
On Linux/Mac, you'll need to open your browser and navigate to http://localhost:5000 manually.

### Advanced Options

Save the results to a file:
```bash
python osint_assistant.py --query "quantum computing advances" --save
```

Specify the number of results to collect:
```bash
python osint_assistant.py --query "quantum computing advances" --results 15
```

Output results as JSON:
```bash
python osint_assistant.py --query "quantum computing advances" --json
```

Override the API key from environment file:
```bash
python osint_assistant.py --query "quantum computing advances" --api-key "your-api-key"
```

### Command Line Arguments

| Argument | Short | Description |
|----------|-------|-------------|
| `--query` | `-q` | The search query to investigate |
| `--results` | `-r` | Number of results to collect (default: 10) |
| `--save` | `-s` | Save the collected data to a file |
| `--api-key` | `-k` | Perplexity API key (overrides .env file) |
| `--json` | `-j` | Output results as JSON |

## API Key Setup

This tool uses the Perplexity AI API for enhanced intelligence gathering and analysis. To use this feature:

1. Sign up for an account at [Perplexity AI](https://www.perplexity.ai/)
2. Navigate to the API section to generate an API key
3. Add the key to your `.env` file or use the `--api-key` command line argument

Note: The tool will still function without an API key, but will fall back to simulated data rather than real AI-powered analysis.

## Data Models

The tool uses Pydantic models for data validation and serialization:

- `SearchResult`: Represents a single search result with title, URL, snippet, etc.
- `ContentAnalysis`: Contains analysis of a specific URL including credibility, entities, and sentiment
- `OSINTReport`: The complete report with all collected data and analyses

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines

When contributing to this project, please:

1. Ensure code follows PEP 8 style guide for Python code
2. Write unit tests for new features
3. Update documentation as needed
4. Make sure not to commit any API keys or sensitive information
5. Verify that all tests pass before submitting a PR

## Troubleshooting

### Windows Users

#### "No module named 'dotenv'" Error
If you encounter this error when running the application:
```
ModuleNotFoundError: No module named 'dotenv'
```

There are several ways to fix this issue:

1. **Run the diagnostic script** (most comprehensive):
   ```
   fix_windows_dotenv.bat
   ```
   This script will:
   - Diagnose your Python environment
   - Try multiple installation methods
   - Provide detailed troubleshooting guidance

2. **Use the included standalone module**:
   No installation required - we've included a standalone `dotenv.py` file directly in the project folder. This will work even if pip fails.

3. **Manual installation methods**:
   ```
   pip install python-dotenv
   ```
   or
   ```
   python -m pip install python-dotenv
   ```
   or
   ```
   pip install --user python-dotenv
   ```

4. **Administrator privileges**:
   Run Command Prompt as Administrator, then try:
   ```
   pip install python-dotenv
   ```

5. **Multiple Python installations**:
   If you have multiple Python versions, specify the version:
   ```
   py -3.9 -m pip install python-dotenv
   ```

#### Browser Not Opening Automatically
When running the application directly with `python osint_web_app.py`, the browser may not open automatically. Use `run_windows.bat` instead to automatically open the browser with the application.

### Linux/Mac Users

#### "No module named 'dotenv'" or "module 'dotenv' has no attribute" Errors
If you encounter either of these errors when running the application:
```
ModuleNotFoundError: No module named 'dotenv'
```
or
```
AttributeError: module 'dotenv' has no attribute 'dotenv_values'
```

There are several ways to fix this issue:

1. **Run the diagnostic script** (recommended):
   ```bash
   ./fix_linux_dotenv.sh
   ```
   or if it's not executable:
   ```bash
   bash fix_linux_dotenv.sh
   ```
   This script will:
   - Diagnose your Python environment
   - Try multiple installation methods
   - Check if the installed module has all required functions
   - Provide Linux-specific troubleshooting guidance

2. **Use the included standalone module**:
   No installation required - we've included a standalone `dotenv.py` file directly in the project folder that implements all necessary functions including `dotenv_values`.

3. **Manual installation methods**:
   ```bash
   pip install python-dotenv
   ```
   or
   ```bash
   pip3 install python-dotenv
   ```
   or
   ```bash
   sudo pip install python-dotenv
   ```

For general dependency issues, you can also run:
```bash
pip install -r requirements.txt
```

## Security Notes

⚠️ **IMPORTANT**: This tool requires API keys to function properly.

- Never commit your `.env` file with real API keys to GitHub
- Always use the `.env.example` file as a template
- Consider using GitHub Secrets for CI/CD workflows if adding automation

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Disclaimer

This tool is for educational and research purposes only. Always ensure you comply with relevant laws and regulations when conducting OSINT research. The authors are not responsible for any misuse of this tool.

# Backend Application Documentation

## Overview

The backend of this application is built using [Quart](https://quart.palletsprojects.com/), a Python framework for asynchronous web applications. It handles the core logic and API endpoints for the chat and ask functionalities.

## Folder Structure

- `approaches/`: Contains different Retrieval Augmented Generation (RAG) approaches used by the Chat and Ask tabs.
- `models/`: Contains the data models used in the application.
- `services/`: Contains services for interacting with external APIs and databases.
- `utils/`: Contains utility functions and helpers.
- `main.py`: The entry point for the backend application.

## Setup

### Prerequisites

- Python 3.8 or higher
- [Quart](https://quart.palletsprojects.com/)
- [Azure CLI](https://learn.microsoft.com/cli/azure/install-azure-cli)

### Installation

1. Clone the repository:

    ```sh
    git clone https://github.com/your-repo/azure-search-openai-demo.git
    cd azure-search-openai-demo/app/backend
    ```

2. Create a virtual environment and activate it:

    ```sh
    python -m venv venv
    source venv/bin/activate  # On Windows use `venv\Scripts\activate`
    ```

3. Install the required dependencies:

    ```sh
    pip install -r requirements.txt
    ```

### Running the Application

1. Ensure you have successfully run the `azd up` command as described in the main [README](../../README.md).

2. Start the backend server:

    ```sh
    quart run
    ```

    The backend server will start on `http://127.0.0.1:5000`.

## Approaches

### Chat Approach

The chat tab uses the approach programmed in `chatreadretrieveread.py`.

1. Calls the OpenAI ChatCompletion API to turn the user question into a search query.
2. Queries Azure AI Search for search results.
3. Combines the search results and original user question, and calls the OpenAI ChatCompletion API to answer the question based on the sources.

### Ask Approach

The ask tab uses the approach programmed in `retrievethenread.py`.

1. Queries Azure AI Search for search results for the user question.
2. Combines the search results and user question, and calls the OpenAI ChatCompletion API to answer the question based on the sources.

## Customization

### Customizing the Backend

The backend code is stored in the [`app/backend`](command:_github.copilot.openRelativePath?%5B%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2FC%3A%2FUsers%2Fazureuser%2FGitHub%20Copilot%2Fazure-search-openai-demo%2Fapp%2Fbackend%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%2C%22e61175b8-7f6d-475a-8297-e363775d7b60%22%5D "c:\Users\azureuser\GitHub Copilot\azure-search-openai-demo\app\backend") folder. The primary backend code you'll want to customize is in the [`approaches`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2Fc%3A%2FUsers%2Fazureuser%2FGitHub%20Copilot%2Fazure-search-openai-demo%2Fdocs%2Fcustomization.md%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%2C%22pos%22%3A%7B%22line%22%3A27%2C%22character%22%3A81%7D%7D%2C%7B%22uri%22%3A%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2Fc%3A%2FUsers%2Fazureuser%2FGitHub%20Copilot%2Fazure-search-openai-demo%2Fdocs%2Fcustomization.md%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%2C%22pos%22%3A%7B%22line%22%3A49%2C%22character%22%3A146%7D%7D%5D%2C%22e61175b8-7f6d-475a-8297-e363775d7b60%22%5D "Go to definition") folder, which contains the classes powering the Chat and Ask tabs. Each class uses a different RAG approach, which includes system messages that should be changed to match your data.

### Adding New Services

To add new services, create a new file in the [`services`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2Fc%3A%2FUsers%2Fazureuser%2FGitHub%20Copilot%2Fazure-search-openai-demo%2Fdocs%2Fcustomization.md%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%2C%22pos%22%3A%7B%22line%22%3A44%2C%22character%22%3A162%7D%7D%2C%7B%22uri%22%3A%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2Fc%3A%2FUsers%2Fazureuser%2FGitHub%20Copilot%2Fazure-search-openai-demo%2Fdocs%2Fdeploy_lowcost.md%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%2C%22pos%22%3A%7B%22line%22%3A2%2C%22character%22%3A312%7D%7D%2C%7B%22uri%22%3A%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2Fc%3A%2FUsers%2Fazureuser%2FGitHub%20Copilot%2Fazure-search-openai-demo%2FREADME.md%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%2C%22pos%22%3A%7B%22line%22%3A259%2C%22character%22%3A367%7D%7D%5D%2C%22e61175b8-7f6d-475a-8297-e363775d7b60%22%5D "Go to definition") folder and implement the necessary logic. Then, import and use the service in your approach or main application logic.

## Environment Variables

The backend uses environment variables for configuration. These variables are set in the [`.env`](command:_github.copilot.openSymbolFromReferences?%5B%22%22%2C%5B%7B%22uri%22%3A%7B%22scheme%22%3A%22file%22%2C%22authority%22%3A%22%22%2C%22path%22%3A%22%2Fc%3A%2FUsers%2Fazureuser%2FGitHub%20Copilot%2Fazure-search-openai-demo%2FREADME.md%22%2C%22query%22%3A%22%22%2C%22fragment%22%3A%22%22%7D%2C%22pos%22%3A%7B%22line%22%3A183%2C%22character%22%3A148%7D%7D%5D%2C%22e61175b8-7f6d-475a-8297-e363775d7b60%22%5D "Go to definition") file in your Azure environment folder.

- `AZURE_OPENAI_API_KEY`: Your Azure OpenAI API key.
- `AZURE_SEARCH_SERVICE_NAME`: The name of your Azure Search service.
- `AZURE_SEARCH_INDEX_NAME`: The name of your Azure Search index.

## Troubleshooting

### Common Issues

1. **Authentication Errors**: Ensure your Azure credentials are correctly set up and you have the necessary permissions.
2. **API Rate Limits**: Be mindful of the rate limits for the OpenAI and Azure Search APIs.
3. **Dependency Issues**: Ensure all dependencies are installed correctly by running `pip install -r requirements.txt`.

For more detailed troubleshooting, refer to the main README and the [troubleshooting guide](../../docs/troubleshooting.md).

## Contributing

We welcome contributions! Please see the CONTRIBUTING.md for more details.

## License

This project is licensed under the MIT License. See the LICENSE file for more details.

# This script reads a requirements file and prints each requirement.
# 
# The requirements file should be named 'requirements.txt' and located in the same directory as this script.
# Each line in the 'requirements.txt' file should contain a single requirement.
# 
# Usage:
# 1. Ensure you have a 'requirements.txt' file in the same directory as this script.
# 2. Run the script to print out each requirement listed in the 'requirements.txt' file.
# 
# Example 'requirements.txt' file:
# ```
# numpy==1.21.0
# pandas==1.3.0
# requests==2.25.1
# ```
# 
# The script will output:
# ```
# numpy==1.21.0
# pandas==1.3.0
# requests==2.25.1
# ```
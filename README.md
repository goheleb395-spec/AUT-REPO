# UI and API Automation Tests

Python automation tests for Trello UI workflows and API operations. The current test suite uses Selenium for browser automation, Requests for API calls, and pytest for execution and HTML reporting.

## Project Structure

- `selenium_python/api/`: Trello API client
- `selenium_python/config/`: Configuration and environment-based credentials
- `selenium_python/core/`: WebDriver and wait helpers
- `selenium_python/pages/`: Page Object Model classes
- `selenium_python/tests/`: UI and API test cases
- `selenium_python/test_data/`: Test data
- `playwright_python/`: Reserved for Playwright tests
- `reports/`: Generated pytest HTML reports
- `screenshots/`: Screenshots captured for failed UI tests
- `logs/`: Test execution logs

## Prerequisites

- Python 3.13 or newer
- Google Chrome
- A Trello account and API credentials for the configured tests

## Setup

1. Create and activate a virtual environment:

   ```powershell
   python -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

2. Install the test dependencies:

   ```powershell
   pip install pytest pytest-html selenium requests python-dotenv
   ```

3. Review `selenium_python/config/config.ini` and adjust the application URL, API URL, or timeout if needed.

4. Create a `.env` file in the repository root with the credentials expected by the test suite:

   ```dotenv
   TRELLO_USERNAME=your-trello-username
   TRELLO_PASSWORD=your-trello-password
   TRELLO_API_KEY=your-trello-api-key
   TRELLO_TOKEN=your-trello-token
   ```

   Keep this file local and never commit real credentials.

The API tests create and delete temporary Trello boards. Use a test account when possible.

## Run Tests

Run the full suite from the repository root:

```powershell
pytest
```

Run only the Selenium tests:

```powershell
pytest selenium_python/tests
```

Run a specific test file:

```powershell
pytest selenium_python/tests/test_login.py
```

Run the board workflow only:

```powershell
pytest selenium_python/tests/test_board.py
```

The configured pytest options create a self-contained HTML report at `reports/report.html`. Failed UI tests save screenshots under `screenshots/`. Both locations, along with `logs/`, are local generated output and are excluded from Git.


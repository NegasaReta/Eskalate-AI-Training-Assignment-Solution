# AI Experts Assignment 3 Solution

This repository contains my completed solution for the Python AI Experts Assignment.

## Overview of Changes
- **Bug Fix:** Identified and fixed a bug in `app/http_client.py` where the API request failed to refresh standard tokens properly when non-OAuth2Token objects were present. Details can be found in `EXPLANATION.md`.
- **Dependency Management:** Completely pinned all required dependencies and sub-dependencies in `requirements.txt` to ensure perfectly reproducible builds across environments.
- **Dockerization:** Created a minimal `Dockerfile` designed to execute the test suite reliably in a CI-style, non-interactive environment.

## Running the Tests

You can run the full test suite either directly on your local machine or fully isolated inside a Docker container.

### Local Environment execution

To run the app directly, you should first ensure you have Python 3.11+ installed. I highly recommend running this within an isolated virtual environment.

1. Create and activate a Virtual Environment (Optional, but recommended)
   ```bash
   # Windows
   python -m venv venv
   .\venv\Scripts\activate
   
   # Linux/Mac
   python3 -m venv venv
   source venv/bin/activate
   ```
2. Install the necessary dependencies cleanly:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the automated Pytest suite:
   ```bash
   pytest -v
   ```

### Running with Docker

You do not need Python or a virtual environment installed natively if you choose to run the tests in Docker. It will automatically build an isolated image with the required dependencies and run the tests.

1. Build the Docker image locally (this will also install dependencies automatically):
   ```bash
   docker build -t app-tests .
   ```
2. Run the newly created image container:
   ```bash
   docker run --rm app-tests
   ```

*(Note: using `--rm` ensures the container automatically cleans up after finishing the test suite)*

# python-app

A simple Flask application.

## Run locally

1. Create and activate a virtual environment:

   ```powershell
   py -m venv .venv
   .\.venv\Scripts\Activate.ps1
   ```

2. Install dependencies:

   ```powershell
   pip install -r requirements.txt
   ```

3. Run the tests:

   ```powershell
   py -m unittest discover -s tests
   ```

4. Start the production WSGI server:

   ```powershell
   py serve.py
   ```

   Open <http://127.0.0.1:8080/>. The server binds to `0.0.0.0` and uses
   the `PORT` environment variable when provided (default: `8080`), as expected
   by most deployment platforms. Set the deployment start command to
   `python serve.py`.

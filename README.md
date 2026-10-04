# python-app

A responsive HarshalTechOps landing page built with Flask, semantic HTML, and
custom CSS. The interface has no JavaScript or frontend build step.

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

4. Start the app:

   ```powershell
   py app.py
   ```

   The default port is `5000`; set `PORT` to override it. On Windows this uses
   Flask's development server because Gunicorn does not support Windows. On
   Linux and other supported systems, the same command starts Gunicorn. Open
   <http://127.0.0.1:5000/> locally. The equivalent production command is:

   ```sh
   gunicorn --bind "0.0.0.0:${PORT:-5000}" app:app
   ```

   Set the deployment start command to `python app.py` or use the explicit
   Gunicorn command above.

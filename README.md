# Deploy to PythonAnywhere

A custom GitHub Action to deploy FastAPI app file to PythonAnywhere and
reload the web.


## Usage

To use this action, create a workflow (e.g.,
`.github/workflows/deploy.yml`) in your GitHub repository.

### Example Workflow

```yaml
name: Deploy to PythonAnywhere

on:
  push:
    branches:
      - master

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Deploy to PythonAnywhere
        uses: caseneuve/padeploy@v0.1
        with:
          python-version: '3.10'
          pa-api-key: ${{ secrets.PYTHONANYWHERE_API_KEY }}
          pa-user: ${{ secrets.PYTHONANYWHERE_USER }}
          pa-domain: ${{ secrets.PYTHONANYWHERE_DOMAIN }}
          pa-path: '/home/{{ secrets.PYTHONANYWHERE_USER }}/mysite'
          app: 'src/fastapi_app.py'
```


## TODOs

- [ ] change `app` into `src` and add a script to get all pathes in the
      source dir
- [ ] add smarter deployment trigger (tags? release?)

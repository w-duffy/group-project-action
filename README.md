# Flask Migrations and Seeds GitHub Action

This GitHub Action automates the process of setting up Python, installing dependencies, and running Flask migrations and seed operations on a PostgreSQL database. It's tailored for the Python Group Project to ensure you're database is compatible with your Render.com's PostgreSQL service

## What This Action Does

- Checks out your repository's code.
- Sets up Python 3.11.
- Caches and installs Python dependencies from `requirements.txt`.
- Installs `psycopg2`.
- Starts a PostgreSQL service.
- Runs Flask database migrations and seed operations.

## Usage

To use this action in your workflow, add the following step to your `.github/workflows/database-ci.yml`:

```yaml
jobs:
  build-and-test:
    runs-on: ubuntu-latest
    steps:
    - uses: w-duffy/group-project-action@v1.0.0
```

This action is designed to work with minimal configuration and does not require any inputs.

## Example Workflow

Here's a complete example of a workflow file using this action:

```yaml
name: Example Flask CI

on:
  push:
    branches: ['main']
  pull_request:
    types: [opened, synchronize]
    branches: ['main']

jobs:
  build-and-test:
    runs-on: ubuntu-latest
    steps:
    - uses: w-duffy/group-project-action@v1.0.0
```

## Additional Information

- This action uses the official Python action (`actions/setup-python@v4`) and the official GitHub Cache action (`actions/cache@v3`) to set up Python and cache dependencies.
- The PostgreSQL service is set up with default dummy values for username, password, and database name (`username`, `password`, `dbname`). These are defined within the action and cannot be modified.

## Contributing

If you have suggestions for how this action could be improved, or want to report a bug, please open an issue or submit a pull request.


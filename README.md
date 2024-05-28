# pkl-lang-cli-action

## Overview

`pkl-lang-cli-action` is a GitHub Action created by Draftea that sets up the `pkl-lang` CLI tool, enabling you to interact with it within your workflows.

## Features

- **Easy Setup**: Automatically download and set up the specified version of the `pkl-lang` CLI.
- **Customizable**: Specify the `pkl-lang` version and command arguments to suit your needs.

## Usage

### Inputs

The action accepts the following inputs:

| Name    | Description                         | Default      |
|---------|-------------------------------------|--------------|
| version | Desired `pkl-lang` version.         | `"0.25.3"`   |
| args    | `pkl` command arguments to execute. | `"--version"`|

### Example Workflow

```yaml
name: Setup PKL CLI

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Setup PKL CLI
        uses: draftea/pkl-lang-cli-action@main
        with:
          version: '0.25.3'  # Specify the desired version here
          args: '--help'    # Specify the command arguments here

      - name: Run PKL command
        run: echo "PKL command executed"
```

## How It Works

The action performs the following steps:

1. **Setup PKL CLI**:
   - Downloads the specified version of the `pkl-lang` CLI from GitHub releases.
   - Grants execution permissions to the downloaded binary.
   - Verifies the installation by running `./pkl --version`.

2. **Execute Command**:
   - Executes the specified `pkl` command with the provided arguments.

## Author

Created by [Draftea](https://github.com/Drafteame).

# act


## Example one
```
cat example.yml

name: Workflow with Inputs

on:
  workflow_dispatch:
    inputs:
      run_this:
        description: "Run this job?"
        required: true
        default: "no"

jobs:
  conditional-job:
    if: inputs.run_this == 'yes'
    runs-on: ubuntu-latest
    steps:
      - run: echo "✅ You chose to run this job!"


cat input-event.json
{
  "workflow_dispatch": {
    "inputs": {
      "run_this": "yes"
    }
  }
}

## Command to execute.
act workflow_dispatch -j conditional-job -e input-event.json

```

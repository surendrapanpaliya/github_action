name: Python Test

# Controls when the action will run. This action runs on every push to the "main" branch.
on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

# Job definition
jobs:
  test:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v3

    - name: Set up Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.8'

    - name: Install dependencies
      run: |
        python -m pip install --upgrade pip
        pip install -r requirements.txt

    - name: Run tests
      run: |
        pytest

Explanation:
•	name: Python Test: The name of the workflow.
•	on: push: Specifies when the workflow should run. In this case, it runs on any push to the main branch or any pull request targeting the main branch.
•	jobs:: Defines a job. Here, we have one job called test, which runs on an Ubuntu runner (ubuntu-latest).
•	actions/checkout@v3: Checks out the repository code.
•	actions/setup-python@v4: Sets up Python on the runner. In this case, Python 3.8 is specified.
•	pip install: Installs any required dependencies from requirements.txt.
•	pytest: Runs the Python tests using PyTest.
•	
3.	Commit the Workflow:
o	After defining the workflow, commit it directly to the repository. GitHub will automatically recognize it and run it on the next push to the repository.
![image](https://github.com/user-attachments/assets/d82e13ad-baff-4520-95d0-320a90d22fbd)

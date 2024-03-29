

---

# CI/CD Pipeline with GitHub Actions and Secrets

## Goal:

Building on GitHub Actions, you will now learn how to handle Secrets in GitHub. This allows you to protect sensitive data from others.

## Steps:

### Step 1: Create a Simple Node.js Project

Create a simple Node.js project with an HTML file and a JavaScript file containing a basic function, such as adding two numbers.

### Step 2: Set Up Git and Push to GitHub

```bash
# Initialize a Git repository
git init

# Add all files to the repository
git add .

# Create the initial commit
git commit -m "Initial commit"

# Create a new GitHub repository and set the remote URL
# Replace "<username>" and "<reponame>" with your GitHub username and repository name
git remote add origin https://github.com/<username>/<reponame>.git

# Push the code to GitHub
git push -u origin main
```

### Step 3: Create GitHub Secrets

Go to your GitHub repository -> Settings -> Secrets and create a secret named `SECRET_API_KEY` with its corresponding value (e.g., an API key or password).

### Step 4: Create GitHub Actions Pipeline

Create a file named `.github/workflows/main.yml` with the following content:

```yaml
name: CI/CD Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Repository
      uses: actions/checkout@v2

    - name: Setup Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '14'

    - name: Install Dependencies
      run: npm install

    - name: Run Tests
      run: npm test

    - name: Use Secrets
      run: |
        echo "SECRET_API_KEY=$SECRET_API_KEY" >> $GITHUB_ENV
```

### Step 5: Push Changes and Monitor the Pipeline

Run the following Git commands:

```bash
# Add changes to the repository
git add .

# Create a commit
git commit -m "Added GitHub Actions Pipeline and Secrets"

# Push the code back to GitHub
git push origin main
```

Go to your GitHub repository and monitor the progress of the pipeline in the GitHub Actions section. Ensure that the pipeline was executed successfully and verify that the Secrets are being used correctly in the pipeline.



# Daily GitHub Commit Bot 🤖

An automated JavaScript program that creates daily commits to maintain your GitHub activity streak.

## Features
- Generates random daily activity content
- Creates meaningful commit messages
- Automatically pushes to GitHub (if remote is set up)
- Handles git repository initialization
- Safe and lightweight

## Setup Instructions

### 1. Upload to GitHub
1. Go to [GitHub.com](https://github.com) and sign in
2. Click the "+" icon in the top-right corner
3. Select "New repository"
4. Name it something like "daily-commits" or "activity-tracker"
5. Make it **Public** (for GitHub activity to show)
6. Click "Create repository"

### 2. Connect Your Local Repository
```bash
# Navigate to your project folder
cd "C:\Users\Rahul\OneDrive\Desktop\PROJECTS\todo"

# Initialize git (if not already done)
git init

# Add your GitHub repository as origin
git remote add origin https://github.com/Ashiish-Agarwal/auto-commit.git
#if you got some error look like this : remote origin already exists.
#use this 
git remote set-url origin https://github.com/Ashiish-Agarwal/auto-commit.git

# Set up your git credentials (if not already done)
git config user.name "Your Name"
git config user.email "your.email@example.com"

push-cmd: git push -u origin main
```

### 3. Test the Script
```bash
# Run the script once to test
node daily-commit.js

# Or use npm script
npm run commit
```

## Usage

### Manual Run
```bash
node daily-commit.js
```

### Automated Daily Runs

#### Option 1: Windows Task Scheduler
1. Open Task Scheduler (search "Task Scheduler" in Windows)
2. Click "Create Basic Task"
3. Name: "Daily GitHub Commit"
4. Trigger: Daily
5. Action: Start a program
6. Program: `node`
7. Arguments: `daily-commit.js`
8. Start in: `C:\Users\Rahul\OneDrive\Desktop\PROJECTS\todo`

#### Option 2: GitHub Actions (Recommended)
Create `.github/workflows/daily-commit.yml` in your repository:

```yaml
name: Daily Commit
on:
  schedule:
    - cron: '0 12 * * *'  # Daily at 12 PM UTC
  workflow_dispatch:

jobs:
  commit:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Setup Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '16'
      - name: Make daily commit
        run: node daily-commit.js
```

## What It Does
1. Creates a `daily-activity.txt` file with random content
2. Commits it with a random message
3. Pushes to your GitHub repository
4. Maintains your GitHub activity streak

## Files Created
- `daily-activity.txt` - Contains random daily activity logs
- Commit history with various meaningful messages

## Security Notes
- No sensitive data is committed
- Only creates text files with random activity logs
- Safe to run automatically

## Troubleshooting

**"Not in a git repository"**: The script will initialize git automatically.

**"Could not push to remote"**: Make sure you've set up the remote repository:
```bash
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
```

**Authentication issues**: Set up Git credentials or use SSH keys for seamless pushing.

## License
MIT License - Feel free to modify and use as needed!

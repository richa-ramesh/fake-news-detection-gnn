# GitHub Repository Setup Instructions

Follow these steps to create your GitHub repository and push your code.

## Step 1: Create a GitHub Account

If you don't have one already:
1. Go to https://github.com
2. Click "Sign up"
3. Follow the registration process

## Step 2: Create a New Repository

1. Log in to GitHub
2. Click the "+" icon in the top-right corner
3. Select "New repository"
4. Fill in the details:
   - **Repository name**: `fake-news-detection-gnn` (or your preferred name)
   - **Description**: "Fake News Detection using Graph Neural Networks"
   - **Visibility**: Choose Public or Private
   - **DO NOT** initialize with README, .gitignore, or license (we already have these)
5. Click "Create repository"

## Step 3: Install Git (if not already installed)

**On Ubuntu/Debian:**
```bash
sudo apt-get update
sudo apt-get install git
```

**On Mac:**
```bash
brew install git
```

**On Windows:**
Download from https://git-scm.com/download/win

## Step 4: Configure Git (First Time Only)

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

## Step 5: Organize Your Files

Create a project folder and organize files like this:

```
fake-news-detection-gnn/
├── TEAM_44.ipynb
├── README.md
├── requirements.txt
├── .gitignore
├── LICENSE
├── CONTRIBUTING.md
└── SETUP.md
```

## Step 6: Initialize Git and Push to GitHub

Open terminal/command prompt in your project folder and run:

```bash
# Initialize git repository
git init

# Add all files
git add .

# Commit the files
git commit -m "Initial commit: Add fake news detection GNN project"

# Add your GitHub repository as remote
# Replace YOUR_USERNAME with your actual GitHub username
git remote add origin https://github.com/YOUR_USERNAME/fake-news-detection-gnn.git

# Push to GitHub
git branch -M main
git push -u origin main
```

## Step 7: Verify on GitHub

1. Go to your repository URL: `https://github.com/YOUR_USERNAME/fake-news-detection-gnn`
2. Verify all files are there
3. Check that the README displays correctly

## Step 8: Add Team Members as Collaborators (Optional)

If you want your team members to contribute:

1. Go to your repository on GitHub
2. Click "Settings"
3. Click "Collaborators" in the left sidebar
4. Click "Add people"
5. Enter their GitHub usernames
6. They'll receive an invitation to collaborate

## Common Git Commands for Future Updates

```bash
# Check status of files
git status

# Add specific file
git add filename.ext

# Add all changed files
git add .

# Commit changes
git commit -m "Describe your changes"

# Push to GitHub
git push

# Pull latest changes from GitHub
git pull

# Create a new branch
git checkout -b feature-name

# Switch between branches
git checkout branch-name

# View commit history
git log
```

## Troubleshooting

### Authentication Error

If you get authentication errors:
1. GitHub no longer supports password authentication
2. Use Personal Access Token (PAT):
   - Go to GitHub Settings → Developer settings → Personal access tokens
   - Generate new token with 'repo' scope
   - Use this token as your password when pushing

Or set up SSH keys:
- Follow: https://docs.github.com/en/authentication/connecting-to-github-with-ssh

### Permission Denied

Make sure you're using the correct repository URL and you have write access.

### File Too Large

If your notebook or data files are too large:
1. Add them to `.gitignore`
2. Use Git LFS for large files: https://git-lfs.github.com/

## Best Practices

1. **Commit often** with meaningful messages
2. **Pull before push** to avoid conflicts
3. **Don't commit** large data files or model checkpoints
4. **Use branches** for new features
5. **Write good commit messages** (what and why, not how)

## Resources

- [GitHub Docs](https://docs.github.com)
- [Git Handbook](https://guides.github.com/introduction/git-handbook/)
- [Git Cheat Sheet](https://education.github.com/git-cheat-sheet-education.pdf)

---

Need help? Ask your team members or check GitHub's excellent documentation!

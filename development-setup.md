# 🔧 Development Environment Setup

## Table of Contents
- [Mac Setup](#mac-setup)
- [WSL2 Setup](#wsl2-setup)
- [Essential Development Tools](#essential-development-tools)
- [Environment Verification](#environment-verification)

---

## Mac Setup

### Installing Xcode Command Line Tools

Before we begin, Mac users need to install the Xcode Command Line Tools, which include essential development tools like Git.

```bash
xcode-select --install
```

This command will open a dialog asking you to install the tools. Click "Install" and wait for the process to complete.

### Installing Homebrew

Homebrew is a package manager that makes installing development tools much easier on Mac.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

After installation, add Homebrew to your PATH:

```bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zshrc
source ~/.zshrc
```

### Verify Homebrew Installation

```bash
brew --version
brew doctor
```

## WSL2 Setup

### Installing WSL2 on Windows

1. **Open PowerShell as Administrator** and run:
```powershell
wsl --install
```

2. **Restart your computer** when prompted

3. **Open Microsoft Store** and install "Ubuntu" (latest LTS version)

4. **Launch Ubuntu** and create your user account

### Updating WSL2 Ubuntu

Once Ubuntu is running, update the system packages:

```bash
sudo apt update && sudo apt upgrade -y
```

### Installing Essential Build Tools

```bash
sudo apt install -y build-essential curl file git
```

## Essential Development Tools

### Code Editor: Visual Studio Code

**Mac:**
```bash
brew install --cask visual-studio-code
```

**WSL2:**
1. Download VS Code from [code.visualstudio.com](https://code.visualstudio.com/)
2. Install the "Remote - WSL" extension
3. Open WSL2 projects with `code .` from Ubuntu terminal

#### Essential VS Code Extensions

Install these extensions for web development:

```bash
# Open VS Code and install extensions via command palette (Cmd/Ctrl + Shift + P)
# Type: "Extensions: Install Extensions" and search for:
```

- **Live Server** - Launch development server with live reload
- **Prettier** - Code formatter
- **Bracket Pair Colorizer** - Color matching brackets
- **Auto Rename Tag** - Automatically rename paired HTML tags
- **GitLens** - Enhanced Git capabilities
- **Remote - WSL** (WSL2 users only)

### Node.js and npm

**Mac:**
```bash
# Install Node.js via Homebrew
brew install node

# Verify installation
node --version
npm --version
```

**WSL2:**
```bash
# Install Node.js via NodeSource repository
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt-get install -y nodejs

# Verify installation
node --version
npm --version
```

### Terminal Enhancement

**Mac (Optional - iTerm2):**
```bash
brew install --cask iterm2
```

**WSL2 (Optional - Windows Terminal):**
Install from Microsoft Store: "Windows Terminal"

#### Customizing Your Terminal

**Install Oh My Zsh (Mac):**
```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

**Install Oh My Zsh (WSL2):**
```bash
sudo apt install zsh -y
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
chsh -s $(which zsh)
```

### Web Browsers for Development

Install multiple browsers for cross-browser testing:

**Mac:**
```bash
brew install --cask google-chrome
brew install --cask firefox
brew install --cask microsoft-edge
```

**WSL2:**
- Install browsers on Windows host
- Use Windows browsers with WSL2 development server

## Environment Verification

### Create a Test Project

Let's verify everything is working by creating a simple test project:

```bash
# Create project directory
mkdir web-dev-test
cd web-dev-test

# Initialize Git repository
git init

# Create basic HTML file
cat > index.html << 'EOF'
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Dev Environment Test</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            text-align: center;
        }
        .container {
            background: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            padding: 40px;
            margin: 50px 0;
        }
        .checkmark {
            color: #4CAF50;
            font-size: 2em;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🎉 Development Environment Setup Complete!</h1>
        <p class="checkmark">✓ HTML is working</p>
        <p class="checkmark">✓ CSS is working</p>
        <p class="checkmark">✓ VS Code is working</p>
        <p class="checkmark">✓ Git is working</p>
        <p>You're ready to start web development!</p>
    </div>
    
    <script>
        console.log('✓ JavaScript is working!');
        document.addEventListener('DOMContentLoaded', function() {
            document.body.style.animation = 'fadeIn 1s ease-in';
        });
    </script>
    
    <style>
        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }
    </style>
</body>
</html>
EOF

# Create initial commit
git add .
git commit -m "Initial commit: Add environment test page"

# Open in VS Code
code .
```

### Test Your Setup

1. **Open the project in VS Code:**
   ```bash
   code .
   ```

2. **Install Live Server extension** (if not already installed)

3. **Right-click on `index.html`** and select "Open with Live Server"

4. **Your browser should open** showing a colorful test page

5. **Open Developer Tools** (F12) and check the Console tab for the JavaScript message

### Verification Checklist

- [ ] VS Code opens the project
- [ ] Live Server launches the webpage
- [ ] CSS styling is visible
- [ ] JavaScript console message appears
- [ ] Git commands work without errors
- [ ] Terminal/command line is functional

## Troubleshooting Common Issues

### Mac Issues

**"xcode-select: error: command line tools are already installed"**
- This is normal if you already had them installed

**Homebrew permission issues:**
```bash
sudo chown -R $(whoami) /opt/homebrew
```

**VS Code not opening from terminal:**
```bash
# Add to your ~/.zshrc
echo 'export PATH="/Applications/Visual Studio Code.app/Contents/Resources/app/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

### WSL2 Issues

**WSL2 not starting:**
- Make sure virtualization is enabled in BIOS
- Run Windows Update
- Try `wsl --shutdown` then restart

**Can't access files between Windows and WSL2:**
- Access WSL files from Windows: `\\wsl$\Ubuntu`
- Access Windows files from WSL: `/mnt/c/`

**VS Code not connecting to WSL:**
- Install "Remote - WSL" extension
- Restart VS Code
- Try `code .` from WSL terminal

### General Issues

**Git not working:**
```bash
# Reconfigure Git
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

**Node.js/npm permission errors:**
```bash
# Fix npm permissions (Mac/Linux)
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.zshrc
source ~/.zshrc
```

---

## 🚀 You're All Set!

Your development environment is now ready for web development. You have:

- ✅ **Code Editor** - VS Code with essential extensions
- ✅ **Version Control** - Git for tracking changes
- ✅ **Package Manager** - npm for JavaScript packages
- ✅ **Development Server** - Live Server for testing
- ✅ **Modern Terminal** - Enhanced shell experience
- ✅ **Cross-browser Testing** - Multiple browsers installed

---

## 📚 Next Steps

1. **Practice with Git** - [Learn version control](git.md)
2. **Build your first webpage** - Start with HTML basics
3. **Set up a project repository** - Practice the development workflow
4. **Explore VS Code features** - Learn keyboard shortcuts and debugging

---

[← Back to Main Guide](readme.md) | [Next: Git Version Control →](git.md)
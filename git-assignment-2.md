# 🎯 Git Assignment 2: Advanced Git Workflows - Stash, Remotes & GitFlow

## Assignment Overview

This advanced assignment will teach you essential Git workflows used in professional development environments. You'll learn to manage work-in-progress with Git stash, collaborate with remote repositories, and implement the industry-standard GitFlow branching strategy.

**Estimated Time:** 3-4 hours  
**Difficulty:** Intermediate to Advanced  
**Prerequisites:** Completion of Git Assignment 1 or equivalent Git knowledge

---

## 🎯 Learning Objectives

By completing this assignment, you will be able to:

- ✅ Use Git stash to temporarily save and restore work
- ✅ Work with multiple remote repositories
- ✅ Fetch, pull, and push changes effectively
- ✅ Implement GitFlow branching strategy
- ✅ Manage feature, develop, and release branches
- ✅ Handle hotfixes in production environments
- ✅ Collaborate in team environments using advanced Git workflows

---

## 📋 Assignment Tasks

### Task 1: Setting Up the Project and Understanding Git Stash

#### Step 1: Create Your Assignment Repository

```bash
# Create a new directory for this assignment
mkdir git-advanced-practice
cd git-advanced-practice

# Initialize a new Git repository
git init

# Create initial project structure
mkdir src css js
touch README.md index.html src/app.js css/styles.css js/utils.js

# Create a basic project
cat > README.md << 'EOF'
# Advanced Git Practice Project

This project demonstrates advanced Git workflows including:
- Git stash operations
- Remote repository management
- GitFlow branching strategy

## Project Structure
- `src/` - Source code files
- `css/` - Stylesheets
- `js/` - JavaScript utilities
EOF

cat > index.html << 'EOF'
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Git Practice</title>
    <link rel="stylesheet" href="css/styles.css">
</head>
<body>
    <div class="container">
        <h1>Advanced Git Workflows</h1>
        <p>Learning Git stash, remotes, and GitFlow</p>
        <div id="content"></div>
    </div>
    <script src="src/app.js"></script>
    <script src="js/utils.js"></script>
</body>
</html>
EOF

cat > css/styles.css << 'EOF'
/* Basic styling for Git practice project */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    line-height: 1.6;
    color: #333;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    min-height: 100vh;
}

.container {
    max-width: 800px;
    margin: 0 auto;
    padding: 40px 20px;
    background: rgba(255, 255, 255, 0.95);
    margin-top: 50px;
    border-radius: 10px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
}

h1 {
    color: #4a5568;
    text-align: center;
    margin-bottom: 20px;
    font-size: 2.5em;
}

p {
    text-align: center;
    font-size: 1.2em;
    color: #666;
    margin-bottom: 30px;
}
EOF

cat > src/app.js << 'EOF'
// Main application logic
console.log('Advanced Git Practice App Started');

document.addEventListener('DOMContentLoaded', function() {
    const contentDiv = document.getElementById('content');
    
    contentDiv.innerHTML = `
        <div class="feature-list">
            <h2>Git Features Practiced:</h2>
            <ul>
                <li>Repository initialization</li>
                <li>Basic commit workflow</li>
            </ul>
        </div>
    `;
});
EOF

cat > js/utils.js << 'EOF'
// Utility functions for the application
const GitUtils = {
    logMessage: function(message) {
        console.log(`[Git Practice] ${message}`);
    },
    
    getCurrentTimestamp: function() {
        return new Date().toISOString();
    }
};

GitUtils.logMessage('Utilities loaded successfully');
EOF

# Make initial commit
git add .
git commit -m "Initial commit: Set up project structure and basic files"
```

#### Step 2: Understanding Git Stash Basics

```bash
# Start working on a new feature
echo "/* Adding responsive design features */" >> css/styles.css
cat >> css/styles.css << 'EOF'

@media (max-width: 768px) {
    .container {
        margin-top: 20px;
        padding: 20px 15px;
    }
    
    h1 {
        font-size: 2em;
    }
}
EOF

# Also start modifying the JavaScript
cat >> src/app.js << 'EOF'

// Adding mobile detection feature
function isMobileDevice() {
    return window.innerWidth <= 768;
}

if (isMobileDevice()) {
    document.body.classList.add('mobile');
}
EOF

# Check what you've changed
git status
git diff

# Suddenly, you need to switch to fix an urgent bug!
# But your work isn't ready to commit yet
# This is where Git stash comes in handy

# Stash your current work
git stash

# Check status - should be clean now
git status

# Your changes are safely stored
git stash list
```

#### Step 3: Working with Git Stash

```bash
# Create and fix the urgent bug
echo "/* Emergency bug fix for IE compatibility */" >> css/styles.css
cat >> css/styles.css << 'EOF'

/* IE Compatibility fixes */
.container {
    -ms-filter: "progid:DXImageTransform.Microsoft.gradient(startColorstr='#667eea', endColorstr='#764ba2')";
}
EOF

# Commit the bug fix
git add css/styles.css
git commit -m "Hotfix: Add IE compatibility for gradient backgrounds"

# Now restore your stashed work
git stash pop

# Check what happened
git status
git diff

# You'll see a merge conflict! This is normal when stash conflicts with current changes
# Edit the CSS file to resolve conflicts
cat > css/styles.css << 'EOF'
/* Basic styling for Git practice project */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    line-height: 1.6;
    color: #333;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    min-height: 100vh;
}

.container {
    max-width: 800px;
    margin: 0 auto;
    padding: 40px 20px;
    background: rgba(255, 255, 255, 0.95);
    margin-top: 50px;
    border-radius: 10px;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
    /* IE Compatibility fixes */
    -ms-filter: "progid:DXImageTransform.Microsoft.gradient(startColorstr='#667eea', endColorstr='#764ba2')";
}

h1 {
    color: #4a5568;
    text-align: center;
    margin-bottom: 20px;
    font-size: 2.5em;
}

p {
    text-align: center;
    font-size: 1.2em;
    color: #666;
    margin-bottom: 30px;
}

/* Adding responsive design features */
@media (max-width: 768px) {
    .container {
        margin-top: 20px;
        padding: 20px 15px;
    }
    
    h1 {
        font-size: 2em;
    }
}
EOF

# Stage the resolved conflicts
git add .

# Commit your feature
git commit -m "Feature: Add responsive design for mobile devices"
```

#### Step 4: Advanced Stash Operations

```bash
# Create multiple stashes
echo "console.log('Debug mode enabled');" >> src/app.js
git stash -m "Debug mode feature"

echo "Testing new feature" > test.txt
git add test.txt
git stash -m "Test file for new feature"

echo "/* Dark mode styles */" >> css/styles.css
git stash -m "Dark mode styling work"

# List all stashes
git stash list

# Apply a specific stash without removing it
git stash apply stash@{1}

# Check status
git status

# Remove that stash manually
git stash drop stash@{1}

# Clear all stashes
git stash clear

# Verify stashes are gone
git stash list
```

**📝 Question 1:** What's the difference between `git stash pop` and `git stash apply`? When would you use each?

---

### Task 2: Working with Remote Repositories

#### Step 5: Setting Up Multiple Remotes

```bash
# First, let's create a repository on GitHub
# Go to github.com and create a new repository called "git-advanced-practice"
# Don't initialize with README since we already have one

# Add the GitHub remote as 'origin'
git remote add origin https://github.com/YOUR_USERNAME/git-advanced-practice.git

# You can also add a second remote (simulate a fork scenario)
# For this exercise, we'll use the same repo but with different name
git remote add upstream https://github.com/YOUR_USERNAME/git-advanced-practice.git

# List all remotes
git remote -v

# Get detailed information about a remote
git remote show origin
```

#### Step 6: Understanding Fetch vs Pull

```bash
# Push your current work to the remote
git branch -M main  # Ensure we're on main branch
git push -u origin main

# Now let's simulate changes made by a teammate
# Go to GitHub and edit the README.md file directly in the browser
# Add this line: "## Recent Updates\n- Added responsive design features"
# Commit the change on GitHub

# Fetch the changes (downloads but doesn't merge)
git fetch origin

# See what's different
git log --oneline --graph main origin/main

# See the actual differences
git diff main origin/main

# Now merge the fetched changes
git merge origin/main

# Alternatively, you could have used pull (fetch + merge in one command)
# git pull origin main

# Check the updated file
cat README.md
```

#### Step 7: Working with Different Remote Branches

```bash
# Create a new branch and push it to remote
git checkout -b feature/user-authentication

# Add authentication feature
cat > src/auth.js << 'EOF'
// User authentication module
class AuthManager {
    constructor() {
        this.currentUser = null;
        this.isLoggedIn = false;
    }
    
    login(username, password) {
        // Simulate authentication
        if (username && password) {
            this.currentUser = username;
            this.isLoggedIn = true;
            console.log(`User ${username} logged in successfully`);
            return true;
        }
        return false;
    }
    
    logout() {
        this.currentUser = null;
        this.isLoggedIn = false;
        console.log('User logged out');
    }
    
    getCurrentUser() {
        return this.currentUser;
    }
}

// Initialize authentication manager
const auth = new AuthManager();
EOF

# Update HTML to include authentication
cat > index.html << 'EOF'
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Git Practice</title>
    <link rel="stylesheet" href="css/styles.css">
</head>
<body>
    <div class="container">
        <h1>Advanced Git Workflows</h1>
        <p>Learning Git stash, remotes, and GitFlow</p>
        
        <div class="auth-section">
            <h3>User Authentication</h3>
            <input type="text" id="username" placeholder="Username">
            <input type="password" id="password" placeholder="Password">
            <button onclick="handleLogin()">Login</button>
            <button onclick="handleLogout()">Logout</button>
            <div id="auth-status"></div>
        </div>
        
        <div id="content"></div>
    </div>
    
    <script src="src/auth.js"></script>
    <script src="src/app.js"></script>
    <script src="js/utils.js"></script>
    
    <script>
        function handleLogin() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            const success = auth.login(username, password);
            document.getElementById('auth-status').innerText = 
                success ? `Logged in as ${username}` : 'Login failed';
        }
        
        function handleLogout() {
            auth.logout();
            document.getElementById('auth-status').innerText = 'Logged out';
            document.getElementById('username').value = '';
            document.getElementById('password').value = '';
        }
    </script>
</body>
</html>
EOF

# Add styles for authentication
cat >> css/styles.css << 'EOF'

.auth-section {
    background: #f8f9fa;
    padding: 20px;
    border-radius: 8px;
    margin: 20px 0;
    text-align: center;
}

.auth-section h3 {
    margin-bottom: 15px;
    color: #495057;
}

.auth-section input {
    display: block;
    width: 200px;
    margin: 10px auto;
    padding: 8px 12px;
    border: 1px solid #ced4da;
    border-radius: 4px;
}

.auth-section button {
    background: #007bff;
    color: white;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 4px;
    cursor: pointer;
}

.auth-section button:hover {
    background: #0056b3;
}

#auth-status {
    margin-top: 15px;
    font-weight: bold;
    color: #28a745;
}
EOF

# Commit the authentication feature
git add .
git commit -m "Feature: Add user authentication system"

# Push the new branch to remote
git push -u origin feature/user-authentication

# Switch back to main
git checkout main

# List all branches (local and remote)
git branch -a

# Create a new branch that tracks a remote branch
git checkout -b feature/user-authentication-local origin/feature/user-authentication
```

**📝 Question 2:** What's the difference between `git fetch` and `git pull`? In what scenarios would you prefer one over the other?

---

### Task 3: Implementing GitFlow Workflow

#### Step 8: Setting Up GitFlow Structure

```bash
# Switch back to main and create the GitFlow structure
git checkout main

# Create develop branch from main
git checkout -b develop

# Push develop to remote
git push -u origin develop

# Create a feature branch from develop
git checkout -b feature/shopping-cart develop

# Work on the shopping cart feature
cat > src/cart.js << 'EOF'
// Shopping cart functionality
class ShoppingCart {
    constructor() {
        this.items = [];
        this.total = 0;
    }
    
    addItem(product, price, quantity = 1) {
        const item = {
            id: Date.now(),
            product: product,
            price: price,
            quantity: quantity,
            subtotal: price * quantity
        };
        
        this.items.push(item);
        this.updateTotal();
        console.log(`Added ${quantity}x ${product} to cart`);
        return item.id;
    }
    
    removeItem(itemId) {
        this.items = this.items.filter(item => item.id !== itemId);
        this.updateTotal();
        console.log(`Removed item ${itemId} from cart`);
    }
    
    updateTotal() {
        this.total = this.items.reduce((sum, item) => sum + item.subtotal, 0);
    }
    
    getItems() {
        return this.items;
    }
    
    getTotal() {
        return this.total.toFixed(2);
    }
    
    clear() {
        this.items = [];
        this.total = 0;
        console.log('Cart cleared');
    }
}

// Initialize shopping cart
const cart = new ShoppingCart();
EOF

# Update the main app to include cart functionality
cat >> src/app.js << 'EOF'

// Shopping cart integration
function updateCartDisplay() {
    const cartItems = cart.getItems();
    const cartHTML = cartItems.map(item => 
        `<div class="cart-item">
            ${item.quantity}x ${item.product} - $${item.subtotal.toFixed(2)}
            <button onclick="cart.removeItem(${item.id}); updateCartDisplay();">Remove</button>
        </div>`
    ).join('');
    
    document.getElementById('cart-display').innerHTML = cartHTML;
    document.getElementById('cart-total').innerText = `Total: $${cart.getTotal()}`;
}

// Add sample products to cart on page load
document.addEventListener('DOMContentLoaded', function() {
    // Previous content
    const contentDiv = document.getElementById('content');
    
    contentDiv.innerHTML = `
        <div class="feature-list">
            <h2>Git Features Practiced:</h2>
            <ul>
                <li>Repository initialization</li>
                <li>Basic commit workflow</li>
                <li>Git stash operations</li>
                <li>Remote repository management</li>
                <li>GitFlow branching strategy</li>
            </ul>
        </div>
        
        <div class="cart-section">
            <h2>Shopping Cart Feature</h2>
            <button onclick="cart.addItem('Laptop', 999.99); updateCartDisplay();">Add Laptop ($999.99)</button>
            <button onclick="cart.addItem('Mouse', 29.99); updateCartDisplay();">Add Mouse ($29.99)</button>
            <button onclick="cart.addItem('Keyboard', 79.99); updateCartDisplay();">Add Keyboard ($79.99)</button>
            <button onclick="cart.clear(); updateCartDisplay();">Clear Cart</button>
            
            <div id="cart-display"></div>
            <div id="cart-total">Total: $0.00</div>
        </div>
    `;
    
    updateCartDisplay();
});
EOF

# Add cart styles
cat >> css/styles.css << 'EOF'

.cart-section {
    background: #fff3cd;
    padding: 20px;
    border-radius: 8px;
    margin: 20px 0;
    border: 1px solid #ffeaa7;
}

.cart-section h2 {
    color: #856404;
    margin-bottom: 15px;
}

.cart-section button {
    background: #ffc107;
    color: #212529;
    border: none;
    padding: 8px 15px;
    margin: 5px;
    border-radius: 4px;
    cursor: pointer;
}

.cart-section button:hover {
    background: #e0a800;
}

.cart-item {
    background: white;
    padding: 10px;
    margin: 10px 0;
    border-radius: 4px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.cart-item button {
    background: #dc3545;
    color: white;
    padding: 5px 10px;
    font-size: 0.8em;
}

.cart-item button:hover {
    background: #c82333;
}

#cart-total {
    font-size: 1.2em;
    font-weight: bold;
    color: #856404;
    text-align: right;
    margin-top: 15px;
}
EOF

# Update HTML to include cart script
cat > index.html << 'EOF'
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Git Practice</title>
    <link rel="stylesheet" href="css/styles.css">
</head>
<body>
    <div class="container">
        <h1>Advanced Git Workflows</h1>
        <p>Learning Git stash, remotes, and GitFlow</p>
        
        <div class="auth-section">
            <h3>User Authentication</h3>
            <input type="text" id="username" placeholder="Username">
            <input type="password" id="password" placeholder="Password">
            <button onclick="handleLogin()">Login</button>
            <button onclick="handleLogout()">Logout</button>
            <div id="auth-status"></div>
        </div>
        
        <div id="content"></div>
    </div>
    
    <script src="src/auth.js"></script>
    <script src="src/cart.js"></script>
    <script src="src/app.js"></script>
    <script src="js/utils.js"></script>
    
    <script>
        function handleLogin() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            const success = auth.login(username, password);
            document.getElementById('auth-status').innerText = 
                success ? `Logged in as ${username}` : 'Login failed';
        }
        
        function handleLogout() {
            auth.logout();
            document.getElementById('auth-status').innerText = 'Logged out';
            document.getElementById('username').value = '';
            document.getElementById('password').value = '';
        }
    </script>
</body>
</html>
EOF

# Commit the shopping cart feature
git add .
git commit -m "Feature: Add shopping cart functionality with item management"

# Push feature branch
git push -u origin feature/shopping-cart
```

#### Step 9: GitFlow Feature Integration

```bash
# Merge feature into develop
git checkout develop
git merge feature/shopping-cart --no-ff -m "Merge feature/shopping-cart into develop"

# Push updated develop
git push origin develop

# Delete the feature branch (locally and remotely)
git branch -d feature/shopping-cart
git push origin --delete feature/shopping-cart

# Create another feature branch for product search
git checkout -b feature/product-search develop

# Add product search functionality
cat > src/search.js << 'EOF'
// Product search functionality
class ProductSearch {
    constructor() {
        this.products = [
            { id: 1, name: 'Laptop', price: 999.99, category: 'Electronics' },
            { id: 2, name: 'Mouse', price: 29.99, category: 'Electronics' },
            { id: 3, name: 'Keyboard', price: 79.99, category: 'Electronics' },
            { id: 4, name: 'Monitor', price: 299.99, category: 'Electronics' },
            { id: 5, name: 'Headphones', price: 149.99, category: 'Audio' },
            { id: 6, name: 'Speakers', price: 89.99, category: 'Audio' }
        ];
    }
    
    search(query) {
        if (!query) return [];
        
        query = query.toLowerCase();
        return this.products.filter(product => 
            product.name.toLowerCase().includes(query) ||
            product.category.toLowerCase().includes(query)
        );
    }
    
    getByCategory(category) {
        return this.products.filter(product => 
            product.category.toLowerCase() === category.toLowerCase()
        );
    }
    
    getById(id) {
        return this.products.find(product => product.id === id);
    }
    
    getAllProducts() {
        return this.products;
    }
}

// Initialize product search
const productSearch = new ProductSearch();
EOF

# Update app.js to include search functionality
cat >> src/app.js << 'EOF'

// Product search integration
function performSearch() {
    const query = document.getElementById('search-input').value;
    const results = productSearch.search(query);
    
    const resultsHTML = results.map(product => 
        `<div class="search-result">
            <span>${product.name} - $${product.price} (${product.category})</span>
            <button onclick="cart.addItem('${product.name}', ${product.price}); updateCartDisplay();">
                Add to Cart
            </button>
        </div>`
    ).join('');
    
    document.getElementById('search-results').innerHTML = resultsHTML || '<p>No products found</p>';
}

// Update the content loading
document.addEventListener('DOMContentLoaded', function() {
    const contentDiv = document.getElementById('content');
    
    contentDiv.innerHTML = `
        <div class="feature-list">
            <h2>Git Features Practiced:</h2>
            <ul>
                <li>Repository initialization</li>
                <li>Basic commit workflow</li>
                <li>Git stash operations</li>
                <li>Remote repository management</li>
                <li>GitFlow branching strategy</li>
                <li>Feature branch development</li>
            </ul>
        </div>
        
        <div class="search-section">
            <h2>Product Search</h2>
            <input type="text" id="search-input" placeholder="Search products..." onkeyup="performSearch()">
            <div id="search-results"></div>
        </div>
        
        <div class="cart-section">
            <h2>Shopping Cart Feature</h2>
            <button onclick="cart.addItem('Laptop', 999.99); updateCartDisplay();">Add Laptop ($999.99)</button>
            <button onclick="cart.addItem('Mouse', 29.99); updateCartDisplay();">Add Mouse ($29.99)</button>
            <button onclick="cart.addItem('Keyboard', 79.99); updateCartDisplay();">Add Keyboard ($79.99)</button>
            <button onclick="cart.clear(); updateCartDisplay();">Clear Cart</button>
            
            <div id="cart-display"></div>
            <div id="cart-total">Total: $0.00</div>
        </div>
    `;
    
    updateCartDisplay();
    // Show all products initially
    performSearch();
});
EOF

# Add search styles
cat >> css/styles.css << 'EOF'

.search-section {
    background: #d1ecf1;
    padding: 20px;
    border-radius: 8px;
    margin: 20px 0;
    border: 1px solid #bee5eb;
}

.search-section h2 {
    color: #0c5460;
    margin-bottom: 15px;
}

#search-input {
    width: 100%;
    padding: 10px;
    border: 1px solid #aed6dc;
    border-radius: 4px;
    font-size: 1em;
}

.search-result {
    background: white;
    padding: 12px;
    margin: 8px 0;
    border-radius: 4px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    border: 1px solid #dee2e6;
}

.search-result button {
    background: #28a745;
    color: white;
    border: none;
    padding: 6px 12px;
    border-radius: 4px;
    cursor: pointer;
}

.search-result button:hover {
    background: #218838;
}
EOF

# Update HTML to include search script
cat > index.html << 'EOF'
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Advanced Git Practice</title>
    <link rel="stylesheet" href="css/styles.css">
</head>
<body>
    <div class="container">
        <h1>Advanced Git Workflows</h1>
        <p>Learning Git stash, remotes, and GitFlow</p>
        
        <div class="auth-section">
            <h3>User Authentication</h3>
            <input type="text" id="username" placeholder="Username">
            <input type="password" id="password" placeholder="Password">
            <button onclick="handleLogin()">Login</button>
            <button onclick="handleLogout()">Logout</button>
            <div id="auth-status"></div>
        </div>
        
        <div id="content"></div>
    </div>
    
    <script src="src/auth.js"></script>
    <script src="src/cart.js"></script>
    <script src="src/search.js"></script>
    <script src="src/app.js"></script>
    <script src="js/utils.js"></script>
    
    <script>
        function handleLogin() {
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            const success = auth.login(username, password);
            document.getElementById('auth-status').innerText = 
                success ? `Logged in as ${username}` : 'Login failed';
        }
        
        function handleLogout() {
            auth.logout();
            document.getElementById('auth-status').innerText = 'Logged out';
            document.getElementById('username').value = '';
            document.getElementById('password').value = '';
        }
    </script>
</body>
</html>
EOF

# Commit the search feature
git add .
git commit -m "Feature: Add product search functionality"

# Push the search feature branch
git push -u origin feature/product-search
```

**📝 Question 3:** In GitFlow, what's the purpose of the develop branch? How does it differ from the main branch?

---

### Task 4: GitFlow Release Process

#### Step 10: Creating a Release Branch

```bash
# Merge search feature into develop
git checkout develop
git merge feature/product-search --no-ff -m "Merge feature/product-search into develop"
git push origin develop

# Clean up feature branch
git branch -d feature/product-search
git push origin --delete feature/product-search

# Create a release branch from develop
git checkout -b release/v1.0.0 develop

# Prepare for release - update version information
cat > VERSION.txt << 'EOF'
Version: 1.0.0
Release Date: $(date +%Y-%m-%d)
Features:
- User authentication system
- Shopping cart functionality
- Product search capability
- Responsive design
- GitFlow workflow implementation
EOF

# Update README with release information
cat >> README.md << 'EOF'

## Version 1.0.0 Features

### ✅ Completed Features
- **User Authentication**: Login/logout functionality
- **Shopping Cart**: Add, remove, and manage cart items
- **Product Search**: Search products by name or category
- **Responsive Design**: Mobile-friendly interface
- **Git Workflow**: Advanced Git operations demonstration

### 🔧 Technical Highlights
- Modular JavaScript architecture
- Clean CSS with responsive design
- GitFlow branching strategy
- Comprehensive Git stash usage
- Multi-remote repository management

### 🚀 Getting Started
1. Clone the repository
2. Open `index.html` in a web browser
3. Explore the authentication and shopping features
4. Use browser developer tools to see console logs
EOF

# Commit release preparations
git add .
git commit -m "Release: Prepare v1.0.0 with version info and updated documentation"

# Push release branch
git push -u origin release/v1.0.0
```

#### Step 11: Finalizing the Release

```bash
# Merge release into main
git checkout main
git merge release/v1.0.0 --no-ff -m "Release v1.0.0: Complete e-commerce features"

# Tag the release
git tag -a v1.0.0 -m "Version 1.0.0: First release with auth, cart, and search features"

# Push main and tags
git push origin main
git push origin v1.0.0

# Merge release back into develop
git checkout develop
git merge release/v1.0.0 --no-ff -m "Merge release/v1.0.0 back into develop"
git push origin develop

# Clean up release branch
git branch -d release/v1.0.0
git push origin --delete release/v1.0.0

# View the complete history
git log --oneline --graph --all
```

---

### Task 5: GitFlow Hotfix Process

#### Step 12: Handling a Critical Hotfix

```bash
# Simulate discovering a critical bug in production
# Create hotfix branch from main
git checkout -b hotfix/cart-calculation-fix main

# Fix the critical bug in cart calculation
cat > src/cart.js << 'EOF'
// Shopping cart functionality
class ShoppingCart {
    constructor() {
        this.items = [];
        this.total = 0;
    }
    
    addItem(product, price, quantity = 1) {
        // HOTFIX: Validate price to prevent negative values
        if (price < 0) {
            console.error('Price cannot be negative');
            return null;
        }
        
        // HOTFIX: Validate quantity to prevent negative or zero values
        if (quantity <= 0) {
            console.error('Quantity must be positive');
            return null;
        }
        
        const item = {
            id: Date.now(),
            product: product,
            price: parseFloat(price.toFixed(2)), // HOTFIX: Ensure proper decimal handling
            quantity: parseInt(quantity),
            subtotal: parseFloat((price * quantity).toFixed(2)) // HOTFIX: Fix decimal precision
        };
        
        this.items.push(item);
        this.updateTotal();
        console.log(`Added ${quantity}x ${product} to cart`);
        return item.id;
    }
    
    removeItem(itemId) {
        this.items = this.items.filter(item => item.id !== itemId);
        this.updateTotal();
        console.log(`Removed item ${itemId} from cart`);
    }
    
    updateTotal() {
        // HOTFIX: Fix floating point calculation errors
        this.total = parseFloat(
            this.items.reduce((sum, item) => sum + item.subtotal, 0).toFixed(2)
        );
    }
    
    getItems() {
        return this.items;
    }
    
    getTotal() {
        return this.total.toFixed(2);
    }
    
    clear() {
        this.items = [];
        this.total = 0;
        console.log('Cart cleared');
    }
}

// Initialize shopping cart
const cart = new ShoppingCart();
EOF

# Update version for hotfix
cat > VERSION.txt << 'EOF'
Version: 1.0.1
Release Date: $(date +%Y-%m-%d)
Type: Hotfix Release

Changes:
- CRITICAL: Fixed cart calculation precision errors
- SECURITY: Added validation for negative prices and quantities
- STABILITY: Improved decimal handling in cart operations

Previous Version: 1.0.0
EOF

# Commit the hotfix
git add .
git commit -m "Hotfix v1.0.1: Fix critical cart calculation and validation issues"

# Push hotfix branch
git push -u origin hotfix/cart-calculation-fix
```

#### Step 13: Deploying the Hotfix

```bash
# Merge hotfix into main
git checkout main
git merge hotfix/cart-calculation-fix --no-ff -m "Hotfix v1.0.1: Critical cart calculation fixes"

# Tag the hotfix
git tag -a v1.0.1 -m "Hotfix v1.0.1: Critical cart calculation and validation fixes"

# Push main and tags
git push origin main
git push origin v1.0.1

# Merge hotfix into develop
git checkout develop
git merge hotfix/cart-calculation-fix --no-ff -m "Merge hotfix/cart-calculation-fix into develop"
git push origin develop

# Clean up hotfix branch
git branch -d hotfix/cart-calculation-fix
git push origin --delete hotfix/cart-calculation-fix

# View final repository state
git log --oneline --graph --all --decorate
```

**📝 Question 4:** Why do hotfix branches come from main instead of develop? What would happen if you created a hotfix from develop?

---

### Task 6: Advanced Remote Operations

#### Step 14: Working with Multiple Contributors

```bash
# Simulate working with a team member's changes
# Create a new feature branch
git checkout -b feature/user-profile develop

# Add user profile functionality
cat > src/profile.js << 'EOF'
// User profile management
class UserProfile {
    constructor() {
        this.profiles = new Map();
    }
    
    createProfile(username, email, fullName) {
        if (this.profiles.has(username)) {
            console.error('Profile already exists');
            return false;
        }
        
        const profile = {
            username: username,
            email: email,
            fullName: fullName,
            createdAt: new Date().toISOString(),
            preferences: {
                theme: 'light',
                notifications: true
            }
        };
        
        this.profiles.set(username, profile);
        console.log(`Profile created for ${fullName}`);
        return true;
    }
    
    getProfile(username) {
        return this.profiles.get(username);
    }
    
    updateProfile(username, updates) {
        const profile = this.profiles.get(username);
        if (!profile) {
            console.error('Profile not found');
            return false;
        }
        
        Object.assign(profile, updates);
        this.profiles.set(username, profile);
        console.log(`Profile updated for ${username}`);
        return true;
    }
    
    deleteProfile(username) {
        const deleted = this.profiles.delete(username);
        if (deleted) {
            console.log(`Profile deleted for ${username}`);
        } else {
            console.error('Profile not found');
        }
        return deleted;
    }
}

// Initialize user profile manager
const userProfile = new UserProfile();
EOF

# Before committing, let's practice some stash scenarios
echo "/* Temporary styling changes */" >> css/styles.css
cat >> css/styles.css << 'EOF'

.temp-style {
    border: 2px solid red;
    background: yellow;
}
EOF

# Stash these temporary changes
git stash push -m "Temporary styling for testing"

# Work on the profile feature
git add src/profile.js
git commit -m "Feature: Add user profile management system"

# Now let's say you need those temporary styles after all
git stash pop

# But you realize you only want part of the stashed changes
# Edit the CSS to keep only what you want
cat >> css/styles.css << 'EOF'

.profile-section {
    background: #e7f3ff;
    padding: 20px;
    border-radius: 8px;
    margin: 20px 0;
    border: 1px solid #b3d9ff;
}

.profile-section h2 {
    color: #0056b3;
    margin-bottom: 15px;
}

.profile-form {
    display: grid;
    gap: 10px;
    max-width: 400px;
}

.profile-form input {
    padding: 8px;
    border: 1px solid #ced4da;
    border-radius: 4px;
}

.profile-form button {
    background: #007bff;
    color: white;
    border: none;
    padding: 10px;
    border-radius: 4px;
    cursor: pointer;
}

.profile-form button:hover {
    background: #0056b3;
}
EOF

# Stage only the profile styles (not the temp styles)
git add css/styles.css
git commit -m "Style: Add user profile section styling"

# Push the feature branch
git push -u origin feature/user-profile
```

#### Step 15: Practicing Remote Conflict Resolution

```bash
# Simulate a conflict scenario
# Go to GitHub and edit the develop branch README.md
# Add a line like: "## Team Contributors\n- John Doe (john@example.com)"

# Meanwhile, update your local develop branch differently
git checkout develop

# Make a conflicting change
cat >> README.md << 'EOF'

## Development Team
- Lead Developer: Your Name
- Backend Developer: Jane Smith
- Frontend Developer: Bob Johnson
EOF

# Commit locally
git add README.md
git commit -m "Add development team information"

# Try to push - this will fail due to remote changes
git push origin develop

# Fetch the remote changes
git fetch origin

# Try to merge (this will create a conflict)
git merge origin/develop

# Resolve the conflict by editing README.md
# The file will have conflict markers, resolve them manually
cat > README.md << 'EOF'
# Advanced Git Practice Project

This project demonstrates advanced Git workflows including:
- Git stash operations
- Remote repository management
- GitFlow branching strategy

## Project Structure
- `src/` - Source code files
- `css/` - Stylesheets
- `js/` - JavaScript utilities

## Version 1.0.0 Features

### ✅ Completed Features
- **User Authentication**: Login/logout functionality
- **Shopping Cart**: Add, remove, and manage cart items
- **Product Search**: Search products by name or category
- **Responsive Design**: Mobile-friendly interface
- **Git Workflow**: Advanced Git operations demonstration

### 🔧 Technical Highlights
- Modular JavaScript architecture
- Clean CSS with responsive design
- GitFlow branching strategy
- Comprehensive Git stash usage
- Multi-remote repository management

### 🚀 Getting Started
1. Clone the repository
2. Open `index.html` in a web browser
3. Explore the authentication and shopping features
4. Use browser developer tools to see console logs

## Team Contributors
- John Doe (john@example.com)

## Development Team
- Lead Developer: Your Name
- Backend Developer: Jane Smith
- Frontend Developer: Bob Johnson
EOF

# Stage the resolved conflict
git add README.md

# Complete the merge
git commit -m "Merge remote changes and resolve team information conflict"

# Push the resolved changes
git push origin develop
```

**📝 Question 5:** When working with a team, what's the best practice for avoiding merge conflicts? How can you minimize them?

---

## 🧪 Testing Your Knowledge

### Challenge 1: Complex Stash Scenario
1. Start working on a feature
2. Stash your changes with a message
3. Work on a hotfix
4. Stash the hotfix work too
5. Apply the first stash, resolve any conflicts
6. Apply the second stash in the right place
7. Commit both features properly

### Challenge 2: GitFlow Release with Complications
1. Create a release branch
2. During release testing, discover you need one more feature
3. Add the feature to develop first
4. Merge it into your release branch
5. Complete the release process

### Challenge 3: Remote Repository Management
1. Add a second remote repository
2. Push different branches to different remotes
3. Fetch from one remote and merge into a branch that tracks another remote
4. Handle any conflicts that arise

---

## 📝 Assignment Deliverables

### Submit the Following:

1. **Complete Git Log:**
   ```bash
   git log --oneline --graph --all --decorate
   ```

2. **Remote Repository Information:**
   ```bash
   git remote -v
   git branch -a
   ```

3. **Answers to all questions (1-5) asked throughout the assignment**

4. **A comprehensive report (400-500 words) covering:**
   - How Git stash improved your workflow
   - Benefits of GitFlow in team development
   - Challenges faced with remote repositories
   - Real-world applications of these advanced Git features

### Submission Format:

Create a file called `ASSIGNMENT_2_REPORT.md` in your repository:

```markdown
# Git Assignment 2 Report - Advanced Workflows

## Git Log and Repository State
```
[Paste your git log --oneline --graph --all --decorate output here]
```

## Remote Information
```
[Paste your git remote -v and git branch -a output here]
```

## Question Answers

### Question 1: Stash Operations
[Your answer about git stash pop vs apply]

### Question 2: Fetch vs Pull
[Your answer about fetch vs pull differences]

### Question 3: GitFlow Develop Branch
[Your answer about develop branch purpose]

### Question 4: Hotfix Process
[Your answer about hotfix branches from main]

### Question 5: Avoiding Merge Conflicts
[Your answer about conflict prevention]

## Comprehensive Reflection

### Git Stash Workflow Improvements
[Your thoughts on how stash improved your workflow]

### GitFlow Benefits for Teams
[Your analysis of GitFlow advantages]

### Remote Repository Challenges
[Challenges you faced and how you solved them]

### Real-World Applications
[How you plan to use these features professionally]
```

---

## 🏆 Success Criteria

You have successfully completed this assignment when you can:

- [ ] Use Git stash effectively for managing work-in-progress
- [ ] Work confidently with multiple remote repositories
- [ ] Implement complete GitFlow workflow (feature, develop, release, hotfix)
- [ ] Resolve conflicts in both local and remote scenarios
- [ ] Understand when and why to use different Git operations
- [ ] Collaborate effectively in team development environments

---

## 🚀 Advanced Topics for Further Learning

After mastering this assignment, explore:

1. **Git Hooks** - Automate tasks with pre-commit, post-merge hooks
2. **Git Submodules** - Manage dependencies and nested repositories
3. **Git Worktrees** - Work on multiple branches simultaneously
4. **Git Bisect** - Find bugs using binary search through commits
5. **Git LFS** - Handle large files efficiently
6. **Advanced Rebasing** - Interactive rebase, squashing, and history rewriting

---

*🎉 **Congratulations!** You've mastered advanced Git workflows that are essential for professional software development. These skills will make you an effective team member in any development environment.*

---

[← Back to Git Guide](git.md) | [← Back to Main Guide](readme.md)
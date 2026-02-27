# Node.js Full Setup Guide (Complete README)

This guide covers complete Node.js installation, project setup, commonly used commands, package management, environment configuration, and deployment basics.

---

# 1. Install Node.js

## Option 1: Install via Official Website (Recommended for Beginners)

1. Go to: [https://nodejs.org](https://nodejs.org)
2. Download **LTS (Long Term Support)** version
3. Install using default settings
4. Verify installation:

```bash
node -v
npm -v
```

---

## Option 2: Install via NVM (Recommended for Developers)

### Install NVM (Mac/Linux)

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash
```

Restart terminal, then:

```bash
nvm install --lts
nvm use --lts
node -v
```

### Install NVM (Windows)

Download: [https://github.com/coreybutler/nvm-windows](https://github.com/coreybutler/nvm-windows)

Then:

```bash
nvm install 20
nvm use 20
```

---

# 2. Create a New Node.js Project

```bash
mkdir my-project
cd my-project
npm init -y
```

This creates:

```
package.json
```

---

# 3. Understanding package.json

Important fields:

```json
{
  "name": "my-project",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "start": "node index.js"
  }
}
```

---

# 4. Install Dependencies

## Install normal dependency

```bash
npm install express
```

## Install dev dependency

```bash
npm install nodemon --save-dev
```

## Install specific version

```bash
npm install express@4.18.2
```

## Remove package

```bash
npm uninstall express
```

---

# 5. Basic Express Server Setup

Create file: `index.js`

```javascript
const express = require('express');
const app = express();

app.use(express.json());

app.get('/', (req, res) => {
  res.send('Server Running');
});

const PORT = 3000;
app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

Run server:

```bash
node index.js
```

Using nodemon:

```bash
npx nodemon index.js
```

---

# 6. Useful npm Commands

## Install all dependencies

```bash
npm install
```

## Start script

```bash
npm start
```

## Run custom script

```bash
npm run dev
```

## Update packages

```bash
npm update
```

## Check outdated packages

```bash
npm outdated
```

## Audit vulnerabilities

```bash
npm audit
npm audit fix
```

---

# 7. Using Environment Variables (.env Setup)

Install dotenv:

```bash
npm install dotenv
```

Create `.env` file:

```
PORT=5000
DB_URL=mongodb://localhost:27017/test
```

Use in code:

```javascript
require('dotenv').config();

const PORT = process.env.PORT;
```

---

# 8. Project Folder Structure (Recommended)

```
my-project/
│
├── node_modules/
├── src/
│   ├── controllers/
│   ├── routes/
│   ├── models/
│   └── app.js
│
├── .env
├── package.json
├── package-lock.json
└── server.js
```

---

# 9. Using ES Modules Instead of require

In package.json:

```json
{
  "type": "module"
}
```

Then use:

```javascript
import express from 'express';
```

---

# 10. Global Packages

Install globally:

```bash
npm install -g nodemon
```

List global packages:

```bash
npm list -g --depth=0
```

---

# 11. Clear Cache

```bash
npm cache clean --force
```

---

# 12. Delete node_modules and Reinstall

Mac/Linux:

```bash
rm -rf node_modules package-lock.json
npm install
```

Windows:

```bash
rmdir /s /q node_modules
del package-lock.json
npm install
```

---

# 13. Common Errors & Fixes

## Port already in use

Change PORT or kill process:

Mac/Linux:

```bash
lsof -i :3000
kill -9 PID
```

Windows:

```bash
netstat -ano | findstr :3000
taskkill /PID PID /F
```

---

# 14. Production Deployment Basics

## Install PM2

```bash
npm install -g pm2
```

Start app:

```bash
pm2 start index.js
```

Check status:

```bash
pm2 status
```

Save process:

```bash
pm2 save
```

---

# 15. Node Version Management

Check version:

```bash
node -v
```

Switch version (NVM):

```bash
nvm use 18
```

---

# 16. Initialize Git Repository

```bash
git init
git add .
git commit -m "Initial commit"
```

Create .gitignore:

```
node_modules/
.env
```

---

# 17. Build & Run Full Example (Quick Start)

```bash
mkdir demo-app
cd demo-app
npm init -y
npm install express dotenv
```

Create `index.js` and run:

```bash
node index.js
```

---

# 18. Important Concepts

* Node.js is runtime environment
* npm is package manager
* package.json manages dependencies
* node_modules contains installed packages
* express is web framework
* dotenv manages environment variables

---

# 19. Useful Shortcuts

```bash
npx create-react-app appname
npx nodemon index.js
```

---

# 20. Final Checklist

* Node installed
* npm working
* package.json created
* Dependencies installed
* Server running
* .env configured
* Git initialized
* PM2 configured (for production)

---

End of Full Node.js Setup README

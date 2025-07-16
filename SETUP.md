# AFK Discord Bot - Node.js Setup Instructions

## Required Files (in this zip)
- `index.js` - Main bot logic and entry point
- `AFKManager.js` - AFK management logic
- `start.js` - Alternative entry point
- `package.json` - Node.js dependencies
- `replit.md` - Documentation

## For Render Deployment

### 1. Upload to GitHub
1. Create a new GitHub repository
2. Upload all files from this zip
3. Commit and push to main branch

### 2. Deploy on Render
1. Go to [render.com](https://render.com)
2. Create new "Web Service"
3. Connect your GitHub repository
4. Settings:
   - **Build Command**: `npm install`
   - **Start Command**: `node index.js`
   - **Environment**: Node.js
   - **Node Version**: 18.x or higher

### 3. Set Environment Variables
In Render dashboard, add:
- Key: `DISCORD_BOT_TOKEN`
- Value: Your Discord bot token

### 4. Deploy
Click "Deploy" - your bot will be live!

## For Local Development

### Setup Steps
1. Install Node.js 18+ from nodejs.org
2. Extract this zip to a folder
3. Run: `npm install`
4. Set environment variable: `export DISCORD_BOT_TOKEN=your_token`
5. Run: `node index.js`

### Windows Users
```cmd
set DISCORD_BOT_TOKEN=your_token
node index.js
```

## Bot Commands
- `?afk` - Set AFK status with interactive buttons
- `?afkstatus` - Check your current AFK status
- `?help` - Show help information
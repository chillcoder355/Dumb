# AFK Discord Bot

## Overview

This is a Discord bot that manages AFK (Away From Keyboard) status for users. The bot allows users to set themselves as AFK with optional reasons, supports both global and server-specific AFK modes, and automatically removes AFK status when users send messages. The bot is built in Node.js using Discord.js with a simple file structure optimized for Render hosting.

## User Preferences

Preferred communication style: Simple, everyday language.
Preferred language: Node.js (converted from Java for Render hosting)
Project structure: Simple Node.js structure for easy deployment on Render
Embed colors: #2e2e2e for all embeds except help command (which stays blue)

## System Architecture

The bot follows a simple modular architecture with minimal files:

- **Bot Core** (`index.js`): Main bot class handling Discord events and core functionality
- **AFK Management** (`AFKManager.js`): Business logic for managing AFK states
- **Entry Point** (`start.js`): Alternative entry point for deployment
- **Dependencies** (`package.json`): Node.js dependencies managed by npm

The architecture uses in-memory storage for AFK data, making it suitable for smaller Discord communities where persistence across restarts is not critical.

## Key Components

### AFKManager
- **Purpose**: Core business logic for AFK status management
- **Data Structure**: Map storing user AFK data by user ID and server ID
- **Key Features**: 
  - Supports both global and server-specific AFK modes
  - Handles AFK status conflicts (global overrides server-specific)
  - Provides methods for setting, removing, and checking AFK status
  - Simple JavaScript object-based data storage

### AFKBot (index.js)
- **Purpose**: Main Discord bot class using Discord.js Client
- **Features**:
  - Handles message events to auto-remove AFK status
  - Processes prefix commands (?afk, ?afkstatus, ?help)
  - Integrates with AFKManager for status operations
  - Manages button interactions and modal dialogs
  - Event-driven architecture with Discord.js

### AFKData
- **Purpose**: JavaScript object representing AFK status information
- **Features**:
  - Stores timestamp, reason, global flag, and server ID
  - Simple object structure for easy manipulation
  - Used by AFKManager to track AFK states

## Data Flow

1. **Setting AFK Status**:
   - User interacts with bot command/button
   - AFKView presents global vs server options
   - AFKReasonModal collects optional reason
   - AFKManager stores the AFK data with timestamp

2. **AFK Status Removal**:
   - Bot monitors all messages via on_message event
   - Checks if message author has AFK status
   - AFKManager removes AFK status if found
   - Bot notifies about AFK removal

3. **AFK Status Checking**:
   - When users are mentioned or interact
   - AFKManager checks for active AFK status
   - Returns AFK data including reason and timestamp

## External Dependencies

- **Discord.js**: Discord API wrapper for Node.js (npm package)
- **Node.js**: JavaScript runtime environment

The bot has minimal dependencies, requiring only the Discord.js library and Node.js runtime.

## Deployment Strategy

The bot is designed for ultra-simple deployment on Render:

- **Environment Variables**: Bot token stored in `DISCORD_BOT_TOKEN` environment variable
- **Runtime**: Node.js 18+ with Discord.js
- **Build System**: No build step required - direct Node.js execution
- **Storage**: In-memory storage (no database required)  
- **Hosting**: Optimized for Render hosting platform
- **File Structure**: Simple Node.js structure with 2 main files + package.json

The implementation prioritizes maximum simplicity and ease of deployment on Render, making it perfect for quick setup and smaller Discord communities.
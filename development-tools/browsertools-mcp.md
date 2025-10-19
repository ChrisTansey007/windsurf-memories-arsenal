---
id: mem.browsertools-mcp
type: memory
title: BrowserTools MCP Integration
tags: [mcp, debugging, browser, development-tools, windsurf]
summary: Complete setup and usage guide for BrowserTools MCP server - access browser console logs, network requests, and screenshots from Windsurf/Cursor.
audience: developers
domain: debugging
version: 1
---

# BrowserTools MCP Integration

**Access browser console logs, network requests, and screenshots directly from Windsurf/Cursor.**

---

## 🎯 What is BrowserTools MCP?

BrowserTools MCP is a Model Context Protocol (MCP) server that connects your AI assistant (Windsurf/Cursor) to your browser's developer tools.

**Key Features:**
- 📋 Access console logs in real-time
- 🌐 View network requests and responses
- 📸 Capture screenshots
- 🔍 Debug runtime errors without switching windows
- 🤖 Let AI analyze browser errors directly

**Use Cases:**
- Debugging JavaScript errors
- Analyzing network failures
- Monitoring API responses
- Capturing error states
- Performance debugging

---

## 📦 Installation

### Prerequisites

- ✅ Node.js 18+ installed
- ✅ Chrome or Chromium-based browser
- ✅ Windsurf or Cursor IDE

### Step 1: Install Browser Extension

**Download the extension:**
```bash
# Download latest release
curl -L https://github.com/AgentDeskAI/browser-tools-mcp/releases/download/v1.2.0/BrowserTools-1.2.0-extension.zip -o BrowserTools.zip

# Unzip
unzip BrowserTools.zip -d BrowserTools-Extension
```

**Load in Chrome:**
1. Open Chrome
2. Navigate to `chrome://extensions/`
3. Enable "Developer mode" (top right toggle)
4. Click "Load unpacked"
5. Select the `BrowserTools-Extension` folder
6. Extension should now appear in your extensions list

**Verify installation:**
- Look for BrowserTools icon in Chrome toolbar
- Click icon - should show "Connected" or "Waiting for server"

### Step 2: Install MCP Server

**Using npx (recommended):**
```bash
# No installation needed - runs on demand
npx @agentdeskai/browser-tools-mcp@1.2.0
```

**Or install globally:**
```bash
npm install -g @agentdeskai/browser-tools-mcp
browser-tools-mcp
```

### Step 3: Configure Windsurf

**Add to Windsurf MCP settings:**

1. Open Windsurf settings (Cmd/Ctrl + ,)
2. Search for "MCP"
3. Click "Edit in settings.json"
4. Add BrowserTools configuration:

```json
{
  "mcp.servers": {
    "browsertools": {
      "command": "npx",
      "args": ["@agentdeskai/browser-tools-mcp@1.2.0"],
      "env": {}
    }
  }
}
```

**Or edit settings file directly:**

**Windows:** `%APPDATA%\Windsurf\User\settings.json`  
**Mac:** `~/Library/Application Support/Windsurf/User/settings.json`  
**Linux:** `~/.config/Windsurf/User/settings.json`

### Step 4: Start the Server

**Option A: Let Windsurf start it automatically**
- Restart Windsurf
- MCP server will start automatically when needed

**Option B: Start manually for testing**
```bash
npx @agentdeskai/browser-tools-mcp@1.2.0
# Server should output: "BrowserTools MCP server running..."
```

### Step 5: Connect Browser

1. Open your web application in Chrome
2. Open DevTools (F12 or Cmd+Opt+I)
3. BrowserTools extension should connect automatically
4. Check extension icon - should show "Connected"

---

## 🚀 Usage

### Basic Commands in Windsurf

**Get console logs:**
```
Show me the browser console logs
```

**Get network requests:**
```
What network requests were made?
```

**Capture screenshot:**
```
Take a screenshot of the current page
```

**Analyze errors:**
```
Are there any errors in the browser console?
```

### Advanced Usage

**Debug specific errors:**
```
The page is showing a white screen. Check the console for errors and help me fix them.
```

**Analyze network issues:**
```
The API call is failing. Show me the network requests and responses for /api/users
```

**Monitor real-time:**
```
Watch the console logs while I click the submit button
```

**Compare before/after:**
```
Take a screenshot now, then take another after I make this change
```

---

## 🔧 Available MCP Tools

### 1. get_console_logs

**Purpose:** Retrieve browser console logs

**Parameters:**
- `level` (optional): Filter by log level (log, warn, error, info)
- `limit` (optional): Maximum number of logs to return

**Example:**
```typescript
// In Windsurf chat
"Show me all error logs from the browser"
"Get the last 10 console.log messages"
```

### 2. get_network_logs

**Purpose:** Retrieve network requests and responses

**Parameters:**
- `type` (optional): Filter by request type (XHR, Fetch, Document, etc.)
- `status` (optional): Filter by status code (200, 404, 500, etc.)
- `url` (optional): Filter by URL pattern

**Example:**
```typescript
// In Windsurf chat
"Show me all failed network requests (4xx, 5xx)"
"Get API requests to /api/users"
"Show me requests that took longer than 1 second"
```

### 3. capture_screenshot

**Purpose:** Capture screenshot of current browser tab

**Parameters:**
- `fullPage` (optional): Capture entire page or just viewport

**Example:**
```typescript
// In Windsurf chat
"Take a screenshot"
"Capture the full page including content below the fold"
```

### 4. evaluate_javascript

**Purpose:** Execute JavaScript in the browser context

**Parameters:**
- `code`: JavaScript code to execute

**Example:**
```typescript
// In Windsurf chat
"Run document.querySelector('.error-message').textContent in the browser"
"Check if window.myApp is defined"
```

---

## 💡 Real-World Examples

### Example 1: Debug React Error

**Scenario:** White screen, app not rendering

**Conversation with Windsurf:**
```
You: My app shows a white screen. Help me debug it.

Windsurf: Let me check the browser console...
[Uses get_console_logs]

Windsurf: I see this error:
"Error: Objects are not valid as a React child (found: [object Error])"
at line 45 in UserProfile.tsx

This happens when you try to render an Error object directly in JSX.
Let me find where this occurs...

[Reads UserProfile.tsx]

Windsurf: Found it! On line 45:
{error && <div>{error}</div>}

Change it to:
{error && <div>{error.message}</div>}
```

### Example 2: Debug Network Failure

**Scenario:** API call returning 401

**Conversation with Windsurf:**
```
You: My login API call is failing with 401. Can you check the network request?

Windsurf: Let me check the network logs...
[Uses get_network_logs with filter for /api/login]

Windsurf: I found the request:
POST /api/login
Status: 401 Unauthorized
Headers:
  Authorization: Bearer undefined

The issue is that the Authorization header is "undefined". 
Let me check where you're setting the token...

[Checks auth code]

Windsurf: Found it - you're calling setAuthToken before the token is available.
Move this call inside the .then() block after getting the token.
```

### Example 3: Debug Hydration Mismatch

**Scenario:** Hydration warnings in Next.js

**Conversation with Windsurf:**
```
You: I'm getting hydration mismatch warnings. Help me find the cause.

Windsurf: Let me check the console...
[Uses get_console_logs with level=warn]

Windsurf: I see multiple warnings:
"Text content did not match. Server: '10:30 AM' Client: '10:31 AM'"

This is caused by rendering timestamps that change between server and client.
Let me find where you're rendering timestamps...

[Searches for Date/time code]

Windsurf: Found it in Header.tsx line 12. You're rendering:
{new Date().toLocaleTimeString()}

This will always mismatch because server time ≠ client time.
Use useEffect to render time only on client, or use suppressHydrationWarning.
```

---

## 🔧 Troubleshooting

### Issue: Extension not connecting

**Symptoms:**
- Extension shows "Disconnected"
- No data in Windsurf

**Solutions:**
```bash
# 1. Verify server is running
npx @agentdeskai/browser-tools-mcp@1.2.0

# 2. Check DevTools is open
# MCP only works when DevTools is open

# 3. Reload extension
# Go to chrome://extensions/
# Find BrowserTools
# Click reload icon

# 4. Check browser console
# Open DevTools console
# Look for BrowserTools messages
```

### Issue: No console logs showing

**Cause:** Logs cleared or filter active

**Solutions:**
- Preserve logs: In DevTools Console, check "Preserve log"
- Clear filters: Remove any console level filters
- Refresh page to generate new logs

### Issue: MCP server not starting in Windsurf

**Solutions:**
```bash
# 1. Check Windsurf settings
# Verify mcp.servers.browsertools is correctly configured

# 2. Restart Windsurf
# Sometimes settings need reload

# 3. Check Node version
node --version  # Should be 18+

# 4. Try manual start
npx @agentdeskai/browser-tools-mcp@1.2.0
# If this fails, check error message
```

### Issue: "Command not found" error

**Cause:** npx not available

**Solution:**
```bash
# Update npm
npm install -g npm@latest

# Or install globally
npm install -g @agentdeskai/browser-tools-mcp
```

---

## 🎯 Best Practices

### 1. Keep DevTools Open
MCP only works when DevTools is open in the browser.

### 2. Preserve Logs
Enable "Preserve log" in DevTools Console to keep logs across page reloads.

### 3. Use Filters
When asking for logs, be specific:
- ❌ "Show me logs" (too broad)
- ✅ "Show me error logs from the last 5 minutes"

### 4. Context is King
Give Windsurf context:
- ❌ "Check network"
- ✅ "Check network requests to /api/users - they're failing with 401"

### 5. Combine with Code
Use MCP together with code analysis:
```
Check the browser console for errors, then help me fix them in UserProfile.tsx
```

### 6. Take Screenshots for Visual Issues
```
Take a screenshot showing the layout issue, then help me fix the CSS
```

---

## 🔐 Security & Privacy

**What data is accessed:**
- ✅ Console logs from current tab
- ✅ Network requests from current tab
- ✅ Screenshots of current tab
- ✅ DOM content when explicitly requested

**What data is NOT accessed:**
- ❌ Other browser tabs
- ❌ Cookies or local storage (unless explicitly queried)
- ❌ Password fields
- ❌ Incognito/private browsing data

**Best practices:**
- Only use on development sites
- Don't use on sites with sensitive data
- Review extension permissions periodically

---

## 🔄 Alternative Tools

If BrowserTools MCP doesn't work for you:

### Option 1: Built-in DevTools
- Use Chrome DevTools directly
- Copy/paste logs to Windsurf manually
- More control but less integrated

### Option 2: Console to File
```javascript
// Log to file instead
const fs = require('fs');
console.log = (...args) => {
  fs.appendFileSync('console.log', args.join(' ') + '\n');
};
```

### Option 3: Remote Debugging
```bash
# Start Chrome with remote debugging
chrome --remote-debugging-port=9222
```

---

## 📚 Further Reading

**Official Documentation:**
- [BrowserTools MCP Docs](https://browsertools.agentdesk.ai/)
- [GitHub Repository](https://github.com/AgentDeskAI/browser-tools-mcp)

**Related Resources:**
- [Model Context Protocol](https://modelcontextprotocol.io/)
- [Windsurf MCP Guide](https://docs.windsurf.ai/mcp)
- [Chrome Extension Development](https://developer.chrome.com/docs/extensions/)

---

## 🔗 Related Arsenal Items

**🔄 Workflow:**
- [Next.js Debug Workflow](https://github.com/ChrisTansey007/ai-workflows-arsenal/blob/main/windsurf/debugging/nextjs-debug-compile.md) - Systematic debugging process

**⚙️ Rule:**
- [React Error Rendering](https://github.com/ChrisTansey007/ai-rules-arsenal/blob/main/windsurf/by-framework/react-error-handling.md) - Fix common React errors

**💭 Memory:**
- [Next.js App Router Memory](../project-types/nextjs-app-router-memory.md) - Next.js development context

**🔗 Example:**
- [Next.js Debugging Example](https://github.com/ChrisTansey007/arsenal-integration-hub/tree/main/examples/nextjs-debugging) - Complete debugging setup

---

## ✅ Setup Checklist

- [ ] Node.js 18+ installed
- [ ] BrowserTools extension installed in Chrome
- [ ] Extension loaded and enabled
- [ ] MCP server configuration added to Windsurf
- [ ] Windsurf restarted
- [ ] Test page open in Chrome
- [ ] DevTools open (F12)
- [ ] Extension shows "Connected"
- [ ] Tested `get_console_logs` command
- [ ] Can capture screenshots

---

## 🎉 Success Criteria

You'll know it's working when:
- ✅ Extension shows "Connected" status
- ✅ Windsurf can read console logs
- ✅ Network requests are visible
- ✅ Screenshots can be captured
- ✅ Windsurf can analyze browser errors
- ✅ Real-time debugging works

---

**Result: Direct access to browser console from your AI assistant - debugging superpower unlocked!** 🚀

# Expert Pair Programming Assistant

An intelligent pair programming partner that combines deep technical knowledge with practical coding experience to provide real-time assistance, code review, problem-solving, and architectural guidance.

## 🎯 Overview

This assistant follows a strict memory-driven development workflow with mandatory approval gates to ensure quality, consistency, and alignment with project requirements. It specializes in modern web development with TypeScript, React, Next.js, and follows industry best practices.

## 🔄 Core Workflow

### Mandatory 5-Step Process
```
🧠 STEP 1: Context → 🔍 STEP 2: Plan → 🛑 STEP 3: Wait for Approval → ⚡ STEP 4: Implement → 🛑 STEP 5: Update Memory
```

**CRITICAL**: Never skip steps or proceed without explicit user approval.

## 🧠 Memory-Driven Development

### Project Memory (`memory.md`)
The assistant maintains project context through a living knowledge base that includes:

- **Project Name & Description**: Core purpose and functionality
- **Tech Stack**: Technologies, frameworks, and tools with versions
- **File Structure**: Comprehensive directory and file documentation
- **Theming Guidelines**: Visual design standards and tokens
- **Content Guidelines**: Voice, tone, and style rules
- **Task Progress**: Chronological implementation tracking

### Memory Initialization
1. Read existing `memory.md` for project context
2. If missing, read `codellm.txt` and create `memory.md`
3. Never proceed without established project context

## 🛠️ Required MCP Tools

### Essential MCPs for Full Functionality

#### 1. **Filesystem MCP** (Built-in)
- `list_allowed_directories` - Discover available directories
- `list_directory` - Explore project structure  
- `read_file` / `read_multiple_files` - Examine existing code
- `write_file` / `edit_file` - Create and modify files
- `search_files` - Find specific files and patterns

#### 2. **Context7 MCP**
- `resolve-library-id` - Find library documentation IDs
- `get-library-docs` - Fetch up-to-date documentation
- Essential for accessing latest library docs (React, Next.js, etc.)

#### 3. **Supabase MCP**
- `list_projects` / `get_project` - Project management
- `execute_sql` / `apply_migration` - Database operations
- `deploy_edge_function` - Serverless function deployment
- `generate_typescript_types` - Type generation
- Required for any Supabase-related development

#### 4. **Browser MCP**
- `browser_navigate` / `browser_snapshot` - Web navigation
- `browser_click` / `browser_type` - UI interaction
- `browser_screenshot` - Visual debugging
- Essential for frontend testing and debugging

#### 5. **Command Execution MCP** (Built-in)
- `execute_command` - Run build commands, tests, package installs
- `get_command_history` - Track executed commands
- `get_console_errors` - Debug runtime issues

### Optional MCPs
- **Analysis Tool (REPL)** - For complex calculations and data processing
- **Web Search** - For researching solutions and documentation

## 📋 Communication Style

### Core Principles
- **Concise and Direct**: Avoid unnecessary explanations
- **Bullet Points**: For plans and structured information
- **Approval Gates**: Always ask "Proceed?" or "Approve?" before implementation
- **Stop and Wait**: Pause for user input at key decision points

### Response Patterns
✅ **Good**: "Plan ready. Proceed?"
❌ **Bad**: "Great question! I'd be happy to help you implement this feature..."

## 🏗️ Technical Standards

### Code Style Guidelines

#### KISS (Keep It Simple, Stupid)
- Return early to reduce nesting
- Handle edge cases upfront
- Avoid unnecessary complexity

#### SSOT (Single Source of Truth)
- Centralize configuration in `config/constants.ts`
- Use shared environment variables
- Avoid duplication across the codebase

#### DRY (Don't Repeat Yourself)
- Extract reusable logic into utilities
- Create shared components for repeated UI
- Use consistent naming patterns

#### YAGNI (You Aren't Gonna Need It)
- Only implement current requirements
- Avoid premature optimization
- Build for today's needs, not hypothetical futures

### TypeScript Requirements
- **No `any` types** - Use explicit types or `unknown`
- **Named parameters** - Always pass objects, never individual parameters
- **Functional patterns** - Prefer functions over classes
- **Path aliases** - Use `@/` imports, not relative paths

### Architecture Patterns
- **File Organization**: `components/`, `config/`, `types/`, `stores/`, `hooks/`, `server-actions/`, `libs/`
- **Naming Conventions**: 
  - Directories: `kebab-case`
  - Variables/Functions: `camelCase`
  - Components: `PascalCase`
- **Data Fetching**: SWR for client-side, Server Components for SSR
- **State Management**: Zustand for client state
- **Forms**: React Hook Form + Zod validation

## 🎨 UI/UX Standards

### Design System
- **Shadcn UI** + **Tailwind CSS** for components and styling
- **Mobile-first** responsive design
- **Accessibility-first** with semantic HTML and ARIA
- **Color consistency** via `globals.css` variables

### Component Guidelines
- Use `lucide-react` for icons
- Implement loading states with `LoadingContent`
- Follow responsive breakpoints: `sm:`, `md:`, `lg:`, `xl:`, `2xl:`
- Avoid arbitrary Tailwind values

### Content & Typography
- **Headlines**: `text-4xl md:text-6xl` with bold emphasis
- **Spacing**: 4-point increments (`p-4`, `p-8`, `p-12`)
- **Hierarchy**: Size indicates importance
- **White space**: When in doubt, add space

## 🚀 Development Workflow

### Step 1: Context Gathering
1. Use `list_allowed_directories` then `list_directory`
2. Read `memory.md` for project context
3. Use `read_multiple_files` to examine related code
4. Never start without understanding the project

### Step 2: Planning & Analysis
1. **Dependency Analysis**: Check if new libraries needed
2. **Context7 Documentation**: Use `resolve-library-id` → `get-library-docs`
3. **Implementation Planning**: List files to create/modify
4. **Present Plan**: Concise bullet points
5. **🛑 MANDATORY PAUSE**: Wait for user approval

### Step 3: Implementation
1. Only proceed after explicit user approval
2. Use `edit_file` for modifications, `write_file` for new files
3. Follow all coding guidelines and TypeScript rules
4. Write clean, functional code with proper error handling

### Step 4: Post-Implementation
1. Ask for explicit approval of implementation
2. **🛑 STOP**: Wait for user input
3. If approved: Update `memory.md` with completed tasks
4. If declined: Return to Step 2 with feedback

## 🧪 Testing & Debugging

### Browser Testing
- Use Browser MCP for frontend testing
- Take screenshots for visual verification
- Check console logs for runtime errors
- Test responsive design across breakpoints

### Development Commands
```bash
# Install dependencies
npm install [package-name]

# Development server
npm run dev

# Build for production
npm run build

# Run tests
npm test

# Lint code
npm run lint
```

### Debugging Approach
1. Use `browser_get_console_logs` for frontend errors
2. Check `get_console_errors` for command execution issues
3. Use `browser_screenshot` for visual debugging
4. Examine network requests and responses

## 📁 Project Structure Template

```
project-root/
├── memory.md                 # Project context and progress tracking
├── README.md                # Project documentation
├── package.json             # Dependencies and scripts
├── next.config.js           # Next.js configuration
├── tailwind.config.js       # Tailwind CSS configuration
├── src/
│   ├── app/                 # Next.js App Router pages
│   ├── components/          # Reusable React components
│   │   └── ui/             # Shadcn UI components
│   ├── config/             # Configuration files
│   ├── hooks/              # Custom React hooks
│   ├── lib/                # Utility libraries
│   ├── stores/             # Zustand state stores
│   ├── types/              # TypeScript type definitions
│   └── utils/              # Helper functions and server actions
└── public/                 # Static assets
```

## 🔧 Configuration Files

### Essential Configurations
- `tsconfig.json` - TypeScript compiler options
- `eslint.config.js` - Code linting rules
- `prettier.config.js` - Code formatting
- `globals.css` - Design system variables
- `components.json` - Shadcn UI configuration

## 📚 Learning Resources

### Documentation Priority
1. **Context7 MCP** - Always get latest library docs
2. **Official documentation** - Framework and library docs
3. **Best practices** - Industry standards and patterns

### Key Technologies
- **Next.js 14+** - React framework with App Router
- **TypeScript** - Type-safe JavaScript
- **Tailwind CSS** - Utility-first CSS framework
- **Shadcn UI** - Component library
- **SWR** - Data fetching library
- **Zustand** - State management
- **React Hook Form** - Form handling
- **Zod** - Schema validation

## 🚨 Critical Rules

### Never Do
- Skip the mandatory 5-step workflow
- Proceed without user approval
- Use `any` types in TypeScript
- Write classes instead of functions
- Use relative imports instead of path aliases
- Implement features without current need (YAGNI)

### Always Do
- Read `memory.md` before starting any task
- Wait for explicit approval at decision points
- Use named parameters for all functions
- Follow mobile-first responsive design
- Update `memory.md` after completing tasks
- Maintain code consistency with existing patterns

## 🎯 Success Metrics

- **Code Quality**: Clean, readable, maintainable code
- **Consistency**: Follows established patterns and conventions
- **Performance**: Optimized and efficient implementations
- **User Experience**: Responsive, accessible, and intuitive interfaces
- **Documentation**: Up-to-date project memory and clear code comments

---

# MCP Installation Guide
## Expert Pair Programming Assistant

This guide provides step-by-step instructions for installing all Model Context Protocol (MCP) tools required for the Expert Pair Programming Assistant to function at full capacity.

## 🎯 Prerequisites

- **Claude Desktop Application** installed
- **Node.js 18+** installed on your system
- **npm** or **yarn** package manager
- **Git** for cloning repositories
- Basic terminal/command line knowledge

## 📋 Required MCP Tools Overview

| MCP Tool | Purpose | Installation Method | Required |
|----------|---------|-------------------|----------|
| Filesystem | File operations & project exploration | Built-in | ✅ Essential |
| Context7 | Latest library documentation | npm install | ✅ Essential |
| Supabase | Database & project management | npm install | ✅ Essential* |
| Browser | Frontend testing & debugging | npm install | ✅ Essential |
| Command Execution | Build commands & scripts | Built-in | ✅ Essential |
| Analysis Tool (REPL) | Complex calculations | Built-in | 🔶 Optional |
| Web Search | Research & documentation | Built-in | 🔶 Optional |

*Required if using Supabase in your projects

## 🚀 Installation Instructions

### Step 1: Access Claude Desktop MCP Settings

1. Open **Claude Desktop**
2. Click on your profile/settings (usually in top-right corner)
3. Navigate to **"Developer"** or **"MCP Settings"**
4. Look for **"Model Context Protocol"** configuration

### Step 2: Configure Built-in MCPs

The following MCPs are built into Claude Desktop and should be enabled by default:

#### ✅ Filesystem MCP
- **Status**: Built-in and enabled
- **Functions**: `read_file`, `write_file`, `list_directory`, `search_files`
- **No installation required**

#### ✅ Command Execution MCP  
- **Status**: Built-in and enabled
- **Functions**: `execute_command`, `get_command_history`
- **No installation required**

#### ✅ Analysis Tool (REPL)
- **Status**: Built-in and enabled
- **Functions**: JavaScript execution environment
- **No installation required**

#### ✅ Web Search
- **Status**: Built-in and enabled  
- **Functions**: `web_search`, `web_fetch`
- **No installation required**

### Step 3: Install External MCPs

#### 🔧 Context7 MCP

**Purpose**: Access latest library documentation

```bash
# Install Context7 MCP server
npm install -g @context7/mcp-server

# Or using yarn
yarn global add @context7/mcp-server
```

**Configuration in Claude Desktop:**
```json
{
  "context7": {
    "command": "npx",
    "args": ["@context7/mcp-server"],
    "env": {}
  }
}
```

#### 🗄️ Supabase MCP

**Purpose**: Database operations and project management

```bash
# Install Supabase MCP server
npm install -g @supabase/mcp-server

# Or using yarn
yarn global add @supabase/mcp-server
```

**Configuration in Claude Desktop:**
```json
{
  "supabase": {
    "command": "npx",
    "args": ["@supabase/mcp-server"],
    "env": {
      "SUPABASE_ACCESS_TOKEN": "your_supabase_access_token"
    }
  }
}
```

**Setup Supabase Access Token:**
1. Go to [Supabase Dashboard](https://supabase.com/dashboard)
2. Navigate to **Settings** → **Access Tokens**
3. Create a new token with appropriate permissions
4. Add token to your environment variables

#### 🌐 Browser MCP

**Purpose**: Frontend testing and web automation

```bash
# Install Browser MCP server (using Playwright)
npm install -g @browser/mcp-server

# Or using yarn
yarn global add @browser/mcp-server
```

**Configuration in Claude Desktop:**
```json
{
  "browser": {
    "command": "npx",
    "args": ["@browser/mcp-server"],
    "env": {}
  }
}
```

**Install Browser Dependencies:**
```bash
# Install Playwright browsers
npx playwright install

# Install Chromium specifically
npx playwright install chromium
```

### Step 4: Complete MCP Configuration

Your final Claude Desktop MCP configuration should look like this:

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["@context7/mcp-server"],
      "env": {}
    },
    "supabase": {
      "command": "npx", 
      "args": ["@supabase/mcp-server"],
      "env": {
        "SUPABASE_ACCESS_TOKEN": "your_supabase_access_token"
      }
    },
    "browser": {
      "command": "npx",
      "args": ["@browser/mcp-server"],
      "env": {}
    }
  }
}
```

## 🔧 Environment Setup

### Required Environment Variables

Create a `.env` file or add to your system environment:

```bash
# Supabase Configuration
SUPABASE_ACCESS_TOKEN=your_supabase_access_token
SUPABASE_PROJECT_REF=your_project_reference

# Optional: Browser Configuration
BROWSER_HEADLESS=true
BROWSER_SLOWMO=100
```

### System Requirements

- **Memory**: 8GB+ RAM recommended
- **Storage**: 2GB+ free space for browser dependencies
- **Network**: Stable internet connection for documentation fetching
- **OS**: Windows 10+, macOS 10.15+, or Linux

## ✅ Verification & Testing

### Step 1: Restart Claude Desktop
1. Close Claude Desktop completely
2. Restart the application
3. Wait for MCP tools to initialize

### Step 2: Test Built-in MCPs

Ask Claude to test built-in functionality:

```
Can you list the current directory and show me the available MCP tools?
```

### Step 3: Test External MCPs

#### Test Context7:
```
Search for React documentation using Context7
```

#### Test Supabase:
```
List my Supabase projects
```

#### Test Browser:
```
Take a screenshot of google.com
```

### Step 4: Verify Expert Assistant Workflow

Test the complete workflow:

```
I want to create a new React component. Follow your standard workflow process.
```

Expected response: Assistant should read memory.md, analyze context, create a plan, and wait for approval.

## 🚨 Troubleshooting

### Common Issues & Solutions

#### MCP Server Not Found
```bash
# Reinstall globally
npm uninstall -g @context7/mcp-server
npm install -g @context7/mcp-server

# Clear npm cache
npm cache clean --force
```

#### Permission Errors
```bash
# Fix npm permissions (Unix/macOS)
sudo chown -R $(whoami) ~/.npm

# Or use yarn instead
yarn global add @context7/mcp-server
```

#### Supabase Authentication Failed
1. Verify your access token is valid
2. Check token permissions in Supabase dashboard
3. Ensure token is correctly set in environment variables

#### Browser MCP Issues
```bash
# Reinstall Playwright
npm uninstall -g @browser/mcp-server
npm install -g @browser/mcp-server
npx playwright install --force
```

#### Claude Desktop Not Recognizing MCPs
1. Check MCP configuration JSON syntax
2. Restart Claude Desktop
3. Check system logs for error messages
4. Verify all npm packages are installed globally

### Debug Commands

```bash
# Check global npm packages
npm list -g --depth=0

# Test MCP servers manually
npx @context7/mcp-server --help
npx @supabase/mcp-server --help
npx @browser/mcp-server --help

# Check Claude Desktop logs (location varies by OS)
# macOS: ~/Library/Logs/Claude/
# Windows: %APPDATA%/Claude/logs/
# Linux: ~/.local/share/Claude/logs/
```

## 🔄 Updates & Maintenance

### Regular Updates
```bash
# Update all MCP servers
npm update -g @context7/mcp-server
npm update -g @supabase/mcp-server  
npm update -g @browser/mcp-server

# Update browser dependencies
npx playwright install
```

### Monthly Maintenance
- Review and update Supabase access tokens
- Clear browser cache and temporary files
- Update Claude Desktop to latest version
- Test all MCP functionality

## 📚 Additional Resources

### Documentation Links
- [MCP Specification](https://spec.modelcontextprotocol.io/)
- [Claude Desktop MCP Guide](https://docs.anthropic.com/en/docs/build-with-claude/mcp)
- [Context7 Documentation](https://context7.com/docs)
- [Supabase MCP Documentation](https://supabase.com/docs/mcp)
- [Playwright Documentation](https://playwright.dev/docs)

### Community Support
- [MCP Community Discord](https://discord.gg/mcp)
- [Claude Developer Forums](https://community.anthropic.com/)
- [GitHub Issues for specific MCP servers](https://github.com/search?q=mcp-server)

## ✨ Success Indicators

You'll know the installation is successful when:

✅ Claude can read and modify files in your project
✅ Claude can fetch latest library documentation via Context7
✅ Claude can manage Supabase projects and databases
✅ Claude can navigate websites and take screenshots
✅ Claude follows the 5-step workflow with memory management
✅ All MCP tools respond without errors

---

**Note**: Some MCP servers may have different installation methods or package names. Always check the official documentation for the most up-to-date installation instructions.

**Remember**: This assistant is designed to be your collaborative partner, not just a code generator. It maintains project context, follows best practices, and ensures every implementation aligns with your project's goals and standards.

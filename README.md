# Copilot CLI Bundle

> **Autonomous AI-Powered Development Assistant**

A fully self-optimizing, ML-powered multi-agent system that analyzes repositories, generates custom agents/skills/workflows, and provides intelligent development assistance.

[![Version](https://img.shields.io/badge/version-1.0.0-blue.svg)](package.json)
[![Node](https://img.shields.io/badge/node-%3E%3D18.0.0-green.svg)](package.json)
[![License](https://img.shields.io/badge/license-MIT-purple.svg)](LICENSE)

---

## 🚀 Quick Start

```bash
# Install globally
npm install -g copilot-cli-bundle

# Or run directly with npx
npx copilot-cli-bundle init

# Initialize in your project
cd your-project
copilot init

# Start interactive mode
copilot chat
```

---

## ✨ Features

### 🤖 Multi-Agent System
- **5 Specialized Agents**: Code Analyzer, Refactorer, Test Generator, Documenter, Security Scanner
- **ML-Powered Selection**: Q-learning optimizes agent selection over time
- **Memory System**: Short-term, long-term, working, episodic, and semantic memory
- **Inter-Agent Communication**: Message routing and coordination

### 🛠️ Skill Library (40+ Skills)
- **File System**: read, write, list, find, copy, delete
- **Code Manipulation**: parse AST, transform, format, minify, generate
- **Git Operations**: status, log, diff, commit, branch
- **Text Processing**: search, replace, extract, parse JSON
- **Data Transformation**: map, filter, group, sort, aggregate
- **Shell Execution**: run commands, npm operations

### 🔄 Workflow Engine
- **DAG Execution**: Parallel and sequential step execution
- **Control Flow**: Conditions, loops, branches
- **Built-in Templates**: Code review, test generation, security audit
- **Error Handling**: Retries, fallbacks, error recovery

### 🔌 MCP Server Integration
- **5 Built-in Servers**: Filesystem, Git, Shell, Analysis, Memory
- **Standard Protocol**: Model Context Protocol compliance
- **Extensible**: Easy to add custom servers

### 📊 Repository Analysis
- **Deep Analysis**: 10-phase comprehensive scanning
- **Language Detection**: 11+ programming languages
- **Framework Detection**: 50+ frameworks
- **Security Scanning**: Vulnerability and secret detection
- **Complexity Analysis**: Cyclomatic complexity, hotspots

### 🧠 Machine Learning
- **Q-Learning**: Agent selection optimization
- **Pattern Recognition**: Learn from past experiences
- **Experience Replay**: Buffer-based learning
- **Auto-Save**: Persistent model storage

---

## 📖 Table of Contents

1. [Installation](#installation)
2. [CLI Commands](#cli-commands)
3. [Agent System](#agent-system)
4. [Skills Library](#skills-library)
5. [Workflow Engine](#workflow-engine)
6. [MCP Servers](#mcp-servers)
7. [Repository Analysis](#repository-analysis)
8. [Configuration](#configuration)
9. [Extending the System](#extending-the-system)
10. [API Reference](#api-reference)
11. [Examples](#examples)
12. [Troubleshooting](#troubleshooting)

---

## 📦 Installation

### Global Installation

```bash
npm install -g copilot-cli-bundle
```

### Project Installation

```bash
npm install --save-dev copilot-cli-bundle
```

### Direct Usage

```bash
npx copilot-cli-bundle <command>
```

### Requirements

- Node.js >= 18.0.0
- npm >= 8.0.0

---

## 🖥️ CLI Commands

### Initialization

```bash
# Full initialization with analysis
copilot init

# Quick initialization
copilot init --quick

# With specific options
copilot init --skip-deps --deep
```

### Analysis

```bash
# Analyze repository
copilot analyze

# Generate audit report
copilot audit

# Show analysis summary
copilot status
```

### Code Operations

```bash
# Code review
copilot review src/index.js
copilot review --all src/

# Generate tests
copilot test src/utils.js
copilot test --coverage

# Generate documentation
copilot docs
copilot docs src/api.js

# Security scan
copilot security
copilot security src/auth.js

# Suggest refactorings
copilot refactor src/complex.js
```

### Workflows

```bash
# List workflows
copilot workflows

# Run workflow
copilot run code-review
copilot run security-audit --context '{"rootDir": "src"}'

# Create custom workflow
copilot workflow create my-workflow
```

### Agents & Skills

```bash
# List agents
copilot agents

# List skills
copilot skills
copilot skills --category code

# Execute specific skill
copilot skill analyze-complexity --file src/index.js
```

### Interactive Mode

```bash
# Start interactive chat
copilot chat

# With specific agent
copilot chat --agent code-analyzer
```

---

## 🤖 Agent System

### Available Agents

| Agent | Type | Skills | Purpose |
|-------|------|--------|---------|
| CodeAnalyzer | analyzer | 5 | Structure, complexity, code smells |
| Refactorer | refactorer | 5 | Extract, rename, simplify, convert |
| TestGenerator | tester | 3 | Unit tests, coverage, fixtures |
| Documenter | documenter | 3 | JSDoc, README, API docs |
| SecurityScanner | security | 3 | Vulnerabilities, secrets, deps |

### Agent Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                      ORCHESTRATOR                            │
│  ┌─────────────────────────────────────────────────────────┐│
│  │ Task Queue │ Agent Selection (ML) │ Load Balancing     ││
│  └─────────────────────────────────────────────────────────┘│
└───────────────────────────┬─────────────────────────────────┘
                            │
          ┌─────────────────┼─────────────────┐
          │                 │                 │
          ▼                 ▼                 ▼
   ┌───────────┐     ┌───────────┐     ┌───────────┐
   │  Agent 1  │     │  Agent 2  │     │  Agent N  │
   │  ─────────│     │  ─────────│     │  ─────────│
   │  Memory   │     │  Memory   │     │  Memory   │
   │  Skills   │     │  Skills   │     │  Skills   │
   │  ML Hook  │     │  ML Hook  │     │  ML Hook  │
   └───────────┘     └───────────┘     └───────────┘
```

### Using Agents Programmatically

```javascript
const { CopilotCLI } = require('copilot-cli-bundle');

const copilot = new CopilotCLI();
await copilot.initialize();

// Execute a skill on specific agent
const result = await copilot.agents.codeAnalyzer.executeSkill(
  'analyze-complexity',
  { filePath: 'src/index.js' }
);

// Let orchestrator choose best agent
const taskResult = await copilot.orchestrator.executeTask({
  skill: 'find-code-smells',
  params: { filePath: 'src/complex.js' }
});
```

---

## 🛠️ Skills Library

### File System Skills

| Skill | Description |
|-------|-------------|
| `read-file` | Read file contents |
| `write-file` | Write content to file |
| `list-directory` | List directory contents |
| `find-files` | Find files matching pattern |
| `copy-file` | Copy file to destination |
| `delete-file` | Delete a file |

### Code Manipulation Skills

| Skill | Description |
|-------|-------------|
| `parse-ast` | Parse code to AST |
| `transform-code` | Apply code transformations |
| `format-code` | Format code style |
| `minify-code` | Minify code |
| `generate-code` | Generate code from template |

### Git Skills

| Skill | Description |
|-------|-------------|
| `git-status` | Get repository status |
| `git-log` | Get commit history |
| `git-diff` | Get file differences |
| `git-commit` | Create a commit |
| `git-branch` | Manage branches |

### Analysis Skills

| Skill | Description |
|-------|-------------|
| `analyze-structure` | Analyze file/directory structure |
| `analyze-complexity` | Calculate complexity metrics |
| `find-code-smells` | Detect anti-patterns |
| `analyze-dependencies` | Map import/export relationships |
| `generate-metrics-report` | Generate comprehensive report |

### Creating Custom Skills

```javascript
const { Skill, SkillRegistry } = require('copilot-cli-bundle/agents/core');

const mySkill = new Skill({
  name: 'my-custom-skill',
  description: 'Does something useful',
  category: 'custom',
  tags: ['example'],
  inputSchema: {
    input: { type: 'string', required: true }
  },
  handler: async ({ input }) => {
    // Your implementation
    return { result: processedResult };
  }
});

skillRegistry.register(mySkill);
```

---

## 🔄 Workflow Engine

### Built-in Workflows

| Workflow | Description | Steps |
|----------|-------------|-------|
| `code-review` | Automated code review | 6 |
| `test-generation` | Generate tests | 3 |
| `documentation-generation` | Generate docs | 4 |
| `refactoring` | Suggest refactorings | 5 |
| `security-audit` | Security analysis | 3 |
| `project-setup` | Initialize project | 4 |
| `cicd-pipeline` | Generate CI/CD config | 3 |

### Workflow Structure

```javascript
{
  id: 'my-workflow',
  name: 'My Workflow',
  description: 'Does something complex',
  steps: [
    {
      id: 'step1',
      type: 'skill',
      skill: 'read-file',
      params: { path: '$input.filePath' },
      output: 'fileContent'
    },
    {
      id: 'step2',
      type: 'skill',
      skill: 'analyze-complexity',
      params: { code: '$fileContent' },
      dependencies: ['step1']
    }
  ]
}
```

### Using WorkflowBuilder

```javascript
const { WorkflowBuilder } = require('copilot-cli-bundle/workflows/engine');

const workflow = new WorkflowBuilder('My Workflow')
  .description('Complex multi-step automation')
  .skill('read-file', { path: '$input.filePath' }, { output: 'content' })
  .skill('analyze-complexity', { code: '$content' }, { output: 'metrics' })
  .transform('$metrics', [
    { type: 'filter', condition: 'item.complexity > 10' }
  ], { output: 'highComplexity' })
  .build();
```

---

## 🔌 MCP Servers

### Built-in Servers

| Server | Tools | Description |
|--------|-------|-------------|
| `filesystem` | 5 | File operations |
| `git` | 4 | Git operations |
| `shell` | 2 | Shell commands |
| `analysis` | 3 | Code analysis |
| `memory` | 5 | Key-value storage |

### Creating Custom MCP Server

```javascript
const { MCPServer } = require('copilot-cli-bundle/mcp-servers');

const myServer = new MCPServer({
  name: 'my-server',
  description: 'Custom functionality'
});

myServer.registerTool({
  name: 'my_tool',
  description: 'Does something',
  inputSchema: {
    type: 'object',
    properties: {
      param: { type: 'string' }
    }
  },
  handler: async ({ param }) => {
    return { result: 'done' };
  }
});

await myServer.start();
```

---

## 📊 Repository Analysis

### Analysis Phases

1. **Structure Analysis** - Files, directories, sizes
2. **Language Detection** - Primary language, distribution
3. **Framework Detection** - Libraries and frameworks
4. **Dependency Analysis** - Package dependencies
5. **Pattern Analysis** - Architecture, design patterns
6. **Complexity Analysis** - Code complexity metrics
7. **Security Scan** - Vulnerabilities, secrets
8. **Testing Analysis** - Test coverage, frameworks
9. **Documentation Analysis** - README, inline docs
10. **Recommendations** - Improvement suggestions

### Analysis Output

```json
{
  "meta": {
    "projectName": "my-project",
    "primaryLanguage": "javascript",
    "analyzedAt": "2025-01-30T..."
  },
  "structure": {
    "totalFiles": 150,
    "totalLines": 25000,
    "totalSize": 2500000
  },
  "languages": {
    "javascript": 120,
    "typescript": 20,
    "json": 10
  },
  "frameworks": [
    { "name": "React", "type": "frontend" },
    { "name": "Express.js", "type": "backend" }
  ],
  "security": {
    "score": 85,
    "issues": [],
    "secrets": []
  },
  "recommendations": [
    {
      "title": "Add test coverage",
      "priority": "high",
      "description": "..."
    }
  ]
}
```

---

## ⚙️ Configuration

### Configuration File (`.copilot/config.json`)

```json
{
  "version": "1.0.0",
  "maxConcurrentTasks": 10,
  "autoAnalyze": true,
  "mlEnabled": true,
  "loggingLevel": "info",
  "agents": {
    "codeAnalyzer": { "enabled": true },
    "refactorer": { "enabled": true },
    "testGenerator": { "enabled": true },
    "documenter": { "enabled": true },
    "securityScanner": { "enabled": true }
  },
  "mcp": {
    "filesystem": { "enabled": true, "autoStart": true },
    "git": { "enabled": true, "autoStart": true },
    "shell": { "enabled": true, "autoStart": false }
  }
}
```

### Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `COPILOT_CONFIG_DIR` | Config directory | `.copilot` |
| `COPILOT_LOG_LEVEL` | Log level | `info` |
| `COPILOT_ML_ENABLED` | Enable ML | `true` |
| `DEBUG` | Debug mode | `false` |

---

## 🔧 Extending the System

### Adding a Custom Agent

```javascript
const { Agent, Skill } = require('copilot-cli-bundle/agents/core');

class MyCustomAgent extends Agent {
  constructor(config = {}) {
    super({
      ...config,
      name: 'MyCustomAgent',
      type: 'custom',
      description: 'My custom agent'
    });
    
    this.registerSkill(new Skill({
      name: 'custom-operation',
      handler: async (params) => {
        // Implementation
        return { result: 'done' };
      }
    }));
  }
}

// Register with orchestrator
copilot.orchestrator.registerAgent(new MyCustomAgent());
```

### Adding a Custom Workflow

```javascript
const { WorkflowBuilder } = require('copilot-cli-bundle/workflows/engine');

const customWorkflow = new WorkflowBuilder('Custom Workflow')
  .skill('step1', 'read-file', { path: '$input.path' })
  .skill('step2', 'transform-code', { code: '$step1' })
  .build();

copilot.workflowEngine.register(customWorkflow);
```

---

## 📚 API Reference

### CopilotCLI

```javascript
const copilot = new CopilotCLI(rootDir);

// Lifecycle
await copilot.initialize();
await copilot.shutdown();

// Analysis
await copilot.analyzeRepository();

// Commands
await copilot.executeCommand('review', ['src/index.js']);

// Properties
copilot.orchestrator    // AgentOrchestrator
copilot.workflowEngine  // WorkflowEngine
copilot.mcpManager      // MCPServerManager
copilot.skillRegistry   // SkillRegistry
copilot.agents          // { codeAnalyzer, refactorer, ... }
```

### AgentOrchestrator

```javascript
// Task execution
const result = await orchestrator.executeTask({
  skill: 'analyze-complexity',
  params: { filePath: 'src/index.js' },
  agentId: 'code-analyzer' // optional
});

// Agent management
orchestrator.registerAgent(agent);
const agents = orchestrator.getAgentsByCapability('analyze-complexity');

// Stats
const stats = orchestrator.getStats();
```

### WorkflowEngine

```javascript
// Registration
engine.register(workflow);

// Execution
const result = await engine.execute('workflow-id', context);

// Control
engine.cancel(runId);
const status = engine.getStatus(runId);
```

---

## 💡 Examples

### Example 1: Automated Code Review

```javascript
const { CopilotCLI } = require('copilot-cli-bundle');

async function reviewCode() {
  const copilot = new CopilotCLI();
  await copilot.initialize();
  
  const result = await copilot.workflowEngine.execute('code-review', {
    rootDir: process.cwd(),
    targetFile: 'src/index.js'
  });
  
  console.log('Review Results:', result);
}
```

### Example 2: Generate Tests for Untested Files

```javascript
async function generateMissingTests() {
  const copilot = new CopilotCLI();
  await copilot.initialize();
  
  // Get coverage analysis
  const coverage = await copilot.agents.testGenerator.executeSkill(
    'analyze-coverage',
    { rootDir: process.cwd() }
  );
  
  // Generate tests for untested files
  for (const file of coverage.result.untested.slice(0, 5)) {
    await copilot.agents.testGenerator.executeSkill(
      'generate-unit-tests',
      { filePath: file, framework: 'jest' }
    );
  }
}
```

### Example 3: Security Audit with Report

```javascript
async function securityAudit() {
  const copilot = new CopilotCLI();
  await copilot.initialize();
  
  const result = await copilot.workflowEngine.execute('security-audit', {
    rootDir: process.cwd()
  });
  
  if (result.results['check-secrets'].count > 0) {
    console.error('⚠️ Secrets detected in code!');
    process.exit(1);
  }
}
```

---

## 🔍 Troubleshooting

### Common Issues

#### "Agent not found"

```bash
# Ensure agents are initialized
copilot status

# Re-initialize
copilot init --force
```

#### "Skill execution timeout"

```javascript
// Increase timeout in config
{
  "skills": {
    "defaultTimeout": 60000
  }
}
```

#### "ML model not loading"

```bash
# Clear model cache
rm -rf .copilot/models

# Re-initialize
copilot init
```

### Debug Mode

```bash
# Enable debug logging
DEBUG=true copilot analyze

# Verbose output
copilot --verbose analyze
```

---

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

---

## 🤝 Contributing

Contributions welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) first.

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/user/copilot-cli-bundle/issues)
- **Discussions**: [GitHub Discussions](https://github.com/user/copilot-cli-bundle/discussions)

---

*Built with ❤️ by the Copilot CLI Bundle team*

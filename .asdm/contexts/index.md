# Workspace Context Index

## Overview

This document serves as the index and guide for AI models to understand and work with this workspace. It provides a structured overview of the workspace content and guides AI models to find relevant context.

## Workspace Information

### Basic Information
- **Workspace Name**: asdm-core-assets-mcp
- **Description**: Core asset repository for the ASDM (AI-First System Development Methodology) platform. Hosts reusable skills, specs, toolsets, and MCP server definitions consumed by AI coding assistants and the ASDM Platform (platform.asdm.ai).
- **Created Date**: 2025
- **Last Updated**: 2026-05-11

### Technology Stack
- **Primary Languages**: TypeScript (tools), Python (skill scripts), Shell/Bash (CRUD generators, CI)
- **Runtime**: Node.js >= 18 (CI uses Node 20)
- **Build Tools**: TypeScript compiler (`tsc`), npm
- **Frameworks Referenced by Skills**: Go Gin + GORM, .NET 8.0 + EF Core, Java 17+ Spring Boot 3 + JPA, Python FastAPI + SQLAlchemy
- **AI/Tooling**: CodeBuddy (`@tencent-ai/codebuddy-code`), Model Context Protocol (MCP)
- **Document Processing**: pypdf, pdfplumber, reportlab, pytesseract (PDF); PptxGenJS, Playwright, Sharp, markitdown (PPTX)
- **CI/CD**: GitHub Actions
- **Kubernetes**: kubectl, Helm v3 (via MCP server)

### Business Context
- **Business Domain**: AI-First Software Development Methodology (ASDM) - providing reusable development assets for AI-assisted software engineering
- **Key Business Processes**:
  1. **Asset Management** - Register, package, and distribute skills, specs, toolsets, and MCP servers
  2. **Workspace Execution** - Run AI coding tasks on target repositories via GitHub Actions + CodeBuddy
  3. **Context Generation** - Analyze external repositories and generate context spaces for AI consumption
  4. **CRUD Code Generation** - Scaffold CRUD boilerplate for Java Spring Boot, .NET, Go, and Python FastAPI
  5. **Document Processing** - PDF manipulation and PowerPoint generation via skill packages
- **Business Rules**:
  - All code, docs, and embedded content must use English for internationalization (see `.codebuddy/rules/project-rules.mdc`)
  - Assets are registered in JSON registry files under `asdm-core-assets/` and must follow the registry schema
  - CI workflows automatically package and upload assets on push to main

## Workspace Structure

### File Tree with Guidance
```
asdm-core-assets-mcp/                         # Root - ASDM Core Asset Repository
├── .asdm/                                     # ASDM runtime configuration
│   ├── contexts/                              # [GENERATED] Context files for AI model reference
│   ├── toolsets/context-builder-7/            # Installed Context Builder toolset (v7)
│   │   ├── actions/                           # Slash command instructions
│   │   │   ├── asdm-context-build.md          #   -> Build workspace context
│   │   │   ├── asdm-context-update.md         #   -> Update workspace context
│   │   │   └── asdm-ddl-context-analysis.md   #   -> DDL-based context analysis
│   │   └── specs/                             # Context templates (architecture, api, data-models, etc.)
│   └── workspace-install.json                 # Workspace installation metadata
├── .codebuddy/                                # CodeBuddy AI assistant configuration
│   ├── commands/                              # Slash commands (8 registered)
│   │   ├── asdm-context-build.md              #   -> Context build command
│   │   ├── asdm-context-update.md             #   -> Context update command
│   │   ├── asdm-ddl-context-analysis.md       #   -> DDL analysis command
│   │   ├── asdm-git-message.md                #   -> Git commit message helper
│   │   ├── asdm-import-mcp.md                 #   -> Import MCP server
│   │   ├── asdm-import-skill.md               #   -> Import skill
│   │   ├── asdm-import-specs.md               #   -> Import specs
│   │   └── summarize.md                       #   -> Summarize content
│   └── rules/project-rules.mdc                # Always-applied rule: English-only content
├── .github/                                   # GitHub configuration
│   ├── prompts/                               # GitHub Copilot prompt files (3 registered)
│   └── workflows/                             # GitHub Actions CI/CD (7 workflows)
│       ├── asdm-workspace-execution.yml       #   -> Execute CodeBuddy AI tasks on target repos
│       ├── asdm-context-space-sync.yml        #   -> Clone, analyze, generate context from repos
│       ├── asdm-workspace-init-pipeline.yml   #   -> Initialize ASDM workspace
│       ├── skill-package.yml                  #   -> Package skills on push (skills/** paths)
│       ├── specs-package.yml                  #   -> Package specs on push (specs/** paths)
│       ├── mcp-package.yml                    #   -> Package MCPs on push (mcps/** paths)
│       └── toolsets-package.yml               #   -> Package toolsets on push (toolsets/** paths)
├── asdm-core-assets/                          # **Core Asset Repository**
│   ├── skills/                                # AI-assisted skill packages (7 registered)
│   │   ├── skills-registry.json               #   -> Skill metadata registry
│   │   ├── pdf-official/                      #   -> PDF manipulation (extract, create, OCR, forms)
│   │   ├── pptx/                              #   -> PowerPoint create/edit (HTML-to-PPTX, OOXML)
│   │   ├── java-springboot-crud/              #   -> Java Spring Boot CRUD generator
│   │   ├── dotnet-crud/                       #   -> .NET CRUD generator
│   │   ├── go-crud/                           #   -> Go CRUD generator
│   │   ├── python-fastapi-crud/               #   -> Python FastAPI CRUD generator (registered, no files)
│   │   ├── sql-ddl/                           #   -> SQL DDL skill (registered, no files)
│   │   └── report-development/               #   -> Report development (registered, no files)
│   ├── specs/                                 # Coding standards and best practices (13 registered)
│   │   ├── specs-registry.json                #   -> Spec metadata registry
│   │   ├── reactjs/                           #   -> React.js coding standards
│   │   ├── nextjs-react-tailwind/             #   -> Next.js + React + Tailwind conventions
│   │   ├── vue3-composition-api/              #   -> Vue 3 Composition API guidelines
│   │   ├── typescript-vite-vue-tailwind-daisyui/ # -> TypeScript + Vite + Vue + Tailwind + DaisyUI
│   │   ├── typescript/                        #   -> TypeScript coding standards
│   │   ├── javascript/                        #   -> JavaScript coding standards
│   │   ├── css/                               #   -> CSS standards
│   │   ├── html/                              #   -> HTML standards
│   │   ├── node/                              #   -> Node.js standards
│   │   ├── java-general/                      #   -> General Java standards
│   │   ├── java-springboot-jpa/               #   -> Java Spring Boot JPA standards
│   │   ├── playwright-e2e-testing/            #   -> Playwright E2E testing
│   │   ├── playwright-integration-testing/    #   -> Playwright integration testing
│   │   └── playwright-accessibility-testing/  #   -> Playwright accessibility testing
│   ├── toolsets/                              # Reusable AI development toolkits (5 registered)
│   │   ├── toolsets-registry.json             #   -> Toolset metadata registry
│   │   ├── basic-tools/                       #   -> Basic development tools
│   │   ├── context-builder/                   #   -> Context builder for workspaces
│   │   ├── prd-builder/                       #   -> PRD (Product Requirements Doc) builder
│   │   ├── prototype-builder/                 #   -> Prototype builder with tools
│   │   └── sample-toolset/                    #   -> Sample toolset template
│   ├── mcps/                                  # Model Context Protocol servers (1 registered)
│   │   ├── mcps-registry.json                 #   -> MCP metadata registry
│   │   └── kubernetes-mcp-server/             #   -> K8s MCP server (22 tools, Helm v3)
│   └── contexts/                              # Context spaces (currently empty)
│       └── contexts-registry.json             #   -> Context metadata registry
└── tools/                                     # Utility tools
    └── codebuddy-log-parser/                  # TypeScript CLI for parsing CodeBuddy logs
        ├── package.json                       #   -> Node.js package config
        ├── tsconfig.json                      #   -> TypeScript compiler config
        └── src/                               #   -> Source code
            ├── index.ts                       #   -> CLI entry point (batch + streaming modes)
            ├── parser.ts                      #   -> Log parsing (10 entry types)
            ├── formatter.ts                   #   -> Output formatting (text, JSON, human-chat)
            └── types.ts                       #   -> TypeScript type definitions
```

### Key Directories Explanation
- **`.asdm/contexts/`**: Contains all context files for AI model reference - this is where generated context lives
- **`asdm-core-assets/skills/`**: Skill packages with SKILL.md guides and scripts - extend AI capabilities for specific tasks
- **`asdm-core-assets/specs/`**: Coding standard documents for various tech stacks - inject into AI context for standards compliance
- **`asdm-core-assets/toolsets/`**: Reusable AI development toolkits with slash commands and specs
- **`asdm-core-assets/mcps/`**: MCP server definitions providing external tool integrations
- **`tools/codebuddy-log-parser/`**: The only compiled TypeScript tool - parses CodeBuddy session logs in CI pipelines
- **`.github/workflows/`**: CI/CD automation for asset packaging and workspace execution

## Development Guidelines

### Building and Compilation
```bash
# Build the log parser tool (only compilable component)
cd tools/codebuddy-log-parser
npm install
npm run build       # Compile TypeScript to dist/

# Development mode
npm run dev         # Run via ts-node

# Production
npm start           # Run node dist/index.js
```

### Testing
No automated test suite is configured. The log parser can be tested manually:
```bash
cd tools/codebuddy-log-parser
npm run dev -- --input log.txt --format text
npm run dev -- --input log.txt --format json
npm run dev -- --input log.txt --format human-chat
```

### Code Quality
- **TypeScript**: Strict mode enabled (`tsconfig.json` strict: true)
- **Project Rule**: All content must use English for internationalization

### CI/CD Workflows
- **Asset Packaging**: Automatically triggered on push/PR to `main` when paths match `skills/**`, `specs/**`, `mcps/**`, or `toolsets/**`
- **Workspace Execution**: Manually triggered via `workflow_dispatch` - runs CodeBuddy AI tasks on a target repository
- **Context Sync**: Manually triggered - clones an external repo, analyzes it with CodeBuddy, generates context space artifacts

## Context Files Reference

This workspace has the following context files available in `.asdm/contexts/`:

1. **[standard-project-structure.md](./standard-project-structure.md)** - Standard project structure and organization
2. **[standard-coding-style.md](./standard-coding-style.md)** - Coding standards and style guidelines
3. **[data-models.md](./data-models.md)** - Data models, relationships, and diagrams
4. **[deployment.md](./deployment.md)** - Deployment configuration and processes
5. **[api.md](./api.md)** - API definitions, endpoints, and documentation
6. **[architecture.md](./architecture.md)** - System architecture and design decisions

## AI Model Guidance

### How to Use This Context
1. **Start with this index** to understand the workspace structure
2. **Refer to specific context files** based on the task at hand
3. **Follow the development guidelines** for building, testing, and deployment
4. **Maintain consistency** with existing patterns and conventions

### Common Tasks
- **Adding a new skill**: Create directory under `asdm-core-assets/skills/`, add SKILL.md and scripts, register in `skills-registry.json`
- **Adding a new spec**: Create directory under `asdm-core-assets/specs/`, add markdown docs, register in `specs-registry.json`
- **Adding a new toolset**: Create directory under `asdm-core-assets/toolsets/`, add INSTALL.md, README.md, actions/, specs/, register in `toolsets-registry.json`
- **Adding a new MCP server**: Create directory under `asdm-core-assets/mcps/`, add config.json with tool definitions, register in `mcps-registry.json`
- **Modifying CI workflows**: Edit files under `.github/workflows/` - be careful with YAML syntax
- **Working on log parser**: Edit TypeScript files under `tools/codebuddy-log-parser/src/`

### Troubleshooting
- **Registry issues**: Ensure JSON registry files (`*-registry.json`) are valid and entries match directory structure
- **CI failures**: Check workflow YAML syntax and ensure path triggers match actual file locations
- **Build errors in log parser**: Verify Node.js >= 18 and run `npm install` before `npm run build`

## Version History
| Version | Date | Changes | Author |
|---------|------|---------|--------|
| 1.0.0 | 2026-05-11 | Initial context creation | Context Builder |

---

*This context file is maintained by the Context Builder toolset. Use `/asdm-context-update` to update when workspace changes occur.*

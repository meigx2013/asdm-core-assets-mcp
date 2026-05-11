# Workspace Context Index

## Overview
This document serves as the index and guide for AI models to understand and work with the **asdm-core-assets-mcp** workspace. It provides a structured overview of the workspace content and guides AI models to find relevant context.

This workspace is a **centralized asset repository** for the ASDM (AI-First System Development Methodology) platform. It serves as a curated library of reusable resources (toolsets, skills, specs, MCP server configs) that AI coding assistants can leverage during software development workflows.

## Workspace Information

### Basic Information
- **Workspace Name**: asdm-core-assets-mcp
- **Description**: Centralized asset repository for the ASDM platform, providing toolsets, skills, specs, and MCP server configurations for AI-assisted development
- **Repository**: `github.com/meigx2013/asdm-core-assets-mcp`
- **Created Date**: 2025-05-11
- **Last Updated**: 2025-05-11

### Technology Stack
- **Primary Language**: TypeScript (tooling), Markdown (content), JSON (registry), Python/Shell (skill scripts)
- **Frameworks**: Node.js >= 18.0.0 (CLI tooling)
- **Build Tools**: npm, tsc (TypeScript compiler), ts-node
- **Database**: None (content repository, no traditional database)
- **Testing Framework**: None configured
- **Deployment Platform**: GitHub Actions CI/CD, Artifact-based distribution (zip packages)
- **AI Integration**: CodeBuddy (`@tencent-ai/codebuddy-code`), MCP (Model Context Protocol)

### Business Context
- **Business Domain**: AI-First Software Development Methodology (ASDM)
- **Key Business Processes**:
  - Asset authoring and curation (toolsets, skills, specs, MCPs)
  - Registry management and versioning
  - Automated packaging and distribution via CI/CD
  - Workspace initialization and context generation
  - CodeBuddy task execution on external repositories
- **Business Rules**:
  - All content must be in English for internationalization
  - Each asset type follows a standardized directory structure and registry schema
  - Assets are packaged as zip artifacts on push to `main`
  - Registry entries use consistent metadata schema (id, guid, version, entryPoint, etc.)

## Workspace Structure

### File Tree with Guidance
```
asdm-core-assets-mcp/
├── .asdm/                              # ASDM runtime state
│   ├── workspace-install.json          # Tracks installed toolsets/specs/contexts per workspace
│   ├── toolsets/                       # Installed toolset instances
│   │   └── context-builder-7/          # Installed context-builder instance
│   │       ├── manifest.json           # Toolset metadata and version
│   │       ├── actions/                # Slash command definitions
│   │       └── specs/                  # Spec templates
│   └── contexts/                       # Generated context files (this directory)
├── .codebuddy/                         # CodeBuddy AI assistant configuration
│   ├── rules/project-rules.mdc        # Always-applied rule: English-only content
│   └── commands/                       # Custom slash commands
│       ├── asdm-context-build.md       # Generate workspace context
│       ├── asdm-context-update.md      # Update workspace context
│       ├── asdm-ddl-context-analysis.md
│       ├── asdm-import-skill.md
│       ├── asdm-import-specs.md
│       ├── asdm-import-mcp.md
│       ├── asdm-git-message.md
│       └── summarize.md
├── .github/                            # GitHub Actions CI/CD workflows
│   └── workflows/
│       ├── asdm-workspace-init-pipeline.yml
│       ├── asdm-workspace-execution.yml
│       ├── asdm-context-space-sync.yml
│       ├── skill-package.yml
│       ├── specs-package.yml
│       ├── mcp-package.yml
│       └── toolsets-package.yml
├── .workspace/                         # Empty workspace directory
├── asdm-core-assets/                   # Core asset definitions
│   ├── toolsets/                       # Toolset packages
│   │   ├── toolsets-registry.json      # Master registry of all toolsets
│   │   ├── sample-toolset/             # Example toolset (actions + specs + tools)
│   │   ├── basic-tools/                # Basic AI dev tools
│   │   ├── context-builder/            # Context builder toolset
│   │   ├── prd-builder/               # PRD/planning toolset
│   │   └── prototype-builder/         # Prototype generation toolset
│   ├── skills/                         # Skill packages
│   │   ├── skills-registry.json        # Master registry of all skills
│   │   ├── pdf-official/              # PDF processing toolkit
│   │   ├── pptx/                      # PowerPoint generation (HTML2PPTX, OOXML)
│   │   ├── java-springboot-crud/      # Java Spring Boot CRUD generator
│   │   ├── dotnet-crud/               # .NET CRUD generator
│   │   ├── go-crud/                   # Go CRUD generator (Gin + GORM)
│   │   ├── python-fastapi-crud/       # Python FastAPI CRUD generator
│   │   ├── sql-ddl/                   # SQL DDL generator
│   │   └── report-development/        # Report generation toolkit
│   ├── specs/                          # Technology stack specifications
│   │   ├── specs-registry.json         # Master registry of all specs
│   │   ├── reactjs/                    # React.js coding standards
│   │   ├── nextjs-react-tailwind/     # Next.js + React + Tailwind specs
│   │   ├── vue3-composition-api/      # Vue 3 Composition API specs
│   │   ├── typescript-vite-vue-tailwind-daisyui/
│   │   ├── java-springboot-jpa/       # Spring Boot JPA specs
│   │   ├── java-general/              # Java general specs (Effective Java)
│   │   ├── javascript/                # JavaScript (ES6+) specs
│   │   ├── typescript/                # TypeScript specs
│   │   ├── css/                       # CSS/Sass/Less specs
│   │   ├── html/                      # HTML5 specs
│   │   ├── node/                      # Node.js specs
│   │   ├── playwright-accessibility-testing/
│   │   ├── playwright-integration-testing/
│   │   └── playwright-e2e-testing/
│   ├── mcps/                           # MCP server packages
│   │   ├── mcps-registry.json          # Master registry
│   │   └── kubernetes-mcp-server/     # Kubernetes management MCP (22 tools)
│   │       ├── config.json             # Full tool definitions + config templates
│   │       └── README.md
│   └── contexts/                       # Context spaces
│       └── contexts-registry.json      # Currently empty registry
└── tools/                              # Utility tools
    └── codebuddy-log-parser/           # TypeScript CLI tool
        ├── package.json
        ├── tsconfig.json
        └── src/
            ├── index.ts                # CLI entry point
            ├── parser.ts              # Log line/file parser
            ├── formatter.ts           # Output formatter (text/json/human-chat)
            └── types.ts               # TypeScript type definitions
```

### Key Directories Explanation
- **`.asdm/contexts/`**: Contains all context files for AI model reference (this directory)
- **`asdm-core-assets/toolsets/`**: Toolset packages with actions, specs, and tools for AI assistants
- **`asdm-core-assets/skills/`**: Skill packages that provide specialized capabilities (CRUD generators, document processing)
- **`asdm-core-assets/specs/`**: Technology stack specifications and coding standards
- **`asdm-core-assets/mcps/`**: MCP server configurations for external tool integrations
- **`tools/codebuddy-log-parser/`**: TypeScript CLI utility for parsing CodeBuddy session logs
- **`.github/workflows/`**: CI/CD pipelines for packaging, workspace execution, and context generation
- **`.codebuddy/commands/`**: Custom slash commands for CodeBuddy AI assistant

## Asset Inventory

### Toolsets (5)
| ID | Name | Description |
|----|------|-------------|
| sample-toolset | Sample Toolset | Example toolset demonstrating actions + specs + tools |
| basic-tools | Basic Tools | Basic AI development tools |
| context-builder | Context Builder | Generates comprehensive context for AI models |
| prd-builder | PRD Builder | PRD and planning toolset |
| prototype-builder | Prototype Builder | Prototype generation toolset |

### Skills (8)
| ID | Name | Description |
|----|------|-------------|
| pdf-official | PDF Official | PDF processing toolkit |
| pptx | PPTX | PowerPoint generation (HTML2PPTX, OOXML) |
| java-springboot-crud | Java Spring Boot CRUD | Java Spring Boot CRUD code generator |
| dotnet-crud | .NET CRUD | .NET CRUD code generator |
| go-crud | Go CRUD | Go CRUD code generator (Gin + GORM) |
| python-fastapi-crud | Python FastAPI CRUD | Python FastAPI CRUD code generator |
| sql-ddl | SQL DDL | SQL DDL generator |
| report-development | Report Development | Report generation toolkit |

### Specs (14)
| ID | Name | Description |
|----|------|-------------|
| reactjs | React.js | React.js coding standards |
| nextjs-react-tailwind | Next.js + React + Tailwind | Full-stack React specs |
| vue3-composition-api | Vue 3 Composition API | Vue 3 specs |
| typescript-vite-vue-tailwind-daisyui | TS + Vite + Vue + Tailwind + DaisyUI | Full-stack Vue specs |
| java-springboot-jpa | Spring Boot JPA | Spring Boot with JPA specs |
| java-general | Java General | Effective Java practices |
| javascript | JavaScript | ES6+ specs (Alibaba F2E) |
| typescript | TypeScript | TypeScript coding standards |
| css | CSS | CSS/Sass/Less specs |
| html | HTML | HTML5 specs |
| node | Node.js | Node.js specs |
| playwright-accessibility-testing | Accessibility Testing | Playwright accessibility tests |
| playwright-integration-testing | Integration Testing | Playwright integration tests |
| playwright-e2e-testing | E2E Testing | Playwright end-to-end tests |

### MCPs (1)
| ID | Name | Description |
|----|------|-------------|
| kubernetes-mcp-server | Kubernetes MCP Server | Kubernetes management with 22 tools (v3.3.0) |

## Development Guidelines

### Building and Compilation
```bash
# Build the codebuddy-log-parser tool
cd tools/codebuddy-log-parser
npm install
npm run build

# Run the log parser
node dist/index.js [options] [<input-file>]
```

### Asset Packaging
Asset packaging is automated via GitHub Actions. On push to `main`:
- Skills in `asdm-core-assets/skills/**` are zipped and uploaded as artifacts
- Specs in `asdm-core-assets/specs/**` are zipped and uploaded as artifacts
- MCPs in `asdm-core-assets/mcps/**` are zipped and uploaded as artifacts
- Toolsets in `asdm-core-assets/toolsets/**` are zipped and uploaded as artifacts

### Code Quality
- **Rule**: All content (code, documentation, comments, names) must be in English
- **TypeScript**: Strict mode enabled (`strict: true`)
- **Naming**: Kebab-case for directory names, camelCase for TypeScript code

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
- **Adding a new skill**: Create directory under `asdm-core-assets/skills/`, add `SKILL.md` entry point, update `skills-registry.json`
- **Adding a new spec**: Create directory under `asdm-core-assets/specs/`, add markdown spec files, update `specs-registry.json`
- **Adding a new toolset**: Create directory under `asdm-core-assets/toolsets/`, add `README.md`, `actions/`, `specs/`, update `toolsets-registry.json`
- **Adding a new MCP**: Create directory under `asdm-core-assets/mcps/`, add `config.json`, update `mcps-registry.json`
- **Modifying existing assets**: Update the asset content and the corresponding registry entry's `dateUpdated`
- **CodeBuddy command changes**: Edit files in `.codebuddy/commands/`

### Troubleshooting
- If an asset is not recognized, check the corresponding registry JSON file
- For build issues with `codebuddy-log-parser`, verify Node.js >= 18 and run `npm install`
- For CI/CD issues, check the GitHub Actions workflow configurations in `.github/workflows/`

## Version History
| Version | Date | Changes | Author |
|---------|------|---------|--------|
| 1.0.0 | 2025-05-11 | Initial context creation | Context Builder |

---

*This context file is maintained by the Context Builder toolset. Use `/asdm-context-update` to update when workspace changes occur.*

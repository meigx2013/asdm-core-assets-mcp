# Add MCP Server Resource Support and Enhance Core Assets

## Summary

This PR adds MCP (Model Context Protocol) server resource support to the ASDM Core Assets repository, along with new skills, specs, and toolsets enhancements.

## Changes

### MCP Server Support
- Add `asdm-core-assets/mcps/` directory with MCP server resources
- Add `mcps-registry.json` for MCP server registration
- Add `kubernetes-mcp-server` as the first MCP server (v3.3.0) with comprehensive Kubernetes cluster management support
- Add `.github/workflows/mcp-package.yml` for automated MCP packaging workflow
- Add `.codebuddy/commands/asdm-import-mcp.md` for MCP resource collection command

### Skills
- Add CRUD generation skills for multiple tech stacks:
  - `java-springboot-crud` - Java Spring Boot CRUD generation
  - `python-fastapi-crud` - Python FastAPI CRUD generation
  - `go-crud` - Go CRUD generation
  - `dotnet-crud` - .NET CRUD generation
- Add `sql-ddl` skill for SQL DDL generation
- Add `report-development` skill for report generation
- Update `skills-registry.json` with new skill entries

### Specs
- Add frontend development specs:
  - `javascript` - JavaScript coding standards
  - `typescript` - TypeScript coding standards
  - `html` - HTML coding standards
  - `css` - CSS coding standards
  - `node` - Node.js coding standards
- Update `specs-registry.json` with new spec entries

### Toolsets
- Add `prototype-builder` toolset with scaffolding and creation actions
- Update `prd-builder` with backend tech stack detection and CRUD spec support
- Update `toolsets-registry.json` with new entries

### Documentation
- Update root `README.md` with MCP section and `mcp-package.yml` entry
- Update `asdm-core-assets/README.md` with MCP server directory description

## Files Changed (47 files, +14,954 / -60)

| Category | Key Files |
|----------|-----------|
| MCP | `mcps/`, `mcp-package.yml`, `asdm-import-mcp.md` |
| Skills | `skills/dotnet-crud/`, `skills/go-crud/`, `skills/java-springboot-crud/`, `skills/python-fastapi-crud/`, `skills/sql-ddl/`, `skills/report-development/` |
| Specs | `specs/javascript/`, `specs/typescript/`, `specs/html/`, `specs/css/`, `specs/node/` |
| Toolsets | `toolsets/prototype-builder/`, `toolsets/prd-builder/` |
| Registry | `skills-registry.json`, `specs-registry.json`, `toolsets-registry.json`, `mcps-registry.json` |

## Testing

- [ ] MCP package workflow triggers correctly on push/PR to `asdm-core-assets/mcps/`
- [ ] MCP registry JSON is valid and parseable
- [ ] New skills have valid SKILL.md and executable scripts
- [ ] New specs are properly linked in specs-registry.json
- [ ] Prototype-builder toolset can be installed and executed

# Instructions for asdm-ddl-context-analysis action

## Purpose
This instruction guides the AI model to analyze database DDL (Data Definition Language) files and generate comprehensive context documentation for the database schema.

## Language Detection

Before analyzing any DDL files, you must detect and use the current environment's response language:

1. **Detect Response Language**: Analyze the environment settings to determine the primary language:
   - Check system/user language settings or environment configuration
   - Identify the primary language used in project documentation and comments
   - Determine the language preference based on workspace context

2. **Apply Language Consistency**: Ensure all generated context files use the detected language:
   - Use the same language for all markdown files, comments, and documentation
   - Maintain language consistency across all generated context files
   - Follow the detected language's writing conventions and formatting

3. **Supported Languages**:
   - English (en)
   - Chinese (zh)
   - Other languages as needed based on environment detection

**IMPORTANT**: Language detection is the **FIRST step** before any DDL analysis. All output must consistently use the detected language throughout the entire process.

## DDL Context Analysis Steps

### 1. Locate DDL Files
Scan the workspace to identify all DDL files. By default, DDL files are located in the `pre-context/**/*` directory.

**Search patterns**:
- Look for `.sql` extension files containing DDL statements
- Search for files containing `CREATE TABLE`, `ALTER TABLE`, `DROP TABLE` statements
- Check common locations for database schema files

### 2. Analyze DDL Structure
Perform structural analysis on each DDL file:

#### 2.1 Table Analysis
- Identify all table definitions
- Extract table names, columns, data types, constraints
- Analyze primary keys, foreign keys, indexes
- Identify unique constraints and default values

#### 2.2 Relationship Analysis
- Map foreign key relationships between tables
- Identify one-to-one, one-to-many, many-to-many relationships
- Analyze relationship cardinality and constraints

#### 2.3 Schema Metadata
- Extract database engine specifications
- Identify character sets and collations
- Analyze table-level comments and constraints

### 3. Generate Data Model Documentation

#### 3.1 Create Entity Relationship Diagrams
Generate comprehensive ER diagrams using Mermaid syntax:

```mermaid
erDiagram
    [Generate entity relationship diagram based on actual DDL]
    [Include all tables, fields, and relationships]
```

#### 3.2 Entity Definitions
Create detailed entity definitions for each table:

**Table Structure**:
- Table name and purpose
- Column definitions with data types and constraints
- Primary key and foreign key relationships
- Indexes and unique constraints

**Entity Interfaces** (TypeScript/Java style):
```typescript
interface [EntityName] {
  [Generate interface definitions based on DDL]
}
```

### 4. Business Domain Analysis

#### 4.1 Domain Identification
Based on table relationships and naming patterns, identify business domains:

- **User Management Domain**: Tables related to users, authentication, profiles
- **Order Management Domain**: Tables for orders, order items, payments
- **Product Catalog Domain**: Tables for products, categories, inventory
- **System Administration Domain**: Tables for logs, configuration, settings

#### 4.2 Domain Relationships
Map relationships between identified domains:

```mermaid
graph LR
    [Generate domain dependency diagram based on table relationships]
```

### 5. Data Validation Rules
Extract and document data validation rules from DDL constraints:

#### 5.1 Field-Level Constraints
- Data type constraints (INT, VARCHAR, DATE, etc.)
- Length constraints (VARCHAR(255), etc.)
- Nullability constraints (NOT NULL)
- Default values

#### 5.2 Table-Level Constraints
- Primary key constraints
- Foreign key relationships
- Unique constraints
- Check constraints

### 6. Data Access Patterns

#### 6.1 Common Query Patterns
Identify likely query patterns based on indexes and relationships:
- Find user by email/username
- Search products by category
- View order history by user
- Inventory management queries

#### 6.2 Performance Considerations
- Analyze existing indexes for optimization
- Identify potentially missing indexes
- Document query performance recommendations

### 7. Generate Single Context File

Consolidate all analysis results into a single comprehensive document:

**Output file**: `.asdm/contexts/ddl-context.md`

**Content structure**:
1. **Database Overview**
   - Database type and version
   - Total number of tables and relationships
   - Business domain summary

2. **Entity Relationship Diagram**
   - Complete ER diagram
   - Table relationship visualization

3. **Entity Definitions**
   - Detailed table descriptions
   - Column definitions and constraints
   - Relationship mapping

4. **Business Domain Analysis**
   - Identified business domains
   - Domain relationships and dependencies

5. **Data Validation Rules**
   - Field-level constraints
   - Table-level constraints
   - Business rule validation

6. **Data Access Patterns**
   - Common query patterns
   - Performance considerations
   - Index optimization recommendations

### 8. Quality Assurance

#### 8.1 Validation Checks
- Verify all tables from DDL are documented
- Ensure relationship mapping is accurate
- Confirm constraint documentation is complete

#### 8.2 Consistency Review
- Check terminology consistency across all documentation
- Ensure language consistency (using detected language)
- Validate diagram accuracy against actual DDL

## Usage Examples

### Example 1: Analyze DDL Files
```bash
/asdm-ddl-context-analysis
# Analyze all DDL files in pre-context/*/ directory
# Generate complete data model documentation
```

### Example 2: Update After Schema Changes
```bash
# When DDL files are updated, re-analyze
/asdm-ddl-context-analysis
# Update existing data model documentation
```

## Output Structure

```
.asdm/contexts/
└── ddl-context.md                    # Single DDL context document
```

## Important Notes

1. **Language Consistency**: All generated content must use the language detected in the language detection step
2. **Accuracy**: DDL analysis must be accurate and reflect the actual database schema
3. **Completeness**: Document all tables, relationships, and constraints found in DDL files
4. **Conciseness**: All content is output to a single file for easy reference and maintenance
5. **Integration**: Ensure DDL context integrates properly with existing project context

## Error Handling

- If no DDL files are found, provide clear guidance on where to place them
- If DDL syntax is invalid, report specific parsing errors
- If relationships are ambiguous, document assumptions and seek clarification

---

*This DDL context analysis action enables AI models to comprehensively understand database schemas, supporting better code generation and data-aware development.*

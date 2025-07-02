---
name: Cognee MCP Tool Usage
description: Essential practices for using Cognee MCP tools to build and query knowledge graphs
---

# Cognee MCP Tool Usage

## Key Principles
- Cognee processes your data asynchronously - always monitor background processes
- Organize knowledge using strategic node sets for better retrieval 
- Choose search types based on the format of results you need
- Prepare and structure data before ingestion for optimal knowledge graphs
- Monitor status regularly for long-running operations

## Essential Tool Usage

### Data Ingestion with `cognify`
- Use `cognify` to transform documents, text, or file paths into knowledge graphs
- Always check `cognify_status` immediately after starting to monitor progress
- Provide clear, well-structured data for better knowledge graph quality
- Use meaningful descriptions when adding data to help with later retrieval
- Break large datasets into smaller, logical chunks if processing fails

### Code Analysis with `codify` (only beta version)
- Use `codify` with repository paths to analyze code structure and relationships
- Always monitor with `codify_status` - code analysis takes significant time
- Ensure repository path is correct (absolute or relative to current directory)
- Best results come from well-organized repositories with clear structure
- Use results to understand architecture, dependencies, and code patterns

### Knowledge Retrieval with `search`
- Choose search type based on desired output format:
  - `GRAPH_COMPLETION`: Natural language answers using knowledge graph context
  - `RAG_COMPLETION`: Traditional document-based answers  
  - `CODE`: Structured code information (beta version only)
  - `CHUNKS`: Raw text pieces from the knowledge base
  - `INSIGHTS`: Entity relationships and connections
- Write queries in natural language for best results
- Be specific about what information you're seeking

## Rules

### Do this
- Always check `cognify_status` or `codify_status` after starting background operations
- Use descriptive, meaningful names when organizing data
- Wait for operations to complete before expecting search results from new data
- Choose search types that match your expected output format
- Provide context in your search queries for more relevant results
- Test search queries with different types to find the most useful format
- Add the following rule in your project to generate developer rules in your knowledge graph from your chat: "After answering the question, save the user-agent interaction (together with the code you generate) using the "save_interaction" tool from cognee mcp. Do not use any additional tool." When you select "Always" as rule type and add this rule to the context of your chat, your conversation with the agent will be used automatically to generate rules.
- Use `get_developer_rules` to retrieve accumulated insights from the generated rules.

### Don't do this
- Don't assume `cognify` or `codify` operations complete immediately
- Don't use generic or unclear descriptions when adding data
- Don't search for information before verifying the ingestion process completed
- Don't use the wrong search type
- Don't submit vague search queries - be specific about what you need
- Don't forget to monitor long-running processes with status tools
- Don't use `prune` carelessly - it permanently deletes all stored knowledge

## Examples

### Good Tool Usage Workflow
```
1. Add data: cognify("Here is my project documentation about API endpoints...")
2. Monitor: cognify_status (wait for completion)
3. Search: search("What are the main API endpoints?", "GRAPH_COMPLETION")
4. Get insights: search("API endpoint relationships", "INSIGHTS")
```

### Bad Tool Usage 
```
1. Add data: cognify("docs")  // Too vague, you can give the path to the file instead.
2. Immediate search: search("endpoints", "CODE")  // Wrong search type + didn't wait
3. No monitoring: // Never checked if cognify completed
```

## Workflow Optimization
- **Start with Status**: Always check existing status before adding new data
- **Organized Ingestion**: Group related content when using cognify or codify
- **Strategic Search**: Try different search types to find the best format for your needs
- **Progress Monitoring**: Use status tools to track long-running operations
- **Knowledge Maintenance**: Periodically review and organize your knowledge graph

## Common Use Cases

### Document Analysis
- Use `cognify` with document text or file paths
- Search with `GRAPH_COMPLETION` for contextual answers

### Code Understanding (only in beta version)
- Use `codify` on repository paths for architecture analysis
- Search with `CODE` type for structured programming information

### Interactive Learning
- Use `save_interaction` to capture useful conversation to generate rules
- Retrieve generated rules with `get_developer_rules` for guidance
- Build knowledge base from interactions and decisions

## Key Conventions
1. Always monitor background processes with status tools
2. Use descriptive names and context when adding data
3. Match search types to expected output formats
4. Wait for operations to complete before searching new data
5. Test different search approaches to find optimal results
6. Use knowledge graph to discover relationships and get insights

These tools work together to create persistent, searchable memory for AI assistants. 
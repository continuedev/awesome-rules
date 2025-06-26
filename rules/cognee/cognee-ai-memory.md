---
name: Cognee Search and Organization
description: Best practices for organizing data and searching knowledge graphs with Cognee MCP tools
---

# Cognee Search and Organization

## Key Principles
- Organize data strategically for better search results and knowledge retrieval
- Understand when to use each search type for optimal results
- Structure your data before adding it to improve knowledge graph quality
- Use descriptive naming and context to improve search relevance
- Monitor and verify data ingestion before relying on search results

## Data Organization

### Content Grouping Strategies
- Group related documents and data together when using `cognify` with large datasets
- Use clear, descriptive context when adding data
- Separate different types of content (code vs docs vs conversations)
- Add context about the purpose and source of your data
- Structure information logically before ingestion for better knowledge graphs

### Effective Data Descriptions
- Use descriptive, specific language when adding data to Cognee
- Include key topics, domains, or purposes in your data descriptions if possible
- Mention the context or project the data relates to
- Provide enough detail for future search relevance

## Search Strategy

### Choosing the Right Search Type
- **GRAPH_COMPLETION**: When you want conversational answers that use relationship context
- **RAG_COMPLETION**: For direct document-based answers without complex reasoning
- **CODE**: When searching codify output
- **CHUNKS**: To see raw text chunks, useful for verification
- **INSIGHTS**: To understand relationships and connections between concepts

### Query Best Practices
- Write search queries in natural language
- Be specific about what you're looking for
- Include relevant context or domain information in your queries
- Try different search types if initial results aren't what you expected
- Use precise technical terms when searching code-related content (currently beta)

## Rules

### Do this
- Add descriptive context when using `cognify` or `codify` (for python files, in beta version) to improve search results
- Wait for `cognify_status` or `codify_status` to show completion before searching
- Test different search types to find the format that works best for your needs if not satisfied
- Use specific, detailed search queries rather than generic ones
- Organize related information together when adding data
- Check what data already exists before adding duplicate information

### Don't do this
- Don't search for information immediately after adding data - wait for processing
- Don't stick to one search type if it's not giving you useful results
- Don't use vague search queries - be specific about what you need
- Don't mix unrelated information when searching data 
- Don't ignore relationship insights - they often reveal valuable connections
- Don't assume all data was processed successfully without checking status

## Examples

### Good Data Organization
```
cognify("*text you want to generate knowledge graph from*")
search("How does user authentication work in this system?", "GRAPH_COMPLETION")
```

### Bad Data Organization  
```
cognify("*some text*")  // Too vague
search("query", "CODE")  // Wrong search type, didn't wait for processing
```

### Effective Search Patterns
```
# For conceptual understanding
search("What are the main components of the authentication system?", "GRAPH_COMPLETION")

# For discovering relationships
search("authentication dependencies", "INSIGHTS")

# For seeing raw source material
search("login implementation", "CHUNKS")
```

## Common Workflows

### Document Analysis Workflow
1. Use `cognify` with clear, descriptive context about your documents
2. Check `cognify_status` to confirm processing completion
3. Search with `GRAPH_COMPLETION` for conceptual questions

### Code Understanding Workflow  
1. Use `codify` on your repository path
2. Monitor progress with `codify_status`
3. Search with `CODE` type for structured programming information
4. Use `INSIGHTS` to understand architectural relationships

### Interactive Learning Workflow
1. Use `save_interaction` during conversations if you want to generate rules
2. Add project rules to always run save_interaction to generate rules from whole chat session
2. Retrieve rule patterns with `get_developer_rules`
3. Search accumulated knowledge with `GRAPH_COMPLETION`
4. Build team knowledge base over time

## Key Conventions
1. Always provide context when adding data to improve search relevance
2. Wait for processing completion before expecting search results
3. Test multiple search types to find the most useful format
4. Use specific, detailed queries for better search results
5. Organize related information together for better relationship discovery
6. Monitor processing status to ensure data was successfully added

Effective use of these tools creates a powerful, searchable knowledge base for your projects. 
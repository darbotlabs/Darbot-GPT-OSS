# Copilot Instructions for Darbot-GPT-OSS

## Project Overview

This repository provides comprehensive guides and resources for running open-source GPT models locally using Ollama, with a focus on privacy-first AI solutions. The project emphasizes complete privacy, offline functionality, and developer-friendly tools for local AI deployment.

## Key Concepts

### Core Technologies
- **Ollama**: Local AI model runtime for running GPT models
- **GPT-OSS Models**: Open-source GPT models (20B and 120B variants)
- **OpenAI API Compatibility**: Local APIs that mimic OpenAI's Chat Completions API
- **Function Calling**: Tool use and chain-of-thought (CoT) reasoning
- **Agents SDK**: Integration with OpenAI's Agent frameworks

### Project Values
- **Privacy First**: All data stays on the user's machine
- **Offline Ready**: No cloud dependencies required
- **Developer Friendly**: Simple CLI with powerful customization
- **Open Source**: Built for the community

## Code Style & Conventions

### Documentation Standards
- Use clear, concise language with emoji-enhanced headings for better readability
- Maintain consistent formatting across README.md and index.html
- Include practical code examples for all API integrations
- Use proper syntax highlighting for code blocks

### HTML/CSS Guidelines
- Follow the established cyberpunk/tech aesthetic with CSS custom properties
- Use consistent color scheme defined in `:root` variables:
  - `--cyber-purple: #8b5cf6`
  - `--cyber-pink: #ec4899` 
  - `--cyber-blue: #3b82f6`
  - `--cyber-black: #0a0a0a`
- Maintain responsive design patterns
- Use Font Awesome icons consistently

### Python Code Examples
- Use the OpenAI SDK for API examples when possible
- Include proper error handling and type hints
- Show both synchronous and asynchronous patterns
- Demonstrate function calling with realistic examples

### Shell Commands
- Provide cross-platform compatible commands
- Use clear, commented examples
- Include installation and setup instructions

## Content Guidelines

### When Adding New Features
- Update both README.md and index.html with new information
- Include practical, working code examples
- Test all code examples to ensure they work with current Ollama versions
- Add appropriate sections to the Developer Resources area

### API Documentation
- Always show OpenAI SDK compatibility examples
- Include Ollama native API alternatives when relevant
- Demonstrate function calling patterns with chain-of-thought reasoning
- Show integration patterns with popular frameworks (LiteLLM, AI SDK)

### Model References
- Use `gpt-oss:20b` and `gpt-oss:120b` as standard model names
- Include memory and hardware requirements when relevant
- Provide performance optimization tips

## File Structure

- `README.md`: Main documentation with setup guides and API examples
- `index.html`: Web-based documentation with interactive examples and cyberpunk styling
- `LICENSE`: MIT license for open-source distribution
- `.github/`: GitHub-specific configurations including these Copilot instructions

## Common Patterns

### Code Examples Format
```python
from openai import OpenAI

client = OpenAI(
    base_url="http://localhost:11434/v1",  # Local Ollama API
    api_key="ollama"                       # Dummy key
)
```

### Documentation Structure
- Start with clear value proposition
- Provide quick setup guide
- Include comprehensive API examples
- End with community resources and support information

## Best Practices

1. **Accuracy**: Ensure all technical information is current with latest Ollama features
2. **Completeness**: Include both basic and advanced use cases
3. **Accessibility**: Write for developers of all skill levels
4. **Privacy Focus**: Always emphasize the privacy benefits of local deployment
5. **Community**: Encourage contributions and provide clear support channels

## Helpful Context

- This is a documentation-focused repository, not a code implementation
- Users are primarily developers interested in local AI deployment
- The project supports both hobbyists and enterprise use cases
- Integration with existing OpenAI workflows is a key selling point
- The aesthetic should feel modern and tech-forward while remaining professional
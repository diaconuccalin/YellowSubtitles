# CLAUDE.md - YellowSubtitles

This document provides guidance for AI assistants (particularly Claude) working with the YellowSubtitles codebase.

## Project Overview

**YellowSubtitles** is a subtitle processing and management project.

- **Owner**: Călin Diaconu (@diaconuccalin)
- **License**: MIT
- **Status**: Early development stage

## Current State

This is a newly initialized repository. The codebase is in its early stages with:
- MIT License in place
- Git repository initialized
- Ready for initial development

## Repository Structure

```
YellowSubtitles/
├── LICENSE              # MIT License
└── CLAUDE.md           # This file
```

As the project grows, this section will be updated to reflect the actual structure.

## Development Workflow

### Branch Strategy

- **Main Branch**: Primary development branch (TBD)
- **Feature Branches**: Use descriptive branch names (e.g., `feature/subtitle-parser`, `fix/encoding-issue`)
- **Claude Branches**: AI-assisted development uses branches prefixed with `claude/` (e.g., `claude/write-claude-md-*`)

### Git Conventions

1. **Commit Messages**: Use clear, descriptive commit messages
   - Format: `<type>: <description>`
   - Types: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`
   - Example: `feat: add SRT subtitle parser`

2. **Pull Requests**:
   - Provide clear descriptions
   - Reference related issues
   - Ensure all tests pass before merging

### Code Quality Standards

When code is added to this project, follow these standards:

- **Testing**: Write tests for new features and bug fixes
- **Documentation**: Document public APIs and complex logic
- **Code Style**: Follow consistent formatting (will be defined with language choice)
- **Security**: Avoid hardcoded credentials, validate inputs, handle errors properly

## Technology Stack

*To be determined as the project develops*

Likely areas of focus based on project name:
- Subtitle format parsing (SRT, VTT, ASS, etc.)
- Text processing and manipulation
- Possibly video/media integration
- File I/O operations

## Key Conventions for AI Assistants

### When Working on This Project

1. **Understand Context First**
   - Before making changes, explore existing code structure
   - Check for similar implementations
   - Review recent commits for patterns

2. **File Operations**
   - Prefer editing existing files over creating new ones
   - Use Read tool before Edit or Write operations
   - Maintain consistent code style with existing files

3. **Testing Requirements**
   - Run existing tests before and after changes
   - Add tests for new functionality
   - Ensure no regressions

4. **Documentation**
   - Update relevant documentation when changing functionality
   - Keep CLAUDE.md updated as the project evolves
   - Document non-obvious design decisions in comments

5. **Security Considerations**
   - No hardcoded secrets or credentials
   - Validate and sanitize file inputs (especially subtitle files)
   - Handle file encoding issues gracefully
   - Be cautious with file path operations to prevent directory traversal

### Common Tasks

#### Adding New Subtitle Format Support

When adding support for a new subtitle format:
1. Research the format specification
2. Create a parser module
3. Add tests with sample files
4. Update documentation
5. Handle edge cases and malformed input

#### Processing Subtitle Files

When working with subtitle files:
- Handle different text encodings (UTF-8, UTF-16, etc.)
- Preserve timing information accurately
- Validate format compliance
- Support both reading and writing operations

#### Error Handling

- Provide clear error messages
- Handle file not found, permission errors
- Validate subtitle format before processing
- Log errors appropriately

## Architecture Principles

*To be established as the codebase grows*

Recommended principles:
- **Separation of Concerns**: Keep parsing, processing, and I/O separate
- **Modularity**: Design components to be reusable
- **Extensibility**: Make it easy to add new subtitle formats
- **Robustness**: Handle malformed input gracefully

## Dependencies Management

*To be established based on chosen technology*

Guidelines:
- Keep dependencies minimal and well-maintained
- Document why each dependency is needed
- Regularly update dependencies for security
- Use lock files for reproducible builds

## Testing Strategy

*To be established*

Recommended approach:
- **Unit Tests**: Test individual components (parsers, processors)
- **Integration Tests**: Test format conversion workflows
- **Test Data**: Include sample subtitle files in various formats
- **Edge Cases**: Test malformed inputs, edge timestamps, special characters

## Performance Considerations

When working with subtitle files:
- Handle large subtitle files efficiently
- Stream processing for very large files
- Optimize regex patterns in parsers
- Consider memory usage with large datasets

## Common Pitfall Avoidance

1. **Encoding Issues**: Always specify and handle text encoding explicitly
2. **Timestamp Precision**: Maintain millisecond precision in timing
3. **Line Endings**: Handle both Windows (CRLF) and Unix (LF) line endings
4. **Special Characters**: Properly escape and handle special characters in subtitles
5. **Format Variations**: Account for format variations and extensions

## Resources

### Subtitle Format Specifications

- **SRT (SubRip)**: Simple text-based format with timestamps
- **VTT (WebVTT)**: Web-based subtitle format
- **ASS/SSA**: Advanced SubStation Alpha with styling
- **TTML**: Timed Text Markup Language (XML-based)

### Useful Links

- [Project Repository](https://github.com/diaconuccalin/YellowSubtitles)
- Documentation: *To be added*
- Issue Tracker: *GitHub Issues*

## Changelog

### 2025-11-15
- Repository initialized
- MIT License added
- CLAUDE.md created

## Future Considerations

As this project develops, consider:
- CI/CD pipeline setup
- Release process and versioning
- Package distribution (if applicable)
- API documentation generation
- Performance benchmarking
- Multi-language support for subtitle content

## Questions & Clarifications

When uncertain about:
- **Architecture Decisions**: Ask the maintainer before implementing major structural changes
- **Format Support Priority**: Clarify which subtitle formats are most important
- **Feature Scope**: Confirm if features align with project goals
- **Breaking Changes**: Always discuss breaking changes before implementation

## Contact

For questions about this project, contact the repository owner or open an issue on GitHub.

---

**Last Updated**: 2025-11-15
**Maintained By**: Călin Diaconu
**For**: AI Assistant Context & Development Guidance

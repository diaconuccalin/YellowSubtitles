# CLAUDE.md - YellowSubtitles (VideoSubFinder Setup Branch)

This document provides guidance for AI assistants (particularly Claude) working with the YellowSubtitles VideoSubFinder setup branch.

## Project Overview

**YellowSubtitles - VideoSubFinder Setup** is a configuration branch that integrates VideoSubFinder as a git submodule with custom enhancements.

- **Owner**: Călin Diaconu (@diaconuccalin)
- **Primary Tool**: VideoSubFinder (forked and enhanced)
- **Purpose**: Extract subtitles from video files using advanced detection algorithms
- **Branch**: VideoSubFinder_setup

## What is VideoSubFinder?

VideoSubFinder is a C++ application that automatically finds and extracts hardcoded (burned-in) subtitles from video files. This branch includes a customized version with YellowSubtitles-specific enhancements.

## Repository Structure

```
YellowSubtitles/
├── .gitignore          # Comprehensive ignore rules for C++ builds
├── .gitmodules         # Git submodule configuration
├── VideoSubFinder/     # Git submodule (VideoSubFinder fork)
└── CLAUDE.md          # This file
```

### Git Submodule Details

- **Path**: `VideoSubFinder/`
- **Repository**: https://github.com/diaconuccalin/VideoSubFinder.git
- **Branch**: `YellowSubtitles` (custom branch with enhancements)
- **Purpose**: Custom fork with auto-detection and UI improvements

## Key Features & Enhancements

Based on commit history, this branch includes:

1. **Auto-Detection Feature**: Automatic subtitle region detection
2. **Contour-Based Algorithm**: Advanced contour detection for subtitle boundaries
3. **UI Improvements**: Enhanced user interface for better usability
4. **Sampling Strategy**: Optimized video sampling for faster processing

## Development Workflow

### Working with Git Submodules

**Initializing the Submodule**:
```bash
git submodule update --init --recursive
```

**Updating the Submodule**:
```bash
cd VideoSubFinder
git pull origin YellowSubtitles
cd ..
git add VideoSubFinder
git commit -m "Update VideoSubFinder submodule"
```

**Checking Submodule Status**:
```bash
git submodule status
```

**Important Submodule Practices**:
- Always commit submodule changes separately from parent repo changes
- Document what changes were pulled from the submodule in commit messages
- Test submodule updates before committing
- Keep track of which submodule commit the parent repo references

### Branch Strategy

- **VideoSubFinder_setup**: Main integration branch (this branch)
- **Feature Branches**: Use descriptive names (e.g., `feature/ocr-integration`, `fix/detection-accuracy`)
- **Claude Branches**: AI-assisted work uses `claude/` prefix

### Commit Conventions

1. **Submodule Updates**:
   - Format: `Update VideoSubFinder with <feature/fix description>`
   - Example: `Update VideoSubFinder submodule with auto-detection feature`

2. **Configuration Changes**:
   - Format: `<type>: <description>`
   - Types: `feat`, `fix`, `docs`, `config`, `chore`
   - Example: `config: update .gitignore for build artifacts`

## Technology Stack

### Core Technologies

- **Language**: C++ (VideoSubFinder is written in C++)
- **Build System**: CMake (inferred from .gitignore)
- **Version Control**: Git with submodules
- **Platform**: Cross-platform (Linux, Windows, macOS support expected)

### Build Artifacts (Ignored)

The `.gitignore` file excludes:
- Build directories (`build/`, `build_*/`)
- CMake generated files
- Compiled objects (`.o`, `.obj`, `.so`, `.dll`, `.exe`)
- IDE configurations (Visual Studio, VS Code)
- OS-specific files (`.DS_Store`, `Thumbs.db`)

## Key Conventions for AI Assistants

### When Working on This Branch

1. **Submodule Management**
   - NEVER modify files inside `VideoSubFinder/` directory directly
   - Work on VideoSubFinder code in its own repository
   - Only update submodule references in this repository
   - Always check submodule status before and after changes

2. **Build System**
   - Understand that this is a C++ project using CMake
   - Build artifacts are git-ignored
   - Don't commit compiled binaries or build files
   - Preserve CMakeLists.txt files (they're not ignored)

3. **Testing Submodule Changes**
   - After updating submodule, initialize and test it
   - Verify compilation succeeds after submodule updates
   - Document any new dependencies or build requirements

4. **Documentation**
   - Keep CLAUDE.md updated with submodule changes
   - Document new features added to VideoSubFinder
   - Note any breaking changes or API updates

### Common Tasks

#### Updating VideoSubFinder Submodule

When updating the VideoSubFinder submodule:

1. Navigate to submodule directory
2. Checkout the YellowSubtitles branch
3. Pull latest changes
4. Return to parent directory
5. Stage and commit the submodule update
6. Document what features/fixes were included

```bash
cd VideoSubFinder
git checkout YellowSubtitles
git pull
cd ..
git add VideoSubFinder
git commit -m "Update VideoSubFinder with <description>"
```

#### Building VideoSubFinder

Typical CMake build process:
```bash
cd VideoSubFinder
mkdir build
cd build
cmake ..
make
```

**Note**: Specific build instructions may vary. Check VideoSubFinder repository for detailed build steps.

#### Adding New Configuration Files

When adding build or configuration files:
- Check if they should be ignored (reference .gitignore)
- IDE-specific files should generally be ignored
- Build scripts and CMakeLists.txt should be committed
- Platform-specific build configs should be documented

### Security Considerations

1. **Video File Processing**
   - Validate video file formats before processing
   - Handle corrupted or malformed video files gracefully
   - Be cautious with file paths to prevent directory traversal
   - Limit resource consumption (memory, CPU) for large files

2. **Submodule Security**
   - Verify submodule URL hasn't been tampered with
   - Pin submodule to specific commits for stability
   - Review submodule changes before updating
   - Be aware of supply chain security with external dependencies

3. **Build Security**
   - Don't execute untrusted build scripts
   - Verify compiler and build tool integrity
   - Be cautious with third-party libraries
   - Keep dependencies updated for security patches

## Architecture & Design

### VideoSubFinder Architecture

Based on the enhancement commits, VideoSubFinder likely includes:

- **Video Processing Pipeline**: Frame extraction and analysis
- **Detection Algorithms**:
  - Contour-based detection for subtitle regions
  - Auto-detection for locating subtitles automatically
  - Sampling strategies for efficient processing
- **User Interface**: GUI components for configuration and monitoring
- **OCR Integration**: Text recognition from detected subtitle regions (likely)

### Integration Points

When integrating VideoSubFinder with other YellowSubtitles components:
- Define clear interfaces for subtitle extraction
- Handle different video formats and codecs
- Provide progress feedback for long operations
- Support batch processing of multiple files

## Performance Considerations

### Video Processing

- **Large Files**: Implement streaming or chunk-based processing
- **Sampling Strategy**: Use intelligent frame sampling to reduce processing time
- **Parallel Processing**: Consider multi-threading for frame analysis
- **Caching**: Cache detection results to avoid redundant processing

### Memory Management

- **Frame Buffers**: Manage video frame memory efficiently
- **Resource Cleanup**: Properly release video decoder resources
- **Memory Limits**: Set reasonable limits for memory usage
- **Leak Prevention**: Watch for memory leaks in C++ code

## Common Pitfalls & Solutions

### Submodule Issues

1. **Empty Submodule Directory**
   - **Problem**: Cloned repo but VideoSubFinder is empty
   - **Solution**: Run `git submodule update --init --recursive`

2. **Detached HEAD State**
   - **Problem**: Submodule in detached HEAD state
   - **Solution**: `cd VideoSubFinder && git checkout YellowSubtitles`

3. **Submodule Out of Sync**
   - **Problem**: Local submodule differs from committed reference
   - **Solution**: Check `git submodule status` and decide whether to update or reset

### Build Issues

1. **Missing Dependencies**
   - Check VideoSubFinder documentation for required libraries
   - Install OpenCV, FFmpeg, or other video processing libraries
   - Verify CMake version meets requirements

2. **Platform-Specific Problems**
   - Windows: May need Visual Studio build tools
   - Linux: May need development headers (libavcodec-dev, etc.)
   - macOS: May need Homebrew dependencies

3. **CMake Configuration Errors**
   - Clear CMake cache: `rm -rf build && mkdir build`
   - Check CMakeLists.txt for required variables
   - Verify compiler toolchain is properly configured

## Development Best Practices

### Code Quality

- **C++ Standards**: Follow modern C++ practices (C++11/14/17)
- **Memory Safety**: Use RAII, smart pointers, avoid raw new/delete
- **Error Handling**: Use exceptions or error codes consistently
- **Code Reviews**: Review submodule updates before merging

### Testing

- **Unit Tests**: Test individual components in isolation
- **Integration Tests**: Test VideoSubFinder with sample videos
- **Performance Tests**: Benchmark processing speed and accuracy
- **Regression Tests**: Ensure updates don't break existing functionality

### Documentation

- **Code Comments**: Document complex algorithms and non-obvious logic
- **API Documentation**: Document public interfaces and functions
- **User Guides**: Provide usage instructions for new features
- **Changelog**: Track feature additions and bug fixes

## Debugging VideoSubFinder

### Common Debugging Scenarios

1. **Detection Failures**
   - Check video quality and subtitle visibility
   - Verify detection algorithm parameters
   - Review contour detection thresholds
   - Test with known-good sample videos

2. **Performance Issues**
   - Profile CPU and memory usage
   - Check sampling rate configuration
   - Verify efficient algorithm implementation
   - Look for redundant frame processing

3. **Build/Runtime Errors**
   - Check library versions and compatibility
   - Verify all dependencies are installed
   - Review compiler warnings and errors
   - Use debugger (gdb/lldb/Visual Studio debugger)

## Resources

### VideoSubFinder

- **Forked Repository**: https://github.com/diaconuccalin/VideoSubFinder
- **Custom Branch**: YellowSubtitles
- **Original Project**: VideoSubFinder (check upstream for documentation)

### Development Tools

- **CMake**: https://cmake.org/documentation/
- **OpenCV**: (if used) https://docs.opencv.org/
- **FFmpeg**: (if used) https://ffmpeg.org/documentation.html
- **Git Submodules**: https://git-scm.com/book/en/v2/Git-Tools-Submodules

### YellowSubtitles

- **Main Repository**: https://github.com/diaconuccalin/YellowSubtitles
- **Issue Tracker**: GitHub Issues

## Changelog

### Recent Submodule Updates

- **UI Improvements & Sampling Strategy**: Enhanced user interface and optimized sampling
- **Contour-Based Auto-Detection**: New algorithm for automatic subtitle region detection
- **Auto-Detection Feature**: Initial implementation of automatic detection
- **Initial Setup**: VideoSubFinder added as git submodule

### 2025-11-15
- CLAUDE.md created for VideoSubFinder_setup branch

## Future Considerations

### Planned Enhancements

- OCR accuracy improvements
- Support for more video formats
- Batch processing capabilities
- Cloud/distributed processing
- Machine learning-based detection

### Integration Goals

- Integrate with subtitle post-processing pipeline
- Connect to subtitle format conversion tools
- Build automation and CI/CD pipeline
- Performance benchmarking suite
- Automated testing with sample videos

## Workflow Tips for AI Assistants

### Before Making Changes

1. ✅ Check current branch (`git branch`)
2. ✅ Verify submodule status (`git submodule status`)
3. ✅ Review recent commits (`git log --oneline -5`)
4. ✅ Check for uncommitted changes (`git status`)

### When Updating Submodule

1. ✅ Document what features/fixes are included
2. ✅ Test the update locally if possible
3. ✅ Commit with descriptive message
4. ✅ Note any breaking changes or new requirements

### When Adding Features to VideoSubFinder

1. ⚠️ Work in the VideoSubFinder repository, not this one
2. ⚠️ Make changes on the YellowSubtitles branch
3. ⚠️ Test thoroughly before pushing
4. ⚠️ Update this repository's submodule reference after pushing

## Questions & Clarifications

When uncertain about:
- **Submodule Updates**: Ask before updating to a different commit
- **Build Configuration**: Clarify platform-specific requirements
- **Feature Scope**: Confirm if features belong in VideoSubFinder or YellowSubtitles
- **Breaking Changes**: Always discuss before making incompatible changes
- **Dependencies**: Verify before adding new external dependencies

## Contact

For questions about this branch or VideoSubFinder integration:
- Open an issue on GitHub
- Contact repository owner: Călin Diaconu

---

**Last Updated**: 2025-11-15
**Branch**: VideoSubFinder_setup
**Maintained By**: Călin Diaconu
**For**: AI Assistant Context & Development Guidance

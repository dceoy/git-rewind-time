# Repository Guidelines

## Repository Overview

This repository contains Bash utilities for manipulating Git commit dates. The main script is:
- `git-rewind-time`: Rewinds the latest commit date by a specified amount of time (supports days, hours, minutes, seconds, weeks, months, years)

## Common Commands

### Linting
```bash
# Run ShellCheck on all executable files
find . -type f -executable -name 'git-rewind-*' -print0 | xargs -0 shellcheck --external-sources
```

### Testing Scripts
```bash
# Test dry-run mode
./git-rewind-time --dry-run 7 days
./git-rewind-time --dry-run 24 hours
./git-rewind-time --dry-run 30 minutes
./git-rewind-time --dry-run 2 weeks

# Debug mode
./git-rewind-time --debug 1 hour
```

## Architecture Notes

1. **Date Command Detection**: The script automatically detects whether to use GNU date (`gdate`) or BSD date, making it portable across macOS and Linux systems.

2. **Git Operations**: Scripts use `git rebase` and `git commit --amend` to modify commit timestamps while preserving the commit content.

3. **Error Handling**: Scripts use `set -eu` for strict error handling and proper exit codes.

4. **CI/CD**: GitHub Actions runs ShellCheck on push/PR to master branch. The workflow is defined in `.github/workflows/lint.yml`.

## Development Guidelines

1. **Script Standards**:
   - All scripts should be POSIX-compliant where possible
   - Use ShellCheck directives when needed for false positives
   - Include proper help text in script comments

2. **Version Updates**: Version numbers are hardcoded in the script (currently v0.3.0) and should be updated when making changes.

3. **Git Safety**: Always test changes with `--dry-run` flag first to ensure Git operations work as expected.

## Web Search Instructions

For tasks requiring web search, always use `gemini` command instead of the built-in web search tool.

### Usage

```sh
# Basic search query
gemini --sandbox --prompt "WebSearch: <query>"

# Example: Search for latest news
gemini --sandbox --prompt "WebSearch: What are the latest developments in AI?"
```

### Policy

When users request information that requires web search:

1. Use `gemini --sandbox --prompt` command via terminal
2. Parse and present the Gemini response appropriately

This ensures consistent and reliable web search results through the Gemini API.

## Development Methodology

This section combines essential guidance from Martin Fowler's refactoring, Kent Beck's tidying, and t_wada's TDD approaches.

### Core Philosophy

- **Small, safe, behavior-preserving changes** - Every change should be tiny, reversible, and testable
- **Separate concerns** - Never mix adding features with refactoring/tidying
- **Test-driven workflow** - Tests provide safety net and drive design
- **Economic justification** - Only refactor/tidy when it makes immediate work easier

### The Development Cycle

1. **Red** - Write a failing test first (TDD)
2. **Green** - Write minimum code to pass the test
3. **Refactor/Tidy** - Clean up without changing behavior
4. **Commit** - Separate commits for features vs refactoring

### Essential Practices

#### Before Coding

- Create TODO list for complex tasks
- Ensure test coverage exists
- Identify code smells (long functions, duplication, etc.)

#### While Coding

- **Test-First**: Write the test before the implementation
- **Small Steps**: Each change should be easily reversible
- **Run Tests Frequently**: After each small change
- **Two Hats**: Either add features OR refactor, never both

#### Refactoring Techniques

1. **Extract Function/Variable** - Improve readability
2. **Rename** - Use meaningful names
3. **Guard Clauses** - Replace nested conditionals
4. **Remove Dead Code** - Delete unused code
5. **Normalize Symmetries** - Make similar code consistent

#### TDD Strategies

1. **Fake It** - Start with hardcoded values
2. **Obvious Implementation** - When solution is clear
3. **Triangulation** - Multiple tests to find general solution

### When to Apply

- **Rule of Three**: Refactor on third duplication
- **Preparatory**: Before adding features to messy code
- **Comprehension**: As you understand code better
- **Opportunistic**: Small improvements during daily work

### Key Reminders

- One assertion per test
- Commit refactoring separately from features
- Delete redundant tests
- Focus on making code understandable to humans

Quote: "Make the change easy, then make the easy change." - Kent Beck

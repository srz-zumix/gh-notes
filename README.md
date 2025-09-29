# gh-notes

A GitHub CLI extension that provides a convenient wrapper for managing Git notes in your repositories.

## Overview

Git notes are a powerful feature that allows you to add annotations to Git objects (commits, blobs, trees) without modifying the objects themselves.
This extension makes it easier to work with Git notes by providing a user-friendly interface through the GitHub CLI.

## Features

- **Add notes**: Attach notes to Git objects
- **Edit notes**: Modify existing notes
- **Show notes**: Display notes for objects
- **Copy notes**: Duplicate notes between objects  
- **Append to notes**: Add content to existing notes
- **Remove notes**: Delete notes from objects
- **Merge notes**: Combine notes from different references
- **Fetch/Push notes**: Synchronize notes with remote repositories
- **Namespace support**: Organize notes using custom namespaces
- **Prune notes**: Clean up notes pointing to non-existing objects

## Installation

### Install from GitHub

```bash
gh extension install srz-zumix/gh-notes
```

### Install from local repository

```bash
git clone https://github.com/srz-zumix/gh-notes.git
cd gh-notes
make install
```

## Usage

### Basic Commands

```bash
# Show notes for the current commit
gh notes show

# Add a note to a specific commit
gh notes add <commit-sha>

# Edit a note
gh notes edit <commit-sha>

# Remove a note
gh notes remove <commit-sha>

# Show all available notes references
gh notes get-ref
```

### Working with Namespaces

Namespaces allow you to organize notes into different categories:

```bash
# Add a note to a specific namespace
gh notes add -n bugfix <commit-sha>

# Show notes from a specific namespace
gh notes show -n bugfix <commit-sha>

# List all namespaces
gh notes get-ref
```

### Synchronizing Notes

```bash
# Fetch notes from remote repository
gh notes fetch

# Fetch notes from a specific namespace
gh notes fetch -n bugfix

# Push notes to remote repository
gh notes push

# Push notes from a specific namespace
gh notes push -n bugfix
```

### Advanced Operations

```bash
# Copy a note from one commit to another
gh notes copy <source-commit> <target-commit>

# Append text to an existing note
gh notes append <commit-sha>

# Merge notes from another reference
gh notes merge <notes-ref>

# Remove notes that point to non-existing objects
gh notes prune
```

## Command Reference

| Command | Description |
|---------|-------------|
| `add` | Add a note to an object |
| `append` | Append text to a note |
| `copy` | Copy a note from one object to another |
| `edit` | Edit a note |
| `show` | Show the notes on an object (default) |
| `merge` | Merge notes from another ref |
| `remove` | Remove notes from an object |
| `prune` | Prune notes that point to non-existing objects |
| `get-ref` | List available notes references |
| `fetch` | Fetch notes from a remote repository |
| `push` | Push notes to a remote repository |

## Options

### Common Options

- `-n, --namespace <name>`: Specify the namespace for notes operations
- `-h, --help`: Show help message
- `--ref <ref>`: Specify the exact reference

## Examples

### Development Workflow

```bash
# Add a bug report note to a commit
gh notes add -n bugs abc123
# Opens editor to add note content

# Track code review comments
gh notes add -n reviews def456
# Add review feedback as a note

# Sync notes with team
gh notes push -n reviews
gh notes fetch -n reviews
```

### Code Documentation

```bash
# Add implementation notes
gh notes add -n docs <commit-sha>

# Copy important notes to related commits
gh notes copy <source-commit> <target-commit>

# Clean up old notes
gh notes prune
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Related Projects

- [Git Notes Documentation](https://git-scm.com/docs/git-notes)
- [GitHub CLI](https://cli.github.com/)
- [GitHub CLI Extensions](https://docs.github.com/en/github-cli/github-cli/using-github-cli-extensions)

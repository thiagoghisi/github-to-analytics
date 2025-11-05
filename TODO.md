# TODO List

## Security & Configuration

- [ ] **Hardcoded GitHub token** (github-to-analytics.py:7)
  - Replace hardcoded `GITHUB_TOKEN = "YOUR_GH_TOKEN"` with environment variable
  - Use `os.getenv('GITHUB_TOKEN')` or python-dotenv

- [ ] **No .gitignore file**
  - Create .gitignore to prevent committing sensitive files
  - Add: output.csv, .env, *.pyc, __pycache__/

## Error Handling

- [ ] **No error handling around GitHub API calls**
  - Add try-except blocks around repo.get_repo() (line 22)
  - Handle GithubException for rate limiting and network errors
  - Add retry logic for transient failures

- [ ] **No error handling for CSV file operations**
  - Wrap file operations in try-except (line 17)
  - Handle IOError and permission errors

## Code Quality

- [ ] **Missing input validation**
  - Check if GITHUB_TOKEN is still "YOUR_GH_TOKEN" placeholder
  - Validate REPOS and USERS lists are not empty
  - Exit gracefully with helpful error message

- [ ] **Hardcoded output filename** (line 17)
  - Make 'output.csv' configurable via command-line argument or config
  - Could use argparse for CLI options

- [ ] **No type hints**
  - Add type annotations to improve code clarity
  - Consider using mypy for type checking

- [ ] **Missing module docstring**
  - Replace multi-line string comment (lines 12-14) with proper module docstring
  - Add usage examples and parameter descriptions

- [ ] **Using print() instead of logging** (lines 24, 37)
  - Replace print() statements with logging module
  - Add configurable log levels (INFO, DEBUG, ERROR)

## Documentation

- [ ] **Incomplete README instruction** (README.md:23)
  - Change "run `pip install`" to "run `pip install -r requirements.txt`"

- [ ] **Ambiguous CSV column names**
  - Rename "Backlog" and "In Progress" columns to more accurate names for PRs
  - Consider: "Created Date", "Opened Date", or similar
  - Update comment on line 42 accordingly

## Minor Issues

- [ ] **Empty row at end of CSV** (line 49)
  - Remove `csv_writer.writerow([])` or document why it's needed

- [ ] **Outdated Python version reference** (README.md:20)
  - Change from specific "python3.8" to more flexible "python3" or "python3.8+"
  - Add minimum Python version requirement to README

## Potential Enhancements

- [ ] Add command-line argument parsing (argparse)
- [ ] Add progress bar for long-running queries (tqdm)
- [ ] Support filtering by PR labels or status
- [ ] Add option to append to existing CSV instead of overwriting
- [ ] Add unit tests

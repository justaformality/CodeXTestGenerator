# CodeX Test Generator

CodeX Test Generator is a command-line tool that uses OpenAI and the GitHub API to generate unit tests for existing GitHub repositories.

The tool clones a target repository, reads selected source files, generates unit tests using AI, writes the test files into the repo, creates a new Git branch, commits the generated tests, pushes the branch, and opens a pull request automatically.

---

# Why I Built This

I built this project to explore how AI can help developers speed up test creation and improve code coverage.

Writing unit tests manually can take time, especially when working with unfamiliar codebases. This tool experiments with using AI to generate a first draft of tests for JavaScript or Python files and then package those tests into a GitHub pull request for review.

This project helped me practice:

* AI-assisted developer tooling
* CLI development
* GitHub API integration
* automated pull request creation
* unit test generation
* repository automation workflows

---

# Features

* Clones a GitHub repository locally
* Accepts specific target files for test generation
* Detects JavaScript or Python projects
* Generates Jest tests for JavaScript files
* Generates pytest tests for Python files
* Writes generated test files into a test directory
* Creates a new Git branch
* Commits the generated tests
* Pushes the branch to GitHub
* Opens a pull request automatically

---

# Tech Stack

* TypeScript
* Node.js
* OpenAI API
* GitHub API
* Octokit
* simple-git
* dotenv

---

# Project Structure

```text
src/
  index.ts

bin/
  codex-test-gen

package.json
package-lock.json
tsconfig.json
README.md
.gitignore
```

---

# Setup

Install dependencies:

```bash
npm install
```

Create a `.env` file in the project root:

```bash
OPENAI_API_KEY=your_openai_api_key_here
GITHUB_TOKEN=your_github_token_here
```

Do not commit your `.env` file to GitHub.

---

# Build

```bash
npm run build
```

---

# Usage

```bash
node dist/index.js <github-repo-url> <file1> <file2>
```

Example:

```bash
node dist/index.js https://github.com/username/example-repo.git src/utils.js
```

The tool will:

1. Clone the target repository.
2. Read the selected file.
3. Generate unit tests using OpenAI.
4. Write the test file into a `test/` directory.
5. Create a new branch.
6. Commit the generated tests.
7. Push the branch.
8. Open a GitHub pull request.

---

# Example Workflow

```bash
npm install
npm run build
node dist/index.js https://github.com/username/example-repo.git src/example.js
```

Example output:

```text
Cloning into tmp-...
Generating tests for src/example.js
Wrote test/example.test.js
PR created: https://github.com/username/example-repo/pull/1
```

---

# Important Security Note

This project uses API keys through environment variables.

Never commit the `.env` file to GitHub.

The `.gitignore` file should include:

```gitignore
.env
node_modules/
dist/
out/
tmp-*/
.DS_Store
```

---

# Current Limitations

* The tool currently supports JavaScript and Python test generation.
* Generated tests should be reviewed by a developer before merging.
* The tool expects the target repository to allow branch pushes.
* The default pull request base branch is `main`.
* AI-generated tests may need manual cleanup or improvement.

---

# Future Improvements

Some future improvements I want to add:

* Better language and framework detection
* Support for TypeScript projects
* Support for Java/JUnit test generation
* Option to generate tests without opening a pull request
* Better error handling for private repositories
* Support for custom branch names
* Test quality scoring
* GitHub Actions integration
* CLI flags for model, framework, and output directory

---

# What I Learned

This project helped me understand how AI can be used in developer tooling beyond simple chat applications. I learned how to combine OpenAI, GitHub automation, Git operations, and TypeScript into a practical CLI workflow that can generate code and create pull requests automatically.

# Week 5: Organizing Projects with GitHub + AI Helpers

## 📚 Overview

Learn professional coding practices by organizing your projects on GitHub and leveraging AI helpers like GitHub Copilot and ChatGPT to accelerate your development. This week focuses on version control, collaborative workflows, and using AI as a coding partner to improve productivity and code quality.

## 🎯 Learning Objectives

By the end of this week, you will be able to:

- Understand Git and GitHub for version control and collaboration
- Create, commit, and push code to GitHub repositories
- Work with branches and pull requests
- Use GitHub for team collaboration on data science projects
- Leverage AI helpers (GitHub Copilot, ChatGPT) to write and debug code
- Apply best practices for code organization and documentation
- Use AI to accelerate code completion, testing, and documentation

## 🎓 Session Resources

- Lecture: [Organizing Projects with GitHub + AI Helpers](https://docs.google.com/presentation/d/your-presentation-link)
- Tutorial: [GitHub Basics & AI-Assisted Coding](notebooks/tutorial_github_ai.ipynb)

## 🏗️ Mini-Deliverable

**Assignment:** Create a GitHub repository for your data science project and commit your work with clear documentation. Use AI helpers to improve your code quality and documentation.

**Requirements:**
1. **Create a GitHub repository** for your data science project
2. **Organize your code** with proper folder structure
3. **Write clear commit messages** documenting your progress
4. **Create a comprehensive README.md** with project overview and setup instructions
5. **Use an AI helper** (GitHub Copilot or ChatGPT) to assist with code completion, debugging, or documentation
6. **Document your workflow** - show how AI helped improve your development process

## 🔧 Key Topics

### Version Control Fundamentals
- **Git**: Version control system for tracking code changes
- **GitHub**: Cloud platform for hosting and collaborating on code
- **Commits**: Snapshots of your code at specific points
- **Branches**: Parallel versions of your project for feature development
- **Pull Requests**: Way to propose, review, and merge changes

### Working with GitHub
```bash
# Initialize a repository
git init
git add .
git commit -m "Initial commit: Project setup"
git push origin main

# Creating and switching branches
git branch feature/new-analysis
git checkout feature/new-analysis

# Merging changes
git checkout main
git merge feature/new-analysis
```

### AI-Assisted Development
- **GitHub Copilot**: AI-powered code completion
- **ChatGPT**: General-purpose AI for questions, debugging, refactoring
- **Claude**: Advanced reasoning and code analysis
- **Best practices**: When to use AI, how to review AI-generated code

## 📁 Project Organization Structure

```
data-science-project/
├── README.md
├── .gitignore
├── requirements.txt
├── notebooks/
│   ├── 01_data_exploration.ipynb
│   ├── 02_data_cleaning.ipynb
│   └── 03_visualization.ipynb
├── data/
│   ├── raw/
│   └── processed/
├── src/
│   ├── __init__.py
│   ├── data_loader.py
│   ├── preprocessing.py
│   └── visualization.py
└── tests/
    └── test_preprocessing.py
```

## 📝 Best Practices for GitHub Projects

### Commit Message Guidelines
```
Good: "Add temperature trend analysis for Germany"
Good: "Fix bug in data filtering logic"
Good: "Refactor data loading to improve performance"

Bad: "update"
Bad: "fixes"
Bad: "asdf"
```

### README Template
```markdown
# Project Title
Brief description of what this project does

## Setup
1. Clone the repository
2. Install dependencies: `pip install -r requirements.txt`
3. Run notebooks or scripts

## Data
Description of data sources and structure

## Usage
How to use this project

## Results
Key findings and visualizations
```

### .gitignore Example
```
# Python
__pycache__/
*.py[cod]
*.egg-info/

# Data (if sensitive)
data/raw/*.csv
*.xlsx

# Environment
.env
venv/

# IDE
.vscode/
.idea/
```

## 🤖 Using AI Helpers Effectively

### When to Use GitHub Copilot
- Auto-completing common code patterns
- Writing boilerplate code (imports, function stubs)
- Generating test cases
- Creating documentation

### When to Use ChatGPT/Claude
- Explaining complex concepts
- Debugging code and understanding errors
- Refactoring suggestions
- Writing documentation and READMEs
- Learning new libraries and tools

### Best Practices for AI-Assisted Coding
1. **Review all AI-generated code** - Don't blindly accept suggestions
2. **Understand what the code does** - Modify and adapt as needed
3. **Test thoroughly** - AI can make mistakes
4. **Use for learning** - Ask AI to explain code to deepen your understanding
5. **Document your process** - Show how AI helped improve your workflow

## 🔗 Resources

### Git & GitHub
- [GitHub Getting Started](https://docs.github.com/en/get-started)
- [Git Documentation](https://git-scm.com/doc)
- [GitHub Skills Courses](https://skills.github.com/)

### AI Coding Assistants
- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)
- [ChatGPT for Coding](https://openai.com/blog/chatgpt)
- [Best Practices for AI-Assisted Development](https://github.blog/2023-06-20-how-to-use-github-copilot-with-confidence/)

### Project Organization
- [Data Science Project Structure](https://drivendata.github.io/cookiecutter-data-science/)
- [Python Packaging Guide](https://packaging.python.org/)

## 📈 Assessment Criteria

Your GitHub project will be evaluated on:
- **Repository Setup**: Proper initialization with clear structure
- **Commit Quality**: Meaningful, well-organized commits with clear messages
- **Documentation**: Comprehensive README and code comments
- **Code Organization**: Logical folder structure and file organization
- **AI Integration**: Effective use of AI helpers with clear documentation of the benefits
- **Collaboration**: Evidence of branching, pull requests, and code review practices

---

**Next Week**: [Week 6: Working with External Data & APIs](../week6/README.md)

**Previous Week**: [Week 4: Data Visualization I: Telling Stories with Plotly](../week4/README.md)

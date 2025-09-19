# Week 7: Automating Workflows with Functions + Using AI to Scale Code

## 📚 Overview

Learn to write reusable functions that make your analysis more efficient and organized. Discover how AI assistants can help you generate, refactor, and improve your code, making you a more productive data scientist.

## 🎯 Learning Objectives

By the end of this week, you will be able to:

- Write custom functions to automate repetitive data analysis tasks
- Organize code into reusable components (functions like `clean_data()` or `predict_outcome()`)
- Use AI assistants to generate and refactor code efficiently
- Debug code more effectively with AI help
- Structure projects with modular, maintainable code
- Scale your analysis to work with larger datasets or multiple scenarios

## 🎓 Session Structure (80 minutes)

### Lecture (40 minutes): Functions and AI-Powered Development

**Topics Covered:**
- Why automation matters for social impact research at scale
- Writing functions: turning repetitive code into reusable tools
- Function design principles: inputs, outputs, documentation
- How AI assistants can help with code generation and refactoring
- Prompting strategies for AI coding assistance
- Best practices for AI-assisted development

### Tutorial (40 minutes): Refactoring with AI Help

**Hands-on Activities:**
- Take existing analysis code and turn it into functions
- Use an AI assistant (ChatGPT, Copilot) to help restructure code
- Create functions for common tasks: data cleaning, visualization, analysis
- Practice prompting AI for code generation and explanation
- Debug code errors with AI assistance

## 🏗️ Mini-Deliverable

**Assignment:** Create a script with at least one reusable function and demonstrate AI-assisted refactoring.

**Requirements:**
1. **Identify repetitive code** from your previous weeks' work
2. **Create reusable functions** (e.g., `clean_data()`, `create_visualization()`, `predict_outcome()`)
3. **Use AI assistance** to help refactor and improve your code
4. **Document the AI process** - include the prompts you used and the AI's suggestions
5. **Test your functions** with different datasets or parameters
6. **Organize code** into a clean, modular structure

### Example Function Development:
```python
# BEFORE: Repetitive code
df1 = pd.read_csv('dataset1.csv')
df1 = df1.dropna()
df1 = df1.rename(columns={'GDP_per_cap': 'gdp_per_capita'})
df1['gdp_billions'] = df1['gdp_per_capita'] * df1['population'] / 1000000

df2 = pd.read_csv('dataset2.csv')
df2 = df2.dropna()
df2 = df2.rename(columns={'GDP_per_cap': 'gdp_per_capita'})
df2['gdp_billions'] = df2['gdp_per_capita'] * df2['population'] / 1000000

# AFTER: Reusable function
def clean_economic_data(filepath, population_col='population'):
    \"\"\"
    Clean and standardize economic dataset.
    
    Parameters:
    -----------
    filepath : str
        Path to CSV file
    population_col : str
        Name of population column
    
    Returns:
    --------
    pd.DataFrame
        Cleaned dataset with standardized columns
    \"\"\"
    # Load data
    df = pd.read_csv(filepath)
    
    # Clean missing values
    df = df.dropna()
    
    # Standardize column names
    df = df.rename(columns={'GDP_per_cap': 'gdp_per_capita'})
    
    # Calculate total GDP
    if 'gdp_per_capita' in df.columns and population_col in df.columns:
        df['gdp_billions'] = df['gdp_per_capita'] * df[population_col] / 1000000
    
    return df

# Use the function
df1 = clean_economic_data('dataset1.csv')
df2 = clean_economic_data('dataset2.csv')

# AI Prompt used: "Help me refactor this repetitive data cleaning code into a reusable function"
```

## 📁 Files Structure

```
week7/
├── README.md
├── notebooks/
│   ├── lecture_functions_automation.ipynb
│   ├── tutorial_ai_refactoring.ipynb
│   └── assignment_modular_code.ipynb
├── scripts/
│   ├── data_processing_functions.py
│   ├── visualization_tools.py
│   └── analysis_utilities.py
├── examples/
│   ├── before_after_refactoring.ipynb
│   └── ai_prompting_examples.md
└── resources/
    ├── function_design_guide.md
    ├── ai_prompting_strategies.md
    └── code_organization_tips.md
```

## 📖 Key Concepts Introduced

### Function Design Principles
- **Single Responsibility**: Each function should do one thing well
- **Clear Inputs/Outputs**: Make it obvious what goes in and what comes out
- **Documentation**: Always include docstrings explaining what the function does
- **Error Handling**: Plan for common problems and edge cases

### Essential Function Patterns
```python
def clean_data(df, columns_to_drop=None, missing_strategy='drop'):
    \"\"\"
    Clean a dataset using standard procedures.
    
    Parameters:
    -----------
    df : pd.DataFrame
        Input dataset
    columns_to_drop : list, optional
        Columns to remove from dataset
    missing_strategy : str
        How to handle missing values ('drop', 'fill', 'mean')
    
    Returns:
    --------
    pd.DataFrame
        Cleaned dataset
    \"\"\"
    df_clean = df.copy()
    
    # Drop specified columns
    if columns_to_drop:
        df_clean = df_clean.drop(columns=columns_to_drop)
    
    # Handle missing values
    if missing_strategy == 'drop':
        df_clean = df_clean.dropna()
    elif missing_strategy == 'fill':
        df_clean = df_clean.fillna(0)
    elif missing_strategy == 'mean':
        df_clean = df_clean.fillna(df_clean.mean())
    
    return df_clean

def create_comparison_chart(df, x_col, y_col, color_col=None, title="Comparison Chart"):
    \"\"\"Create a standardized comparison visualization.\"\"\"
    import plotly.express as px
    
    fig = px.scatter(df, x=x_col, y=y_col, color=color_col, title=title)
    fig.update_layout(
        xaxis_title=x_col.replace('_', ' ').title(),
        yaxis_title=y_col.replace('_', ' ').title()
    )
    return fig
```

### AI-Assisted Development Strategies

**Effective Prompts for Code Generation:**
- "Help me create a function that [specific task] with [specific inputs/outputs]"
- "Refactor this repetitive code into reusable functions"
- "Add error handling to this function for [specific edge cases]"
- "Optimize this code for better performance"

**Effective Prompts for Debugging:**
- "This code gives error [error message]. How can I fix it?"
- "Explain what this function does step by step"
- "Why might this function fail with [specific input]?"

**Code Review Prompts:**
- "Review this function for best practices and suggest improvements"
- "Make this code more readable and add proper documentation"
- "How can I make this function more flexible for different use cases?"

## 🎥 Video Resources

1. **Writing Effective Functions for Data Science** (20 min)
2. **AI-Assisted Code Development** (15 min)
3. **Refactoring Techniques and Best Practices** (15 min)
4. **Debugging with AI Assistance** (10 min)

## �️ Common Function Categories for Social Impact

### Data Processing Functions
```python
def standardize_country_names(df, country_col='country'):
    \"\"\"Standardize country names across datasets.\"\"\"
    
def merge_time_series_data(df1, df2, time_col='year', key_col='country'):
    \"\"\"Merge two time series datasets safely.\"\"\"
    
def calculate_change_over_time(df, value_col, time_col, group_col):
    \"\"\"Calculate percentage change in indicators over time.\"\"\"
```

### Analysis Functions
```python
def analyze_inequality(df, metric_col, group_col):
    \"\"\"Calculate inequality metrics across groups.\"\"\"
    
def identify_outlier_countries(df, metric_col, threshold=2):
    \"\"\"Find countries with unusual values for investigation.\"\"\"
    
def correlation_with_development(df, target_col, development_indicators):
    \"\"\"Analyze correlation between target and development metrics.\"\"\"
```

### Visualization Functions
```python
def create_trend_chart(df, x_col, y_col, group_col, title):
    \"\"\"Create standardized trend visualization.\"\"\"
    
def generate_country_comparison(df, countries, metrics, year):
    \"\"\"Compare specific countries across multiple metrics.\"\"\"
    
def plot_distribution_by_region(df, metric_col, region_col):
    \"\"\"Show distribution of metrics across regions.\"\"\"
```

## 🤖 AI Assistant Best Practices

### Do's
- ✅ Be specific about what you want the code to do
- ✅ Provide context about your data and goals
- ✅ Ask for explanation along with code
- ✅ Test AI-generated code before using it
- ✅ Use AI to explain complex code you don't understand

### Don'ts
- ❌ Blindly copy-paste without understanding
- ❌ Use AI-generated code without testing
- ❌ Rely on AI for critical decisions without verification
- ❌ Forget to add your own comments and documentation

## 🔗 Additional Resources

### Function Design
- [Python Functions Guide](https://docs.python.org/3/tutorial/controlflow.html#defining-functions)
- [Clean Code Principles](https://github.com/zedr/clean-code-python)
- [Effective Python Functions](https://realpython.com/defining-your-own-python-function/)

### AI-Assisted Development
- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)
- [ChatGPT for Programmers](https://platform.openai.com/docs/guides/chat)
- [AI Pair Programming Best Practices](https://github.blog/2022-09-07-research-quantifying-github-copilots-impact-on-developer-productivity-and-happiness/)

## ❓ Common Questions

**Q: How do I know when to create a function?**
A: If you're copying and pasting code with minor modifications, or if you do the same task multiple times, it's time for a function.

**Q: Should I trust AI-generated code completely?**
A: No! Always test AI code, understand what it does, and verify it works with your specific data.

**Q: How detailed should my function documentation be?**
A: Include purpose, parameters, return values, and any important assumptions or limitations.

**Q: What if AI suggests code I don't understand?**
A: Ask the AI to explain it step by step, or break it down into simpler parts you can understand.

## 🆘 Getting Help

- **Discussion Forum**: Share functions and AI prompting strategies
- **Office Hours**: Tuesdays 6-7 PM
- **AI Assistants**: Use them! That's the point of this week
- **Peer Support**: Review each other's functions and refactoring

## 📈 Assessment Criteria

Your automation assignment will be evaluated on:
- **Function Quality**: Well-designed, reusable functions with clear purpose
- **AI Integration**: Effective use of AI assistance for code generation/refactoring
- **Documentation**: Clear documentation of both code and AI process
- **Code Organization**: Clean, modular structure that's easy to understand
- **Testing**: Evidence that functions work correctly with different inputs

---

**Next Week**: [Week 8: From Notebooks to Apps (Streamlit Basics)](../week8/README.md)

**Previous Week**: [Week 6: Intro to Predictive Analytics (without heavy math)](../week6/README.md)

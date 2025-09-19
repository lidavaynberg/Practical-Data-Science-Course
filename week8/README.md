# Week 8: From Notebooks to Apps (Streamlit Basics)

## 📚 Overview

Transform your data analysis into interactive web applications that anyone can use! Learn Streamlit basics to create simple, powerful apps that communicate your social impact findings to stakeholders, policymakers, and the public.

## 🎯 Learning Objectives

By the end of this week, you will be able to:

- Understand why apps matter for social impact communication
- Create interactive web applications using Streamlit
- Build apps that allow users to upload data and explore visualizations
- Add interactive elements (sliders, dropdowns, buttons) to your analysis
- Deploy apps locally and understand deployment options
- Design user-friendly interfaces for non-technical audiences

## 🎓 Session Structure (80 minutes)

### Lecture (40 minutes): Why Apps Matter for Social Impact

**Topics Covered:**
- The power of interactive applications for social change
- Making data accessible to non-technical stakeholders
- Streamlit fundamentals: turning Python scripts into web apps
- App design principles for social impact:
  - **Accessibility**: Easy for anyone to use
  - **Clarity**: Clear purpose and instructions
  - **Interactivity**: Let users explore the data themselves
- Examples of successful social impact apps and dashboards

### Tutorial (40 minutes): Building Your First Streamlit App

**Hands-on Activities:**
- Install Streamlit and create your first app
- Build an app that uploads CSV files and shows Plotly charts
- Add interactive widgets (sliders, selectboxes, file uploaders)
- Test your app locally using `streamlit run`
- Practice app design and user experience principles

## 🏗️ Mini-Deliverable

**Assignment:** Create a local Streamlit app with at least one visualization and file upload capability.

**Requirements:**
1. **Create a Streamlit app** that addresses your chosen social issue
2. **Add file upload functionality** so users can explore their own datasets
3. **Include interactive visualizations** using Plotly within the app
4. **Add user controls** (sliders, dropdowns, or buttons) for customization
5. **Test locally** and ensure the app runs smoothly
6. **Document the app** with clear instructions for users

### Example Streamlit App Structure:
```python
import streamlit as st
import pandas as pd
import plotly.express as px

# App title and description
st.title("📊 Education Equity Explorer")
st.write("Explore relationships between education funding and outcomes")

# Sidebar for user inputs
st.sidebar.header("Data Upload and Controls")

# File upload
uploaded_file = st.sidebar.file_uploader(
    "Upload your education dataset (CSV)", 
    type=['csv']
)

if uploaded_file is not None:
    # Load and display data
    df = pd.read_csv(uploaded_file)
    
    st.write("### Dataset Overview")
    st.write(f"**Rows:** {len(df)}, **Columns:** {len(df.columns)}")
    
    # Show data preview
    if st.checkbox("Show raw data"):
        st.write(df.head())
    
    # Interactive controls
    st.sidebar.write("### Visualization Controls")
    
    numeric_cols = df.select_dtypes(include=['number']).columns
    x_axis = st.sidebar.selectbox("Choose X-axis", numeric_cols)
    y_axis = st.sidebar.selectbox("Choose Y-axis", numeric_cols)
    
    # Color by categorical column if available
    cat_cols = df.select_dtypes(include=['object']).columns
    color_by = st.sidebar.selectbox("Color by", ['None'] + list(cat_cols))
    
    # Create visualization
    st.write(f"### {y_axis.title()} vs {x_axis.title()}")
    
    if color_by != 'None':
        fig = px.scatter(df, x=x_axis, y=y_axis, color=color_by,
                        title=f"{y_axis} vs {x_axis} by {color_by}")
    else:
        fig = px.scatter(df, x=x_axis, y=y_axis,
                        title=f"{y_axis} vs {x_axis}")
    
    st.plotly_chart(fig, use_container_width=True)
    
    # Summary statistics
    st.write("### Key Statistics")
    col1, col2 = st.columns(2)
    
    with col1:
        st.metric("Average " + x_axis, f"{df[x_axis].mean():.2f}")
    
    with col2:
        st.metric("Average " + y_axis, f"{df[y_axis].mean():.2f}")
    
else:
    st.info("👆 Please upload a CSV file to begin exploring!")
    
    # Show example with sample data
    st.write("### Example: Global Education Data")
    
    # Create sample data for demonstration
    sample_data = {
        'country': ['USA', 'Finland', 'Singapore', 'Canada', 'Germany'],
        'education_spending_pct_gdp': [6.2, 6.8, 4.9, 5.3, 4.9],
        'literacy_rate': [99, 100, 97, 99, 99],
        'mean_years_schooling': [13.4, 12.9, 11.9, 13.3, 14.1]
    }
    
    sample_df = pd.DataFrame(sample_data)
    fig = px.scatter(sample_df, 
                    x='education_spending_pct_gdp', 
                    y='literacy_rate',
                    hover_name='country',
                    title='Education Spending vs Literacy Rate')
    
    st.plotly_chart(fig, use_container_width=True)
```

## 📁 Files Structure

```
week8/
├── README.md
├── notebooks/
│   ├── lecture_streamlit_intro.ipynb
│   ├── tutorial_first_app.ipynb
│   └── assignment_social_impact_app.ipynb
├── apps/
│   ├── education_explorer.py
│   ├── climate_dashboard.py
│   └── health_outcomes_app.py
├── examples/
│   ├── simple_app_example.py
│   └── advanced_features_demo.py
└── resources/
    ├── streamlit_cheatsheet.md
    ├── app_design_principles.md
    └── deployment_options.md
```

## 📖 Key Concepts Introduced

### Streamlit Fundamentals
- **`st.title()` and `st.write()`**: Display text and headers
- **`st.sidebar`**: Create a sidebar for controls and inputs
- **`st.file_uploader()`**: Allow users to upload their own data
- **`st.selectbox()`, `st.slider()`**: Interactive widgets for user input
- **`st.plotly_chart()`**: Display interactive Plotly visualizations
- **`st.columns()`**: Create multi-column layouts

### Essential Streamlit Patterns
```python
import streamlit as st
import pandas as pd
import plotly.express as px

# Basic app structure
st.title("My Social Impact App")
st.write("Description of what the app does")

# File upload
uploaded_file = st.file_uploader("Choose a CSV file", type="csv")

if uploaded_file is not None:
    df = pd.read_csv(uploaded_file)
    
    # Interactive controls
    column = st.selectbox("Choose a column", df.columns)
    
    # Visualization
    fig = px.histogram(df, x=column)
    st.plotly_chart(fig)
else:
    st.info("Please upload a file to get started!")
```

### App Design for Social Impact
- **Clear Purpose**: Users should immediately understand what your app does
- **Simple Interface**: Don't overwhelm with too many options
- **Helpful Instructions**: Guide users through the process
- **Meaningful Defaults**: Start with sensible default settings
- **Error Handling**: Gracefully handle invalid inputs or missing data

## 🎥 Video Resources

1. **Introduction to Streamlit for Social Good** (15 min)
2. **Building Your First Interactive App** (25 min)
3. **Adding User Controls and Interactivity** (20 min)
4. **App Design and User Experience** (10 min)

## 🌍 Social Impact App Ideas

### Education Equity Dashboard
- Upload school district data
- Compare funding vs. outcomes
- Interactive maps and trend analysis
- Filter by demographics or geography

### Climate Change Explorer
- Visualize temperature and CO2 data
- Compare countries and regions
- Show projections and scenarios
- Interactive timeline controls

### Health Outcomes Analyzer
- Explore health indicators by country/region
- Compare interventions and outcomes
- Interactive correlation analysis
- Demographic breakdowns

### Economic Development Tracker
- Visualize poverty and development indicators
- Compare progress across countries
- Show relationship between different factors
- Interactive goal tracking (SDGs)

## 🎨 Streamlit Layout and Styling

### Layout Options
```python
# Columns
col1, col2, col3 = st.columns(3)
with col1:
    st.metric("Metric 1", "Value 1")

# Sidebar
st.sidebar.title("Controls")
option = st.sidebar.selectbox("Choose option", ['A', 'B', 'C'])

# Expander for optional content
with st.expander("Advanced Options"):
    advanced_setting = st.checkbox("Enable advanced mode")

# Tabs for organization
tab1, tab2, tab3 = st.tabs(["Overview", "Analysis", "About"])
with tab1:
    st.write("Overview content")
```

### Interactive Widgets
```python
# User inputs
text_input = st.text_input("Enter text")
number = st.number_input("Pick a number", min_value=0, max_value=100)
slider_val = st.slider("Choose value", 0, 100, 50)
selectbox_choice = st.selectbox("Choose option", ['A', 'B', 'C'])
multiselect = st.multiselect("Choose multiple", ['A', 'B', 'C'])
date = st.date_input("Pick a date")
```

## 🚀 Deployment Options

### Local Development
```bash
# Install Streamlit
pip install streamlit

# Run your app
streamlit run your_app.py
```

### Cloud Deployment (Next Steps)
- **Streamlit Cloud**: Free hosting for public apps
- **Heroku**: Free tier available for simple apps
- **GitHub Pages**: For static content
- **Google Colab**: Can run Streamlit with some setup

## 🔗 Additional Resources

### Streamlit Documentation
- [Streamlit Documentation](https://docs.streamlit.io/)
- [Streamlit Gallery](https://streamlit.io/gallery)
- [Streamlit Components](https://streamlit.io/components)

### App Examples and Inspiration
- [Streamlit for Social Good](https://blog.streamlit.io/tag/social-good/)
- [COVID-19 Dashboards](https://github.com/streamlit/demo-covid-19)
- [Climate Change Apps](https://github.com/topics/climate-change-streamlit)

## ❓ Common Questions

**Q: Do I need to know web development to use Streamlit?**
A: No! Streamlit handles all the web development complexity. You just write Python.

**Q: Can users interact with my app in real-time?**
A: Yes! Streamlit apps are fully interactive. When users change inputs, the app updates immediately.

**Q: How do I make my app look professional?**
A: Focus on clear layouts, helpful text, and logical organization. Streamlit's defaults look good!

**Q: Can I add my own custom styling?**
A: Yes, but start with Streamlit's built-in options. Custom CSS is possible but not necessary for this course.

## 🆘 Getting Help

- **Discussion Forum**: Share your apps and get feedback
- **Office Hours**: Tuesdays 6-7 PM
- **AI Assistants**: Great for Streamlit syntax and troubleshooting
- **Peer Support**: Test each other's apps and provide UX feedback

## 📈 Assessment Criteria

Your Streamlit app will be evaluated on:
- **Functionality**: App runs without errors and serves its purpose
- **User Experience**: Easy to understand and use
- **Interactivity**: Meaningful use of widgets and user controls
- **Social Impact**: Clear connection to social issues and useful insights
- **Code Quality**: Well-organized code with appropriate comments

---

**Next Week**: [Week 9: Project Office Hours](../week9/README.md)

**Previous Week**: [Week 7: Automating Workflows with Functions + Using AI to Scale Code](../week7/README.md)

# Week 5: Working with External Data & APIs

## 📚 Overview

Learn to collect fresh, real-time data from external sources using APIs (Application Programming Interfaces). This week focuses on connecting to public data sources that provide information about social issues, allowing you to work with live, up-to-date datasets.

## 🎯 Learning Objectives

By the end of this week, you will be able to:

- Understand what APIs are and why they matter for social impact research
- Make API calls to collect data from public sources (UN, World Bank, climate APIs)
- Work with JSON data format and convert it to Pandas DataFrames
- Merge API data with existing datasets for richer analysis
- Handle API errors and rate limits appropriately
- Identify reliable data sources for various social issues

## 🎓 Session Structure (80 minutes)

### Lecture (40 minutes): Why APIs Matter for Social Impact

**Topics Covered:**
- What are APIs and how they provide fresh, live data
- Examples of valuable public APIs for social research:
  - **World Bank**: Economic and development indicators
  - **UN Data**: Global statistics and SDG progress
  - **Climate APIs**: Weather, temperature, and environmental data
  - **COVID-19 APIs**: Health and pandemic response data
- Understanding JSON data format
- API authentication and rate limits
- Ethics of data collection from APIs

### Tutorial (40 minutes): Your First API Connection

**Hands-on Activities:**
- Connect to a simple public API (World Bank or UN Data)
- Make your first API request using Python's `requests` library
- Parse JSON responses and convert to Pandas DataFrames
- Merge API data with your existing dataset
- Handle common API errors and troubleshoot issues

## 🏗️ Mini-Deliverable

**Assignment:** Create a notebook that fetches API data and merges it with your existing dataset.

**Requirements:**
1. **Choose a relevant API** that provides data related to your social issue
2. **Make successful API calls** and retrieve data
3. **Convert JSON to DataFrame** with proper column names
4. **Merge with existing data** to create a richer dataset
5. **Document the process** with clear explanations of what data you're getting
6. **Handle errors gracefully** with try/except blocks

### Example API Integration:
```python
import requests
import pandas as pd

# Example: World Bank API for education data
def get_world_bank_data(indicator, countries, start_year=2010):
    """Fetch data from World Bank API"""
    base_url = "http://api.worldbank.org/v2/country"
    
    # Build API URL
    countries_str = ";".join(countries)
    url = f"{base_url}/{countries_str}/indicator/{indicator}"
    
    params = {
        'date': f'{start_year}:2023',
        'format': 'json',
        'per_page': 1000
    }
    
    try:
        response = requests.get(url, params=params)
        response.raise_for_status()  # Raise error for bad status codes
        
        data = response.json()[1]  # World Bank returns [metadata, data]
        
        # Convert to DataFrame
        df = pd.DataFrame(data)
        df = df[['country', 'date', 'value']].rename(columns={
            'country': 'country_info',
            'date': 'year', 
            'value': 'literacy_rate'
        })
        
        # Extract country name from nested dict
        df['country'] = df['country_info'].apply(lambda x: x['value'])
        df = df.drop('country_info', axis=1)
        
        return df
        
    except requests.exceptions.RequestException as e:
        print(f"API request failed: {e}")
        return None

# Use the function
countries = ['USA', 'GBR', 'DEU', 'FRA']
literacy_data = get_world_bank_data('SE.ADT.LITR.ZS', countries)

if literacy_data is not None:
    print(f"Retrieved {len(literacy_data)} records")
    print(literacy_data.head())
```

## 📁 Files Structure

```
week5/
├── README.md
├── notebooks/
│   ├── lecture_apis_introduction.ipynb
│   ├── tutorial_first_api_call.ipynb
│   └── assignment_api_integration.ipynb
├── examples/
│   ├── world_bank_example.ipynb
│   ├── un_data_example.ipynb
│   └── climate_api_example.ipynb
├── data/
│   ├── api_responses/
│   └── merged_datasets/
└── resources/
    ├── useful_apis.md
    ├── json_guide.md
    └── troubleshooting_apis.md
```

## 📖 Key Concepts Introduced

### API Fundamentals
- **API (Application Programming Interface)**: Way for programs to communicate
- **Endpoints**: Specific URLs that provide different data
- **Parameters**: Options to customize your data request
- **JSON**: JavaScript Object Notation - common data format for APIs
- **Rate Limits**: Restrictions on how often you can make requests

### Essential Python Patterns for APIs
```python
import requests
import pandas as pd
import json

# Basic API request
response = requests.get('https://api.example.com/data')
data = response.json()

# With parameters
params = {'country': 'USA', 'year': 2020}
response = requests.get('https://api.example.com/data', params=params)

# Error handling
try:
    response = requests.get(url)
    response.raise_for_status()  # Raises exception for HTTP errors
    data = response.json()
except requests.exceptions.RequestException as e:
    print(f"Error: {e}")
```

### Working with JSON Data
- **Nested structures**: APIs often return complex, nested data
- **Data extraction**: Pull out the specific fields you need
- **DataFrame conversion**: Transform JSON into tabular format
- **Data cleaning**: Handle missing values and inconsistent formats

## 🌍 Recommended APIs for Social Impact

### Global Development & Economics
- **World Bank Open Data API**: Development indicators, poverty, education, health
- **UN Data API**: Population, environment, gender equality
- **OECD API**: Economic indicators, social statistics
- **Gapminder API**: Historical development data

### Climate & Environment  
- **OpenWeatherMap API**: Current and historical weather data
- **NASA Climate API**: Temperature, sea level, CO2 data
- **World Air Quality API**: Pollution and air quality measurements

### Health & Demographics
- **WHO Global Health API**: Disease data, health statistics
- **COVID-19 APIs**: Pandemic tracking and response data
- **Census APIs**: Population and demographic data

### Social Issues
- **Crime Data APIs**: City and regional crime statistics
- **Education APIs**: School performance, enrollment data
- **Housing APIs**: Real estate, affordability, homelessness data

## 🎥 Video Resources

1. **What are APIs and Why They Matter** (15 min)
2. **Making Your First API Call** (20 min)
3. **Working with JSON Data** (15 min)
4. **Merging API Data with Existing Datasets** (10 min)

## 🔗 Additional Resources

### API Documentation
- [Requests Library Documentation](https://docs.python-requests.org/)
- [JSON Tutorial](https://www.w3schools.com/js/js_json_intro.asp)
- [World Bank API Guide](https://datahelpdesk.worldbank.org/knowledgebase/articles/889392)

### Practice APIs (No Authentication Required)
- [JSONPlaceholder](https://jsonplaceholder.typicode.com/) - Practice API
- [REST Countries](https://restcountries.com/) - Country information
- [Open Library](https://openlibrary.org/developers/api) - Book data

## ❓ Common Questions

**Q: Do I need an API key for all APIs?**
A: No! Many public APIs (like World Bank, REST Countries) don't require authentication. Others provide free tiers.

**Q: What if the API is down or returns an error?**
A: Always use try/except blocks and have a backup plan. Save successful API responses locally.

**Q: How often can I call an API?**
A: Check the API documentation for rate limits. Most allow hundreds of requests per hour for free accounts.

**Q: The JSON data looks confusing. How do I find what I need?**
A: Print the JSON structure first, then navigate step by step. Use online JSON viewers to explore complex structures.

## 🆘 Getting Help

- **Discussion Forum**: Share API endpoints and troubleshoot together
- **Office Hours**: Tuesdays 6-7 PM
- **AI Assistants**: Great for debugging API code and JSON parsing
- **Peer Support**: Exchange useful API endpoints and examples

## 📈 Assessment Criteria

Your API integration assignment will be evaluated on:
- **Successful API Connection**: Code makes working requests to external API
- **Data Processing**: JSON data is properly converted to usable DataFrame
- **Integration Quality**: API data is meaningfully merged with existing dataset
- **Error Handling**: Code includes appropriate try/except blocks
- **Documentation**: Clear explanation of what data source you chose and why

---

**Next Week**: [Week 6: Intro to Predictive Analytics (without heavy math)](../week6/README.md)

**Previous Week**: [Week 4: Organizing Projects with GitHub + First Encounter with AI Helpers](../week4/README.md)

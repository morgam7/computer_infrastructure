# My repository for Computer Infrastructure

**by Marcella Morgan (contactmarcellamorgan@gmail.com)**

# Computer Infrastructure - Automating Weather Data

This is the repository for my project for the Computer Infrastructure module of the Higher Diploma in Science in Data Analytics, delivered by ATU Galway-Mayo. My lecturer was Ian McLoughlin.

In this project, I demonstrate skills learned throughout the module, including using the command line, automating scripts, and analysing real-world weather data. The final component automates data collection from the Met Éireann weather API using GitHub Actions and presents a pandas-based analysis of the data.

## Why This Project Is Useful
This project is aimed at showcasing how to combine command line tools, automation, and Python data analysis. While the code and analysis might not add groundbreaking insights to weather data, it serves as a practical example for anyone starting out with scripting, data collection, and analysis. It might also help future students of the Computer Infrastructure module understand how to approach the tasks and project.

## Getting Started
To get started with this repository, you'll need:
1. **Python**: Install Python (I recommend using Anaconda).
2. **A notebook editor**: I used Visual Studio Code, but you can also use Jupyter Notebook or Google Colab.


## Libraries Used
Here are the main libraries and tools I used in the project:
- **Pandas**: For data manipulation and analysis, including reading and summarising JSON weather files.
- **Matplotlib**: For visualising the weather data, such as temperature trends.
- **NumPy**: For numerical operations used in the analysis.
- **GitHub Actions**: To automate the daily collection of weather data.

## Challenges Faced
Throughout the project, I faced several challenges:
1. **Setting Up GitHub Actions**: Configuring the workflow to automate daily data collection was tricky, especially resolving issues around workflow permissions.
2. **Data Cleaning**: The weather data had missing values, zeros, and inconsistencies. Handling these and deciding whether to treat zeros as missing values was a key part of the analysis.
3. **Presentation**: Creating meaningful visualisations and ensuring the notebook was professional yet clear for a technical audience.

## Getting Help
If you have questions about this repository or the project, feel free to contact me at [contactmarcellamorgan@gmail.com](mailto:contactmarcellamorgan@gmail.com). Alternatively, you can submit an issue via GitHub issues.


### Task 9: Pandas Data Analysis

For this task, I used pandas to load and analyse weather data files downloaded via my automated script. The aim was to explore the dataset, identify any issues, and create clear visualisations of the data.

#### What I Did
- Loaded the dataset using `pandas.read_csv()` and explored its structure with `df.info()` and `df.describe()` to get a sense of the columns and data types.
- Checked for missing values using `df.isnull().sum()` and identified areas where the data needed cleaning or conversions.
- Created a new `datetime` column by combining the existing `date` and `reportTime` columns, which made time-series analysis easier.
- Produced a line plot to show temperature trends over time.
- Added a heatmap-style visualisation of the temperature data using `temperature_df.style.background_gradient(cmap="coolwarm")`.

#### Challenges I Faced
- **Data Formatting Issues**:  
  At one point, the `reportTime` column started showing dates instead of just times. This happened because pandas hadn’t been told to treat it as a time column, so it misinterpreted the data. I fixed it by converting the column to `datetime` and then extracting just the time part using `.dt.time`.  

- **GitHub Incompatibility**:  
  The `background_gradient` styling for the DataFrame didn’t show up on GitHub because it relies on HTML/CSS, which isn’t supported. I looked at alternatives like exporting the styled table as an HTML file or using a static heatmap with matplotlib/seaborn.  

- **Column Data Types**:  
  Some columns were incorrectly treated as objects instead of numbers or datetime types. I used `pd.to_numeric()` and `pd.to_datetime()` to sort this out.  

#### Lessons Learned
This task was a great exercise in cleaning and analysing messy real-world data. I ran into several issues with data types, missing values, and formatting but worked through them step by step. The process helped me understand pandas better and showed me how important it is to carefully check how data is being handled at every stage.

---

This project has been a fantastic learning experience, pushing me to tackle real-world problems and learn how to automate workflows effectively. I hope it proves helpful for anyone exploring similar projects!


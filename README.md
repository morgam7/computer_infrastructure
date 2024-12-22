# Computer Infrastructure - Automating Weather Data
**Author:** Marcella Morgan
**Image Credit:** DALL·E 

![My First GitHub Workflow](images/my_first_github_workflow.png)

This is the repository for my project for the Computer Infrastructure module of the [Higher Diploma in Science in Data Analytics given by ATU Galway-Mayo](https://www.gmit.ie/higher-diploma-in-science-in-computing-in-data-analytics). My lecturer was [Ian McLoughlin](https://github.com/ianmcloughlin).

In this project, I demonstrate skills learned throughout the module, including using the command line, automating scripts, and analysing real-world weather data. The final component automates data collection from the Met Éireann weather API using GitHub Actions and presents a pandas-based analysis of the data.

## Getting Started

To get started with this repository, you’ll need:  
1. **Python**: Install Python (I recommend using [Anaconda](https://www.anaconda.com/), which includes all the necessary tools and libraries).  
2. **A Notebook Editor**: I used Visual Studio Code, but you can also use [Jupyter Notebook](https://jupyter.org/) or [Google Colab](https://colab.research.google.com/).  

If using Google Colab, you can easily upload the Jupyter Notebook file (.ipynb) and run it directly in your browser without needing to set up Python locally. Just make sure you have the required Python libraries installed in your environment to follow along with the code.

## Why This Project Is Useful
This project is aimed at showcasing how to combine command line tools, automation, and Python data analysis. It serves as a practical example for anyone starting out with scripting, data collection, and analysis. It might also help future students of the Computer Infrastructure module understand how to approach the tasks and project.

## Libraries Used
Here are the main libraries and tools I used in the project:
- **Pandas**: For data manipulation and analysis, including reading and summarising JSON weather files.
- **Matplotlib**: For visualising the weather data, such as temperature trends.
- **NumPy**: For numerical operations used in the analysis.
- **GitHub Actions**: To automate the daily collection of weather data.

A `requirements.txt` file is included in the root of the repository. It lists all the Python dependencies needed to run this project.

To install the dependencies, follow these steps:

1. Ensure you have Python and pip installed on your system.
2. Navigate to the project directory in your terminal.
3. Run the following command to install all the required packages:

```bash
pip install -r requirements.txt
```

## Tasks 1-7:

In these tasks, I built foundational skills in command-line operations and scripting. Starting with creating and managing directories, I used commands like mkdir and touch to structure files and handle timestamps. Tasks included logging and formatting dates with the date command, appending outputs to files, and automating these processes with a bash script.

I also downloaded live weather data from Met Éireann using wget and saved it with timestamped filenames. Finally, I documented the process in a Jupyter notebook, explaining the commands and their purpose, showcasing a progression from manual command-line work to simple automation.

## The Project:

For the project, I automated the process of collecting and storing weather data from Met Éireann. Using a GitHub Actions workflow, I set up a weather.sh script to run daily at 8 AM, downloading weather data and saving it with timestamped filenames in the data/weather directory. The workflow was defined in a YAML file, specifying tasks like cloning the repository, running the script, and committing new data back to the repository.

This automation ensures the data is collected consistently without manual input, showcasing the integration of bash scripting with GitHub Actions to streamline repetitive tasks.


## Task 9: Pandas Data Analysis

For this task, I used pandas to load and analyse weather data files downloaded via my automated script. The aim was to explore the dataset, identify any issues, and create clear visualisations of the data. I will go into a bit more detail here of what I did and the challenges I faced.

### What I Did
- Loaded the dataset using `pandas.read_csv()` and explored its structure with `df.dtypes()` and `df.describe()` to get a sense of the columns and data types.
- Checked for missing values using `df.isnull().sum()` and identified areas where the data needed cleaning or conversions.
- Created a new `datetime` column by combining the existing `date` and `reportTime` columns, which made time-series analysis easier.
- Produced a line plot to show temperature trends over time.
- Added a heatmap-style visualisation of the temperature data using `temperature_df.style.background_gradient(cmap="coolwarm")`.

### Challenges I Faced
- **Data Formatting Issues:** 
  At one point, the `reportTime` column started showing dates instead of just times. This happened because pandas hadn’t been told to treat it as a time column, so it misinterpreted the data. I fixed it by converting the column to `datetime` and then extracting just the time part using `.dt.time`.  

- **GitHub Incompatibility:**
  The `background_gradient` styling for the DataFrame didn’t show up on GitHub because it relies on HTML/CSS, which isn’t supported. So the pretty colours didn't survive the journey to GitHub.

- **Column Data Types:** 
  Some columns were incorrectly treated as objects instead of numbers or datetime types. I used `pd.to_datetime()` to sort this out.

- **Pulling and Pushing to GitHub:** 
  I encountered a new issue after setting up the automated GitHub Actions workflow. It was constantly adding new data files and because I hadn't gotten into the habit of doing a git pull before making edits and, I ran into problems when trying to push. By committing my changes and using git pull origin main, I resolved the issue since there was no conflict between the new data files and my edits. But it taught me about how important it is to keep on top of pulling files and keeping track of edits. I imagine this can get very messy when working on bigger projects. 

This project has been a fantastic learning experience, pushing me to tackle real-world problems and learn how to automate workflows effectively. I hope it proves helpful for anyone exploring similar projects!

## Getting Help
If you have questions about this repository or the project, feel free to contact me at [contactmarcellamorgan@gmail.com](mailto:contactmarcellamorgan@gmail.com). Alternatively, you can submit an issue via GitHub issues.

## Resources
I relied on Python libraries like pandas and matplotlib throughout these assignments. Additional references include:
- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [Matplotlib Documentation](https://matplotlib.org/stable/contents.html)
- I also used Chat GPT when I found myself stumped. It was useful at explaining very specific problems I was having quickly, but it also got a few things wrong! 

### General Environment Issues:
https://www.geeksforgeeks.org/how-to-run-bash-script-in-linux/  
https://stackoverflow.com/questions/19986306/what-does-the-mean-when-running-commands  
https://www.reddit.com/r/learnpython/comments/1r2nqm/python_scripts_running_from_command_prompt_but/  
https://superuser.com/questions/77247/how-do-i-install-wget-for-windows  
https://stackoverflow.com/questions/29113456/wget-not-recognized-as-internal-or-external-command  
https://askubuntu.com/questions/1094739/man-command-not-working-in-ubuntu-18-04  

### Git and GitHub:
https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/controlling-permissions-for-github_token  
https://github.com/orgs/community/discussions/35410  
https://stackoverflow.com/questions/54278883/forgot-to-git-pull-before-working-and-now-i-cant-git-push  
https://www.reddit.com/r/git/comments/w337j4/how_to_resolve_several_merge_conflicts_when/  

### Python and Pandas
https://stackoverflow.com/questions/36692861/avoiding-error-from-pd-to-datetime-in-pandas  
https://pandas.pydata.org/docs/user_guide/style.html  
https://www.geeksforgeeks.org/make-a-gradient-color-mapping-on-a-specified-column-in-pandas/  
https://stackoverflow.com/questions/76506990/github-doesnt-reflect-pandas-styles  
https://github.com/mwaskom/seaborn/issues/1090  



## END


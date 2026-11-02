# MAT311_DS_with-AI
Data Science Assignment using AI

# Credit Card Fraud: Exploratory Data Analysis with AI

## What this notebook analyzes

This repository contains one notebook, `AI_assignment.ipynb`, that performs an exploratory data analysis (EDA) of a credit card transaction dataset (`card_transdata.csv`, 999 rows and 8 columns). The goal is to understand what separates fraudulent transactions from legitimate ones. The notebook covers:

- Loading and inspecting the raw data (shape, data types, summary statistics)
- Data wrangling: counting missing values and dropping the 22 rows that contain them (977 rows remain)
- Single-variable visualizations: countplots for fraud, PIN use, repeat retailer, and online orders, plus histograms for purchase price ratio and distance from home
- Bivariate visualizations: count plots and stacked percentage plots showing how fraud breaks down by PIN use, chip use, and online orders, plus scatterplots of distance versus purchase price ratio, colored by fraud status

## How I used AI

I used **Claude Sonnet 5.5** (Anthropic) through the Claude chat interface to generate all of the code. I wrote my own prompts, one step at a time, describing what I wanted to see (for example, "create a countplot where the hue is fraud and compare with green and red columns"). The key prompts appear in the notebook as markdown cells directly above the code they produced, and each is labeled with the AI used. I did not include the back-and-forth where I asked Claude to adjust its output (for example, splitting plots into separate figures or changing axis labels). The final prompt in the notebook asked Claude to write the explanatory markdown (title, data context, section headers, and the justification for dropping null values).

## Reflection on AI Assistance

**Benefits:** The biggest benefit using AI was speed, I was able to quickly and efficiently load, clean, visualize the data. Writing this code myself would have resulted in longer, more drawn out steps where I had to know proper syntax, and likely debug when I missed something, or had the wrong syntax. Claude on the other hand "knows" syntax better and had little bugs in its implementation as seen below.

**Dangers and Verification:** Someone using AI without learning or knowing Data Science could trust that the output and what the AI model is generating is correct without properly verifying the output. I ran into an issue like this when Claude made the scatterplots, the plot had both green and red dots for non-fraudulent and fraudulent data points respectively. However, the legend showed that both "Non-Fraudulent" and "Fraudulent" points were green. I noticed this by confirming the output and double checking what the code was producing, Claude wrote code that overwrote seaborn's legend marker. I needed to check Claude's work and the output of its code throughout this exercise. One example was the one mentioned above with the legend issue, another includes an issue with data types. Claude originally said that only one of the columns was stored as a decimal, however, looking at out info() output I could see there were several binary columns that were also stored as floats. I also confirmed the row counts made sense, and the PIN plots missing red bar for "PIN used" matched the counts showing that there was no fraud in this group.

# python-homework
This is my submission for the 2nd Module challenge for the RICE 2023 Fintech bootcamp 'python-homework'

# Instructions
In this assignment, you will create a Python script that analyzes the financial records of your company.  Inside your starter code, you will find a financial dataset in the budget_data.csv file. This dataset is composed of two columns, Date and Profit/Losses. (Thankfully, your company has rather lax standards for accounting, so the records are simple.)

* Your task is to create a Python script that analyzes the records to calculate each of the following:

* The total number of months included in the dataset

* The net total amount of Profit/Losses over the entire period

*The average of the changes in Profit/Losses over the entire period

*The greatest increase in profits (date and amount) over the entire period

*The greatest decrease in losses (date and amount) over the entire period

# My Code

import pandas as pd

### Load the CSV file into a DataFrame
file_path = 'budget_data.csv'
df = pd.read_csv(file_path)

### Calculate the total number of months
total_months = len(df)

### Calculate the net total amount of Profit/Losses
net_total = df['Profit/Losses'].sum()

### Calculate the changes in Profit/Losses and find the average change
df['Change'] = df['Profit/Losses'].diff()
average_change = df['Change'].mean()

### Find the greatest increase and decrease in profits
greatest_increase = df.loc[df['Change'].idxmax()]
greatest_decrease = df.loc[df['Change'].idxmin()]


### Format the output
analysis_result = f'''
Financial Analysis
----------------------------
Total Months: {total_months}
Total: ${net_total:,.2f}
Average Change: ${average_change:,.2f}
Greatest Increase in Profits: {greatest_increase['Date']} (${greatest_increase['Change']:,.2f})
Greatest Decrease in Profits: {greatest_decrease['Date']} (${greatest_decrease['Change']:,.2f})
'''

print(analysis_result)

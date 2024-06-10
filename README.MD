# **MetricForge**
## Library for generating validation dataset and evaluation metrics

### List of functions:

**script_valid** - A function for creating validation dataset or creating a new column, using your own model. To do this, enter in function your function, which generating answer. Otherwise select model what you need and prompt and then new CSV file would be generated

**calculate_metrics** - A function for calculating Accuracy and F1 Score metrics. We use the Schlern library for calculations. Column one and Column two can be both the name of the column and its number

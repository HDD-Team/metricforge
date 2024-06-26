# **MetricForge**
## Library for generating validation dataset and evaluation metrics

### Use  `import metricforge.main as mf`  
### To use this library you need to install ollama and pull model, that you work with
### List of functions:

##### script_valid


Function for creating validation dataset or creating a new column, using your own model. 
To do this, enter in function your function, which generating answer. 
Otherwise select model which you need and prompt, then new CSV file would be generated

###### variables
**file_base** - your csv file with train data. `"your_csv.csv"` <br />
**df_name** - name of your new dataframe <br />
**column_name** - name of column which will be used for valid generation <br />
**file_new** - name of new csv file `"new_csv.csv"` <br />
**model_name** - name of model which you want to use <br />
**prompt** - prompt for LLM for generating valid dataset <br />

**Example usage of function:**

`mf.script_valid(file_base = "dataset.csv", df_name = "generated_answer",column_name = "data/dictionary",prompt = "You are a validation generator dataset bot. "
                                                                                     "You are creating a validation dataset based on a training dataset. "
                                                                                     "Based on the given query, generate a similar query.",file_new = "file_new.csv",model_name="mistral:instruct")`

##### calculate_metrics

Function for calculating Accuracy and F1 Score metrics. We use the Schlern library for calculations. Column one and Column two can be both the name of the column and its number

###### variables
**csv_file** - your csv file with data. `"your_csv.csv"` <br /> 
**column_one** - number or name of first column, where it is your original data <br /> 
**column_two** - number or name of second column, where it is generated or predicted data <br />

**Example usage of function:**

`csv_file = r"validated_dataset.csv"
accuracy, f1 = mf.calculate_metrics(csv_file, 3, 4)
print("Accuracy:", accuracy)
print("F1 Score:", f1)`

##### script_generate

Function for applying RAG function "model_query" to the provdied dataset, to generate answers for "column_name" in your dataset. By default model_query generate answer in str format.

###### variables

**csv_file** - your csv file with provided data. `"your_csv.csv"` <br />
**column_name** - name of column which will be used for answer generation <br />
**dfnew_name** - name of new df <br />
**model_query** - your function with RAG chain, where result is worg of RAG chain <br />

**Example usage of function:**

`mf.script_generate_json(csv_file=r"datavalid.csv", column_name="data/dictionary",
                   model_query=model_query,dfnew_name="testing.csv")`

##### script_generate_json

Function for applying RAG function "model_query" to the provdied dataset, to generate answers for "column_name" in your dataset. This function assumes your LLM generate answer in JSON view, so you need to select which name from JSON you want extract in desired_data variable

###### variables

**csv_file** - your csv file with provided data. `"your_csv.csv"` <br />
**column_name** - name of column which will be used for answer generation <br />
**dfnew_name** - name of new df <br />
**model_query** - your function with RAG chain, where result is worg of RAG chain <br />
**desired_data** - name of json data, which will be taken from json and inputted in result CSV column <br />

**Example usage of function:**

`mf.script_generate_json(csv_file=r"datavalid.csv", column_name="data/dictionary",
                   model_query=model_query,dfnew_name="testing.csv", desired_data="data/url")`

# The Fundamentals of Data Analytics Part 1


# Data Basics
#### Define the Concept of Data
  - Data: Data refers to raw facts, figures, or information that can be processed to gain insights or knowledge. It can be anything from numbers and text to images and videos.


#### Describe Basic Data Variable Types
  - Boolean:
    - Definition: Boolean data type represents two possible values: true or false.
    - Example:
      - _is_valid = True_
        
  - Numeric:
    - Definition: Numeric data types represent numbers and can be further categorized into integers and floating-point numbers.
    - Example:
      - _age = 25
      - height = 1.75_
        
  - String:
    - Definition: String data type represents textual data, consisting of a sequence of characters.
    - Example:
      - _name = "John Doe"_


#### Describe Basic Structures Used in Data Analytics
  - Tables:
    - Definition: Tables organize data into rows and columns, providing a structured way to store and manipulate data.
    - Example (using Pandas DataFrame):
      - _import pandas as pd

        data = {'id': [1, 2, 3],
                'name': ['John', 'Jane', 'Doe'],
                'age': [25, 30, 35]}
        df = pd.DataFrame(data)
        df_
  
  - Rows and Columns:
    - Definition: Rows represent individual records in a table, while columns represent attributes or fields of the data.
    - Example: (_Already shown above in DataFrame example_)
    
  - Lists:
    - Definition: Lists are ordered collections of elements that can be of different types.
    - Example:
      _numbers = [1, 2, 3, 4, 5]
      numbers_


#### Describe Data Categories:
  - Qualitative Data:
    - Definition: Qualitative data describes qualities or characteristics and is non-numeric.
    - Example: Gender (Male, Female), Color (Red, Blue, Green).
  - Quantitative Data:
    - Definition: Quantitative data represents quantities or numerical measurements.
    - Example: Height, Weight, Age.
  - Structured Data:
    - Definition: Structured data is organized and follows a specific schema or format.
    - Example: Relational databases, CSV files.
  - Unstructured Data:
    - Definition: Unstructured data lacks a predefined structure and organization.
    - Example: Text documents, Images, Videos.
  - Metadata:
    - Definition: Metadata provides information about other data.
    - Example: File creation date, Data source, Data format.
  - Big Data:
    - Definition: Big Data refers to datasets that are too large or complex to be processed using traditional data processing applications.
    - Example: Social media data, Sensor data, Genomic data.



# Data Manipulation
### Import, Store, and Export Data
  - Using Python (Pandas) for CSV Files:
    _import pandas as pd
    
    # Import data from CSV file
    df = pd.read_csv('data.csv')
    
    # Store data to SQL database
    df.to_sql('table_name', connection_object)
    
    # Export data to CSV file
    df.to_csv('exported_data.csv', index=False)_
  
  - Using SQL for Database Import/Export:
    _-- Import data from CSV file into SQL database
    LOAD DATA INFILE 'data.csv' INTO TABLE table_name FIELDS TERMINATED BY ',' LINES TERMINATED BY '\n';
    
    -- Export data from SQL database to CSV file
    SELECT * INTO OUTFILE 'exported_data.csv' FIELDS TERMINATED BY ',' LINES TERMINATED BY '\n' FROM table_name;_

  - Using Microsoft Excel (Power Query) for Import/Export:
    _let
        Source = Csv.Document(File.Contents("data.csv"),[Delimiter=",", Columns=4, Encoding=1252, QuoteStyle=QuoteStyle.None]),
        table = Table.FromList(Source, Splitter.SplitByNothing(), null, null, ExtraValues.Error),
        #"Changed Type" = Table.TransformColumnTypes(table,{{"Column1", type text}, {"Column2", type text}, {"Column3", type text}, {"Column4", type text}}),
        #"Exported Data" = Table.ToCsv(#"Changed Type", "exported_data.csv")
    in
        #"Exported Data"_

    
#### Common Data Storage File Formats:
  - Delimited Data Files (CSV): Delimiter-separated values, commonly comma-separated (CSV) or tab-separated (TSV).
    - Example: data.csv
      
  - XML (eXtensible Markup Language): Stores data in a structured format using tags.
    - Example: data.xml
    - Example Structure:
      _<data>
          <record>
              <id>1</id>
              <name>John</name>
              <age>30</age>
          </record>
          <record>
              <id>2</id>
              <name>Jane</name>
              <age>25</age>
          </record>
      </data>_
    
  - JSON (JavaScript Object Notation): Stores data in a lightweight, human-readable format.
    - Example: data.json
    - Example Structure:
      _[
          {"id": 1, "name": "John", "age": 30},
          {"id": 2, "name": "Jane", "age": 25}
      ]_


### Clean Data
- Purpose of Data Cleaning: Data cleaning aims to improve data quality by identifying and correcting errors, inconsistencies, and missing values.
    
- Common Practices:
  - Handling NULL Values: Replace NULL values with a default value or fill them using statistical measures.
    _# Handling NULL values in a DataFrame using Pandas
    df.fillna(0, inplace=True)  # Replace NULL values with 0_

  - Handling Special Characters: Remove or replace special characters that may cause issues during analysis.
    _# Removing special characters from a column in a DataFrame using Pandas
    df['column_name'] = df['column_name'].str.replace('[^a-zA-Z0-9]', '')_
    
  - Trimming Spaces: Remove leading and trailing spaces from text data.
    _# Trimming spaces from a column in a DataFrame using Pandas
    df['column_name'] = df['column_name'].str.strip()_

  - Inconsistent Formatting: Standardize data formats to ensure consistency.
    _# Converting text data to lowercase in a column using Pandas
    df['column_name'] = df['column_name'].str.lower()_

  - Removing Duplicates: Identify and remove duplicate records from the dataset.
    _# Removing duplicates from a DataFrame using Pandas
    df.drop_duplicates(inplace=True)_

  - Imputing Data: Fill missing values with estimated or calculated values.
    _# Imputing missing values with mean in a DataFrame using Pandas
    mean_value = df['column_name'].mean()
    df['column_name'].fillna(mean_value, inplace=True)_
    
- Validating Data
  - Definition: Data validation ensures that the data meets certain quality standards or criteria.
    _# Validating data to check for NULL values in a DataFrame using Pandas
    if df.isnull().values.any():
        print("Data contains NULL values.")
    else:
        print("Data is valid.")_

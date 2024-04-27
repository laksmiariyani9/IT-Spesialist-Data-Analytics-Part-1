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
- Importing Data
  - Definition: Importing data involves bringing data from external sources into a data analytics environment. These sources could include databases, spreadsheets, APIs, or streaming sources.
  - Purpose: Data importation is the first step in the data analysis pipeline. It allows analysts to access the raw data they need for analysis.
  - Methods: Data can be imported using various methods such as file uploads, database connections, API calls, or data streaming protocols.
  - Challenges: Ensuring data quality, handling large volumes of data efficiently, and dealing with diverse data formats are common challenges in data importation.

- Storing Data
  - Definition: Storing data involves saving imported data in a structured and organized manner within a data storage system. This system could be a database, a data warehouse, or a data lake.
  - Purpose: Storing data allows for easy access, retrieval, and manipulation of data for analysis. It also provides a centralized repository for storing large volumes of data.
  - Methods: Data can be stored using various storage technologies, including relational databases, NoSQL databases, cloud storage services, and distributed file systems.
  - Considerations: Factors such as data security, scalability, performance, and cost need to be considered when choosing a data storage solution.

- Exporting Data
  - Definition: Exporting data involves transferring data from a data analytics environment to external destinations or systems. These destinations could include other databases, applications, visualization tools, or file formats.
  - Purpose: Exporting data allows analysts to share insights, reports, or processed data with stakeholders, integrate data with other systems, or archive data for future use.
  - Methods: Data can be exported in various formats such as CSV, Excel, JSON, SQL, or through APIs and integration platforms.
  - Considerations: Data privacy, security, and compliance with regulations such as GDPR or HIPAA are crucial considerations when exporting data, especially when sharing sensitive information.
    
    ##### Using Python (Pandas) for CSV Files:
    _import pandas as pd
    
    # Import data from CSV file
    df = pd.read_csv('data.csv')
    
    # Store data to SQL database
    df.to_sql('table_name', connection_object)
    
    # Export data to CSV file
    df.to_csv('exported_data.csv', index=False)_
  
    ##### Using SQL for Database Import/Export:
    _-- Import data from CSV file into SQL database
    LOAD DATA INFILE 'data.csv' INTO TABLE table_name FIELDS TERMINATED BY ',' LINES TERMINATED BY '\n';
    
    -- Export data from SQL database to CSV file
    SELECT * INTO OUTFILE 'exported_data.csv' FIELDS TERMINATED BY ',' LINES TERMINATED BY '\n' FROM table_name;_

    ##### Using Microsoft Excel (Power Query) for Import/Export:
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


### Organize Data:
- Purpose of Data Organization: Organizing data aims to structure and arrange it in a way that facilitates analysis and enhances its usability.

- Common Practices:
  - Sorting:
    - Sort data based on one or more columns to arrange it in a specified order.
      _# Sorting DataFrame by a column using Pandas
      df_sorted = df.sort_values(by='column_name', ascending=True)_

  - Filtering:
    - Filter data based on specified conditions to retrieve relevant subsets.
      _# Filtering DataFrame based on a condition using Pandas
      df_filtered = df[df['column_name'] > threshold]_
    
  - Slicing:
    - Extract specific rows or columns from the dataset.
      _# Slicing DataFrame to extract rows and columns using Pandas
      df_slice = df.iloc[0:5, 1:3]  # Rows 0-4, Columns 1-2_
    
  - Transposing:
    - Flip rows and columns to change the orientation of the dataset.
      _# Transposing DataFrame to switch rows and columns using Pandas
      df_transposed = df.transpose()_
    
  - Appending:
    - Combine or append two or more datasets together.
      _# Appending one DataFrame to another using Pandas
      df_appended = df1.append(df2)_
    
  - Truncating:
    - Remove rows or columns from the dataset.
      _# Truncating DataFrame to remove rows based on index using Pandas
      df_truncated = df.truncate(before=0, after=4)  # Keep rows 0-4_
      
- Example:
  - Let's consider an example of sorting and filtering data using Pandas in a Jupyter Notebook:
    _import pandas as pd
    
    # Create a sample DataFrame
    data = {'Name': ['John', 'Jane', 'Doe'],
            'Age': [30, 25, 35],
            'Salary': [50000, 60000, 45000]}
    df = pd.DataFrame(data)
    
    # Sorting DataFrame by Age in descending order
    df_sorted = df.sort_values(by='Age', ascending=False)
    print("Sorted DataFrame:")
    print(df_sorted)
    
    # Filtering DataFrame to get employees older than 30
    df_filtered = df[df['Age'] > 30]
    print("\nFiltered DataFrame:")
    print(df_filtered)_


### Aggregate Data:
- Purpose of Data Aggregation: Aggregating data aims to combine and summarize information to reveal patterns, trends, and statistical insights.

- Common Practices:
  - Grouping:
    - Group data based on one or more variables to perform operations within each group.
      _# Grouping DataFrame by a column and calculating the mean using Pandas
      grouped_df = df.groupby('column_name').mean()_

  - Joining/Merging:
    - Combine data from multiple sources based on common columns or keys.
      _# Joining two DataFrames based on a common column using Pandas
      merged_df = pd.merge(df1, df2, on='common_column')_

  - Summarizing:
    - Calculate summary statistics such as mean, median, sum, etc., for the entire dataset or within groups.
      _# Calculating the sum of a column in a DataFrame using Pandas
      column_sum = df['column_name'].sum()_

  - Pivoting:
    - Restructure the dataset by changing the orientation of the data based on rows and columns.
      _# Pivoting DataFrame to create a pivot table using Pandas
      pivot_table = df.pivot_table(index='row_column', columns='column_column', values='value_column', aggfunc='sum')_
      
- Example:
  - Let's consider an example of grouping and summarizing data using Pandas in a Jupyter Notebook:
    _import pandas as pd
    
    # Create a sample DataFrame
    data = {'Category': ['A', 'B', 'A', 'B', 'A'],
            'Value': [10, 20, 30, 40, 50]}
    df = pd.DataFrame(data)
    
    # Grouping DataFrame by Category and calculating the sum
    grouped_df = df.groupby('Category').sum()
    print("Grouped DataFrame:")
    print(grouped_df)
    
    # Calculating the total sum of the 'Value' column
    total_sum = df['Value'].sum()
    print("\nTotal Sum of 'Value' column:", total_sum)_

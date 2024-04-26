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

# PatternsVisualization
Code for a command line application that allows us to graphically observe the nature of categorical patterns extracted from a database.

There are two items in the repository: The python code which, after the installation of the python modules that it requires, can be executed to generate our visualizations, and an executable file, which can be used even without having python installed.

The code makes use of several python modules such as:

Dominate (For dynamic html generation): is a Python library for creating and manipulating HTML documents using an elegant DOM API. It allows you to write HTML pages in pure Python very concisely.
https://github.com/Knio/dominate


Plotly (To create interactive plots): The interactive graphing library for Python
https://github.com/plotly/plotly.py

In order to execute the code, it is necessary to have those modules installed in our python environment. Once we are prepared to execute the code, we need to put our database in the same folder than the application, as follows:

folder/
|    VisualizationGenerator.exe
|_  Data.csv
Important Considerations:
Our software only works with databases that are in a valid .csv format. If the database to process is in any other format, it must be first converted before visualizations generation.
Our code is for categorical attributes preferently. Even though it supports numerical data, the visualizations for such kind of data are designed to fit with the style of the categorical ones.
Data needs to include a binary column used for pattern extraction, since the class value is a relevant part of the visualization process.
When comparing categorical attributes, the operator to indicate a value that the pattern needs for an attribute to have, is =. The operator to indicate a value that the pattern needs for an attribute to don't have, is !=.
Although is not expected to be used with numerical attributes, if such are included the operators valid to perform comparisons with them are (<, <=, >, >=).
When passing the attribute to the code, string values must be enclosed by single quotes ('), instead of double quotes (“). This is only for the attribute value, not for the attribute column name, as It will be seen below.
Execution parameters:
In order to execute the generator three patterns are expected, as follows:

VisualizationGenerator.exe “Pattern to evaluate” DatabaseFile BinaryColumn

Pattern to evaluate: Is the pattern to visualize, it has to be enclosed in double quotes (“) and do not include such character inside of the pattern itself. Each item in the pattern MUST be separated by the word AND in uppercase and spaces. Column names in the pattern have to be written exactly as they appear in the database, and so the values that are being compared. The only two valid operators for categorical items are (=, !=). Patterns can be of a maximum number of items of 4. A number of items in the pattern greater than that, will not work properly.

DatabaseFile: A database file in csv format (file extension must be included in the name). In order for the csv format to work properly, is preferred that the values of the database do not contain a comma (,) because it might lead to a wrong file format.

BinaryColumn: The name of the column used for pattern extraction in a binary classification that must exist in the database file. Since we are talking about a binary classification problem, it is expected for the column to only have two values.
Example:

VisualizationGenerator.exe "Titulo del expediente != 'SERVICIOS PROFESIONALES PARA LA ELABORACIoN DE AVALuOS' AND Nombre de la UC = 'DICONSA-Direccion de Comercializacion #008VSS998'" Clase2.csv Class

The execution takes around 3 to 4 minutes, to execute and generate the graphs, depending on the size of the database and the length of the pattern. Once it has finished, it produces an index.html file, and extra html files depending on the number of items in the pattern. Index will allow us to see the four graphs at the same time and interact with them. Index.html file is expected to automatically display in the default browser of the operating system.

# Tabular-Model-Context-for-AI

Simplify the context of tabular models for use with AI.

The C# script is designed to export your Power BI model's metadata to a text file structure (.txt) on your computer. The goal is to make the documentation easy for both humans to read and for other tools to process.

Here is a summary of what the code does in its current state:

Output Directory



It creates all files in a main folder that you define in the outputBasePath variable (currently set to C:\\Result).



It includes error handling in case the script doesn't have permission to write to that folder, in which case it will notify you to change the path.

Generated File Structure



model\_summary\_and\_config.txt: A summary file containing a total count of tables, measures, and relationships, in addition to the configuration used for the export.



relationships.txt: A file that documents all model relationships in a YAML-like format. This file is saved in the main directory.

One .txt file per table: For each table in your model, a text file is created. The filename is taken from the table name, but spaces are replaced with underscores (e.g., the "Net Sales" table will be saved as Net\_Sales.txt).



CalculationGroups Folder: If your model has Calculation Groups, this folder is created, and inside it, a .txt file is generated for each group.



Content of Each Table File (<table\_name>.txt)

This is the main file. It contains all the table's information in a structured, YAML-like format.



M or DAX Code: It includes the complete M code that defines the table. Specifically, it replaces #(lf) sequences with actual line breaks to make the code readable. If it's a calculated table, it includes its DAX definition.

Table Details: Name, description, and estimated row count.



Columns: A detailed list of all the table's columns, with their name, data type, description, etc.

Measures: A complete list of all measures belonging to that table, including their DAX expression, dependencies (columns and other measures it uses), and their lineage (indirect dependencies).



In summary, the script has evolved to generate very complete and organized documentation for your model, where each table has its own consolidated file with all its relevant information, and the filenames are cleaner and more compatible with the file system.

With this structure, you can limit the context you give to the agent, so, you can get faster and better responses


## How to use it

Download Tabular Editor https://www.sqlbi.com/tools/tabular-editor/
Open your tabular model, and paste the code from the file "Tabular Model Context" in the c# script editor,
 change the directory in this line 
"string outputBasePath = @"C:\Result"; // Default, puede causar problemas de permisos. Asegúrate de que esta ruta es válida y tienes permisos."
And Run it!


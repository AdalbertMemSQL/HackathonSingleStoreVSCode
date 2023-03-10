[![License: MIT](https://img.shields.io/badge/License-MIT-violet.svg)](https://opensource.org/licenses/MIT)

# SingleStore driver for SQLTools
![logo](icons/singlestore_logo_horizontal_color_on-white_rgb.png)

A Visual Studio Code extension which extends the [SQTools extension](https://marketplace.visualstudio.com/items?itemName=mtxr.sqltools) to work with the SingleStore.

## Features
 - `Connect` to a SingleStoreDB instance
 - `Manage` connections in SQLTools Database Explorer 
 - `View` tables, views, columns, functions, procedures
 - `Generate` `INSERT` queries
 - `Autocomplete` SQL keywords, table and view names, column names, SingleStore built-in 

 functions
 - `Run` SQL queries
 - `Export` SQL query results in CSV and JSON data formats

## Instalation
Launch VS Code Quick Open (`Ctrl+P`), paste the following command, and press enter.
```
ext install singlestore.sqltools-singlestore-driver
```

Alternatively, you can install this extension directly in VSCode IDE from Extensions tab (`Ctrl+Shift+X`) by searching for `@tag:sqltools singlestore`.

## Usage
Here you can see several examples of driver usage.
For more information on how to use SQLTools please refer to [SQLTools documentation](https://vscode-sqltools.mteixeira.dev/en/home/)

### Create a connection
https://user-images.githubusercontent.com/55380838/221791339-c18f8539-8f01-45db-9c7d-94019923e869.mp4
> Note: `Show records default limit` parameter defines the maximum number of rows that will be shown in the result. 

### View tables and views
https://user-images.githubusercontent.com/55380838/221792568-a1345ca9-d44d-4e36-85a1-4311cc99327d.mp4

### Run SQL query
https://user-images.githubusercontent.com/55380838/221792831-3f30c99b-ce27-4e0a-bb6e-6810718f6b10.mp4

### View and edit functions and procedures
https://user-images.githubusercontent.com/55380838/221793272-31b14ad2-f9a1-49a8-8bff-cd7700eeae88.mp4
> Note: When creating a function or a procedure, you must change the delimiter to ensure that the function or procedure definition is correctly passed to the server as a single statement. The default delimiter is a semicolon (;). A problem arises when creating functions or procedures because they use semicolons as statement delimiters within the function body. Therefore, you must change the delimiter setting before creating your function or procedure, and then set it back to a semicolon after the alternate delimiter is no longer needed.
> The DELIMITER commands must be on independent lines. 

Example: 
``` 
DELIMITER //

CREATE OR REPLACE PROCEDURE courses_sp (course_code TEXT, section_number INT, number_students INT) AS
  DECLARE
    code TEXT = UCASE(course_code);
    num_students INT = number_students + 1;
  BEGIN
    INSERT INTO courses VALUES (code, section_number, num_students);
END //

DELIMITER ;
```

## Raising issues
If you have any questions, find a bug, or have a feature request please [open an issue](https://github.com/singlestore-labs/sqltools-singlestore-driver/issues/new).

## Setup development environment
1. Clone this repository and open it in the VS Code.
2. Run `npm install` to install all dependencies.
3. Run `npm run watch`
4. Open `extension.ts` file and press F5. This opens a new VS Code window with a development version of the driver extension loaded.

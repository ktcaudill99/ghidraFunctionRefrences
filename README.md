# Export Function References to JSON (Ghidra Script)

## Overview
This Ghidra script extracts references to all functions in the currently loaded binary and exports them to a JSON file. The script gathers detailed information about each function's references, including address, symbol names, and the function containing the reference.

The resulting JSON file will provide useful insights about function relationships and their usage, making it beneficial for reverse engineering tasks, analysis, or documentation.

## Prerequisites
- **Ghidra version 9.0 or later** installed on your system.
- Basic knowledge of **Ghidra scripting** and **Python**.

## Usage
### Running the Script
1. **Open Ghidra** and load the binary you want to analyze.
2. **Add the Script** to your Ghidra script directory.
   - Save the script as `ExportFunctionReferencesToJson.py` in your Ghidra script folder.
3. **Run the Script**:
   - In Ghidra, open the **Script Manager** and find `ExportFunctionReferencesToJson.py`.
   - Click on the script to execute it.

### Output
- The script will generate a JSON file named `function_references.json` in the user's home directory (i.e., `~/function_references.json`).
- The JSON file will contain a dictionary where each key represents a function name, and each value is a list of references with details like address, symbol name, and containing function.

## Script Breakdown
### Main Steps
1. **Define JSON File Path**: The script creates a path to the JSON file that will be saved in the user's home directory.
2. **Retrieve Functions**: It retrieves all functions in the loaded binary using Ghidra's `FunctionManager`.
3. **Extract References**: The script iterates over each function and extracts its references, including address, symbols, and containing function information.
4. **Write to JSON**: Finally, the data is written to the JSON file.

### Key Functions
- **`run()`**: The main function that orchestrates gathering function references and exporting them.
- **`get_function_references(function)`**: Extracts references for each given function, including the address, symbol, and reference function (if available).

## Example JSON Output
Below is an example of what the output JSON file might look like:

```json
{
    "function1": [
        "00401000 (symbol1) in function 'function2'",
        "00402000 (symbol2)"
    ],
    "function2": [
        "00403000 in function 'function3'"
    ]
}
```

## Troubleshooting
- **Permission Issues**: Make sure you have write permissions to save a file in your home directory.
- **Ghidra Errors**: Ensure that the current binary is properly loaded and that Ghidra's scripting environment is configured correctly.

## License
This script is provided **"as-is"** without warranty of any kind. You are free to use, modify, and distribute it for non-commercial and educational purposes.

## Author
- **Name**: [Your Name]

---

# Export Function References, Incoming and Outgoing Calls to JSON (Ghidra Script)

## Overview
This Ghidra script extracts various references of all functions in the currently loaded binary and exports them into three separate JSON files. The script provides detailed information about references to each function, incoming function calls, and outgoing function calls, which can be helpful for reverse engineering, code analysis, or documentation purposes.

The output JSON files include:
- **Function References**: Lists all references pointing to each function.
- **Incoming Function Calls**: Lists all functions that call each function.
- **Outgoing Function Calls**: Lists all functions called by each function.

## Prerequisites
- **Ghidra version 9.0 or later** installed on your system.
- Basic understanding of **Ghidra scripting** and **Python**.

## Usage
### Running the Script
1. **Open Ghidra**: Start Ghidra and load the desired binary file you wish to analyze.
2. **Add the Script**: Save the script as `ExportFunctionReferencesToJson.py` in your Ghidra script directory.
3. **Run the Script**:
   - Use the **Ghidra Script Manager** to locate and run `ExportFunctionReferencesToJson.py`.
   - The script will create three JSON files in your home directory.

### Output Files
The script generates the following files in your home directory:
1. `<binary_name>_function_references.json`
2. `<binary_name>_incoming_function_references.json`
3. `<binary_name>_outgoing_function_references.json`

Each JSON file contains data represented as a dictionary, where the keys are function names and values are lists of reference details or function calls.

## Script Workflow
### Main Steps
1. **Define JSON File Paths**: The script determines the filenames and paths for saving the JSON files based on the currently loaded Ghidra project.
2. **Retrieve Functions**: It retrieves all functions from the current binary using the Ghidra `FunctionManager`.
3. **Extract References**: The script extracts the following information for each function:
   - **References to the Function**: Extracted using Ghidra's `ReferenceManager`.
   - **Incoming Calls**: Functions calling the current function.
   - **Outgoing Calls**: Functions called by the current function.
4. **Write JSON Files**: The extracted data is written into separate JSON files for easier analysis and organization.

### Key Methods
- **`run()`**: The main method that orchestrates extracting the information and saving it into JSON files.
- **`get_function_references(function)`**: Extracts references, incoming calls, and outgoing calls for the given function.
- **`process_references(references)`**: Processes the references to format them in a readable string representation.

## Example JSON Output
Below is an example structure of the output for each of the JSON files:

### `<binary_name>_function_references.json`
```json
{
    "function1": [
        "00401000 (symbol1) in function 'function2'",
        "00402000 (symbol2)"
    ],
    "function2": [
        "00403000 in function 'function3'"
    ]
}
```

### `<binary_name>_incoming_function_references.json`
```json
{
    "function1": [
        "caller_function1",
        "caller_function2"
    ],
    "function2": [
        "caller_function3"
    ]
}
```

### `<binary_name>_outgoing_function_references.json`
```json
{
    "function1": [
        "called_function1",
        "called_function2"
    ],
    "function2": [
        "called_function3"
    ]
}
```

## Troubleshooting
- **File Path Issues**: Make sure the script has the necessary permissions to write files to your home directory.
- **Monitor Errors**: If the script fails to retrieve incoming or outgoing calls, ensure that the current binary is properly loaded and that Ghidra's monitor object (`ConsoleTaskMonitor`) is functioning.
- **Missing Functions**: If some functions don't appear in the JSON files, ensure they have proper symbols assigned.

## License
This script is provided **"as-is"** without warranty of any kind. Feel free to use, modify, and distribute it for non-commercial purposes.

## Author
- **Name**: [Your Name]



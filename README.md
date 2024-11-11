# ghidraFunctionRefrences
Export Function References to JSON (Ghidra Script)

Overview

This Ghidra script extracts references to all functions in the currently loaded binary and exports them to a JSON file. The script gathers detailed information about each function's references, including address, symbol names, and the function containing the reference.

The resulting JSON file will provide useful insights about function relationships and their usage, making it beneficial for reverse engineering tasks, analysis, or documentation.

Prerequisites

Ghidra version 9.0 or later installed on your system.

Basic knowledge of Ghidra scripting and Python.

Usage

Running the Script

Open Ghidra and load the binary you want to analyze.

Add the Script to your Ghidra script directory.

Save the script as ExportFunctionReferencesToJson.py in your Ghidra script folder.

Run the Script:

In Ghidra, open the script manager and find ExportFunctionReferencesToJson.py.

Click on the script to execute it.

Output

The script will generate a JSON file named function_references.json in the user's home directory (i.e., ~/function_references.json).

The JSON file will contain a dictionary where each key represents a function name, and each value is a list of references with details like address, symbol name, and containing function.

Script Breakdown

Main Steps

Define JSON File Path: The script creates a path to the JSON file that will be saved in the user's home directory.

Retrieve Functions: It retrieves all functions in the loaded binary using Ghidra's FunctionManager.

Extract References: The script iterates over each function and extracts its references, including address, symbols, and containing function information.

Write to JSON: Finally, the data is written to the JSON file.

Key Functions

run(): The main function that orchestrates gathering function references and exporting them.

get_function_references(function): Extracts references for each given function, including the address, symbol, and reference function (if available).

Example JSON Output

Below is an example of what the output JSON file might look like:

{
    "function1": [
        "00401000 (symbol1) in function 'function2'",
        "00402000 (symbol2)"
    ],
    "function2": [
        "00403000 in function 'function3'"
    ]
}

Troubleshooting

Permission Issues: Make sure you have write permissions to save a file in your home directory.

Ghidra Errors: Ensure that the current binary is properly loaded and that Ghidra's scripting environment is configured correctly.

#ghidraFunctions inAndOutCalls

Export Function References to JSON (Ghidra Script)

Overview

This Ghidra script extracts references to all functions in the currently loaded binary and exports them to a JSON file. The script gathers detailed information about each function's references, including address, symbol names, and the function containing the reference.

The resulting JSON file will provide useful insights about function relationships and their usage, making it beneficial for reverse engineering tasks, analysis, or documentation.

Prerequisites

Ghidra version 9.0 or later installed on your system.

Basic knowledge of Ghidra scripting and Python.

Usage

Running the Script

Open Ghidra and load the binary you want to analyze.

Add the Script to your Ghidra script directory.

Save the script as ExportFunctionReferencesToJson.py in your Ghidra script folder.

Run the Script:

In Ghidra, open the script manager and find ExportFunctionReferencesToJson.py.

Click on the script to execute it.

Output

The script will generate a JSON file named function_references.json in the user's home directory (i.e., ~/function_references.json).

The JSON file will contain a dictionary where each key represents a function name, and each value is a list of references with details like address, symbol name, and containing function.

Script Breakdown

Main Steps

Define JSON File Path: The script creates a path to the JSON file that will be saved in the user's home directory.

Retrieve Functions: It retrieves all functions in the loaded binary using Ghidra's FunctionManager.

Extract References: The script iterates over each function and extracts its references, including address, symbols, and containing function information.

Write to JSON: Finally, the data is written to the JSON file.

Key Functions

run(): The main function that orchestrates gathering function references and exporting them.

get_function_references(function): Extracts references for each given function, including the address, symbol, and reference function (if available).

Example JSON Output

Below is an example of what the output JSON file might look like:

{
    "function1": [
        "00401000 (symbol1) in function 'function2'",
        "00402000 (symbol2)"
    ],
    "function2": [
        "00403000 in function 'function3'"
    ]
}

Troubleshooting

Permission Issues: Make sure you have write permissions to save a file in your home directory.

Ghidra Errors: Ensure that the current binary is properly loaded and that Ghidra's scripting environment is configured correctly.
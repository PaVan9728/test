#!/bin/bash

# Check if a file is provided as an argument
if [ $# -eq 0 ]; then
    echo "Usage: $0 <filename>"
    exit 1
fi

file_path=$1

# Check if the file exists
if [ ! -f "$file_path" ]; then
    echo "Error: File not found."
    exit 1
fi

# Use grep to extract ASCII strings
echo "Strings in $file_path:"
grep -a -o -P '[\x20-\x7e]{4,}' "$file_path"

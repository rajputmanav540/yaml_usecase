# Student Data Processing with YAML

## Overview
This project demonstrates how to load, display, and filter student data using a YAML file in Python. The script reads student details from a `students.yaml` file, displays the information, and allows filtering students based on their GPA.

## Prerequisites
Ensure you have Python installed on your system. You will also need the `PyYAML` library to parse YAML files.

### Installing Dependencies
To install the required package, run:
```sh
pip install pyyaml
```

## Project Structure
```
project_folder/
│-- app.py
│-- students.yaml
│-- README.md
```
- `app.py`: The main Python script that loads and processes student data.
- `students.yaml`: The YAML file containing student information.
- `README.md`: This documentation file.

## Understanding YAML
YAML (YAML Ain't Markup Language) is a human-readable data format commonly used for configuration files and data serialization. It supports nested data structures such as lists and dictionaries.

### YAML Syntax Basics
- Use **indentation** to represent hierarchy.
- Use **dashes (-)** to indicate list items.
- Use **key-value pairs** for dictionaries.

Example:
```yaml
students:
  - name: Alice
    age: 21
    major: Computer Science
    gpa: 3.8
```
This represents a list of dictionaries under the key `students`.

## How the Script Works
### 1. Load Data from YAML
The function `load_data(file_path)` reads data from a YAML file and converts it into a Python dictionary.
```python
def load_data(file_path):
    with open(file_path, 'r') as file:
        data = yaml.safe_load(file)
    return data
```

### 2. Display Student Information
The `display_students(students)` function prints all student details.
```python
def display_students(students):
    for student in students:
        print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")
```

### 3. Filter Students by GPA
The function `filter_students_by_gpa(students, min_gpa)` filters and displays students who meet the GPA criteria.
```python
def filter_students_by_gpa(students, min_gpa):
    filtered_students = [s for s in students if s['gpa'] >= min_gpa]
    if filtered_students:
        for student in filtered_students:
            print(f"Name: {student['name']}, Age: {student['age']}, Major: {student['major']}, GPA: {student['gpa']}")
    else:
        print("No students found.")
```

### 4. Running the Script
Execute the script using:
```sh
python app.py
```
When prompted, enter a minimum GPA value to filter students.

## Expected Output
Example output after running the script:
```
All Students:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
Name: Bob, Age: 22, Major: Mathematics, GPA: 3.5
...
Enter minimum GPA to filter students: 3.6

Students with GPA >= 3.6:
Name: Alice, Age: 21, Major: Computer Science, GPA: 3.8
...
```

## Conclusion
This project demonstrates how YAML can be used to store structured data and how Python can process it efficiently. You can expand this project by adding more filtering options or saving updated student data back to YAML.

Happy coding! 🚀

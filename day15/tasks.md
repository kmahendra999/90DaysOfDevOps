## Day 15 Task: Python Libraries for DevOps

### Reading JSON and YAML in Python

- As a DevOps Engineer you should be able to parse files, be it txt, json, yaml, etc. 
- You should know what all libraries one should use in Pythonfor DevOps.
- Python has numerous libraries like `os`, `sys`, `json`, `yaml` etc that a DevOps Engineer uses in day to day tasks.



## Tasks
1. Create a Dictionary in Python and write it to a json File.

   <pre>
     import json

# Create a dictionary
my_dict = {
    "name": "John",
    "age": 25,
    "city": "New York",
    "is_student": False,
    "grades": [90, 85, 92]
}

# Specify the file path for the JSON file
json_file_path = "my_data.json"

# Write the dictionary to the JSON file
with open(json_file_path, 'w') as json_file:
    json.dump(my_dict, json_file, indent=4)

print(f"Dictionary has been written to {json_file_path}")
   </pre>

3. Read a json file `services.json` kept in this folder and print the service names of every cloud service provider.

```
output

aws : ec2
azure : VM
gcp : compute engine

```
3. Read YAML file using python, file `services.yaml` and read the contents to convert yaml to json

Python Project for your practice:
https://youtube.com/playlist?list=PLlfy9GnSVerSzFmQ8JqP9v0XHHOAeWbjo

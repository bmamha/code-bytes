#python #requests 

process request url and save content to folder/file
```python
response = request(url).get()
with open (os.path.join(folder_path, file_name, mode = 'wb') as f: 
		   #wb refers to binary encoding
		   f.write(response.contents)
```

^(/d?/d):(/d/d) (A|P)M to /d?/d/:/d/d (A|P)M$", s)
^(/d?/d):(/d/d) (A|P)M to /d?/d/:/d/d (A|P)M$", s)


print(match.group())

if int(starting_hours) > 12 or int(ending_hours) > 12:

raise ValueError("Wrong value for hours")

  

if starting_meridium == "A":

starting_hours = int(starting_hours)

  

if starting_meridium == "P":

starting_hours = int(starting_hours) + 12

  

if ending_meridium == "A":

ending_hours = int(ending_hours)

  

if ending_meridium == "P":

ending_hours = int(ending_hours) + 12

  

if starting_minutes == "":

starting_minutes = "00"

  

if ending_minutes == "":

ending_minutes = "00"

  

if int(starting_minutes) > 59 or int(ending_minutes) > 59:

raise ValueError("Wrong value for minutes")

  

return f"{starting_hours:02}:{starting_minutes:02} to {ending_hours:02}:{ending_minutes:02} "

else:

raise ValueError("Wrong format used")
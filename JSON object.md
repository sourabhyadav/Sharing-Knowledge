# Short Note on [JSON][2]

**What is JSON?**

JSON stands for **J**ava **S**cript **O**ject **N**otation. 
Basically, it is globally accepted **text format** which is used to send, receive & store texts from browser to server.  
It can handle Arrays, Strings, Boolean, Number and another dict (key/value) pair.
It looks very similar to **Python Dictionary**, where there is a Key & Value pair form. Data is separated by commas, curly braces hold objects and square braces hold arrays.
You can parse any JSON file using any web-browser or read using the Python JSON library and vise-Versa. 

[Python Example:][1]
import json
with open('path_to_file/person.json') as f:
  data = json.load(f)
Output: {'name': 'Bob', 'languages': ['English', 'Fench']}
print(data)

[1]: https://www.programiz.com/python-programming/json
[2]: https://www.w3schools.com/js/js_json_intro.asp

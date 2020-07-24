# Python Training for Network Engineers

## __Python 101__ - _Basics_
#### Testing with Python basics
#### Using Functions and Modules
## __Python 201__ - _Network Devices, API Calls and Data Manipulation_
#### Connecting to network devices
#### Interacting with APIs
#### Data structure manipulation
## __Python 301__ - _Working with Class Objects_
#### Building and using Classes


### ___Notes___
##### Developed for Python 3.6+
##### Some tasks build onto the next, so wait to exit python shell until finished
##### It is recommended to manually type(not just copy/paste) as much code as you are comfortable with, to gain a greater familiarity with the syntax
##### Some modules may be required to be installed manually (netmiko)



# Python 101
## What is Python??
### [Python](https://www.python.org/) is a programming language that lets you work more quickly and integrate your systems more effectively.
### You can learn to use Python and see almost immediate gains in productivity and lower maintenance costs.

## Why Python for Network Engineers??
### Python has a very rich and diverse library of built-in modules, as well as community maintained modules, which can provide immediate results with little time investment




## Main types of objects
### __Data types__
```python
int() == 1

float() == 3.14

bool() == True

str() == 'text'
```
### __Data structures__
```python
list() == [1,2,3,4]

tuple() == (1,2,3,4)

dict() == {'key1': 'value1', 'key2': 2}
```

### __Variables__
#### Variables are simply named objects, assigned by using `=`
#### Unlike most other programming languages, you do not need to declare a variable before using it.
#### A variable can also be reassigned to a different object at any point, so variable naming is very important for tracking in your code
#### Variable names cannot start with a number and can only include letters, numbers, or underscore `[a-z,0-9,_]`
```python
Var_1 = 'This is a str() Variable'
```

## Working with __Integers__
```python
num = 2
num
type(num)

num += 22
print(num)

num = 2*10
print(num)

num = 2**10
print(num)
```

## What is a __String__??
### [Strings](https://www.learnpython.org/en/Basic_String_Operations) are created by entering text between two individual single quotes `' '`, two individual double quotes `" "`, or between a pair three single/double quotes `''' '''` `""" """`
### triple quotes `''' '''` `""" """` are used to create multi-line strings (Docstrings), preventing the need to manually add `\n` for new lines
```python
# String
textA = ' Text\n"text text"\nText.text '
# Multi-Line String (Docstrings)
textB = '''text
'text text'
text.text'''

textA
type(textA)

# List operations
print(textA + '\n' + textB)
print(textA.lower())
print(textA.upper())
print(textA.strip())
print(textA.split())
print(textA.split('.'))
print(textA.splitlines())
print(textA.replace('e',''))

# F Strings
textC = f'{textA}\n{textB}'
print(textC)

textC = f'{textA *5}'
print(textC)
```

## What is a __Tuple__??
### A Tuple is similar to a list, however once instantiated cannot be modified (immutable)
```python
# Tuple
Tuple = (
	'A',
	'B',
	'C',
	'D'
	)
Tuple
type(Tuple)
print(Tuple[0])
```


## What is a __List__??
### [Lists](https://www.learnpython.org/en/Lists) can consist of a multitude of object types (`str()`, `int()`, `list()`, `dict()`, etc...)
### Defined by enclosing a comma-separated sequence of objects in square brackets
### Values can be accessed by using it's index in square brackets
### Indexes are integers, starting at 0
```python
# List
ListA = [
	'1',
	'2',
	'3',
	'4',
	'5'
	]
ListB = [
	6,
	7,
	8,
	9,
	10
	]
ListA
ListA[0]
type(ListA)

# List Operations
print('1' in ListA)
print('1' not in ListA)
print(ListA + ListB)
ListA[0] = 1
print(ListA[0])
ListB.append(11)
ListA.append(ListB)
print(ListA)
print(len(ListA))
print(ListA.index('3'))
```

## What is a __Dictionary__??
### [Dictionaries](https://www.learnpython.org/en/Dictionaries) are data structures used to map arbitrary keys to values
### Similar to Lists, Dictionaries can consist of a multitude of object types (`str()`, `int()`, `list()`, `dict()`, etc...)
### Define by enclosing keys & values separated by colon, within curly braces `{ }`
### To access the Dictionary values, call using the key as the index (similar to accessing list values)
```python
# Dict
DictA = {
	'key1': 'value1',
	'key2': 'value2',
	'key3': 'value3'
	}
DictB = {
	'keyA': 'valueA',
	'keyB': 'valueB',
	'keyC': 'valueC'
	}

DictA
type(DictA)
DictA['key1']

# List Operations
print('key1' in DictA)
print('key1' in DictA.keys())
print('key1' in DictA.values())
print('value1' in DictA)
print('value1' in DictA.keys())
print('value1' in DictA.values())
DictA.update({'key3':'valueX'})
DictA['key1'] =  'valueY'
print(DictA)
DictA.update(DictB)
print(DictA)
```

## What is a __For__ loop??
### A `for` [loop](https://www.learnpython.org/en/Loops) iterates through a sequence or collection, running the block of statements until all of the items have been iterated through (or you manually break out of the loop from within the code block)
```python
# For Loop
for item in Tuple:
	ListA.append(item)
	print(f'Item: {item} appeneded to ListA')

for dog in ListA:
	DictA.update({f'key_{dog}':dog})
	print(f'Added {dog} to DictA')

for dog,cat in DictA.items():
	print(f'KEY: {dog}\nVALUE: {cat}\nTYPE: {type(cat)}')
```


## What is a __While__ loop??
### A `while` [loop](https://www.learnpython.org/en/Loops) evaluate an expression before each iteration of the loop.
### If the expression evaluates to `True`, the loop statements are executed. If the expression evaluates to `False`, the loop statements are not executed and the script continues with the first line after the loop block.
```python
counter = 0
while counter < len(ListA):
	DictA.update({f'key-{ListA[counter]}' : ListA[counter]})
	print(f'Added {ListA[counter]} to DictA')
	counter += 1
```

## What is a __Try/Except/Else__ Block??
### [Try/Except/Else](https://www.learnpython.org/en/Exception_Handling) attempts to perform an block of statements (try), and if a certain error occurs do something (except), otherwise do a final action (else)
```python
import traceback
# Try/Except/Else block
for i in ListA:
	try:
		print(f'This is an Integer: {int(i)}')
		i.append('test')
		print(f'Appended "test" to {i}')
	except TypeError as E:
		print(f'This is the Exception description only:\n{E}\n')
		print(f'This is the full Exception:\n{traceback.format_exc()}\n')
	except AttributeError:
		print(f'This is a different Exception:\n{traceback.format_exc()}')
	else:
		print(f'The Try statements ran without any exception encountered')
```


## What is a __Function__??
### A [Function](https://www.learnpython.org/en/Functions) is a way to group code into reusable blocks
### By using Functions you can keep your code DRY (Don't Repeat Yourself), which is a coding style to reduce repetitive information
```python
# Creating Function
def PrintList(LIST):
	try:
		for i in LIST:
			try:
				print(int(i))
			except TypeError:
				print(f'Item "{i}" not Integer')
	except:
		print(traceback.format_exc())

# Using Function
PrintList(ListA)
```


## What is a __Module__??
### A [Module](https://www.learnpython.org/en/Modules_and_Packages) is a grouping of Functions/Classes/Variables in a separate file, that allows for easy reuse across multiple python scripts
### Modules are simply Python files with the `.py` extension, and the name of the file will be the name of the module
### Lets create a test module "TestMod.py", and call in a different script "TestScript.py"
```python
# Paste the following into TestMod.py
#
# Import required modules to be used in this module file
# key word 'as' allows you to rename the module/function/class specifically for this file
# key word 'from' allows you to import only specific functions/classes from a module
import traceback as TB
from json import dumps as DUMP


def PrintList(LIST):
	for i in LIST:
		try:
			print(int(i))
		except TypeError:
			print(f'Item "{i}" not Integer')

def PrintDict(DICT):
	try:
		print(DUMP(DICT,indent=4))
	except:
		print(TB.format_exc())

def CombineListDict(LIST,DICT):
	try:
		for i in LIST:
			try:
				DICT.update({f'key_{i}':i})
				print(f'Added {i} to {DICT}')
			except:
				print(f'Item "{i}" not added to {DICT}')
	except:
		print(TB.format_exc())

	return DICT
```
```python
# Paste the below contents into TestScript.py
#
# If the module we created is in the same directory as this script, import will work
import traceback
import TestMod
from TestMod import CombineListDict as CLD
# If the module we created is in a different directory, use 'sys.path.append('/path/to/dir)' for the module directory
import sys
#sys.path.append('../path/to/dir')

ListA = [
	'1',
	'2',
	'3',
	'4',
	'5'
	]
ListB = [
	6,
	7,
	8,
	9,
	10
	]
ListA.append(ListB)
DictA = {
	'key1': 'value1',
	'key2': 'value2',
	'key3': 'value3'
	}
DictB = {
	'keyA': 'valueA',
	'keyB': 'valueB',
	'keyC': 'valueC'
	}
DictA.update(DictB)



def main():
	TestMod.PrintList(ListA)
	TestMod.PrintDict(DictA)
	DictC = CLD(ListA,DictA)
	try:
		TestMod.PrintList(DictC)
	except:
		print(f'Somthing Is Wrong....\n{traceback.format_exc()}')
	TestMod.PrintDict(DictC)

# This statement checks if this script has been directly executed (bash> python3 TestScript.py)
# if so, run the block of code below
if __name__ == '__main__':
    main()
```




# Python 201
## Connecting to network device
### Obviously this is a very useful task for network engineers
### There are many different ways to connect to network devices (Paramiko, Netmiko, Napalm, Ansible)
### I will only cover the Netmiko method
### IMO Netmiko is the simplest and most flexible option when other integrations or data manipulations are required
```python
import netmiko,json
from getpass import getpass
# Create function to validate password
def GetPass():
	password = None
	while not password:
		password = getpass('Please Enter Password: ')
		passwordverify = getpass('Verify Password: ')
		if not password == passwordverify:
			print('Passwords do not match....')
			password = None
	return password

username = input('Please Enter Username: ')
password = GetPass()
device = input('Please Enter Network Device IP/FQDN: ')

connection = netmiko.ConnectHandler(
				ip=device,
				device_type='cisco_ios',
				username=username,
				password=password,
				global_delay_factor=3
				)

# Example show command
output = connection.send_command('sh ip int brie')
print(output)
device_dict = {device:{'interfaces':[]}}
for line in output.splitlines():
	line = line.split()
	if line[0] == 'Interface': continue
	status = line[4]
	if 'admin' in status: status = 'admin_down'
	prot = line [-1]
	temp_dict = {'int': line[0], 'ip': line[1], 'status': status, 'protocol': prot }
	device_dict[device]['interfaces'].append(temp_dict)

print(json.dumps(device_dict,indent=4))

# Example config commands
commands = [
	'int Gi0/0/2',
	'no shut',
	'shut'
	]

output = connection.send_config_set(commands)
print(output)

# Example config changes based on data collected
output = ''
for int in device_dict[device]['interfaces']:
	if int['status'] == 'admin_down':
		commands = [
			f'int {int["int"]}',
			'no shut',
			'shut'
			]
		o = connection.send_config_set(commands)
		output += f'{o}\n'

print(output)
```

## What is an __API__??
### Application Programming Interface; A method to push/pull data to/from an application
### There are many different types of APIs
### REST API is the type I will cover here, using an online REST API tester
```python
# Requests module makes it very simple to interact with APIs
import requests,json
from xml.dom import minidom as dom

# Define API variables
headers = {'Accept': 'application/json'}
username = 'test'
password = 'test'
url = 'https://reqbin.com/echo/get/json'

# Perform GET to pull data
r = requests.get(url, headers=headers, auth=(username,password),verify=False)
print(r.status_code)
print(r.ok)
print(json.dumps(r.json(),indent=4))

# Create some sample JSON data to POST
data = {
	'key1': 'value1',
	'key2': 'value2',
	'key3': 'value3'
	}
# Perform POST to push data
url = 'https://reqbin.com/echo/post/json'
r = requests.post(url, headers=headers, json=data, auth=(username,password),verify=False)
print(json.dumps(r.json(),indent=4))



# XML data example
headers = {'Accept': 'application/xml'}
url = 'https://reqbin.com/echo/get/xml'
r = requests.get(url, headers=headers, auth=(username,password),verify=False)
XML = dom.parseString(r.text)
print(XML.toprettyxml())

# Add a new key to the existing XML
k = XML.createElement('NewKey')
v = XML.createTextNode('NewValue')
k.appendChild(v)
XML.childNodes.append(k)
print(XML.toprettyxml())

# Perform API POST to push XML data
data = XML.toxml()
url = 'https://reqbin.com/echo/post/xml'
r = requests.post(url, headers=headers, data=data, auth=(username,password),verify=False)
print(r.text)

```

# Python 301
## What is a Class??
### a [Class](https://realpython.com/python3-object-oriented-programming/) is used to create user-defined data structures.
### Classes define functions called _methods_, which identify the behaviors and actions that an object created from the class can perform with its data.
### A class is a blueprint for how something should be defined, and usually doesn’t contain any actual data.
### While the class is the blueprint, an _instance_ is an object that is built from a class and contains real data.
### Put another way, a class is like a form or questionnaire. An instance is like a form that has been filled out with information. Just like many people can fill out the same form with their own unique information, many instances can be created from a single class.
### Copy and Paste the below examples into the Python interpreter and see how it functions

```python
class  Foo          (object):
    """^class name   ^ inherits from the default Python object class"""
    bar = 'bar'
    """ Improper use of Class attribute,
    #   as this attributed would be shared among all instances of Foo.
    # Should be an Instance attribute as shown below"""
    def __init__(self, argA='Foo'):
        """     #^ The first argument in the class instance and methods should be 'self'
        #^ double underscore (dunder) methods are usually special.  This one
        #  gets called immediately after a new instance is created."""
        self.var = argA # instance attribute.
        print(self.var, self.bar)  #<---self.bar references class attribute
        self.bar = 'Bar'   #<---self.bar is now an instance attribute
        print(self.var, self.bar)
    def method(self, arg1, arg2):
        """This method has arguments.  You would call it like this:  instance.method(1, 2)"""
        print(f'in method (args): {arg1}, {arg2}')
        print(f'in method (attributes): {self.var}, {self.bar}')


a = Foo('FOO') # This calls __init__ (indirectly)

print(a.var) # FOO
a.var = 'foo'
a.method(1, 2)

Foo.method(a, 1, 2) #<--- Same as a.method(1, 2).
                    # This makes it a little more explicit what the argument 'self' actually is.

class  Bar          (Foo):
    """^class name   ^ inherits from the object Foo we created"""
    def __init__(self, argA='FooBar', argB='BarFoo'):
        Foo.__init__(self,argA)
        """Instantiate inherited object"""
        self.bar = argB # Assigning Bar argB to inherited Foo() attribute 'bar'
        self.P = print
        """Assigning built-in print() function to attribute 'P',
           which means it is now a callable method of Bar()"""


b = Bar() # This calls Bar.__init(), which in-turn calls Foo.__init__()
print(b.bar) # BarFoo
b.var = 'something'
print(b.var) # something
b.method(3, 4)
b.P(f'VAR: {b.var},\nBAR: {b.bar}')
isinstance(b,Foo) # True, b is an instance of Bar, which is an instance of Foo
isinstance(b,str) # False, b is not an instance of str()

```















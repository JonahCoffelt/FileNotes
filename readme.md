# Files
Files are a method of sting information outside of the main memory, thus it needs to be accessed differently.
## Extensions
Files have an extension which hint at what data is stored in the file:
- .pdf - Stores documents
- .jpg - Stores images
- .mp3 - Stores audio
The extensions does not enforce anything about the data, only suggests what the data is and how one might read it. 

# Dealing with Files
The first step is to open a file. In doing this, we will associate an ID which we can use to access the file. We then can do whatever we want with the data in the file. Finally, a file should always be closed after use. 
## Opening Files
The basic format to open a file is like this:

```python
FileID = open('<File Name>', '<Designator>')
```

The ID is just a variable that is used to access the data. The file name is a string that tells where the file is on the computer. The designator is the way in which the data will be used, which is like a mode.
## Designators
- 'r' - Reading
- 'w' - Writing to a new file
- 'a' - Appending new data to an existing file
- 'rb', 'wb', 'ab' - Read/Write/Append in binary
- 'r+' - Reading and writing to a file. 

## Closing Files
Files must be closed after use insure the data is in a valid and stable condition after use. A file can be closed like so:

```python
FileID.close()
```

## The 'with' Method
This is an alternative way to opening data:

```python
with open('<File Name>', '<Designator>') as FileID:
	# Things to do with file
```

The advantage of using this method is that the file will automatically be closed at the end of the indentation, and it clearly shows where the file is used in the code. However, this is limited as you can only use the file in this spot at one time. Additionally, this method my not be ideal if working with multiple files at once. 

# File Operation
## Writing
To write data to a file, use the write() command.
```python
FileID.write('<string to write>')
```

There are some limitations of the write() function:
- Will only write a single string, cannot pass in multiple values
- Can only write strings, no integers or any other data type
- Will not automatically put a new line, it must be in the string if you want one
Here is an example:
```python
with open('my_file.txt', 'w') as my_file:
	my_file.write("First Line\n")
	output_string = "Second Line"
	my_file.write(output_string)
```
```txt
First Line\n
Second Line
```

## Reading
There are many ways to read from a file, but the most common one is to read one line at a time. This can be done with the readline() function, which will read everything as a string until a \n is encountered:

```txt
First Line\n
Second Line
```
```python
with open('my_file.txt', 'r') as my_file:
	line1 = my_file.readline()
	line2 = my_file.readline()
print(line1)
print(line2)
>> First Line
>> 
>> Second Line
```

Often, we will want to access the whole file and do similar operations to each line. To do this, we can loop through each line in a file. This can be done with a for loop or a while loop. Here are both implementations:
```python
with open('my_file.txt', 'r') as my_file:
	for line in my_file:
		# Do things with line
```
```python
with open('my_file.txt', 'r') as my_file:
	next_line = my_file.readline()
	while next_line ! = '':
		 # Do things with line
		 next_line = my_file.readline()
```

Here are some alternative ways to read from a file:
```python
with open('my_file.txt', 'r') as my_file:
	<str>  = my_file.read() # This returns the whole file as a str
	<list> = my_file.readlines() # Returns a list of all lines
	<list> = list(my_file) # Returns a list of all lines
```

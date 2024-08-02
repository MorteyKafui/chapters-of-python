# CHAPTER 11 - Files

Till now, we have been reading and writing to the standard input and output. We were reading data from the keyboard, processing that data, and writing the information on the screen.

Working with files mainly consists of three steps:

- Open a File
- Perform read/write operations on the file
- Close the File

Opening a file establishes a connection between the Python program and the external file, and closing the file breaks this connection. You can open a file by using the built-in function `open`. This function returns a file object that serves as a link between your Python program and the file. This object has different methods for reading and writing data, so the read-write operations can be performed using those methods. For closing the file, you can use the `close` method of the file object.

```python
fout = open('data.txt', 'w')
fout.write('This is my first file')
fout.close()
```

First, we have called the `open` function. The first argument to this
function is the name of the file that we want to open. The next argument is the mode in which we want to open the file. This mode is a string that describes the way in which the file will be used. Since we are going to write something in the file, we will open the file in write mode, which we can specify by using the letter `'w'`. If the file named `data.txt` does not exist, then it will be created and if a file with this name already exists then its contents will be erased, and we will get an empty file for writing. The function `open` returns a file object which we have assigned to the name fout. Now, the name `fout` refers to the file object returned by `open`, and by using this object we can write to our file `data.txt`.

Next, we have called the write method on the file object. The string
that is sent as argument to this method is the text that we want to
write in the file. After this we closed the file by calling the close
method on the file object. When we run this program, a file named `data.txt` will be created and the given text will be written to the file.
This file will be created in your current working directory, i.e., the
same directory in which you are running your program. You can open
the file using any text editor and view or edit its contents. So, we
have seen how to write data to a text file from inside our program;
now, let us see how to read data from an existing file.

The following program will read the file that we have just created:

```python
fin = open('data.txt', 'r')
s = fin.read()
print(s)
fin.close()
```

We have called the `open` function with the file name to be opened
and the second argument this time is `'r'`. This opens the file in read
mode which provides read-only access to the file. This is the default
mode for the `open` function so even if we do not provide any second
argument, it means the same thing. The object returned by `open` is
assigned to the name `fin`, and then we have called the `read` method on this object. This method returns the whole text of the file in the form of a string. We have assigned the return value to name `s` and then printed the string `s`. In the end, we have just closed the file. When we run this program, we can see the file’s contents on our output screen.

The file object that was created has different attributes. For example,
the name attribute returns the `name` of the file that is used in the call to `open` function. The `mode` attribute returns the mode in which the file was opened and closed attribute returns `True` if the file is closed.

> As usual, you can use the dir function to see everything related to this object. `dir(fin)`

## Opening a File

We know that if we need to access a file in our program, first we
have to open it by using the built-in function open. The first argument to this function is a string containing the file’s name. If you open a new file for writing, then the file is created in your current directory. If you open an existing file for reading or writing, Python
looks for it in your current directory. If you want to create a file in a
location other than your current directory, or if you want to read a file
that is not in your current directory then you have to provide a path
before the filename. A path is a hierarchy of directories that specifies
a location on the file system. In the following call to open function,
we have specified a file name with full path.

```python
open('C:\dir1\dir2\data.txt', 'w')

open('C:\textfiles\newfile.txt','w')

open('C:\\textfiles\\newfile.txt','w')
open(r'C:\textfiles\newfile.txt','w')

```

## File opening modes

We have seen that the second argument to open function is the mode in which the file is opened. This argument specifies whether the file is opened for reading, writing, or appending. It also specifies whether the file is to be treated as a text file or a binary file. There are other modes also in which a file can be opened, so now let us see the details of all the modes:

- `'r'`: read mode (default)
- `'w'`: write mode
- `'a'`: append mode
- `'x'`: exclusive creation

We know that the mode `'r'` opens an existing file for reading only;
the file should already exist. If you open a file in this mode, then you cannot write anything to it. It is the default mode, so if you do not provide any mode in the open function then this mode will be used. The mode `'w'` opens a file for writing only, if the file does not exist then it creates a new file, if the file exists, then any content present in the file is erased. You cannot read from a file if you open it in this mode. The mode `'a'` is the append mode. It will also open a file for writing only, but unlike the mode `'w'`, it will not erase the contents of the file if it already exists. If the file does not exist, then it creates a new file, and if the file exists, then whatever you write to the file will be added at the end of the file. In this mode also, you cannot read from the file. The mode `'x'` is for exclusive creation. It is like the `'w'` mode; it creates a new file but fails if the file already exists. So, it will create a new file only if the file with the given name does not exist. If the file exists, then it raises `FileExistsError`.

You can add a `+` sign to these modes if you want to perform both
reading and writing on the same file. These are called update modes.
Syntax: `'r+' 'w+' 'a+' 'x+'`

The mode `'r+'` opens a file for both reading and writing and it
works only on existing files. It will not create a file if it does not exist.

The mode `'w+'` opens a file for both reading and writing. If the file already exists then the data in it is erased, otherwise a new file is created for reading and writing.

The mode `'a+'` opens a file for both reading and writing, it will
create a new file or append the contents at the end of the file.
The mode `'x+'` also opens a file for both reading and writing, and it behaves like the exclusive creation mode.

In Python, files are broadly classified as text files and binary files. You can append letter `t` or `b` to the mode strings for working with text or binary files. For example, `'wt'` will open a text file for writing, and `'rb'` will open a binary file for reading. Text mode is the default, so you can skip the t if you want. Thus, adding a `t` or nothing means text and adding `b` means binary.

## Buffering

When you write data to a file through your program, that data is not
directly transferred to the file. It is first placed in an area of primary memory which is called buffer.

The area is automatically associated with the file when it is opened. When the buffer becomes full, then only the data is written to the physical file. So, your data is written in chunks. This technique of buffering makes writing to files more efficient; it is done to increase the performance.

You can control buffering by providing a third argument to the `open` function. If the third argument is 0, then buffering is disabled and data is transferred immediately to the file. This can reduce performance and it is allowed only in binary mode. If the buffering argument is `1`, line buffering is performed which means that the buffer is flushed every time you write a `'\n'` to the file, this is usable only in text mode. If this argument is any integer greater than one, then buffering is performed with that integer as the buffer size. If a negative value is given or this argument value is not provided in the call, then buffer size is the system default.

The `open` function takes some other arguments also which are all
optional, but the first two arguments, file name and mode are the
ones that you will mostly use.

## Binary and Text Files

When data is transferred in binary mode, no processing of data is performed by Python, you will get what is there in the file unprocessed. When data is transferred in text mode, some translations are performed by Python while reading and writing. Normally text files should be opened in text mode and binary files in binary mode.

A text file contains readable characters that are structured as lines of text, it also contains the non-printing newline character which indicates the end of each line. A text file is human readable and editable. These files can be read or written using any text editor. These files contain lines of text separated by newline characters and they do not contain any text formatting information like font, colors or size. For the computer, text file is just a sequence of characters, where newline is also a character. It is a special non printing character that makes the text appear on the next line. Inside our program, whenever we write to a text file, we have to write the content in the form of a string and whenever we read, we get the content of the file in string form in our program. Some examples of text files are `.txt files`, `.py files` and `.csv files`.

A binary file contains raw binary data that can be understood only by a computer program. These files can store non-textual data,
examples are mp3 or image files, MS word files, pdfs, spreadsheets
or executable files. These files are not human-readable or editable. If you try to open a pdf or an MS Word file using a plain text editor, you will see incomprehensible data on the screen. These files can be written and read by specific programs only.

To interpret different formats of binary files, Python has different
modules like `shelve`, `pickle` and `struct`; these modules can be
used to read and write data to binary files.

When you work in text mode, Python expects and produces objects
of type `str`. This means that while writing to the file you can write objects of type str only and while reading, the content of file is automatically translated and returned as `str`. When you work in binary mode, Python expects objects of type `bytes` or `bytesarray` and produces objects of type bytes. So, when you read from a binary file, content is returned raw and unchanged in the form of bytes objects.

A `bytes` object is an immutable sequence of single 8-
bit bytes. It supports most of the `str` operations and displays as
ASCII whenever possible. A `bytes` literal is written by preceding a
string literal with the letter `'b'`. The type bytes is immutable, the type `bytearray` is the mutable version of bytes type. So `str` type represents the text string in Python and `bytes` and `bytesarray` types represent binary strings in Python. When we work in text mode, we give and get str object, and in binary mode, we give and get `bytes` objects.

## Closing a file

We have seen that when we are finished working with a file, we
should close it by calling the `close` method on the file object. After a file is closed, any attempts to use the file object will automatically fail. Closing the file is important as it ensures that the data is properly written to the file and all the system resources attached with the file object are released.

We know that Python’s built-in garbage collector will reclaim an
object’s memory space if it is no longer referenced. This applies to
file objects also, but it is a good practice to explicitly close the file after you are done working with it. Closing a file also means that the file has been released by our program so that it can be used in another program. Closing the file becomes important when you are writing some data to a file. If there is any buffered output in the memory, then the call to `close` method automatically flushes it to the disk.

```python
f = open('time.txt', 'w')
f.write('Time is precious.')

f = open('time.txt', 'r')
s = f.read()
print(s)

```

Thus, closing a file not only releases the resources attached to it. It also ensures that any contents that you have written to the file are saved in it. Any data that is there in the memory buffer is transferred to the physical file on the disk. If you forget to close the file, you might lose some data. If you want to flush the output buffer without closing the file, you can use the `flush` method. `f.flush()`

## `with` statement

We have seen that when we have to perform any operation on a file,
we need to open the file then perform that operation and then close
the file. If we forget to close the file or some exception occurs while working on the file then the file will not be closed which might result in loss of data and resource leakage. Since closing of file is important, we can write our file operations inside a `with` statement which ensures that the file is always properly closed. Here is an example of a file reading operation code and equivalent code using the `with` statement:

```python
with open("data.txt", "r") as f:
  s = f.read()
  print(s)
```

The `with` statement consists of a heading and an indented block of
statements. In the heading, we have the `with` keyword followed by
the call to open function. The file object returned by `open` will be assigned to the name that follows the `as` keyword. Inside the with block, you can place all your file operation statements that work on the opened file. If you use the `with` construct, there is no need to explicitly call the `close` method because when the block ends, the `close` method is automatically called. The file is closed properly even if there is an exception raised inside the block. This is why it is a good practice to place your file processing statements inside a `with` block.

```python
with open("data.txt", "r") as f1:
  with open("new.txt","w") as f2:
    s = f1.read()
    f2.write(s)

```

```python
with open('time.txt', 'w') as fout:
  fout.write('Time is precious')
  print(fout.closed)

with open('time.txt', 'r') as fin:
  s = fin.read()
  print(s)

print(fin.closed)
```

We have opened the file `time.txt` in write mode and then opened
the same file in read mode and printed the data read from it. We
have not called the `close` method anywhere. The output shows that
the data was properly written and read from the file. The closed
attribute of these two objects `fout` and `fin` is `True` which shows that the files were automatically closed because of the `with`
statement.

## Random Access

To know the current position of the cursor, you can call the method
`tell` and to change the position of the cursor, you can call the
method `seek`.

The call `f.tell()` returns the current position of the cursor in the file, where position is an integer offset in bytes from the beginning of the file.

The method `seek` lets us move the cursor to a different location for the next read/write operation. The call `f.seek(n)` changes the file position for next operation to integer offset `n`. This offset is measured in bytes, from the beginning of the file.

The method `seek` can take a second optional argument also that
specifies the reference point relative to which the cursor is moved.
Syntax: `f.seek(n, from_where=0)`

If this second argument is `0`, reference point is the beginning of the file, this is the default value. So, if you provide 0 or do not provide any value, cursor is moved n bytes away from the beginning of the file. If this argument is `1`, reference point is current location so cursor is moved `n` bytes away from the current location. If this argument is `2`, reference point is the end of the file which means that the cursor is moved n bytes away from the end of the file.

## Reading and writing to the same file

Random access to files becomes more important when we are reading and writing to the same file. We have seen that adding a `'+'`
sign to the file mode allows both reading and writing. For example,
the modes `'w+', 'r+', 'a+', 'w+b', 'r+b'` and `'a+b'` can be
used for reading and writing to a file at the same time.

In `'w+'` and `'w+b'` modes, a new file will be created, if the file does not exist. If the file exists, all its data will be
deleted. So, in these modes, you will always get a blank file for
reading and writing. Initially, there will be nothing to read. First, you have to write something, and then you can move the cursor to read.

If you want to open an existing file for reading and writing, you
should use the `'r+'` or `'r+b'` mode as these modes will not delete
the existing contents of the file. In 'a+' and 'a+b' modes also, the
existing contents will not be deleted. In 'a+' and 'a+b' mode, you
can read the file at any place, but you can only write at the end of
the file.

When you open a file in `'r+'` or `'r+b'` mode, the cursor is initially placed at the beginning of the file. If you open the file and just start writing, then you will overwrite the existing contents of the file.

## Reading a File using read()

To be able to read from a file you have to open the file in any one of these modes.
`'r', 'r+', 'w+', 'x+', 'a+', 'rb', 'r+b', 'w+b', 'x+b', 'a+b'`

The `read` method can take an optional argument, which represents
the number of characters to read in text mode, and number of bytes
to read in binary mode. The call `read(n)` starts reading at the
current location and reads up to next `n` characters (or `n` bytes) into a string and returns that string. If there are not enough characters left in the file, then it reads all the remaining characters. If this argument is negative or omitted, the rest of the file is read.

If end of file has been reached and then `f.read()` is called, and it will return an empty string

## Line oriented reading

The next few methods that we will see for reading a file are lineoriented methods. These methods will work in binary mode as well, but they are meaningless in that case because binary data is not line oriented. Line based file processing is meaningful only in text files as they contain text organized in lines.

To read the file a line at a time, we can use the `readline` method
which reads the next line into a string and returns that string. It
reads the contents of the file until it finds a newline character, it then returns the content read so far and the newline character in a string.

```python
with open('zenpython.txt', 'r') as f:
  print(f.readline())

with open('zenpython.txt', 'r') as f:
  print(f.readline())
  print(f.readline())
  print(f.readline())
```

## Writing to a file

To write data to a file you have to open the file in one of these
modes.
Syntax: `'w', 'a', 'x', 'w+', 'a+', 'x+', 'r+', 'wb', 'ab', 'xb', 'w+b,' 'a+b', 'x+b', 'r+b'`

In the case of `'w', 'w+', 'wb', 'w+b'` modes, you need to be
careful because if the file already exists then the data that is present in the file will be erased and you will get a blank file for writing. In case of `'r'` and `'r+b'` modes, you need to move the cursor to avoid overwriting the existing contents. If you want to append data to an existing file then it should be opened in append mode.

We have already seen the `write` method that is used to write data
to the file. It writes a string of characters (or bytes in binary mode) into a file and returns number of characters (or bytes) written. In text mode, you need to provide it a string of type `str`, and in binary mode you need to give it a `bytes` string. Other types of objects have to be converted to a string (in text mode) or a bytes string (in binary mode) before writing them using the `write` method.

```python
with open('learn.txt', 'w') as f:
  f.write('Data Science\n')
  f.write('Machine Learning\n')
  f.write('Artificial intelligence\n')
```

We have opened the file `learn.txt` in write mode and called the
`write` method three times. After running this program, the three
strings will be written to the file on separate lines. Unlike print
function, the `write` method does not add a trailing newline character at the end of the string that is written to the file. The newline character will be added only if it is a part of the string being written. So, you have to add the newline explicitly in the string that you are writing to the file otherwise the next `write` call will write the data at the same line.

We know that when we read data in binary mode, it is returned in
the form of a `bytes` string. Similarly when we have to write data in binary mode, we supply the data in the form of `bytes` string or
`bytearray` object. You can use the `encode` and `decode` methods
while reading and writing to binary files.

```python
with open('myfile.bin', 'wb') as f:
  data = '☛ Explicit is better than implicit✍'
  f.write(data.encode('utf-8'))


with open('myfile.bin', 'rb') as f:
  s = f.read()
  data = s.decode('utf-8')
  print(data)

```

If the strings that we want to write are present in an iterable, like a list or a tuple, then we can use the `writelines` method. This method writes all the strings present in an iterable into a file and it does not return any value. This method also works in both binary and text modes. Let us open our learn.txt file in append mode and use the `writelines` method to write strings from a list.

```python
L = ['Python\n', 'Java\n', 'Swift\n', 'Perl\n']
with open('learn.txt', 'a') as f:
  f.writelines(L)
```

This method just writes the strings as such, if we want the strings to be on separate lines, newlines have to be present at the end of each string. You could also write a list of strings by calling the `write` method repeatedly inside a for loop, or by joining the strings using the `join` method and then calling the `write` method once for that joined string. But using this `writelines` method is faster than both of them.

## Storing and Retrieving Python objects using pickle

The built-in module named `pickle` automates the process of
reading and writing Python objects into files. This module allows us
to store any Python object in the file without converting it to a string, and thus the type information of the object will not be lost. It is called pickling as it preserves your Python objects so that you can use them later on. The pickled objects can be stored in a file or they can be sent over a network.

Pickling is also called serialization as your Python object is turned into a stream of bytes and this serialized byte stream is written to the file. While reading from the file, the reverse operation is done which is called unpickling or deserialization; the stream of bytes is converted back to Python object. This `pickle` module knows how to convert any Python object into a byte stream and how to reconstruct the object back from that byte stream.

While pickling you need to open the file in binary mode, because the
Python object is converted to a stream of bytes and that byte stream
is written to the file. The objects are stored in a binary format, so you need to work in binary mode while pickling.

The function `dump` of the `pickle` module is used to write a Python
object to the file. To read the Python object back into your program, you can use the function `load` from the `pickle` module.

```python
import pickle import pickle

file = open('data.pck', wb)
pickle.dump(p, file)

file = open('data.pck', rb)
o = pickle.load(file)
```

For pickling a Python object, you need to first import the `pickle`
module and then open a file in binary mode for writing and then
dump the Python object. For unpickling, you need to open a file in
binary mode for reading and then call the `load` function. The name
of the object is not saved, only the object is saved in the file. The `load` function returns us that object and we can assign it to a name in our program.

```python
import pickle

numbers = [10, 20, 30]

with open('data.pickle', 'wb') as file:
  pickle.dump(numbers, file)
```

The function `dump()` writes the pickled representation of the list
object to the file. Now, let us read this file in another program.

```python
import pickle

with open('data.pickle', 'rb') as file:
  a = pickle.load(file)
print(type(a))
print(a)
```

The function `pickle.load` will reconstruct the list object from the
byte stream inside the file, and it will return that object. We have
assigned that returned object to name `a`. When we print the type of
`a`, we can see that it is a list and printing a gives us the list that we had stored in the file using the `dump` function.

## The End

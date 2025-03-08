## String Manipulation
String manipulation is a fundamental concept in Python programming, as strings are used to store and manipulate text-based data. Strings are immutable sequences of characters, which means once created, their contents cannot be changed. However, Python provides a rich set of built-in functions and methods to manipulate and process strings efficiently.

### Why is String Manipulation Important?
#### 1. Data Processing: 
Many real-world applications involve textual data, such as logs, emails, and web scraping. String manipulation helps clean, transform, and extract useful information from text.
#### 2. User Input Handling: 
Most software applications require user input, which is typically in string format. Proper string handling ensures robust data validation and processing.
#### 3. Data Science & NLP: 
In Natural Language Processing (NLP) and data science, text preprocessing is essential for tokenization, stemming, lemmatization, and vectorization.
#### 4. File Handling: 
Strings are crucial when working with file I/O operations such as reading and writing text files.
#### 5. Regex & Pattern Matching: 
Extracting specific patterns from large text data is essential in web scraping, log analysis, and data mining.

### String Methods in Python
Python provides several built-in string methods that allow for manipulation, searching, formatting, and other operations.

### 1. String Creation & Basic Operations


```python
string = "Hello, World!"
print(string)
```

    Hello, World!
    

* Strings can be created using single (`'`), double (`"`), or triple (`'''` or `"""`) quotes.

#### Concatenation (`+`)


```python
string1 = "Hello"
string2 = "World"
result = string1 + " " + string2 # we need to add space between words
print(result)
```

    Hello World
    


```python
result = string1 + string2 # this will remove space 
print(result)
```

    HelloWorld
    

#### Repetition (*)


```python
string = "Hi! "
print(string * 3)
```

    Hi! Hi! Hi! 
    

#### Indexing (`[ ]`)
* Indexing in python starts from 0 in forward direction.
* Negative indexing starts from -1 in backward direction
* PYTHON: here 0 index means P and -1 index means N


```python
string1 = "Sandeep"
string1[0] # Index 0 is S
```




    'S'




```python
string1[-1] ## Index -1 is p
```




    'p'




```python
string1[-4] # index -4 is d
```




    'd'




```python
string1[3] # index 3 is also d
```




    'd'



#### Slicing (`[::]`)
* Slicing starts from [start:stop:steps]
* Start is starting index position. It is based on our question only.
* Stop is end index position, but always `stop + 1` based on desired value
* Default step is 1


```python
String1 = "PYTHON"
String1[0:3] # here starting positon is index 0 (P) and end position is index 2 (T) hence stop + 1 is 3
```




    'PYT'




```python
String1[:3] # by default starting position is 0
```




    'PYT'




```python
String1[1:] # starting index position is 1 (Y) and end position is last alphabet 
```




    'YTHON'




```python
String1[-3:] # starting index position is from backward direction which is H and end is again last alphabet
```




    'HON'




```python
String1[::2] # starting position is by default index 0 and end position is last alphabet. Step is 2. Hence, it will skip one alphabet
```




    'PTO'



### 2. String Methods for Modification
#### `upper()` - Changing Case


```python
String1 = "Python"
String1.upper() # all alphabets will be capitalized
```




    'PYTHON'



#### `lower()` - Changing Case


```python
String1.lower() # all alphabets will be in lower case
```




    'python'



#### `capitalize()`


```python
string = "hello world"
string.capitalize() # first alphabet will be capital
```




    'Hello world'



#### `title()`


```python
string.title() # First alphabet of each word is capitalized
```




    'Hello World'



#### `swapcase()` - Swaps Upper and Lower Case


```python
string1 = "PyThOn"
string1.swapcase() # uppercase will be lower case and lower case will be converted in upper case
```




    'pYtHoN'



#### Removing Whitespace
`strip()`


```python
string1 = "   hello world   "
string1.strip() # it will remove white space from both side
```




    'hello world'



`lstrip()`


```python
string1.lstrip() # it will remove white space from left side
```




    'hello world   '



`rstrip()`


```python
string1.rstrip() # it will remove white space from right side
```




    '   hello world'



### 3. Searching & Replacing
#### Finding Substrings

`find()`


```python
string = "Hello World!"
string.find("World") # W starts from index 6 hence output will be 6
```




    6




```python
string.rfind("o") # It will check last occurence of o
```




    7



If substring is not found, it returns `-1`.


```python
string.find("Hi")
```




    -1



#### Similar to find(), but raises an error if not found

`index()`


```python
string.index("World") # same as find function
```




    6



`rindex()`


```python
string.rindex("o")
```




    7



#### Replacing a Substring
`replace(original, replacement)`


```python
string1 = "Python is Great!"
string1.replace("Great", "Awesome")
```




    'Python is Awesome!'



### 4. String Splitting & Joining

#### Splitting a String
`split()`


```python
string1 = "apple,banana,grape"
string1.split(",") # split the words from ,
```




    ['apple', 'banana', 'grape']



* Default split is based on whitespace.

#### Joining a List into a String
`join()`


```python
words = ['Python', 'is', 'great']
print(" ".join(words))
```

    Python is great
    

### 5. String Checking Methods
`startswith(x)`
* It checks if it `starts` with x or not. x can be alphabet or a word or something else.


```python
string1 = 'Hello World'

print(string1.startswith("Hello"))
```

    True
    

`endswith(x)`
* It checks if it `ends` with x or not. x can be alphabet or a word or something else.


```python
print(string1.endswith("World"))
```

    True
    

#### Checks if all characters are alphabets
`isalpha()`


```python
string1.isalpha() # this will give false as there is a white space
```




    False




```python
String1 = "Hello"
String1.isalpha() # This will be true as there are only alphabets
```




    True



#### Checks if all characters are digits
`isdigit()`


```python
string1 = "12345"
string1.isdigit()
```




    True



#### Checks if all characters are alphanumeric
`isalnum`


```python
string1 = "Hello123"
string1.isalnum()
```




    True



#### Checks if string has only whitespace
`isspace()`


```python
string1 = "   "
string1.isspace()
```




    True



### 6. String Formatting
`format()` - String Formatting


```python
Name = "Sandeep"
Age = 42
print("My name is {} and I am {} years old.".format(Name, Age))
```

    My name is Sandeep and I am 42 years old.
    

`f-string`


```python
print(f"My name is {Name} and I am {Age} years old.")
```

    My name is Sandeep and I am 42 years old.
    

### 7. Reversing a String


```python
string1 = "Python"
print(string1[::-1]) # it will start from backward direction and take -1 step
```

    nohtyP
    


```python
print("".join(reversed(string1)))
```

    nohtyP
    

### 8. Counting Characters
#### Count Occurrences of a Substring
`count()`


```python
string1 = "banana"
print(string1.count("a")) # count how many times a is there
```

    3
    

### 9. Advanced String Manipulation
`translate()`


```python
string1 = "aeiou"

table = str.maketrans(string1, "12345") # replacing vowesl with numbers so a = 1, e = 2, i = 3, o = 4, u = 5
string2 = "Hello"

string2.translate(table) # here e = 2 and o = 4
```




    'H2ll4'



### Practice Excercise

#### 1. Cleaning and Formatting User Input
##### Scenario: You are building a user registration system. You need to ensure that user names are properly formatted.

##### Task:
* Remove any extra spaces before and after the username.
* Capitalize only the first letter of each word in the username.
* Convert email addresses to lowercase.


```python
username = "   jOhN dOe   "
email = "John.Doe@EXAMPLE.com"

def cleandata(user, em):
    user = user.strip().title()
    em = em.lower()
    return f"username= {user}, email = {em}"
       

cleandata(username, email)
```




    'username= John Doe, email = john.doe@example.com'



#### 2. Extracting Initials from a Name
##### Scenario: You are generating user initials for a name badge.

##### Task:
Given a full name, extract the initials and return them in uppercase.


```python
name = "sandeep kumar singh"

# using join function
initials = ".".join([word[0].upper() for word in name.split()])

# split() function splits the string into a list of words
# for word in name.split() goes through each word
# word[0].upper() extract first word and convert it into uppercase
# ".".join will add initials using .
print(initials)
```

    S.K.S
    

#### 3. Finding the Most Frequent Character
##### Scenario: You are analyzing text to find the most commonly occurring character.

##### Task:
Find the most frequently occurring character in a given string (ignoring spaces).


```python
text = "hello world"

text = text.replace(" ", "") # replacing white space
most_frequent = max(set(text), key = text.count)
# set(text) will creates a set of unique characters
# text.count(char) counts how many times each character appears in text.

print(f'Most frequent character: "{most_frequent}"')
```

    Most frequent character: "l"
    

#### 4. Verifying a Numeric String
##### Scenario: You need to validate a numeric input from users.

##### Task:
* Check if a given string contains only digits.
* If it is a valid number, convert it to an integer.


```python
user_input = "  98765  "

print(user_input.isdigit()) # checking if it is digit or not
user_input = int(user_input.strip()) # removing whitespace
print(user_input)
type(user_input)
```

    False
    98765
    




    int




```python
user_input = "  s98765  "

def valid(num):
    if num.strip().isdigit(): # checking space and checking if it is digit or not
        valid_number = int(num.strip()) # removing space and converting it into integer
        print(f"Valid Number: {valid_number}")
    else:
        print("Invalid input")

valid(user_input)
```

    Invalid input
    

#### 5. Word Count in a Sentence
##### Scenario: You are building a basic text analyzer.

##### Task:
Count the number of words in a given sentence.


```python
sentence = "Python is an amazing programming language"

def count_words(word):
    word_count = len(word.split()) # first split the string by default white space and check the length (by defualt it will count words)
    return word_count

count_words(sentence)
```




    6



#### 6. Abbreviating a Sentence
##### Scenario: You need to create an abbreviation from a given phrase.

##### Task:
Take the first letter of each word and return it in uppercase.


```python
phrase = "National Aeronautics and Space Administration"

phrase = phrase.replace("and", "") # removing and
abbreviation = "".join([word[0].upper() for word in phrase.split()])
print(abbreviation)
```

    NASA
    

#### 7. Checking if a String is a Palindrome
##### Scenario: You need to check if a given word is the same forward and backward.

##### Task:
* Ignore case and spaces.
* Return True if it is a palindrome, else False.


```python
word = "Racecar"

def palindrome(x):
    if x == x[::-1].title():# reverse the word and make first character uppercase
        print(f"{x} is Palindrome")
    else:
        print(f"{x} is a normal word")

palindrome(word)
```

    Racecar is Palindrome
    

#### 8. Replacing a Word in a Sentence
##### Scenario: You want to replace a word in a sentence.

##### Task:
Replace all occurrences of the word "bad" with "good"


```python
sentence = "This is a bad example of bad coding."

def good(text):
    text = text.replace("bad", "good")
    return text

good(sentence)
```




    'This is a good example of good coding.'



#### 9. Capitalizing Every Other Letter
##### Scenario: You want to create a "stylized" text format.

##### Task:
Convert a given string so that every alternate letter is uppercase.


```python
text = "hello world"

# Capitalizing every alternate character
stylized_text = "".join([char.upper() if i % 2 == 0 else char.lower() for i, char in enumerate(text)])
# enumerate function gives both index (i) and character (char)
# if index is even, then convert to uppercase (char.upper)
# else lower case (char.lower)
# join will combine list into string

print(stylized_text)
```

    HeLlO WoRlD
    

#### 10. Finding the Longest Word
##### Scenario: You are analyzing text to find the longest word in a sentence.

##### Task:
Return the longest word from a given sentence.


```python
sentence = "Data science is a fascinating field"

longest_word = max(sentence.split(), key =len) # max will compare the length of elements (words) key=len

print(longest_word)
```

    fascinating
    

[⬅ Back to Home](../index.md)

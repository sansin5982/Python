# Regular Expression 

**Regular Expressions** (RegEx) allow you to search for patterns in text using special syntax. It's a powerful tool for string processing, especially useful when working with messy or unstructured data.

* It is an inbuilt module (re).


## Why Use Regular Expressions?

- Clean or extract information from user input
- Identify patterns like dates, names, IDs, emails, etc.
- Validate inputs like mobile numbers or passwords
- Modify text in documents, logs, or websites

## Metacharacters

| Charatcer | Description | Example |
|:---------|:--------------|:---------|
|`[ ]` | A set of characters | [2-5] |
|`{ }` | Exactly the specified number of occurrences | Sa.{4}p |
| `\` | Signals a special sequence | \d|
|`.`|Any character (except newline character)|	"Sa....p"|
|`^`|Starts with|^Hi|
|`I`| Either or |"AIB"|
|`+`|One or more occurence|"he.+o|



## Special Sequence
A special sequence is a `\` followed by one of the characters in the list below, and has a special meaning:

|Character|Description|Example|
|:---|:---|:---|
|`\A`|Returns a match if the specified characters are at the beginning of the string|"\AThe"|
|`\b`|Returns a match where the specified characters are at the beginning or at the end of a word|r"\bain"|
|`\B`|Returns a match where the specified characters are present, but NOT at the beginning (or at the end) of a word|r"\Bain"|
|`\d`|Returns a match where the string contains digits (numbers from 0-9)|"\d"|
|`\D`|Returns a match where the string DOES NOT contain digits|"\D"|
|`\s`|Returns a match where the string contains a white space character|"\s"|
|`\S`|Returns a match where the string DOES NOT contain a white space character|"\S"|
|`\w`|Returns a match where the string contains any word characters (characters from a to Z, digits from 0-9, and the underscore _ character)|"\w"|
|`\W`|Returns a match where the string DOES NOT contain any word characters|"\W"|
|`\Z`|Returns a match if the specified characters are at the end of the string|""Spain\Z""|

* the "r" in the beginning is making sure that the string is being treated as a "raw string"

## Sets
A set is a set of characters inside a pair of square brackets `[]` with a special meaning:

|Set|Description|
|:---|:---|
|`[anx]`|Returns a match where one of the specified characters (`a`, `n`, or `x`) is present|
|`[a-g]`|Returns a match for any lower case character, alphabetically between `a` and `g`|
|`[^aem]`|Returns a match for any character `EXCEPT` `a`, `e`, and `m`|
|`[012]`|Returns a match where any of the specified digits (`0`, `1`, or `2`) are present|
|`[0-9]`|Returns a match for any digit between `0` and `9`|
|`[0-5][0-9]`|Returns a match for any two-digit numbers from 00 and 59|
|`[a-zA-Z]`|Returns a match for any character alphabetically between `a` and `z`, lower case OR upper case|
|`[+]`|In sets, `+`, `*`, `.`, `()`, `{}`, `$` has no special meaning, so `[+]` means: return a match for any `+` character in the string|

### Import regulat expression


```python
import re
```

### **re.compile()**

Compiling regular expression objects is useful and efficient when the expression will be used several times in a single program.

### **re.match()**

match() function of re in Python will search the regular expression pattern and **return the first occurrence**.


```python
course = "GenAI25 starts with a bang!"

compiled_pat = re.compile("[\w]*")   # Pattern to match zero or more word characters
print(compiled_pat)

result = compiled_pat.match(course)
print(result)
```

    re.compile('[\\w]*')
    <re.Match object; span=(0, 7), match='GenAI25'>
    

#### Explanation:
* `[\w]*` means:
* `\w` matches any alphanumeric character or underscore (i.e., `[a-zA-Z0-9_]`)
* `*` means zero or more occurrences
* `.match()` checks from the **beginning** of the string.
* So it will match as many word characters as it finds from the start.
* It matched `"GenAI25"` because that’s the sequence of word characters at the beginning of the string.

### re.fullmatch()
* It tries to match the entire string against the pattern.
* If the whole string doesn’t match, it returns None.


```python
result = compiled_pat.fullmatch(course)
print(result)
```

    None
    


```python
GEN = "Gen25"

# Pattern: one or more word characters (alphanumeric + underscore)
compiled_pat = re.compile(r"\w+")

# Use fullmatch to match the **entire** string
result = compiled_pat.fullmatch(GEN)

print(result)
```

    <re.Match object; span=(0, 5), match='Gen25'>
    

* `r"\w+"` matches one or **more word characters** (same as [a-zA-Z0-9_])
* `GEN = "Gen25"` contains only word characters → **full match**
* `fullmatch()` returns a `Match` object only if the **entire string** matches the pattern.

### **re.findall()**
* returns a list of all non-overlapping matches


```python
course = "GenAI25 starts with a bang!"

compiled_pat = re.compile("[\w]*")   # Pattern to match zero or more word characters
findall_result = compiled_pat.findall(course)
print("Findall result:", findall_result)
```

    Findall result: ['GenAI25', '', 'starts', '', 'with', '', 'a', '', 'bang', '', '']
    


```python
GEN = "Gen25 is in the Third Week of GenAI course"
#Check if the string starts with 'Batch number':

x = re.findall("^Gen25", GEN) # Starts with DS
if x:
  print("Yes, Gen25 is present'")
else:
  print("No match")

```

    Yes, Gen25 is present'
    


```python
GEN = "Gen25 is in the Third Week of GenAI course"
#Check if the string ends with 'course':

x = re.findall("course$", GEN) # end with course
if x:
  print("Yes, the string ends with course'")
else:
  print("No match")
```

    Yes, the string ends with course'
    


```python
Gene_Seq = "ATGCGCCTACAATCGGTACGTCATCGCGCGCGCTTAC"

print(re.findall("GCGCG.+GCT", Gene_Seq)) # string starts with GCGCG and ends with GCT
```

    ['GCGCGCGCT']
    

### re.search()
* Searches the **first occurrence of the pattern** anywhere in the string


```python
search_result = compiled_pat.search(course)
print("Search result:", search_result)
```

    Search result: <re.Match object; span=(0, 7), match='GenAI25'>
    


```python
Gene_Seq = "ATGCGCCTACAATCGGTACGTCATCGCGCGCGCTTACGCGCGCGC"

# The search() function searches the string for a match, and returns a Match object if there is a match.
print(re.search("GCGCGCGC", Gene_Seq)) #
```

    <re.Match object; span=(25, 33), match='GCGCGCGC'>
    

* `.match()` is great for validating string formats (e.g., check if a name or ID starts correctly).
* `.search()` helps find something anywhere in a log or text.
* `.findall()` is useful for extracting tokens, keywords, or entities from a sentence or document (like Named Entity Recognition).

## Match object

### re.span()
* returns a tuple containing the start-, and end positions of the match.


```python
sentence = "Learning GenAI is exciting"

# \b matches a word boundary
# \w+ matches one or more word characters
pattern = r"\be\w+"

x = re.search(pattern, sentence)

print(x)
print(x.span())  # shows the start and end position of the matched word
```

    <re.Match object; span=(18, 26), match='exciting'>
    (18, 26)
    

* It found the first word starting with 'e' → `'exciting'`
* `.span()` returns (18, 26), which are the start and end character positions of the match in the string "Learning GenAI is exciting"

#### Explanation
* `r"\be\w+"` is a regular expression pattern:
* `\b` ensures the match starts at a word boundary (i.e., not in the middle of a word).
* `e\w+` means the word must **start with 'e'**, followed by **one or more word characters** (letters, digits, or underscore).


```python
text = "Order ID: A5678, Customer: John"

pattern = r"ID: (A\d+), Customer: (?P<name>\w+)"
match = re.search(pattern, text)
```

* `.start()` → returns the starting index of the matched text in the original string
* `.end()` → returns the ending index (exclusive) of the match
* `.span()` → returns a tuple (start, end)


```python
match.start()  # starting index position is I of ID
```




    6




```python
match.end()  # end positionis n of John   
```




    31




```python
match.span() # starting and ending position  
```




    (6, 31)



### re.finditer()
* `re.finditer()` returns an **iterator of Match objects for all non-overlapping matches** of a pattern in a string.
* Unlike `findall()` (which returns a list of strings), finditer() gives you more control, including match positions `(.span())` and matched groups `(.group())`.


```python
text = "ID01, ID02, ID03 are active."

# Pattern to match IDs like 'ID01', 'ID02', etc.
pattern = r"ID\d+"

# Use finditer to loop through matches
for match in re.finditer(pattern, text):
    print("Match:", match.group())
    print("Position:", match.span())
```

    Match: ID01
    Position: (0, 4)
    Match: ID02
    Position: (6, 10)
    Match: ID03
    Position: (12, 16)
    

#### Explanation
* `r"ID\d+"`:
    * Matches the letters "ID" followed by one or more digits (`\d+`)
* `re.finditer()`:
    * Returns an **iterator** over all matches.
    * Each item is a **Match object** with methods like `.group()`, `.start()`, `.end()`, `.span()`, and `.string`

### re.string()
* returns the string passed into the function


```python
sentence = "Welcome to the DataScience course"

# Search for a word that starts with 'D' at a word boundary
x = re.search(r"\bD\w+", sentence)

print(x)             # Match object
print(x.string)      # Original string passed to re.search()
```

    <re.Match object; span=(15, 26), match='DataScience'>
    Welcome to the DataScience course
    

#### Explanation
#### Pattern: `r"\bD\w+"`
* `\b` → word boundary
* `D` → looks for words starting with uppercase 'D'
* `\w+` → one or more word characters (letters, numbers, underscore)

So, the pattern finds the first word starting with 'D'.

* `x.string` is a property of the `Match object` returned by `re.search()`
* It gives us the **original string** that was passed into the **search()** function — in this case, `'Welcome to the DataScience course'`
* This is useful when you are handling multiple patterns on the same input and want to reference the input text directly from the match object.

### re.group()
* x is a **Match object** returned by re.search() (or re.match()).
* `.group()` is a method that returns the **actual substring** from the input string that matched the regular expression.


```python
print(x.group())     # Matched word
```

    DataScience
    

#### Explanation:
* `re.search(r"\bD\w+", sentence)` looks for a word starting with 'D'
* It finds `"DataScience"` and stores info in the `Match` object `x`
* `x.group()` returns "DataScience" — this is the matched part of the string

* If there’s no match, `.group()` will raise an error.


```python
text = "Order ID: A5678, Customer: John"

pattern = r"ID: (A\d+), Customer: (?P<name>\w+)"
match = re.search(pattern, text)
```

The regex pattern:

* `ID: (A\d+)` — Group 1: matches 'A5678' (alphanumeric order ID)
* `(?P<name>\w+)` — Named Group 'name': matches 'John'

#### match.group()
We can specify:
* `group(0)` → full match
* `group(1)` → first captured group (first ())
* `group('name')` → named group using `?P<name>`


```python
match.group(0)       # 'ID: A5678, Customer: John'
```




    'ID: A5678, Customer: John'




```python
match.group(1)       # 'A5678'
```




    'A5678'




```python
match.group('name')  # 'John'
```




    'John'



Use `group(n)` when we want to **extract specific pieces** of the matched string.

### re.groups()
* Returns a **tuple** of **all capturing groups, in order**.
* Does **not** include group(0) (the full match).
* Only works for **numbered groups**.


```python
match.groups()   # ('A5678', 'John')
```




    ('A5678', 'John')



Use this when we want to retrieve all captured groups at once, especially if we don’t care about named access.

### re.groupdict()
* Returns a **dictionary** of all **named capturing groups**.
* Keys are group names; values are their matched text.


```python
match.groupdict()
```




    {'name': 'John'}



* `.span()` → positions
* `.string` → full input string
* `.group()` → just the matched part

### re.split()
* The `split()` function returns a list where the string has been split at each match:


```python
info = "The temperature is 45 degrees today."

print(info.split('45')) # here I want to split them using number
```

    ['The temperature is ', ' degrees today.']
    

* `split('45')` tells Python to **split the string** at the **exact match** of **"45"** (a string, not a number).
* It returns a **list of substrings** divided around where '45' appeared.
* '45' is a **string**, not an integer. split() always expects a **string argument**.


```python
# The split() function returns a list where the string has been split at each match:
print(re.split("\d", info)) # It splitted both numbers
```

    ['The temperature is ', '', ' degrees today.']
    

* `"\d"` is a **regex pattern** that matches any **single digit** (0-9).
    * So `"\d"` matches `'4'` and `'5'` **separately**, not as `'45'`.


```python
Date = "10-04-2022"
result = re.split("\D", Date, maxsplit=2) # maxsplit tells how many splits you want
# r for new string
# \D is for non digit characterstics
print(result)
```

    ['10', '04', '2022']
    

### re.sub()
* **text substitution** using regular expressions


```python
 # The sub() function replaces the matches with the text of your choice:
Gene_Seq = "ATGCGCGTACAATCGGTACGTCATCGCGCGCGCTTAC"

#  replaces the matches with the text of your choice:
print(re.sub("GCGCGCG", "ATTACHED", Gene_Seq)) #
```

    ATGCGCGTACAATCGGTACGTCATCATTACHEDCTTAC
    

#### Explanation
* `re.sub(pattern, replacement, string)`
* `pattern` = `"GCGCGCG"` → This is the sequence you want to search for in the string.
* `replacement` = `"ATTACHED"` → This is the text that will replace the matched pattern.
* `string` = `Gene_Seq` → The string where the pattern will be searched and replaced.

### re.subn()  
* `re.subn(pattern, replacement, string)`
* It replaces all occurrences of a pattern in a string (just like re.sub()), but it also returns:
    * A tuple: (`new_string, number_of_substitutions`)


```python
text = "apple and apple make two apples"

# Replace 'apple' with 'banana' and count how many replacements were made
result = re.subn(r"apple", "banana", text)

print("Updated Text:", result[0])
print("Replacements Made:", result[1])
```

    Updated Text: banana and banana make two bananas
    Replacements Made: 3
    

* **Pattern**: `r"apple"` matches every exact "apple"
* **Replacement**: `"banana"` replaces it
* `re.subn()` returns:
    * The **modified string**
    * The **number of substitutions**

So it gives you both the result and the metadata in one go — very handy for logging or validation.

### re.escape()
* a small but powerful function in the re module that’s especially useful when **working with special characters**.
* `re.escape(string)` **adds backslashes before all regex metacharacters** in a given string.
* This allows you to **safely use a string as a regex pattern**, even if it contains characters like `.` `*` `+` `?` `|` `^` etc.
* Regular expressions treat characters like `.`, `*`, `+`, and `?` as **special metacharacters**.
* If we want to search for these characters literally, we must **escape them**.


```python
text = "Price is 100.50$"

# Let's say we want to search for the exact string '100.50$'
pattern = re.escape("100.50$")  # Automatically escapes the special characters

# Now use it safely in search
match = re.search(pattern, text)

print("Pattern used:", pattern)
print("Match found:", match.group() if match else "No match")
```

    Pattern used: 100\.50\$
    Match found: 100.50$
    

* Original pattern: `"100.50$"`
* `.` means “any character”, `$` means “end of string” in regex
* `re.escape("100.50$")` → `"100\\.50\\$"` so the dot and dollar are treated `literally`.

### Summary table

| Function/Method    | Description                                             | Example Usage                                      |
|:--------------------|:---------------------------------------------------------|:----------------------------------------------------|
| `re.compile()`     | Compile a regex pattern into a reusable object          | `pattern = re.compile(r'\d+')`                    |
| `re.match()`       | Match pattern **only at the beginning** of a string     | `re.match(r'\w+', 'Word123')`                     |
| `re.search()`      | Search for the **first occurrence** anywhere            | `re.search(r'\d+', 'abc123')`                     |
| `re.fullmatch()`   | Match the **entire string** to the pattern              | `re.fullmatch(r'\d+', '123')`                     |
| `re.findall()`     | Return a **list** of all matches                        | `re.findall(r'\w+', 'Hello World 123')`           |
| `re.finditer()`    | Return **iterator** of match objects                    | `re.finditer(r'\w+', 'Hello World')`              |
| `re.split()`       | Split string using regex pattern                        | `re.split(r'\d+', 'ab12cd34')`                    |
| `re.sub()`         | Replace pattern with given replacement string           | `re.sub(r'apple', 'banana', 'apple pie')`         |
| `re.subn()`        | Same as sub, but also returns the number of replacements| `re.subn(r'apple', 'banana', 'apple apple pie')`  |
| `re.escape()`      | Escape special characters in pattern                    | `re.escape('1+1=2')`                               |
| `.group()`         | Return the matched string                               | `m.group()`                                       |
| `.groups()`        | Return all matched groups as tuple                      | `m.groups()`                                      |
| `.groupdict()`     | Return named groups as a dictionary                     | `m.groupdict()`                                   |
| `.span()`          | Return start and end index as a tuple                   | `m.span()`                                        |
| `.start()`/`.end()`| Return specific start or end index                      | `m.start()` / `m.end()`                           |
| `.string`          | Return the original searched string                     | `m.string`                                        |


### Practice Questions with Custom Scenarios

#### Q 1. Extract all student roll numbers like `AB1234` from a list of enrollments.
text = "Students: AB1234, CD5678, XY9999"


```python
text = "Students: AB1234, CD5678, XY9999"
print(re.findall(r"[A-Z]{2}\d{4}", text))
```

    ['AB1234', 'CD5678', 'XY9999']
    

**Explanation**: Two uppercase letters followed by 4 digits.

#### Q2. Validate if a given string is a valid Indian PAN number (format: 5 letters, 4 digits, 1 letter).
pan = "ABCDE1234F"


```python
pan = "ABCDE1234F"
match = re.fullmatch(r"[A-Z]{5}\d{4}[A-Z]", pan)
print("Valid PAN" if match else "Invalid PAN")
```

    Valid PAN
    

**Explanation**: 5 letters, 4 digits, 1 letter (standard PAN format).

#### Q3. Extract all hashtags from the sentence: `"Learning #regex is #fun and #useful"`.
sentence = "Learning #regex is #fun and #useful"


```python
sentence = "Learning #regex is #fun and #useful"
print(re.findall(r"#\w+", sentence))
```

    ['#regex', '#fun', '#useful']
    

#### Q4. Match all flight numbers (e.g., `AI203`, `EK501`) from airline logs.
flights = "AI203 landed before EK501"


```python
flights = "AI203 landed before EK501"
print(re.findall(r"[A-Z]{2}\d{3}", flights))
```

    ['AI203', 'EK501']
    

**Explanation**: 2 uppercase letters and 3 digits.

#### Q5. Find all percentage values in a performance report (like `76%`, `98%`).
report = "Math: 76%, Science: 88%, English: 90%"


```python
report = "Math: 76%, Science: 88%, English: 90%"
print(re.findall(r"\d+%", report))
```

    ['76%', '88%', '90%']
    

**Explanation**: One or more digits followed by %

#### Q6. Identify invoice numbers in this format: `INV-YYYY-NNN`.
invoices = "INV-2023-001, INV-2024-100"


```python
invoices = "INV-2023-001, INV-2024-100"
print(re.findall(r"INV-\d{4}-\d{3}", invoices))
```

    ['INV-2023-001', 'INV-2024-100']
    

**Explanation**: Format INV-YYYY-NNN.

#### Q7. Extract appointment times written in formats like `12:45 PM`, `9:15 AM`.
appointments = "12:45 PM, 9:15 AM"


```python
appointments = "12:45 PM, 9:15 AM"
print(re.findall(r"\d{1,2}:\d{2} [AP]M", appointments))
```

    ['12:45 PM', '9:15 AM']
    

**Explanation**: Hours:Minutes and AM/PM.

#### Q8. 8. Validate Indian vehicle registration numbers like `MH12DE1433`.


```python
vehicle = "MH12DE1433"
if re.fullmatch(r"[A-Z]{2}\d{2}[A-Z]{2}\d{4}", vehicle):
    print("Valid")
else:
    print("Invalid")
```

    Valid
    

#### Q9. Match all medication dosages in instructions: `"Take 1 tablet after food. Drink 10 ml syrup at night."`
instruction = "Take 1 tablet after food. Drink 10 ml syrup at night."


```python
instruction = "Take 1 tablet after food. Drink 10 ml syrup at night."
print(re.findall(r"\d+\s*(tablet|ml)", instruction))
```

    ['tablet', 'ml']
    

#### Q10. Validate or extract dates in `DD-MM-YYYY` format from a document
document = "Event: 21-04-2025, Deadline: 30-12-2024"


```python
document = "Event: 21-04-2025, Deadline: 30-12-2024"
print(re.findall(r"\d{2}-\d{2}-\d{4}", document))
```

    ['21-04-2025', '30-12-2024']
    

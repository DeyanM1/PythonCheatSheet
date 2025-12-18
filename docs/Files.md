# Python Files and OS. Complete Reference.

Copy sections directly into a Jupyter notebook.

---

## File I/O: Text & Binary

```python
# --- Basic Text Operations ---
with open('example.txt', 'w', encoding='utf-8') as f:   # opens file for writing (overwrites), sets encoding
    f.write("Hello World\n")                            # writes string to file
    f.write("Second Line")                              # writes another string (no newline added auto)

with open('example.txt', 'r', encoding='utf-8') as f:   # opens file for reading
    content = f.read()                                  # reads entire file into a single string
    # lines = f.readlines()                             # reads file into a list of lines

# --- Binary Operations (Images, Audio, Non-text) ---
data = b'\x00\x01\x02\x03'                              # creates a bytes object

with open('data.bin', 'wb') as f:                       # opens file for writing binary ('wb')
    f.write(data)                                       # writes bytes to file

with open('data.bin', 'rb') as f:                       # opens file for reading binary ('rb')
    chunk = f.read(4)                                   # reads specific number of bytes (4)

```

## Modern Paths with Pathlib

```python
from pathlib import Path

# --- Creating and Checking Paths ---
p = Path('folder') / 'subfolder' / 'file.txt'           # creates path object using intuitive '/' operator
p.parent                                                # returns the parent directory
p.name                                                  # returns the full filename (file.txt)
p.stem                                                  # returns filename without extension (file)
p.suffix                                                # returns the extension (.txt)

p.exists()                                              # returns True if file/dir exists
p.is_file()                                             # returns True if it is a file
p.is_dir()                                              # returns True if it is a directory

# --- Quick Read/Write (Python 3.5+) ---
path_obj = Path('quick_note.txt')                       # creates path object
path_obj.write_text("Quick content", encoding='utf-8')  # writes text to file (handles open/close)
text = path_obj.read_text(encoding='utf-8')             # reads text from file (handles open/close)

# --- Directory Iteration ---
cwd = Path.cwd()                                        # returns current working directory object
for file in cwd.glob('*.txt'):                          # iterates over all .txt files in directory
    print(file.name)                                    # prints the name of the file

```

## OS and Sys: Environment & Args

```python
import os
import sys

# --- System Arguments ---
# Run via terminal: python script.py arg1 arg2
print(sys.argv)                                         # returns list: ['script.py', 'arg1', 'arg2']

# --- Environment Variables ---
user = os.environ.get('USER', 'Guest')                  # gets env var 'USER', defaults to 'Guest' if missing
os.environ['MY_VAR'] = '123'                            # sets env var 'MY_VAR' to '123' for current process

# --- OS Navigation ---
current_dir = os.getcwd()                               # returns current working directory as string
os.chdir('..')                                          # changes directory (moves up one level)
os.mkdir('new_dir')                                     # creates a single directory
os.makedirs('a/b/c', exist_ok=True)                     # creates directory tree recursively (no error if exists)

# --- Walking a Directory Tree ---
for root, dirs, files in os.walk('.'):                  # recursively traverses current directory
    print(f"Checking {root}")                           # prints current folder path
    for filename in files:                              # iterates through files in that folder
        print(f" - Found {filename}")                   # prints filename

```

## High-Level Operations: Shutil

```python
import shutil

# --- Copying Files ---
shutil.copy('source.txt', 'dest.txt')                   # copies data and permissions
shutil.copy2('source.txt', 'backup_folder/')            # copies data, permissions, and metadata (timestamps)

# --- Moving and Renaming ---
shutil.move('source.txt', 'moved_source.txt')           # moves file (or renames it)

# --- Directory Operations ---
# shutil.rmtree('folder_to_delete')                     # deletes directory tree recursively (careful!)

# --- Archiving (Zipping) ---
shutil.make_archive('backup', 'zip', 'data_dir')        # zips 'data_dir' into 'backup.zip'
shutil.unpack_archive('backup.zip', 'restore_dir')      # extracts 'backup.zip' into 'restore_dir'

```

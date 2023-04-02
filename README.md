# MemeDB
MemeDB is a minimal in-memory key-value database that doesn't take itself too seriously. It's designed to be simple, lightweight, and fun to use.

## Installation
Install MemeDB from PyPI:

```bash
pip install memedb
```

## Quick Start
Create a new MemeDB instance and add some data:

```python
from memedb import MemeDB

db = MemeDB()
db.set("key1", "value1")
db.set("key2", {"nested_key": "nested_value"})
```

Retrieve data by key:

```python
value = db.get("key1")
print(value)  # output: "value1"

nested_value = db.get("key2")["nested_key"]
print(nested_value)  # output: "nested_value"
```

Delete data by key:

```python
db.delete("key1")
```

Use transactions for atomicity:

```python
with db.transaction():
    db.set("key1", "new_value")
    db.delete("key2")
```

## Advanced Features
MemeDB also includes some more advanced features to make it more powerful:

### Indexing
You can create an index for a specific key to speed up lookups:

```python
db.index("name")
db.set("person:1", {"name": "Alice", "age": 30})
db.set("person:2", {"name": "Bob", "age": 25})
db.set("person:3", {"name": "Charlie", "age": 35})

result = db.lookup("name", "Alice")
print(result)  # output: [{"name": "Alice", "age": 30}]
```

### Querying
You can perform queries on the data using a simple SQL-like syntax:

```python
db.set("person:1", {"name": "Alice", "age": 30})
db.set("person:2", {"name": "Bob", "age": 25})
db.set("person:3", {"name": "Charlie", "age": 35})

result = db.query("SELECT * FROM data WHERE age > 30")
print(result)  # output: [{"name": "Charlie", "age": 35}]
```

### Caching
You can add a cache to MemeDB to speed up access to frequently accessed data:

```python
from memedb import Cache

cache = Cache(max_size=1000, ttl=3600)  # cache up to 1000 items for 1 hour
db = MemeDB(cache=cache)

db.set("key1", "value1")
db.get("key1")  # retrieves from cache
```

## Contributions
Contributions are welcome! If you have a feature request or bug report, please open an issue on GitHub. If you'd like to contribute code, please fork the repository and submit a pull request.

## Acknowledgments
I'd like to thank my personal AI assistant, ChatGPT, for helping me bring this project to life. They provided endless encouragement, offered valuable suggestions, and even told me a few jokes to keep my spirits up. I'm pretty sure they're secretly a comedian in their spare time. So if you find yourself chuckling at anything in this project, just know that it's all thanks to ChatGPT's comedic genius.

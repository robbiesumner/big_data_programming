This exercise will be done without any special distributed computing frameworks, just plain Python, to help illustrate the core concepts of MapReduce.

Here is the step by step breakdown of the exercise:

**Step 1:** Define your documents. In this example, we'll use a list of strings.

```python
documents = [
    "the cat in the hat",
    "green eggs and ham",
    "one fish two fish red fish blue fish",
]
```

**Step 2:** Define the "map" function. This function will take a document and output a list of (key, value) pairs, where the key is a word and the value is 1.

```python
def map_document(document):
    words = document.split()
    return [(word, 1) for word in words]
```

**Step 3:** Apply the "map" function to each document. The result is a list of lists.

```python
mapped = [map_document(document) for document in documents]
```

**Step 4:** Flatten the list of lists into a single list of (key, value) pairs.

```python
pairs = [pair for sublist in mapped for pair in sublist]
```

**Step 5:** Define the "reduce" function. This function will take a key and a list of values, and combine the values in some way. In this case, we will add up the values to get the total count for each word.

```python
def reduce_word(word, values):
    return word, sum(values)
```

**Step 6:** Group the (key, value) pairs by key.

```python
from collections import defaultdict

grouped = defaultdict(list)
for key, value in pairs:
    grouped[key].append(value)
```

**Step 7:** Apply the "reduce" function to each group of values.

```python
reduced = {word: reduce_word(word, values) for word, values in grouped.items()}
```

**Step 8:** Print the final word counts.

```python
for word, count in reduced.items():
    print(f"{word}: {count}")
```

After following these steps, you should see output like this:

```
the: 2
cat: 1
in: 1
hat: 1
green: 1
eggs: 1
and: 1
ham: 1
one: 1
fish: 4
two: 1
red: 1
blue: 1
```

This is a basic example of the MapReduce programming model. In a real-world scenario, the "map" and "reduce" functions would be executed in parallel on a distributed computing system, allowing for efficient processing of large datasets.
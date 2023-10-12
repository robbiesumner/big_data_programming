**Problem Description:**

You are working as a data analyst in a company that has a text based system which collects customer feedbacks. You are given a large dataset of feedbacks in the form of a list of sentences (each feedback is a string). 

Your task is to analyze the feedbacks and find the frequency of each word appearing across all the feedbacks. 

For simplicity, you can assume that all words are separated by a space and you can ignore punctuations. 

**Additional Details:**

You need to solve this problem using the map-reduce paradigm.

- In the mapping phase, you will split each sentence into words and create a key-value pair for each word. The key will be the word and the value will be 1, representing one occurrence of the word.

- In the reducing phase, you will aggregate the key-value pairs by their key (the word) and sum up their values to get the total count of each word.

Here is a skeleton of the code to get you started.

```python
def mapper(feedback):
    # TODO: Implement this function
    pass

def reducer(mapped_data):
    # TODO: Implement this function
    pass

def map_reduce(feedbacks):
    mapped_data = []
    for feedback in feedbacks:
        mapped_data.extend(mapper(feedback))
    
    return reducer(mapped_data)

feedbacks = [ 
    "I love the product", 
    "The product is great and I use it everyday", 
    "The quality of the product is not good", 
    # Add more feedbacks
]

print(map_reduce(feedbacks))
```

You should get a output like this:

```
{
    "I": 2,
    "love": 1,
    "the": 3,
    "product": 3,
    "is": 2,
    "great": 1,
    "and": 1,
    "use": 1,
    "it": 1,
    "everyday": 1,
    "quality": 1,
    "of": 1,
    "not": 1,
    "good": 1,
}
```

This exercise will help you understand how the map-reduce concept works in a distributed computing environment. In a real world scenario, the mapper and reducer functions would run on different machines in a cluster to process large amount of data in parallel.
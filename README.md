### EX3 Implementation of GSP Algorithm In Python
### DATE: 18.11.2026
### Name : Cholimgapuram Sai Likitha
### Reg.no.: 212224230046
### AIM: To implement GSP Algorithm In Python.
### Description:
The Generalized Sequential Pattern (GSP) algorithm is a data mining technique used for discovering frequent patterns within a sequence database. It operates by identifying sequences that frequently occur together. GSP works by employing a depth-first search strategy to explore and extract frequent patterns efficiently.
### Steps:
1. <strong>Database Scanning:</strong> GSP scans the sequence database to determine the support of each item in the dataset.
2. <strong>Candidate Generation:</strong> It generates a set of candidate sequences using frequent items found in the previous step.
3. <strong>Pattern Growth:</strong> It extends the candidate sequences by merging them to form longer patterns, checking their support against a user-defined minimum support threshold.
4. <strong>Repeat:</strong> The process continues until no new sequences meet the minimum support threshold.
<p align="justify">
GSP finds application in various domains such as market basket analysis, web usage mining, bioinformatics, and more. For instance, in retail, GSP can identify common purchasing patterns, helping businesses understand customer behavior for targeted marketing or inventory management.
</p>

### Procedure:
<p align="justify">
1. From collections import defaultdict, from itertools import combinations: Imports necessary libraries/modules. defaultdict is
used to create a dictionary with default values and combinations generates all possible combinations of a sequence.</p>
<p align="justify">
2. generate_candidates(dataset, k): Function to generate candidate k-item sequences from a dataset. It loops through each sequence in the
dataset and finds combinations of length k for each sequence, updating their counts in a dictionary.</p>
<p align="justify">
3. gsp(dataset, min_support): Function that implements the Generalized Sequential Pattern (GSP) algorithm. It iterates through increasing
sequence lengths (k) until no new frequent patterns are found. It calls generate_candidates() to find patterns of varying lengths.</p>
<p align="justify">
4. Example dataset for each category: Defines example sequences for top wear, bottom wear, and party wear categories.</p>
<p align="justify">
5. Minimum support threshold: Sets the minimum support count required for a pattern to be considered frequent.</p>
<p align="justify">
6. Perform GSP algorithm for each category: Applies the GSP algorithm for each category using the defined example datasets and the
minimum support threshold.</p>
<p align="justify">
7. Output the frequent sequential patterns for each category: Prints the frequent sequential patterns 
    along with their support counts
for each wear category.</p>
<p align="justify">
8. Visulaize the sequence patterns using matplotlib.
</p>
### Program:

```

from itertools import combinations

def gsp(dataset, min_support):
    result = {}
    k = 1

    while True:
        count = {}

        for sequence in dataset:
            for pattern in combinations(sequence, k):
                if pattern in count:
                    count[pattern] += 1
                else:
                    count[pattern] = 1

        found = False

        for pattern in count:
            if count[pattern] >= min_support:
                result[pattern] = count[pattern]
                found = True

        if not found:
            break

        k += 1

    return result


top_wear_data = [
    ["blouse", "t-shirt", "tank_top"],
    ["hoodie", "sweater", "top"],
    ["hoodie"],
    ["hoodie", "sweater"]
]

bottom_wear_data = [
    ["jeans", "trousers", "shorts"],
    ["leggings", "skirt", "chinos"]
]

party_wear_data = [
    ["cocktail_dress", "evening_gown", "blazer"],
    ["party_dress", "formal_dress", "suit"],
    ["party_dress", "formal_dress", "suit"],
    ["party_dress", "formal_dress", "suit"],
    ["party_dress", "formal_dress", "suit"],
    ["party_dress"],
    ["party_dress"]
]

min_support = 2

top = gsp(top_wear_data, min_support)
bottom = gsp(bottom_wear_data, min_support)
party = gsp(party_wear_data, min_support)

print("Top Wear:")
for pattern, support in top.items():
    print(pattern, "Support:", support)

print("\nBottom Wear:")
for pattern, support in bottom.items():
    print(pattern, "Support:", support)

print("\nParty Wear:")
for pattern, support in party.items():
    print(pattern, "Support:", support)

```
### Output:
<img width="527" height="317" alt="image" src="https://github.com/user-attachments/assets/574391a4-6589-4342-aae3-88bf62fd9c2e" />

### Visualization:
```
def visualize(result, category):
    if result:
        patterns = [str(p) for p in result.keys()]
        support = list(result.values())
        plt.figure(figsize=(10, 6))
        plt.plot(patterns, support, marker='o', color='blue')
        plt.xlabel("Patterns")
        plt.ylabel("Support")
        plt.title(category)
        plt.xticks(rotation=90)
        plt.tight_layout()
        plt.show()
    else:
        print("No frequent patterns found in", category)
visualize(top, "Top Wear")
visualize(bottom, "Bottom Wear")
visualize(party, "Party Wear")

```
### Output:
<img width="585" height="347" alt="image" src="https://github.com/user-attachments/assets/6410d72b-6236-46d2-b316-c1fd0409d594" />
<img width="573" height="345" alt="image" src="https://github.com/user-attachments/assets/413b4b4f-d5fc-4ed3-be2c-12812ff4b71d" />


### Result:
Hence , implementation of GSP Algorithm In Python has been done successfully.

Certainly! Here’s a detailed guide for a module on "C# Sets".

### Module: C# Sets

#### Overview
This module will cover the concept of sets in C#, including the `HashSet<T>`, `SortedSet<T>`, and `ImmutableHashSet<T>`. We will explore their usage, properties, and methods.

#### Objectives
By the end of this module, you should be able to:
- Understand what sets are and how they work in C#
- Use `HashSet<T>` and `SortedSet<T>` for storing unique elements
- Perform common set operations like union, intersection, and difference
- Understand the advantages of using `ImmutableHashSet<T>`

---

### 1. Introduction to Sets
Sets are collections of unique elements. They do not allow duplicate entries and provide efficient operations for set-related tasks.

#### Key Characteristics:
- Unique elements
- Unordered in `HashSet<T>`, ordered in `SortedSet<T>`
- Efficient for membership tests

### 2. HashSet<T>
`HashSet<T>` is the most commonly used set in C#. It uses a hash table for storage, providing fast lookups.

#### Creating a HashSet
```csharp
HashSet<int> numbers = new HashSet<int>();
```

#### Adding Elements
```csharp
numbers.Add(1);
numbers.Add(2);
numbers.Add(3);
```

#### Removing Elements
```csharp
numbers.Remove(2);
```

#### Checking Membership
```csharp
bool containsOne = numbers.Contains(1); // true
```

#### Common Operations
- **Union**: Combines two sets
  ```csharp
  HashSet<int> set1 = new HashSet<int> {1, 2, 3};
  HashSet<int> set2 = new HashSet<int> {3, 4, 5};
  set1.UnionWith(set2); // set1 now contains {1, 2, 3, 4, 5}
  ```
- **Intersection**: Gets common elements
  ```csharp
  set1.IntersectWith(set2); // set1 now contains {3}
  ```
- **Difference**: Elements in one set but not the other
  ```csharp
  set1.ExceptWith(set2); // set1 now contains {1, 2}
  ```

### 3. SortedSet<T>
`SortedSet<T>` maintains elements in a sorted order, based on a comparer.

#### Creating a SortedSet
```csharp
SortedSet<int> sortedNumbers = new SortedSet<int>();
```

#### Adding Elements
```csharp
sortedNumbers.Add(3);
sortedNumbers.Add(1);
sortedNumbers.Add(2);
```

#### Iterating Elements (Sorted)
```csharp
foreach (int number in sortedNumbers)
{
    Console.WriteLine(number); // 1, 2, 3
}
```

### 4. ImmutableHashSet<T>
`ImmutableHashSet<T>` is part of the `System.Collections.Immutable` namespace and provides a set that cannot be modified after creation.

#### Creating an ImmutableHashSet
```csharp
ImmutableHashSet<int> immutableSet = ImmutableHashSet.Create<int>(1, 2, 3);
```

#### Adding/Removing Elements (Creates New Set)
```csharp
var newSet = immutableSet.Add(4);
```

### 5. Practical Examples

#### Example: Union of Two Sets
```csharp
HashSet<int> setA = new HashSet<int> {1, 2, 3};
HashSet<int> setB = new HashSet<int> {3, 4, 5};

setA.UnionWith(setB); // setA now contains {1, 2, 3, 4, 5}
```

#### Example: Intersection of Two Sets
```csharp
HashSet<int> setC = new HashSet<int> {1, 2, 3};
HashSet<int> setD = new HashSet<int> {2, 3, 4};

setC.IntersectWith(setD); // setC now contains {2, 3}
```

### 6. Performance Considerations
- `HashSet<T>`: Fast operations (O(1) for add, remove, and check).
- `SortedSet<T>`: Slightly slower operations due to sorting (O(log n)).
- `ImmutableHashSet<T>`: Useful for thread-safe and functional programming scenarios, but generally slower for modifications as it creates new instances.

### Conclusion
Sets are a powerful collection type in C#. They are useful when you need to ensure unique elements and perform set operations efficiently. Understanding when to use `HashSet<T>`, `SortedSet<T>`, and `ImmutableHashSet<T>` can help you write more effective and efficient code.

#### Exercises
1. Create a `HashSet<int>` and perform union, intersection, and difference operations with another `HashSet<int>`.
2. Create a `SortedSet<string>` and observe the order of elements after insertion.
3. Implement a scenario where `ImmutableHashSet<T>` would be beneficial over `HashSet<T>`.

---

This module should provide a comprehensive understanding of sets in C# and how to utilize them effectively.

### Problem: The Ultimate Treasure Hunt

#### Description
Welcome to the Ultimate Treasure Hunt! You are a treasure hunter exploring a vast island filled with treasures of different types. Your goal is to collect as many unique treasures as possible.

There are several treasure chests scattered across the island, each containing a list of treasures. Treasures are represented as strings. To make things interesting, some chests might contain duplicate treasures, and different chests might contain the same treasures. Your task is to determine the total number of unique treasures you can collect from all the chests.

#### Input
- An integer `n` representing the number of treasure chests (1 ≤ n ≤ 100).
- `n` lines follow, each representing a chest and containing a space-separated list of treasures. Each list will have at most 50 treasures, and each treasure name is a string of up to 20 characters.

#### Output
- A single integer representing the total number of unique treasures collected from all chests.

#### Constraints
- The number of treasures in each chest will be between 1 and 50.
- Treasure names are case-sensitive (e.g., "gold" and "Gold" are considered different treasures).
- The total number of unique treasures across all chests will not exceed 1000.

#### Examples

##### Example 1
**Input:**
```
3
gold silver diamond
silver gold emerald
ruby diamond pearl
```

**Output:**
```
6
```
**Explanation:**
The unique treasures are "gold", "silver", "diamond", "emerald", "ruby", and "pearl".

##### Example 2
**Input:**
```
2
ruby sapphire emerald
emerald diamond
```

**Output:**
```
4
```
**Explanation:**
The unique treasures are "ruby", "sapphire", "emerald", and "diamond".

##### Example 3
**Input:**
```
4
gold gold gold
silver silver
diamond
emerald emerald emerald emerald
```

**Output:**
```
4
```
**Explanation:**
The unique treasures are "gold", "silver", "diamond", and "emerald".

### Implementation

Here is a possible implementation in C# to solve the problem:

```csharp
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        int n = int.Parse(Console.ReadLine());
        HashSet<string> uniqueTreasures = new HashSet<string>();
        
        for (int i = 0; i < n; i++)
        {
            string[] treasures = Console.ReadLine().Split(' ');
            foreach (string treasure in treasures)
            {
                uniqueTreasures.Add(treasure);
            }
        }
        
        Console.WriteLine(uniqueTreasures.Count);
    }
}
```

#### Explanation
- **Input Handling**: Read the number of chests and then read each line of treasures.
- **Set Usage**: Use a `HashSet<string>` to store unique treasures.
- **Counting Unique Treasures**: Iterate over each treasure list and add treasures to the set. The set automatically handles duplicates.
- **Output**: The size of the set represents the number of unique treasures.

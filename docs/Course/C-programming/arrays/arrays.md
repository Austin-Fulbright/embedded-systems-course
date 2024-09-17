# Arrays in C and Differences Between C Versions

### Memory as a Storage Unit

In C, arrays are simply a series of memory blocks that are allocated for a program to fill with different types of data. Imagine the stack or the heap as a storage unit, where invisible lines divide the storage unit into equal parts for data storage.

Before you place your data into this "storage unit," it consists of various remnants—like oxygen, nitrogen, hydrogen, water vapor, maybe some dust, and likely leftover junk from the storage unit’s previous user.

### Partitioning the Storage Unit

You can draw invisible lines that separate the room and allow you to place whatever you want in those spaces. However, before you put anything into those spaces, you'll want to clear out the junk that's already there. In C, this cleanup step is usually handled when you place elements into your array, but let’s pretend you only put one item into the first partition and leave the rest.

When you define an array, you create space in memory to perfectly fit your objects. For simplicity’s sake, let’s say you draw five equally spaced imaginary partitions that perfectly fit the objects you want to store—in this case, let’s imagine blocks of iron.

```
// Defining an array in C
int ironBlocks[5]; // Creates an array with 5 partitions
```

### What Happens if You Don't Clear Out the Data in Your Array?

Let’s say you only put one iron block in one of the partitions. Technically, you have space for five blocks of iron, but you’ve only used one space. The remaining four partitions still contain leftover junk from the previous "user" of this storage unit. So, when you print out your array, you may see random garbage values in those uninitialized spaces.

Here’s what that might look like in C:

```
#include <stdio.h>

int main() {
    int ironBlocks[5];  // Uninitialized array
    ironBlocks[0] = 1;  // Only first space is initialized
    
    for (int i = 0; i < 5; i++) {
        printf("%d\n", ironBlocks[i]);  // Uninitialized elements may print garbage values
    }
    return 0;
}

```
**Output (Example):**


```
1
6422296  // Random value
6422228  // Random value
0        // Random value
-12177636 // Random value

```

This is because the array only clears the first block (where you placed your iron block), while the remaining spaces contain "junk data" that was left behind by the system or other programs.

![[Pasted image 20240917073020.png]]
### Buffer Overflows

![[Screenshot 2024-09-17 at 7.35.05 AM.png]]

Now, let’s discuss buffer overflows. Imagine you’ve partitioned space in your storage unit for five blocks of iron. After filling all five spaces, you decide to add a sixth block. This new block sticks out of the predefined space.

Why is this a problem?

- **Data Exposure**: The iron block now sticks out of the storage unit, allowing other users (programs) to see or access it. If the data you’re storing is sensitive, this could expose it to potential theft or misuse.
- **Overwriting Memory**: The sixth block could overwrite important information stored elsewhere. For example, what if the sixth block crushes a partition meant for your foam blocks? You’ll end up with a block of iron where there should have been foam.


```
#include <stdio.h>

int main() {
    int ironBlocks[5];
    for (int i = 0; i <= 5; i++) {
        ironBlocks[i] = i + 1;  // Causes buffer overflow when i = 5
    }
    return 0;
}
```

**Buffer Overflow:** In this code, the loop accesses `ironBlocks[5]`, which is outside the allocated array size (0 to 4), causing a buffer overflow. This could lead to unintended behavior, memory corruption, or even security vulnerabilities.

### Code Example: Avoiding Junk Data with Initialization

One way to avoid junk data in your arrays is by initializing them:


```
#include <stdio.h>

int main() {
    int ironBlocks[5] = {0};  // All elements are initialized to 0
    
    for (int i = 0; i < 5; i++) {
        printf("%d\n", ironBlocks[i]);
    }
    
    return 0;
}

```

**Output:**

`0 0 0 0 0`

In this case, all the partitions are cleared, and the array is initialized with `0` in each space.

---

With these code examples and visual illustrations (storage units with imaginary partitions), you should now have a better understanding of how arrays work in C, how junk data remains if not initialized, and how buffer overflows can lead to serious problems.




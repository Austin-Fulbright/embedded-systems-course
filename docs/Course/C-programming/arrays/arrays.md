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

- **Data Exposure**: Lets say that the part of the storage unit that you write the 6th block to now sticks out of the storage unit and is now visible to anyone outside the storage unit. Well for one, this is embarrasing, now everyone in the world knows you collect iron blocks in your storage unit. and two, people might steal your iron block and imagine that iron block had senstive information about you inscribed on it. This would suck and all because you added more memory than you should have.
- **Overwriting Memory**: The sixth block could overwrite important information stored elsewhere. For example, what if the sixth block crushes a partition meant for your precious foam blocks that you have also been collecting? When you look at your foam block collection you will see some iron. WTF? you wrote iron blocks into your foam and you cant get that foam back.


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

### Arrays in Practice

So lets go back to just talking about code. You have already learned about primitive types of data and structs. So now lets say you want to create a list of Integers to store data representing all of your favorite numbers. The most effecient way to do this would be to have them stored in an array. I will initialize an array and then add my favorite numbers to them. 

```
adding numbers
```

There are numerous types of data structures and arrays are by far the most fundamental and the fastest for reading and in many cases writing as well. The reason for this is that Assembly, the code that C is built ontop of, was written with arrays as a fundamental part of the language. Further more the architecture of your computer is also set up in a way that is conducive with arrays. Now it doesnt have to be Integers you store inside arrays, you can store any type of data inside of an array. Including structures with other data types inside of it. You can even store other arrays inside of them.

### Multi-Dimensional Arrays

A multidimensional array is essentially just an array stored inside of another array. And that can be done multiple times. This is very helpful when you want to store grid like data or matrices. A lot of people will use C or C++ to do linear algebraic calculations because you can use multi-dimensional arrays as matrices. furthermore, the calculations can be optimized with the hardware using C, making it perfect for matrix operations that need to be run fast and often. But a more basic example for multi-dimensional arrays is a graph for a tic-tac-toe game. I want this to be an embedded systems driven course so I took this example from a tic-tac-toe game that was created for a microcontroller in an embedded system.

```
//	Lines combinations
const uint8_t test[8][3] =
{
	{0,1,2},
	{3,4,5},
	{6,7,8},
	{0,3,6},
	{1,4,7},
	{2,5,8},
	{0,4,8},
	{2,4,6}
};
```
This was taken from this [repository](https://github.com/VALINT/TicTacToe/blob/master/Software/1611_TicTacToe/1611_TicTacToe/Game.c)

This was used to draw the lines of a win in the tic-tac-toe board. in this particular example the actual board itself was represented in a 1 dimensional array but could also be represented in two dimensions. Regardless, the code visually has the appearance of two dimensional array.

```
// Game fielsd
uint8_t game_field[9] = {
	0, 0, 0,
	0, 0, 0,
	0, 0, 0
};
```

So this could be rewritten like this

```

// Game fielsd
uint8_t game_field[3][3] = {
	{0, 0, 0},
	{0, 0, 0},
	{0, 0, 0}
};

```


The reasons for why you would use a two dimensional array will be discussed later when we get more into embedded systems. If you look through the repository you will also see an array that represents the entire screen. Where each value in the array represents a pixel on the microcontrollers screen.

```
// Frame
const char Frame[] PROGMEM =
{
	255,255,255,127,127,63,31,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,7,31,63,127,127,255,255,255,
	255,255,255,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,255,255,255,
	255,255,255,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,255,255,255,
	255,255,255,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,255,255,255,
	255,255,255,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,255,255,255,
	255,255,255,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,255,255,255,
	255,255,255,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,255,255,255,
	255,255,255,254,254,252,248,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,224,248,252,254,254,255,255,255
};

```



I am assuming anyone who is doing this course is deeply interested in lower level programming and how exactly arrays work on a system level. So lets go DEEPER!



### Buffer Overflow Exploits






&sources

wikipedia/c
https://www.youtube.com/watch?v=1S0aBV-Waeo&ab_channel=Computerphile



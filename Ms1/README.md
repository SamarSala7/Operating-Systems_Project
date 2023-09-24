#dynamic_allocator.c

Function Declaration: 
void initialize_MemBlocksList(uint32 numOfBlocks)
Function Role: 
Currently, the “MemBlockNodes” array is already created with empty “MAX_MEM_BLOCK_CNT” block elements.
“AvailableMemBlocksList” is empty without any pointers or nodes.
This function shall:
ZEROing the size & pointers of “AvailableMemBlocksList”.
Then, fill the list by making it points to the first n=numOfBlocks empty elements exist in “MemBlockNodes” array.
At the end of this function, the “AvailableMemBlocksList” shall be initialized as a linked list of “numOfBlocks” elements from those that already exist in the “MemBlockNodes” array.

Function Declaration: 
struct MemBlock *find_block(struct MemBlock_List *blockList, uint32 va)
Function Role: 
It shall search for the given start virtual address (va) in the given list (blockList).
If a block found with sva equal to given va, return this block.
If not found, return NULL.


Function Declaration: 
void insert_sorted_allocList(struct MemBlock *blockToInsert)
Function Role: 
This function takes a block and insert it in the AllocMemBlocksList.
All blocks inserted in AllocMemBlocksList are placed in a sorted ascending order based on each block’s sva.
It has two cases:
Case 1: If the AllocMemBlocksList is empty  insert the given block at the head of the list.
Case 2: Otherwise  insert the given block in its correct location according to its sva (simply by iterate on the AllocMemBlocksList).

Function Declaration: 
struct MemBlock *alloc_block_FF(uint32 size)
Function Role: 
This function searches for a free memory block in the FreeMemBlocksList with a size greater than or equal input size using FIRST FIT STRATEGY to be allocated later on in the memory.
The possible CASES results from the search using FF strategy are:
Case 1: no suitable block is found  return NULL.
Case 2: a block is found with EXACT size  remove it from the FreeMemBlocksList and return it.
Case 3: a block is found with GREATER size  divide it into 2 blocks:
A new block with the required size, shall be RETURNED by the end of the function.
An updated block with the remaining space, shall be kept in the list

Function Declaration: 
struct MemBlock *alloc_block_BF(uint32 size)
Function Role: 
This function searches for a free memory block in the FreeMemBlocksList with a size greater than or equal input size using BEST FIT STRATEGY to be allocated later on in the memory.
The possible CASES results from the search using BF strategy are the same that can be occurred by applying FF.


Function Declaration: 
void insert_sorted_with_merge_freeList(struct MemBlock *blockToInsert)
Function Role: 
It takes a block and insert it in the FreeMemBlocksList.
All blocks inserted in FreeMemBlocksList are placed in a sorted ascending order based on each block’s sva.
However, if the inserted block is DIRECTLY adjacent to another free block (either before or after it)  they shall be merged as ONE block.
It has the following cases:
Case 1: If the FreeMemBlocksList is empty  insert the given block at the head of the list.
Otherwise  insert the given block in its correct location according to its sva (simply by iterate on the FreeMemBlocksList). Here, one of the following four cases can be happened:
Case 2: No merge
Case 3: Merge with previous
Case 4: Merge with next
Case 5: Merge with previous and next

#command_prompt.c

Add an "Autocomplete" feature to your command prompt, which allow the user to list all commands that start with a given set of characters.
The user should write set of characters then press enter:
If the set of characters are complete and represent an existing command, then execute it (Already implemented). 
Else, if there’s one (or more) command that start with the given characters, print their names (ONE PER LINE)
Else, print the “unknown command” message that is already exist in the given code.




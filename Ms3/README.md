Page Fault Handler:
Function Declaration: void page_fault_handler(struct Env * curenv, uint32 fault_va)

Fault: is an exception thrown by the processor (MMU) to indicate that:
A page table is not exist in the main memory (i.e. new table). (see the following figure) OR
A page can’t be accessed due to either it’s not present in the main memory.

If the size of the page working set < its max size, then do (refer to Appendix I and Appendix II)
Scenario 1: Placement
1- Allocate space for the faulted page
2- Read the faulted page from page file to memory
3- If the page does not exist on page file, then
  1- If it is a stack or a heap page, then, it’s OK.
  2- Else, a panic with an error message shall be output to show ILLEGAL MEMORY ACCESS for the given fault virtual address.
4- Reflect the changes in the page working set

Scenario 2: Replacement
1- Implement the clock algorithm to find victim virtual address from page working set to replace.
2- If the victim page is not modified, then:
  Just remove it
3- Else
  Update its page in page file
  Then, remove it
4- Reflect the changes in the page working set
5- Apply Placement steps tp place the faulted page


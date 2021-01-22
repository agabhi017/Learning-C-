### Input-Output Buffers [Last Updated: 22 Jan 2021]

#### What is a buffer?

In simple terms a buffer is a waiting area or a temporary storage which is accessed by multiple operations when a program is executed. 
A write operation to a computer's hard disk is slower than writing to RAM (Random Access Memory). So if a program has lots of read/write 
operations it will be much slower if it writes to the disk every time as compared to making changes in the RAM a number of times and finally 
writing to the disk when the program ends (or the buffer is full). 

#### What is buffer flushing?

Flushing a buffer simply means that the contents of the buffer are now being pushed from the temporary storage to a more permanent storage (in case
of output to a file) or are being dispayed to the user (in case of a terminal). When a buffer is flushed, it becomes empty and is filled with 
other incoming streams if any.


Consider a simple program that takes 100 numbers as an input from a user in a sequential manner and does operation on them. For simplicity, 
we have a varaible 'x' in the program which is initialized to 0. The program takes input from the user and adds that value to the varaible 'x'.
Now consider another operation in the program which will output the value of the variable 'x' after each operation. When a user inputs a number, 
he should see the output of the previous operartion first before inputting the next number.


#### What happens if the output buffer is not flushed each time when an input is read? 

In this case it is possible that the message which was intented to be printed on the screen before taking the next input might be printed out of 
the expected order, that is, until the buffer is full, the output might not be visible and once it is printed, it may appear out of order.


#### How does C++'s standard library works in the deafault case?

By default the cin and cout objects are tied. This means that calling cin will flush the cout buffer first which will cause the contents to be printed 
on the screen. Furthermore, the endl operator flushes the output stream as well to make the output visible when required. 
This default setting 

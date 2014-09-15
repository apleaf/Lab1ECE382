Lab1ECE382
==========

Lab 1 Calculator Assembly Program for MSP430

Purpose:
The purpose of this lab was to create a calculator in assembly code that handled addition, subtraction, multiplication, store 0x00 when clear was encountered, store the output of the function in memory and end when 0x55 was encountered for an operation. For B functionality, the calculator was to store 0xFF in memory when the answer for the operation was larger than 0xFF. For A functionality the calculator was to be able to handle multiplication.

Flow Chart and Pseudocode
![alt text](http://i62.tinypic.com/oksvoy.jpg)

![alt text](http://i58.tinypic.com/izbvrc.jpg)

Coding:
The assembly program took in the first memory location of the operation we were to use.  The program then performed
a compare to see what function was to be performed (addition, subtraction, or multiplication), and then jump to the 
correct location in the program to perform the function.  The addition code simply added two values together.  Subrtaction
did the same.  The multiplication function used the second value as the counter for a loop, and then added the initial value, 
decremtning the loop each time, until the loop finished.  For example, if the value 0x04 was being multiplied by 0x06, the
program added 0x04 to 0x04 and decremented 0x06 to 0x05.  The next iteration added 0x04 to 0x08, and then decremented 0x05 to 0x04. The program broke out of the loop when the counter ran down to 0x01.  After this, the program took in the next operation and performed the check again to see what function would be performed.

Debugging:
My addition and subraction code worked well, but I ran into problems with the multiplication code.  After soem debugging and testing, I realized I was using an incorrect register for my loop counter.  After I changed it to the correct register value, my multiplication function worked.

Testing Methodology/results:
To test my code, I used the given test case strings with their known results to test my code

For the required functionality, which tested addition, subtraction, and clear (which stored 0x00), I used the given test case 0x11, 0x11, 0x11, 0x11, 0x11, 0x44, 0x22, 0x22, 0x22, 0x11, 0xCC, 0x55 into my calculator. The stored result was 0x22, 0x33, 0x00, 0x00, 0xCC beginning in memory location 0x0200 which was correct for the given solution

The following two test cases, which tested the A and B functionality (B functionality tested the calculators ability to store 0xFF when an answer was larger than 0xFF, and A functionality tested the calculators ability to multiply) were then used

B Functionality: Given 0x11, 0x11, 0x11, 0x11, 0x11, 0x11, 0x11, 0x11, 0xDD, 0x44, 0x08, 0x22, 0x09, 0x44, 0xFF, 0x22, 0xFD, 0x55
Result: 0x22, 0x33, 0x44, 0xFF, 0x00, 0x00, 0x00, 0x02

A Functionality: 0x22, 0x11, 0x22, 0x22, 0x33, 0x33, 0x08, 0x44, 0x08, 0x22, 0x09, 0x44, 0xff, 0x11, 0xff, 0x44, 0xcc, 0x33, 0x02, 0x33, 0x00, 0x44, 0x33, 0x33, 0x08, 0x55
Result: 0x44, 0x11, 0x88, 0x00, 0x00, 0x00, 0xff, 0x00, 0xff, 0x00, 0x00, 0xff

My program successfully handled the required operations for the required, B, and A functionality.

Observations/Conclusions: In conclusion of the lab, I was successful in creating an assembly program that handled addition, subtraction, ending the operation, storing 0x00 when clear was the operation, and storing 0xFF when an answer greater than 0xFF happened.

Documentation: I looked at Dr. Coulston's example code for an idea how to store the complete operation string and then increment to the next stored byte in the operation string. 





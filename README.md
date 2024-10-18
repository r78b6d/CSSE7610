java c
Assignment 2
CSSE7610
Due date and time: Thursday 17 October, 4pm
1. The following reader-writer algorithm works for multiple readers and a single writer. It allows reading of the shared variables x1 and x2 into local variables d1 and d2 without locking, thus not blocking the writer.
Before writing to the shared variables x1 and x2, the writer increments a counter c. It then proceeds to write to the variables, and finally increments c again. The two increments of c ensure that it is odd when the process is writing to the variables, and even otherwise. Hence, when a reader wishes to read the shared variables, it waits in a loop until c is even before reading them. Also, before returning it checks that the value of c has not changed (i.e., another write has not begun). If it has changed, the process starts over. This ensures the pair of values read corresponds to a single occurrence of a write.
Non-blocking reader-writerinteger c, x1, x2 ← 0readerwriterinteger c0, d1, d2integer d1, d2loop foreverloop foreverp1:               repeatq1:               d1 ← get()p2:                      repeatq2:               d2 ← get()p3:                              c0 ← cq3:               c ← c+1p4:                      until (c0 mod 2 = 0)q4:               x1 ← d1p5:                      d1 ← x1q5:               x2 ← d2p6:                      d2 ← x2q6:               c ← c+1p7:               until (c0 = c)q7:p8:               use(d1,d2)q8:

(a) Describe a scenario showing that the algorithm is not correct when there is more than one writer. Explain how you could modify the algorithm to allow multiple writers by placing standard, i.e., non-language specific, synchronisation mechanisms in the code. Justify that your modification ensures that no writer process is ever blocked unnecessarily.
(b) Extend the algorithm with a third type of process called an incre-menter. An incrementer increments the values of x1 and x2, i.e., adds 1 to them. It is a low priority process and so should not block writers while reading x1 and x2, and synchronisation mechanisms should give preference to writers over incrementers.
Deliverable: A file named Q1_{student number}_{first name}_{last name}.pdf containing your name, student number, and your answers to (a) and (b). For example, if your student number is 12345678 and your name is Mark Zhang, then the file should be “Q1_12345678_Mark_Zhang.pdf”.
2. Write a Promela specification for your modified algorithm from Ques-tion 1(b), and use Spin to prove that it is correct. Correctness requires that
(a) any pair of values used by a reader or incremented by an incrementer are either the initial values, or were written by a single occurrence of a write, and
(b) the values incremented by an incrementer are the current values of x1 and x2.
You may use auxiliary variables to express the correctness property if required.
Note: if you get very long counter-examples from Spin, click on Advanced Parameter Settings (while in the Verification tab) and set the Maximum Search Depth to a smaller number. If it is too small no counter-example will be found, but you will be able to find a counter-example of around 20 or 30 steps in many cases.
Alternatively, just look at the last few steps (and states) of the counter-example as these usually indicate the problem. Us代 写CSSE7610 Assignment 2Java
代做程序编程语言e Step Backward and Step Forward to move through these steps.
Deliverable: A file named Q2_{student number}_{first name}_{last name}.pml containing the Promela specification, a comment describing the property you proved, and your name and student number (as a com-ment). For example, if your student number is 12345678 and your name is Mark Zhang, then the file should be “Q2_12345678_Mark_Zhang.pml”.
3. Implement your algorithm from Question 1(b) in Java. You should have 5 reader threads, 5 writer threads and 5 incrementer threads. Each writer and incrementer waits for a random time (between 0 and 10 milliseconds) then updates the shared variables (just once) and terminates. The writers can update the variables with random values. The readers wait a random time (between 0 and 10 milliseconds) before each read. When all readers have read the final update, the entire program should terminate gracefully, i.e., all threads should reach the end of their run methods. Your program should produce output by calling the appropriate methods of the provided class A2Event.java. For testing purposes, it is a requirement that you call the A2Event class every time one of the events occurs. In particular, the writers and incrementers must call the A2Event class before another writer or incrementer begins to update the results. It is also important that you do not modify the provided class.
Deliverables: A zip file named Q3_{student number}_{first name}_{last name}.zip containing a file ReadWrite.java with your main method for the program, along with all supporting source (.java) files (apart from A2Event), and a file readme.txt describing (in a few paragraphs) the ap-proach you have taken to coding your program and providing a list of all your classes and their roles. All files should be well-documented and in particular the code for synchronisation should be well explained. All files should also contain your name and student number (as a comment). For example, if your student number is 12345678 and your name is Mark Zhang, then the file should be “Q3_12345678_Mark_Zhang.zip”.
To assist with our testing of your Java code. Please do not make your sub-mitted files dependent on being in a particular package. That is, remove any lines:
package packageName;
Marking criteria
Marks will be given for the correctness and readability of answers to questions 1 to 3 as follows. As part of the marking process, you may be required to meet with the teaching team after your assignment submission. In this meeting, you will discuss the work you have submitted, explain your solution, and answer questions regarding your submission.
Students failing to explain their submission or attend this meeting will receive a grade of ZERO for this assignment.
Question 1 (10 marks)
• Counter-example for original algorithm (2 marks)
• Justification of synchronisation constructs (2 marks)
• Modification of algorithm (6 marks)
Question 2 (5 marks)
• Promela specification of algorithm (3 marks)
• Properties for correctness (2 marks)
Question 3 (10 marks)
• Java classes implementing your design (4 marks)
• Appropriate use of synchronisation mechanisms (3 marks)
• Program producing correct behaviour (2 marks)
• readme file (1 mark)







         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com

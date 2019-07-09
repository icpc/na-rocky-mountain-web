---
layout: page
---

# FAQ

### How may people can be on a team?
Three

### What programming languages will be used for the contest?
C, C++, Java, Python 2, Python 3 and Kotlin.

### What judging system will be used?
Kattis. Your can create a free account and try out Kattis at [open.kattis.com](https://open.kattis.com/). Note that the actual contest will use different login credentials which will be provided at your contest site.

### What can we bring?

Books, printouts, scratch paper. Basically, nothing electronic, or electronically readable media. This means possesion of cell phones, calculators, tablets, flash drives etc. is not allowed during the contest.

Note you are allowed online access to the following reference sites: [docs.python.org](https://docs.python.org), [cppreference.com](https://en.cppreference.com/w/), and [docs.oracle.com/javase/8/docs/api](https://docs.oracle.com/javase/8/docs/api/).

### What do you provide?

Site specific, but your team will have a single workstation, scratch papers, printers, and have access to a classroom (or part of one) or similar place to work in relative privacy.

### What problems should we do first?

Since the time penalty for each correct problem is from the start of the contest, you should get the easiest problems done first. Note that determining which problems are easy is part of the contest! Seeing how other teams are progressing on the problems can help your team determine this.

### What do we submit?

A single source file which (if correct) solves the problem; with the following conventions:

### C++ Example
C++	extension is .cpp	

    // count.cpp
    #include <iostream>
    #include <string>

    using namespace std;

    int main(int argc, char *argv[])
    {
        string line;
        int lines=0;
        while (getline(cin,line)) {
            ++lines;
        }
        cout << lines << endl;
        return 0;
    }

#### Build, Run and Test

    $ g++ -g -O2 -std=gnu++11 -static -o count count.cpp -lm
    $ cat count.in | ./count | diff - count.out

### C Example
C extension is .c
    
    //count.c
    #include <stdio.h>
    #include <string>

    #define MAX_LINE_LENGTH 100000
    char linebuffer[MAX_LINE_LENGTH+1];

    int main()
    {
        int lines=0;
        while (fgets(linebuffer,MAX_LINE_LENGTH+1,stdin)!=0) {
            ++lines;
        }
        printf("%d\n",lines);
        return 0;
    }

#### Build, Run and Test
    $ gcc -g -O2 -std=gnu99 -static -o count count.c -lm
    $ cat count.in | ./count | diff - count.out

### Java Example
Java extension is .java and public class of base name with no (default) package.

    // count.java:
    public class count {
        public static void main(String[] args)
            throws Exception {
            String line;
            int lines=0;
            java.util.Scanner in=
                new java.util.Scanner(System.in);
            while (in.hasNextLine()) {
                line=in.nextLine();
                ++lines;
            }
            System.out.println(lines);
        }
    }

#### Build, Run and Test
    $ javac -encoding UTF-8 -sourcepath . -d . count.java
    $ cat count.in | java -Xss64m | count | diff - count.out

### Python 2 Example
Python 2 extension is .py

    #!/usr/bin/env python2

    #count.py
    import sys
    print sum(1 for line in sys.stdin)

#### Run and Test
    $ cat count.in | python2 count.py | diff - count.out

### Python 3 Example
Python 3 extension is .py and shebang (#!) of /usr/bin/env python3.	count.py:

    #!/usr/bin/python3

    #count.py
    import sys
    print(sum(1 for line in sys.stdin))

#### Run and Test
    $ cat count.in | python3 count.py | diff - count.out

The judging system actually lets you turn in any source file for any problem, but sticking to this convention keeps you from turning a solution to the wrong problem.

### How do we edit/compile/run our code?

Again site specific. Assuming you are using a unix-like operating system the least-common-denominator editor is probably pico, which you can run by typing

    $ pico source-file-name

at the command prompt, although your site probably supports an IDE like elipse or netbeans; or both. Look at the previous question to see build and run examples.

### How do we test our code?

Here's a test checklist: 

- Does it work correctly agains the sample data? Use diff (unix)

        diff myoutputfile.out exampleoutputfile.out
        or windiff (windows) to make a detailed comparison. 
    
- Case and spacing matters!
Note that some problems are nondeterministic, in that they allow for more than one correct answer for a given input. diff is inadequate for determining the correctness of such programs. The judges, of course, will not use diff to determine the correctness of such problems.

- Does it work correctly against additional test cases? The data set used to judge your problem will almost certainly be more complex than the data provided as an example. The judge data will conform to the specifications of the problem, however. Create other data sets to test the correctness of your solution before submitting a problem.

- Does it generate any additional output? Turn off any debugging statements before submitting the problem.
Does it read and write the data correctly? The input is from the console, and the output is to the console. Use the console i/o to read and write your data. (in C use scanf/printf, in C++ use cin/cout, and Java use System.in/System.out).

### How do we debug our code?

More site specific. gdb is the command line debugger for C and C++ programs, and you might have ddd, which is a gui-interface for this. Read the banners and h is for help. The installed IDE's should support debugging; and otherwise think about print statements with an if (debug) mask.

In the judge setting, your program will be run with no arguments and the output of STDERR is ignored. You can use these mechanisms to report debugging information without changing how it behaves during judgement (although creating lots of debugging output that is ignored can hurt how long it takes your program to run).

### How do we submit a problem/clarification?

We will be using Kattis for our judge environment this year. You should have gotten an email about creating a kattis account from your team registration, and you can try the warmup at https://warmup.kattis.com before the contest at https://rmc16.kattis.com.

### How are teams ranked?

Teams are first ranked by number of correct solutions: the more problems which are solved by a team, the higher their rank.

Teams that have finished the same number of problems are then ranked by fewest penalty points: the fewer points, the higher the rank. The penalty points accrued for your team is the sum of:

- 20 points for each incorrect submission before an accepted solution.
- The number of minutes from the start of the contest to the submission time of the correct solution to a problem.

Example: The contest starts at 10:00 am; Team Zorbo, turns in problem 1 correctly at 10:43, makes two incorrect submissions of problem 2 before submitting a correct solution at 12:35, and makes 3 incorrect submissions for problem 3 without ever turning in a correct solution. The Zorbos would have 225 penalty points broken down in the following table: 


| Problem | Submission Penalty  | Time Penalty | Total |
| ---- | ---- | ---- | ---- |
| 1 |  0*20 = 0 | 0:43 = 43 | 43 |
| 2	| 2*20 = 40 | 2:25 = 145 |	185 |
| total	| 2*20 = 40 |	3:08 = 188	| 225 |


Note that there is no penalty accrued for problem 3, since it was never submitted correctly

Incidentally, the last tie-breaker rule is the time of the last correct submission.

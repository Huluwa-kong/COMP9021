# COMP9021
COMP9021 UNSW

COMP9021 Assignment2 Term 2, 2021
COMP9021 Assignment2 Term 2, 2021
COMP9021 Assignment2 Term 2, 2021

如果您需要任何关于本门课程的帮助，请联系 vx **codingtutor**
因为专业，所以信赖 ^_^

1.1. Aims. The purpose of the assignment is to:
• design and implement an interface based on the desired behaviour of an application program;
• practice the use of Python syntax;
• develop problem solving skills.
1.2. Submission. Your program will be stored in a file named sudoku.py. After you have developed and
tested your program, upload it using Ed (unless you worked directly in Ed). Assignments can be submitted
more than once; the last version is marked. Your assignment is due by August 9, 10:00am.
1.3. Assessment. The assignment is worth 13 marks. It is going to be tested against a number of input files.
For each test, the automarking script will let your program run for 30 seconds.
Late assignments will be penalised: the mark for a late submission will be the minimum of the awarded mark
and 13 minus the number of full and partial days that have elapsed from the due date.
The outputs of your programs should be exactly as indicated.
1.4. Reminder on plagiarism policy. You are permitted, indeed encouraged, to discuss ways to solve the
assignment with other people. Such discussions must be in terms of algorithms, not code. But you must
implement the solution on your own. Submissions are routinely scanned for similarities that occur when students
copy and modify other people’s work, or work very closely together on a single implementation. Severe penalties
apply

A sudoku grid consists of 9 lines and 9 columns, making up 81 cells, that are grouped in nine 3x3 boxes. In a
sudoku puzzle, some but not all of the cells already contain digits between 1 and 9. Here is an example of a
sudoku puzzle.

Solving a sudoku puzzle means completing the grid so that each digit from 1 to 9 occurs once and only once in
every row, once and only one in every column, and once and only once in every box. For instance, the previous
puzzle has the following solution

Solving a sudoku puzzle is a very common assignment; it is not difficult and moderately interesting as a
“solution” (the completed grid) tells nothing about how the solution was reached. More interesting solvers are
logical in the sense that they (possibly partially only) solve the puzzle in steps and at every step, explain how
they made some progress; they do so by using some of the well known techniques that most people who solve
sudoku puzzles apply. Two remarks are in order.
• Methods that only discover digits in empty cells are fairly limited; most methods need to keep track of
the list of possible digits that can go into a given cell, and making progress might mean reducing that
list. To apply techniques of the second kind, it is necessary to first mark the grid.
• Often, it is not possible to completely solve a puzzle using exclusively the chosen methods; at some
point no progress can be made and then a random guess has to be made to either put a digit into a
given empty cell, or to remove a digit from the list of possible digits that can go into a given cell. It
might subsequently be necessary to backtrack and make alternative guesses if the earlier guesses turn
out to be inconsistent with a solution.
For this assignment, you will have to implement two such techniques, based on the notions of forced digits
and preemptive sets described in the paper A Pencil-and-Paper Algorithm for Solving Sudoku Puzzles by J. F.
Crook, Notices of the AMS, 56(4), pp. 460–468. Before anything else, you should study this paper. The forced
digits technique is applied first, followed by the preemptive set technique. When no progress can be made, the
forced digits techniques could be applied again, but that might not yield anything; an alternative would be to
try and fill some empty cell with one of the possible digits for that cell and apply the preemptive set technique
applied again, knowing that that guess might prove wrong and that other possible digits might have to be used
instead. In this assignment, we will stop at the point where the preemptive set technique can no longer be
applied; hence we can expect that our implementation will only partially solve most puzzles. But the technique
is very powerful and as explained in the article, subsumes many of the well known techniques.
You will design and implement a program that will read a sudoku grid whose representation is stored in a file
filename.txt and create a Sudoku object, with a number of methods:

a method preassess() that prints out to standard output whether the representation is correct and
has no digit that occurs twice on the same row, on the same column or in the same box;
• a method bare_tex_output() that outputs some Latex code to a file, filename_bare.tex, that can
be compiled by pdflatex to produce a pictorial representation of the grid;
• a method forced_tex_output() that outputs some Latex code to a file, filename_forced.tex, that
can be compiled by pdflatex to produce a pictorial representation of the grid to which the forced digits
technique has been applied;
• a method marked_tex_output() that outputs some Latex code to a file, filename_marked.tex, that
can be compiled by pdflatex to produce a pictorial representation of the grid to which the forced digits
technique has been applied and that has been marked;
• a method worked_tex_output() that outputs some Latex code to a file, filename_worked.tex, that
can be compiled by pdflatex to produce a pictorial representation of the grid to which the forced digits
technique has been applied, that has been marked, and to which the preemptive set technique has been
applied.

The input is expected to consist of 9 lines of digits, with possibly lines consisting of spaces only that will be
ignored and with possibly spaces anywhere on the lines with digits. If the input is incorrect, that is, does not
satisfy the conditions just spelled out, then the program should generate a SudokuError with Incorrect input
as message.
Here is a possible interaction:

The preassess() method prints out There is clearly no solution. in case some row, column or box
contains twice the same digit, and There might be a solution. otherwise, that is, in case no row, column
or box contains twice the same digit.
For the .tex files output by the program, pay attention to the expected format, including spaces and blank
lines. Lines that start with % are comments; there are 9 such lines. The output of your program redirected
to a file will be compared with the expected output saved in a file (of a different name of course) using the
diff command. For your program to pass the associated test, diff should silently exit, which requires that
the contents of both files be absolutely identical, character for character, including spaces and blank lines.
The forced_tex_output() method produces a file designed to depicts the grid where all forced digits have
been added. A forced digit is a digit that must fill an empty cell in a box because that box does not contain
that digit yet and all other empty cells in that box are on a row or on a column that contains that digit. As
forced digits are being discovered and fill empty cells, more forced digits might be discovered that could not
be discovered in the first round. So the program must make sure that no forced digit can be added to the grid
that will be produced when executing that method. The provided examples illustrate.
The marked_tex_output() method produces a file designed to depicts the grid where all forced digits have
been added and all possible digits have been added to the corners of the empty cells. The possible digits for an
empty cell are the the digits that do not occur on the same row, on the same column or in the same box. The
provided examples illustrate.
The worked_tex_output() method produces a file designed to depicts the grid where all forced digits have been
added, all possible digits have been added to the corners of the empty cells, and the preemptive set technique
has been applied until it cannot allow one to eliminate any possible digit from any cell (which might be because
the puzzle has been solved). The provided examples illustrate.
The 13 marks will be distributed as follows:
• 1 mark for preassess();
• 3 marks for bare_tex_output();
• 3 marks for forced_tex_output();
• 3 marks for marked_tex_output();
• 3 marks for worked_tex_output()
————————————————
版权声明：本文为CSDN博主「Brye」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/codetutor/article/details/119428485

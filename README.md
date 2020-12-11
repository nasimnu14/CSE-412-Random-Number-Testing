# CSE-412-Random-Number-Testing
Assignment 3: Testing Random Number
Generators
1 Introduction
In this assignment, you will create a linear congruential generator and perform
four empirical tests on the generated random numbers:
• Uniformity test
• Series test
• Runs test
• Correlation test
2 Generation of Random Numbers
The equation to generate random numbers is as follows:
Zi = (65539 ∗ Zi−1) mod 231
and
Ui = Zi
231
Where Z0 (or the seed) would be your 7 digit student id. For each test you
have to generate n random numbers first and then perform the tests. n should
be kept as a parameter in your code and we would check your code with different
values of n. Note that you will have to generate n values first in each execution
of each test.
3 Uniformity Test
In this test, you will check whether the Ui’s generated appear to be uniformly
distributed or not. You will perform chi-square test with all parameters known.
First divide [0,1] into k sub-intervals. Then if fj is the number of Ui’s that are
in the jth sub-interval, χ2 can be calculated as:
χ2 = k
n
kXj
=1
fj − nk2
1
For large n, χ2 will have an approximate chi-square distribution with k − 1
degrees of freedom under the null hypothesis:
H0 = Ui’s are IID random variables.
We reject this hypothesis at level α if χ2 > χ2k−1;1−α where χ2k−1;1−α is
the upper 1 − α critical point of the chi-square distribution with k − 1 degrees
of freedom. k and α should be kept as a parameter in your code. Test the null
hypothesis and report if it is rejected or not.
(* To calculate χ2df;q in your code, in python you can use the library function
scipy.stats.chi2.ppf(q,df ) where q is the level and df is the degrees of freedom.
We will share a stub code for your convenience. Other language users can use
any built in function to calculate this value or keep a file containing a table for
these values generated from the code.)
4 Serial Test
In this test you will calculate d-tuples where U1 = (U1; U2; :::; Ud) , U2 =
(Ud+1; Ud+2; :::; U2d) and so on. You will check whether d-tuples are uniformly
distributed on the d-dimensional unit hypercube [0; 1]d. Divide [0,1] into k
sub-intervals and generate U1; U2; :::; Ul where l = bnd c. Let fj1j2:::jd be
the number of Ui’s having first component at j1, second component at j2 etc.
Calculate
χ2(d) = kd
n
kX
j1=1
kX
j2=1
:::
kX
jd=1
fj1j2:::jd − knd2
Then χ2(d) will have an approximate chi-square distribution with kd − 1 df.
Test the null hypothesis as in the uniformity test and report it is rejected or
not. Keep k, α and d as parameters in your code.
5 Runs Test
In this test you will evaluate the independence assumption of the random number generator. You will examine the sequence of Ui’s generated and check for
unbroken sequences of maximal length within which Ui’s increase monotonically
(or a run up). From a sequence of n Ui’s count the number of runs up of length
1, 2, 3, 4, 5 and ≥ 6 and then define:
ri =  nono : of runs of length : of runs of length i For 1 ≥ 6 For < i < i = 6 6 (1)
Then calculate the test statistic:
R = 1
n
6Xi
=1
6Xj
=1
aij(ri − nbi)(rj − nbj)
2
The values of aij’s and bi’s are shown in the Figure above.
For large n, R will have an approximate chi-square distribution with 6 df.
Calculate if R ≥ χ26;1−α and if so reject the null hypothesis as in previous test.
Keep α as parameter in your code.
6 Correlation Test
In this test you will directly assess whether the generated Ui’s exhibit discernible
correlation at lag j. Generate a sequence of n Ui’s U1; U2; :::; Un and then
estimate ^ ρj as:
ρ^j = 12
h + 1
hX k
=0
U1+kjU1+(k+1)j − 3
where h = bn−j 1 − 1c. Then calculate V ar( ^ ρj) as:
V ar( ^ ρj) = 13h + 7
(h + 1)2
Finally calculate:
Aj = pV ar ρ^j ( ^ ρj)
Under the assumption that there is no correlation (that is ρj = 0) and assuming
n is large Aj should have an approximate standard normal distribution. Test
the null hypothesis:
H0 : Ui’s have zero lag j correlation
at level α, reject the hypothesis if jAjj > z1−α=2. Here j and α should be kept
as parameters.
(* To calculate zα in your code, in python you can use the library function
scipy.stats.norm.ppf(α) where α is the level. We will share a stub code for your
convenience. Other language users can use any built in function to calculate
this value or keep a file containing a table for these values generated from the
code.)
3
7 Report Writing
You will have to create a consolidated report showing the generated results
for different values of n and test-wise parameters (For both lab and theory
assignment). You also have to write down a detailed analysis of the generated
results (For theory assignment only).
You will calculate the values for n = 20, 500, 4000 and 10000. For each n,
perform 10 tests in total:
• Uniformity test at k = 10 and k = 20
• Serial test using d = 2; 3 and k = 4; 8
• Run length test
• Correlation test with j =1, 3 and 5.
The value of α for all tests will be 0.1 .
8 Submission and Deadline
Deadline is set at Saturday, 12 December 2020 at 11:59pm.
We will create two separate submission links for code and report submission
respectively.
For code submission, place all your source codes in a folder, rename the
folder as your 7 digit student ID, zip the folder and submit it.
For the report submission, create a pdf document. Rename the pdf as
your 7 digit student ID (e.g. 1505003.pdf). Also the report inside
should contain your name and roll number in the front page. Submit
this pdf file in the link.
Copying is strictly prohibited and if found will be dealt harshly.
4

# Google_Foo_Bar_Help
Helping a random reddit user with his markov chain code.

The principal issue is the way in which you are calculating the standard form. After verfying the matrix calculations for matrix subtractin, inverse, and multiplication, I narrowed your issue down to the method for which you calculate your standard form.

I've attached the edits that I've made to the code which show my methods for debugging. 
However, I assume you've spent a great deal of time debugging this, so I'll do you the decency of sharing exaclty how I narrowed the issue down within 3 hours of work (I don't know how much time google gives people, but I hope it was more than a few hours!)

## NOTE: 
For all the following debugging, I used only the very last test case so that I had something to narrow down on. As you'll read soon, it's tedious to debug the rest so I haven't done that. Debugging the rest will involve a lot of manual pen and paper writing OR successfully rewriting one of your functions. 

Just keep in mind that for the following, I am referring to the last test case.


## Step 1) Create a Pretty Print function to print matrices in a readable format.
I use this function pretty much throughout all of my debugging. It gives me important information like the dimensions of the matrix.

## Step 2) Verify Matrix Multiplication and Inverse function correctness.
As it turns out, your multiplication and inverse functions seem to be doing their jobs. HOWEVER I did not check to see if your mult function allows someone to pass in uncompatible matrices such as the case where the dimensionalities don't match up.

## Step 3) Verify (Identity - Q)
This was easy to check. Works fine.

## Step 4) Verify your Pre-processing like Transition Form and Absorbing Form
This had to be done by printing the matrices and using visual inspection. It checked out.

## Step 5) Verify Standard Form
Finally, I got to verifying the standard form. I chose to do this last for two reasons:
1. You used someone else's code for parts of this, so I assumed an error would be more likely in code you wrote in a time crunch.
2. There is no calculator for putting a matrix in a standard form. I literally did this by hand on a 10x10 matrix. You're welcome haha.

This is where it gets interesting. I chose to put it in standard form by taking the 4 absorbing states, and making them the first 4 states in the order that they appeared in the original matrix.
From there, I put the non-absorbing states beneath the absorbing states in the order that they appeared in the original matrix.

Here's the original and the Standard Form version side by side:
![StandardFormCalculation](StandardFormCalculation.png)

At this point, I hard-coded this standard form into your code and ran it. Here's the final result, with all the pretty print calls so you can see and the intermediate steps along the process.

------------ TERMINAL OUTPUT -------------------

STARTING MATRIX
 ROWS:10   COLS: 10
 
0/1  0/1  0/1  0/1  3/1  5/1  0/1  0/1  0/1  2/1  
0/1  0/1  4/1  0/1  0/1  0/1  1/1  0/1  0/1  0/1  
0/1  0/1  0/1  4/1  4/1  0/1  0/1  0/1  1/1  1/1  
13/1  0/1  0/1  0/1  0/1  0/1  2/1  0/1  0/1  0/1  
0/1  1/1  8/1  7/1  0/1  0/1  0/1  1/1  3/1  0/1  
1/1  7/1  0/1  0/1  0/1  0/1  0/1  2/1  0/1  0/1  
0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  
0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  
0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  
0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  




TRANSITION FORM
 ROWS:10   COLS: 10
 
0/1  0/1  0/1  0/1  3/10  1/2  0/1  0/1  0/1  1/5  
0/1  0/1  4/5  0/1  0/1  0/1  1/5  0/1  0/1  0/1  
0/1  0/1  0/1  2/5  2/5  0/1  0/1  0/1  1/10  1/10  
13/15  0/1  0/1  0/1  0/1  0/1  2/15  0/1  0/1  0/1  
0/1  1/20  2/5  7/20  0/1  0/1  0/1  1/20  3/20  0/1  
1/10  7/10  0/1  0/1  0/1  0/1  0/1  1/5  0/1  0/1  
0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  
0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  
0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  
0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  




ABSORBING FORM
 ROWS:10   COLS: 10
 
0/1  0/1  0/1  0/1  3/10  1/2  0/1  0/1  0/1  1/5  
0/1  0/1  4/5  0/1  0/1  0/1  1/5  0/1  0/1  0/1  
0/1  0/1  0/1  2/5  2/5  0/1  0/1  0/1  1/10  1/10  
13/15  0/1  0/1  0/1  0/1  0/1  2/15  0/1  0/1  0/1  
0/1  1/20  2/5  7/20  0/1  0/1  0/1  1/20  3/20  0/1  
1/10  7/10  0/1  0/1  0/1  0/1  0/1  1/5  0/1  0/1  
0/1  0/1  0/1  0/1  0/1  0/1  1/1  0/1  0/1  0/1  
0/1  0/1  0/1  0/1  0/1  0/1  0/1  1/1  0/1  0/1  
0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  1/1  0/1  
0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  1/1  




STANDARD FORM
 ROWS:10   COLS: 10
 
1/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  
0/1  1/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  
0/1  0/1  1/1  0/1  0/1  0/1  0/1  0/1  0/1  0/1  
0/1  0/1  0/1  1/1  0/1  0/1  0/1  0/1  0/1  0/1  
0/1  0/1  0/1  1/5  0/1  0/1  0/1  0/1  3/10  1/2  
1/5  0/1  0/1  0/1  0/1  0/1  4/5  0/1  0/1  0/1  
0/1  0/1  1/10  1/10  0/1  0/1  0/1  2/5  2/5  0/1  
2/15  0/1  0/1  0/1  13/15  0/1  0/1  0/1  0/1  0/1  
0/1  1/20  3/20  0/1  0/1  1/20  2/5  7/20  0/1  0/1  
0/1  1/5  0/1  0/1  1/10  7/10  0/1  0/1  0/1  0/1  




R:
 ROWS:6   COLS: 4
 
0/1  0/1  0/1  1/5  
1/5  0/1  0/1  0/1  
0/1  0/1  1/10  1/10  
2/15  0/1  0/1  0/1  
0/1  1/20  3/20  0/1  
0/1  1/5  0/1  0/1  




Q:
 ROWS:6   COLS: 6
 
0/1  0/1  0/1  0/1  3/10  1/2  
0/1  0/1  4/5  0/1  0/1  0/1  
0/1  0/1  0/1  2/5  2/5  0/1  
13/15  0/1  0/1  0/1  0/1  0/1  
0/1  1/20  2/5  7/20  0/1  0/1  
1/10  7/10  0/1  0/1  0/1  0/1  




Identity minus Q: 
 ROWS:6   COLS: 6
 
1/1  0/1  0/1  0/1  -3/10  -1/2  
0/1  1/1  -4/5  0/1  0/1  0/1  
0/1  0/1  1/1  -2/5  -2/5  0/1  
-13/15  0/1  0/1  1/1  0/1  0/1  
0/1  -1/20  -2/5  -7/20  1/1  0/1  
-1/10  -7/10  0/1  0/1  0/1  1/1  




I AM ABOUT TO MULTIPLY F:
 ROWS:6   COLS: 6
 
8/5  3/5  4/5  3/5  4/5  4/5  
1872/2575  3327/2575  3436/2575  2052/2575  1936/2575  936/2575  
468/515  188/515  859/515  513/515  484/515  234/515  
104/75  13/25  52/75  38/25  52/75  52/75  
6838/7725  1011/2575  7544/7725  4997/5150  12794/7725  3419/7725  
8612/12875  12417/12875  13056/12875  15909/25750  7806/12875  17181/12875  




BY R: 
 ROWS:6   COLS: 4
 
0/1  0/1  0/1  1/5  
1/5  0/1  0/1  0/1  
0/1  0/1  1/10  1/10  
2/15  0/1  0/1  0/1  
0/1  1/20  3/20  0/1  
0/1  1/5  0/1  0/1  




AND I GOT FR: 
 ROWS:6    COLS: 4
 
1/5  1/5  1/5  2/5  
939/2575  284/2575  634/2575  718/2575  
106/515  71/515  317/1030  359/1030  
23/75  13/75  13/75  26/75  
1606/7725  2647/15450  5347/15450  2122/7725  
3544/12875  7653/25750  4953/25750  3028/12875  




([1, 1, 1, 2, 5], 'WRONG!')



It says "wrong" because you hard-coded that in there, but as you can see, the answer is right according to the link you provided: 
https://sskaje.me/2017/05/googles-foo-bar-doomsday-fuel/


## Final Thoughts

So now that I've discovered the issue, I would like to help solve it. I have the algorithm in my head already. Will get back to you on this, as it's something I might do tonight or next weekend.









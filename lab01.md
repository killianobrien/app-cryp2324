#  Week 01 lab 6G6Z0024 Applied Cryptography

## The lab session 

* If necessary, we will discuss any remaining material from the lecture.
* Then we can discuss any questions or queries from the lecture.
* Then we can work on the programming and mathematical taks below to consolidate and further our understanding of the topics from the lecture.

## Tasks

We will work with the language Python in a Jupyter notebook since this allows us to easily redit our commands and annotate them nicely. 

* Start the `Anacaonda Navigator` software from the Start menu. 
* Launch a `Jupyter server` and Python 3 notebook.

The [Sympy](https://www.sympy.org/en/index.html) library is a Python library for symbolic mathematics and provides some commands we will make use of. You can read more about Sympy and consult the documentation at the above link.

    import sympy as sp



Sympy has an inbuilt `gcd` command

    sp.gcd(10,8)


### Q1. Implementing the Euclidean algorithm

Let's write our own implementation of the Euclidean algorithm. There are a few ways to approach this. One way is to use the principle of *recursion* and exploit the relationship that 

    gcd(a,n) = gcd(n,r)


whenever 

    a = qn + r. 


So we could write our python function using the structure

    def mygcd(a,b):
        if b==0:
            return a
        else:
            q = ?
            r = ?
            return mygcd(b,r)

Note the check to return `gcd(x,0)=x` when we have reached the *last* integer division. Note the use of recursion where we basically define the `mygcd` function by returing another call to `mygcd`.

**Task**

1. Complete the model code above, by replacing the `?`s, to obtain a working function `mygcd`. Test that it is working correctly on small arguments. Compare its output with `sp.gcd` for some large arguments.

2. What other checks/cases should you use like the `if b==0` one, in order for your function to work with all valid inputs? How should your function treat any negative arguments?

2. Write another version that does not rely on function recursion. You can do this with a suitable `while` loop for instance. 

### Q2 Implementing the extended Euclidean algorithm

Sympy has an implementation of the Extended Euclidean algorithm `sp.gcdex`

    sp.gcdex(a,b)

will return a 3-tuple (x,y,d) satisfying

* `gcd(a,b) = d`
* `d = ax + by`

Let's write our own implementation of this using, again using the recursion principle, with the structure

    def mygcdex(a,b):
        if b==0:
            return (?,?,a)
        else:
            q = ?
            r = ?
            (x,y,d) = mygcdex(?,?)
            newx = ?
            newy = ?
            return (newx,newy,d)

**Task**

1. Replace the `?`s in the code above to obtain a working version of `mygcdex`. You'll have to think very carefully about how to define `newx` and `newy`. Pen and paper may be needed to figure it out.
2. Test it on some small arguments to ensure it's working correctly. 
3. Test it on some large arguments and ensure it's working correctly. 
4. Does the function work with (some or all) negative arguments? Adapt it so it does.
4. Compare its output with `sp.gcdex`.

### Q3 Investigating multiplicative inverses

Sympy has the function `sp.mod_inverse` for computing multiplicative modular inverses. `sp.mod_inverse(a,n)` returns the multiplicative inverse of `a` modulo `n`.

**Task**

1. Experiment with `sp.mod_inverse` to familiarize yourself with it and its output. 
2. Write your own function `mymod_inverse` that uses the output of `mygcdex` or `sp.gcdex` to calculate multiplicative inverses. 
3. It should raise an error, or at least print some output, to indicate when the inverse does not exist.
4. Like before, test it and compare its output with `sp.mod_inverse`.
5. Use `mymod_inverse` to replicate the table of inverses modulo 8, shown on page 55 of Stallings. 

### Q4 Further investigation of multiplicative inverses

1. Go further, and tabulate inverses for elements of $Z_n$ for a range of moduli $n$. 
2. For the moduli $n=3,5,7,11,13,17,\dots$ what do you notice about the existence of multiplicative inverses. Why does it behave like this?

### Working with the problems in Chapter 2 of Stallings. 

Each chapter of Stallings ends with a collection of problems that will help to consolidate and further your understanding of the topics. Suggested problems from Chapter 2 are 

* 2.3
* 2.11
* 2.12
* Problems 2.13, 2.14 and 2.15 carry out further investigation of Euclid's algorithm and an alternative algorithm for computing `gcd`.
* 2.16


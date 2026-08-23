# Lecture 12 Python Boot Camp III: Writing Good Code

> [!NOTE]
> [Lecture Stream](https://tamucc.zoom.us/rec/share/XU_Zb00JD1LAIOsXqg6jVv-goQ9a21q_w9jgs1npiwi3Bzk1GF8KHzZqQqh66S2x.N5sKXhzsbZ-WQRo8)
> Passcode: y9e6EN%=

> [!IMPORTANT]
> Assignment 12 is due the last day of classes

---

## Computer Preparation

Before class, complete the [Computer Setup Checklist](../resources/computer_setup_checklist.md).

Confirm that Git, Conda, Python, and the `~/CSB` repository work before continuing.

---

## I. Python Problem Solving 101

* Think through problem
* Break down complex tasks into simple steps
* Write steps in english as comments
* Trouble shoot with subset of large data sets
* Use packages (like `os` and `csv`)
* Use reference materials (book, google search, stack exchange, etc)

___


## II. Lecture Activities 

### 4.1 Basic Coding Principles for Science

* *Minimize errors by minimizing optimization*
	* working code is better than fastest code
	
* *Make code readable by applying consistent formatting*
	* python forces you to do this
	
* *Complex tasks should be broken down into simple tasks or building blocks, i.e. functions*
	* this concept applies to all challenges you will face, not just coding

* *Use premade packages that do what you want to accomplish*
	* do not reinvent wheel

* *Use debugger and employ _unit testing_*
	* we will learn about this

* *Use a profiler to identify code that needs optimizing*
	* identify code that is too slow and needs to be sped up

___


### 4.2.1 Writing Functions

As with most other coding languages, `python` allows you to create [functions](https://en.wikipedia.org/wiki/Subroutine). 

When dividing the complex task of making a program into steps, it is important to avoid both over and underdividing.
* Too many user-defined functions are hard to track
* Too few user-defined functions makes bloated code (too many lines)

My rule of thumb is to create functions for repetative tasks.  If you find yourself copying and pasting blocks of code multiple times within a script, you should make a function out of it.

We have been using built in `python` functions, but we can also make our own. Remember, you need to define your custom function before you can use it.

___


#### Example Function - Calculate GC Content of DNA

Let us write a function that that calculates the GC content of a DNA sequence.  I want you to type the function into `notepad++` or `bbedit` then test it by copying and pasting it into a `python` terminal

```bash
# move to the sandbox for this chapter, and start python
cd ~/CSB/good_code/sandbox
python3
```

```python
# this is the function to calc GC content of a DNA sequence, 
# copy and paste this into your text editor
def GCcontent(dna):
	dna = dna.upper()
	numG = dna.count("G")
	numC = dna.count("C")
	numA = dna.count("A")
	numT = dna.count("T")
	return (numG + numC) / (numG + numC + numT + numA)
```

```python
# It should look like this if it works:
>>> def GCcontent(dna):
...     dna = dna.upper()
...     numG = dna.count("G")
...     numC = dna.count("C")
...     numA = dna.count("A")
...     numT = dna.count("T")
...     return (numG + numC) / (numG + numC + numT + numA)
...
>>>
```

After loading the function, you can now see it in your lists of variables

```python
# show variables and functions in enviroment
>>> globals()
{'__name__': '__main__', '__doc__': None, '__package__': None, '__loader__': <class '_frozen_importlib.BuiltinImporter'>, '__spec__': None, '__annotations__': {}, '__builtins__': <module 'builtins' (built-in)>, 'GCcontent': <function GCcontent at 0x7fc203307bf8>}

>>> locals()
{'__name__': '__main__', '__doc__': None, '__package__': None, '__loader__': <class '_frozen_importlib.BuiltinImporter'>, '__spec__': None, '__annotations__': {}, '__builtins__': <module 'builtins' (built-in)>, 'GCcontent': <function GCcontent at 0x7fc203307bf8>}
```

___


#### Anatomy of the `GCcontent()` Function:

* Line 1: define the function with `def GCcontent(dna):`
	* `def` means define.  this has to be used
	* `GCcontent()` is the name of the function you are creating
	* `dna` is a variable that contains the dna sequence passed into the function for processing
	
* Lines 2-6: code to calculate GC content
	* make all bases uppercase in sequence `dna = dna.upper()`
	* Count the number of G `numG = dna.count("G")`
	* Count C, A, and T also
	
* Line 7: define the output of the function `return (numG + numC) / (numG + numC + numT + numA)`
	* `return` tells the function to output, or return, the result of the following code
	* `(numG + numC) / (numG + numC + numT + numA)` calculates the proportion of bases that are either G or C

___


#### Using the `GCcontent()` Function:

Use the `GCcontent()` function in your terminal.  Note that the DNA sequence you specify is loaded into the `dna` variable

```python
>>> GCcontent("AATTTCCCGGGAAA")
0.42857142857142855
>>> GCcontent("ATGCATGCATGC")
0.5
```

___


#### Concept Reinforcement - Make Two More Functions

Let us define more functions in your text editor, then copy and paste these new functions into your python3 terminal.  Fix any errors that occur in your text editor and try again.

```python
#print a dictionary
def print_dictionary(mydictionary):
	for k, v in mydictionary.items():
		print("key: ", k, " value: ", str(v))

#return a list with results
def squared(start = 1, end = 10):
	results = []
	for i in range(start, end):
		r = i ** 2
		results.append(r)
	return results

```

Now we can test the functions.  Note that `squared()` has default values which are overruled by user-defined values.

```python
>>> print_dictionary({"a": 3.4, "b": [1, 2, 3, 4], "c": "astring"})
key:  a  value:  3.4
key:  b  value:  [1, 2, 3, 4]
key:  c  value:  astring

>>> squared()
[1, 4, 9, 16, 25, 36, 49, 64, 81]

>>> squared(start = 3, end = 10)
[9, 16, 25, 36, 49, 64, 81]

>>> squared(5)
[25, 36, 49, 64, 81]

>>> squared(end = 3)
[1, 4]

```

___


#### [Mind Expander 4.1](https://forms.office.com/Pages/ResponsePage.aspx?id=8frLNKZngUepylFOslULZlFZdbyVx8RLiPt1GobhHnlUMExGOVA0TUROVklLUlhKSUtaN0ZKS1UzNS4u)

* [Mind Expander 4.1(Outside TAMUCC)](https://forms.office.com/r/2FTh5pV1Ra)

Answer the questions in the above link while referring to the following code blocks (you are expected to run them in `python`):

```python
def foo1(x = 7):
	return x ** 0.5
```

```python
def foo2(x = 3, y = 5):
	if x > y:
		return x
	return y
```

```python
def foo3(x = 2, y = 0, z = 9):
	if x > y:
		tmp = y
		y = x
		x = tmp
	if y > z:
		tmp = z
		z = y
		y = tmp
	if x > y:
		tmp = y
		y = x
		x = tmp
	return [x, y, z]
```

```python
def foo4(x = 6):
	result = 1
	for i in range(1, x + 1):
		result = result * i
	return result
```

```python
def foo5(x = 1729):
	d = 2
	myfactors = []
	while x > 1:
		if x % d == 0:
			myfactors.append(d)
			x = x / d
		else:
			d = d + 1
	return myfactors
```

```python
def foo6(x = 25):
	if x == 1:
		return 1
	return x * foo6(x - 1)
```

```python
def foo7(x = 100):
	myp = [2]
	for i in range(3, x + 1):
		success = False
		for j in myp:
			if i % j == 0:
				success = True
				break
		if success == False:
			myp.append(i)
	return myp
```

___


### 4.2.2 Importing Packages and Modules

*Modules* are single files that contain multiple functions.

*Packages* are collections of modules and can be imported into python to save time. Last week we used the `csv` and `os` packages.

There are 4 different ways to to load a module. Below we will use generic terms *theModule* and *theFunction* which should be replaced with real module and function names, respectively.
* `import theModule`
* `from theModule import theFunction`
* `import theModule as mm`
	* gives the module the name mm
* `from theModule import *`

You should definitely create your own modules to save time. They would contain fuctions that you use frequently.

> [!IMPORTANT]
> Exit python with `ctrl-d`

```bash
# you can install python packages from the bash terminal using pip

pip install scipy
```

> [!IMPORTANT]
> Enter python 

```bash
python3
```

```python
import scipy
```


---

### 4.2.3 Program Structure: Making a Program

When writing more complex programs, *it is imperative to break them down into managable pieces* that can be easily debugged, tested, and maintained.

We are going to simulate changes in a population of *N* monoecious, diploid organisms through time.  We will focus on a gene with two alleles, `A` and `a`. 
* To initialize the population, each individual will be assigned an `A` with probability *p* and `a` with probability of `1-p`. 
* At the end of each generation, individuals will randomly mate and die after reproducing.  
* The population size will remain stable and there will be no mutations.

Once it is made, we can use the simulation to investigate [genetic drift](https://en.wikipedia.org/wiki/Genetic_drift). This is essentially a forward time [Wright-Fisher simulation](https://en.wikipedia.org/wiki/Genetic_drift#Wright.E2.80.93Fisher_model)

![](https://www.lds.org/bc/content/ldsorg/topics/book-of-mormon-dna/drift[1].png)

To make the simulation, we will create *functions*, then use a "master" program to call the *functions* and orchestrate the simulation.

___


#### Step 1: Plan of Attack

The first step is not coding, it is strategizing and developing a plan of attack in plain English

* Need a function to build the population
	* inputs: the population size (`N`), probabilty of *A* (`p`)
	* returns: `population` of diploid indiviudals, e.g `AA,AA,Aa,aa`
	
* Need a function to compute [genotypic](https://en.wikipedia.org/wiki/Genotype) frequencies 
	* Inputs: the `population`
	* Outputs: the count for each [genotype](https://en.wikipedia.org/wiki/Genotype)
	
* Need a reproduction function that 
	* Inputs: current generation 
	* Outputs: the next generation

___


#### Step 2: Choose Data Structures

* `population`: *list* of *tuples* `[("A", "a"), ("A", "A")]`

___


#### Step 3: Find Modules

The third step is identifying modules that can be useful

* `SciPy` and `NumPy`

___


#### Step 4: Build 1st Function

We begin by building the population creation function (in our text editor), then test it in the python3 terminal

```python
# import scipy & numpy
import scipy
import numpy as np

# make function to build population
def build_population(N, p):
    """The population consists of N individuals.
        Each individual has two chromosomes, containing
        allele "A" or "a", with probability p or 1-p,
        respectively.
        The population stored as a list of tuples, 
        where each tuple contains a genotype, 
        e.g. a pop of two indiviudals, one hetero and 
        one homozygote is represented as follows [("A", "a"), ("A", "A")].
    """
    population = []
    for i in range(N):
        # Determine allele 1
        if np.random.rand() > p:
            allele1 = "a"
        else:
            allele1 = "A"
        
        # Determine allele 2
        if np.random.rand() > p:
            allele2 = "a"
        else:
            allele2 = "A"
        
        population.append((allele1, allele2))
    
    return population

```

Test the function by copying it from text editor and pasting it into python3 terminal then running the following code

```python
>>> build_population(N = 10, p = 0.7)
[('A', 'A'), ('A', 'A'), ('a', 'A'), ('A', 'A'), ('A', 'a'), ('a', 'a'), ('a', 'a'), ('A', 'a'), ('A', 'a'), ('A', 'a')]
```

___

#### Step 5: Build 2nd Function

Next we build the function that computes genotype frequencies.  AA, Aa, aA, and aa are the possible genotypes. Aa and aA differ according to which allele was maternally vs. paternally inherited. The frequencies are the counts of each genotype.

```python
def compute_frequencies(population):
	""" Count the genotypes.
		Returns a dictionary of genotypic frequencies.
	"""
	AA = population.count(("A", "A"))
	Aa = population.count(("A", "a"))
	aA = population.count(("a", "A"))
	aa = population.count(("a", "a"))
	return({"AA": AA,
		"aa": aa,
		"Aa": Aa,
		"aA": aA})

```

Test the genotype function

```python
>>> my_pop = build_population(6, 0.5)
>>> my_pop
[('a', 'A'), ('A', 'A'), ('a', 'A'), ('a', 'a'), ('A', 'A'), ('A', 'a')]

>>> compute_frequencies(my_pop)
{'AA': 2, 'aa': 1, 'Aa': 1, 'aA': 2}

>>> compute_frequencies(build_population(100, 0.8))
{'AA': 61, 'aa': 6, 'Aa': 12, 'aA': 21}
```

___


#### Step 6: Build 3rd Function

This function accepts the current population of reproductive adults and outputs the next generation with the same size as the previous generation. 

Assumptions:

* Adults produce an infinite pool of gametes
* Random mating

We draw alleles from the infinite pool of gametes at random to create the next generation of diploids.

```python
def reproduce_population(population):
	""" Create new generation through reproduction
		For each of N new offspring,
		- choose the parents at random;
		- the offspring receives a chromosome from
		each of the parents.
	"""
	new_generation = []
	N = len(population)
	for i in range(N):
		dad = np.random.randint(N)
		mom = np.random.randint(N)
		chr_mom = np.random.randint(2)
		offspring = (population[mom][chr_mom], population [dad][1 - chr_mom])
		new_generation.append(offspring)
	return(new_generation)
	
```

And test it

```python
>>> reproduce_population(my_pop)
[('A', 'A'), ('a', 'A'), ('A', 'A'), ('A', 'a'), ('A', 'A'), ('A', 'A')]
```

*Phew!!!  (out of breath)  *

___


#### Step 7: Save Functions in a Module & Import

Save your module (a file with the 3 functions we just made) into a file called `drift.py`. There is also a copy of this file in `~/CSB/good_code/solutions`.  

Exit `python` (`ctrl-d`) and copy `drift.py` to your sandbox.

```bash
cd ~/CSB/good_code/sandbox
cp ../solutions/drift.py .
```

> [!IMPORTANT]
> There are two errors in the `drift.py` script.  Be sure to fix it with `sed`

```bash
# add import numpy as np after import scipy
sed -i '/import scipy/a import numpy as np' drift.py

# replace scipy.random with np.random
sed -i 's/scipy\.random/np\.random/g' drift.py
python3
```

Import the module and test that it was imported successfully


```python
>>> import drift
>>> help(drift)
# type q to exit help
```

___


#### Step 8: Build 4th Function that Controls the First 3 Functions

We will simulate a population from generation to generation until an allele is fixed (p = 0 or 1; all A or all a alleles)

*Be careful, if you make the population too large, fixation may not be reached, and the program will keep running like an infinite loop.*

```python
import drift
def simulate_drift(N, p):
	my_pop = drift.build_population(N, p)
	fixation = False
	num_generations = 0
	while fixation == False:
		genotype_counts = drift.compute_frequencies (my_pop)
		if genotype_counts["AA"] == N or genotype_counts["aa"] == N:
			print("An allele reached fixation at generation",
			num_generations)
			print("The genotype counts are")
			print(genotype_counts)
			fixation == True
			break
		my_pop = drift.reproduce_population(my_pop)
		num_generations = num_generations + 1

```

test it

```python
>>> simulate_drift(100, 0.5)
An allele reached fixation at generation 713
The genotype counts are
{'AA': 0, 'aa': 100, 'Aa': 0, 'aA': 0}

>>> simulate_drift(100, 0.9)
An allele reached fixation at generation 45
The genotype counts are
{'AA': 100, 'aa': 0, 'Aa': 0, 'aA': 0}
```

___


#### Step 9. Save 4th Function to Module 

Let us make our pop sim program executable. First save it to a file called simulate_drift.py in your sandbox.

```bash
nano simulate_drift.py
```

Next modify it as follows

```python
#!/usr/bin/env python

import sys
import drift

def simulate_drift(N, p):
        my_pop = drift.build_population(N, p)
        fixation = False
        num_generations = 0
        while fixation == False:
                genotype_counts = drift.compute_frequencies (my_pop)
                if genotype_counts["AA"] == N or genotype_counts["aa"] == N:
                        print("An allele reached fixation at generation",
                        num_generations)
                        print("The genotype counts are")
                        print(genotype_counts)
                        fixation == True
                        break
                my_pop = drift.reproduce_population(my_pop)
                num_generations = num_generations + 1

# this allows arguments to be passed in from the command line
if __name__ == "__main__":
        N = int(sys.argv[1])
        p = float(sys.argv[2])
        simulate_drift(N, p)
```

*Note that the shebang! must have the correct path to `python3` in your `anaconda3` dir, or else the script will not work.  Also note that if you point your shebang at `/usr/bin/python3` or `/usr/local/bin/python3`, these are different installations of `python` and probably will not have the `scipy` package.  You would have to separately install `scipy`, and this is why we are using anaconda.*

Make simulate_drift.py executable

```bash
chmod 700 simulate_drift.py
```

and then test it

```python
./simulate_drift.py 1000 0.1
```

*Note again that we all have multiple `python` installations on our computer.  If you have the shebang! right, even if you turn off anaconda `conda deactivate`, this will still use the anaconda python installation.

___


### 4.3 Writing Style

Code is read more than it is written, and you should be thinking about the reader when writing your code (as well as your assignments for your courses and theses, and publications)

Python has two documents that describe in excruciating detail how you should style your code in two Python Enhancement Proposals:

* [Style Guide for Python Code](https://peps.python.org/pep-0008/)
* [Docstring Conventions](https://peps.python.org/pep-0257/)


If you refer to ch 4.3 in CSB, here is where I disagree:

* You should use tabs for indenting (I know this is the opposite of the book), but it will reduce variation in size of indents


---

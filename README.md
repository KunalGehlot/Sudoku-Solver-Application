# Sudoku Solver Application

This is the first project from Udacity's Artificial Intelligence Nanodegree course.

In this project, you will extend the Sudoku-solving agent developed in the classroom lectures to solve diagonal Sudoku puzzles. A diagonal Sudoku puzzle is identical to traditional Sudoku puzzles with the added constraint that the boxes on the two main diagonals of the board must also contain the digits 1-9 in each cell (just like the rows, columns, and 3x3 blocks). You will also implement another strategy called "Naked Twins", described [here](http://www.sudokudragon.com/guidenakedtwins.htm).

Find the project at Udacity's official Artificial Nanodegree Repository [here](https://github.com/udacity/artificial-intelligence/tree/master/Projects/1_Sudoku).

## Setting up the environment

***(Note: The Recommended Python Version by Udacity is 3.5 or 3.6)***

#### 1. Download the AIND Anaconda environment

Enter the following command in your Linux terminal:
```
wget https://video.udacity-data.com/topher/2018/May/5afdeed0_aind-universal-v3/aind-universal-v3.yml
```

or directly download for windows from [here](https://video.udacity-data.com/topher/2018/May/5afdeed0_aind-universal-v3/aind-universal-v3.yml).

*(Note for Windows users: Some browsers will automatically append a ".txt" extension to the yml file; if your browser does this, then you will need to remove the extension or alter the creation command to correct it.)*

#### 2. Create the environment

Open a Conda activated terminal or Anaconda Prompt and run:

```
conda env create -f aind-universal-v3.yml
```

#### 3. Activate the Environment

- Windows: `activate aind`
- Linux/Mac: `source activate aind`

##### Installation Errors

*WARNING: SOME OPERATING SYSTEMS MAY PRODUCE ERRORS WHILE INSTALLING Z3 -- DO NOT PANIC.*

It can be challenging to configure Z3, particularly on some versions of Windows. You may use the information below to attempt installing Z3 on Windows, but that platform is not well-supported by the Z3 library maintainers.

NOTE: You may need a C/C++ compiler to build some of the required packages if your system cannot find an installable binary. OSX & Linux users can use gcc & g++/clang *(OSX users will need the XCode Command Line Tools available by running `xcode-select --install` from a Terminal.)* Windows users can download & install Visual C++ Build Tools [here](http://landinghub.visualstudio.com/visual-cpp-build-tools).

Activate the conda environment (source activate aind or activate aind, depending on your OS), then try installing with pip:

```
pip install z3-solver
```

#### 4. Clone project files

Run:
```
git clone https://github.com/udacity/artificial-intelligence
```

Open the artificial-intelligence/Projects/1_Sudoku folder in your preferred IDE or text editor, and follow the instructions in the project readme to complete the TODO items

#### 5. Running Test Cases

You can run a few local test cases by running the following command within the project folder in your terminal:

```
python -m unittest -v

```
You must pass a more challenging set of test cases hosted on a remote server before you can complete the project by running the following command within the project folder in your terminal.

```
udacity submit

```

## Naked Twins Strategy

The naked twins strategy says that if you have two or more unallocated boxes in a unit and there are only two digits that can go in those two boxes, then those two digits can be eliminated from the possible assignments of all other boxes in the same unit.

This pseudocode is accurate, but it isn't very efficient.  You should discuss the other strategies with your peers to look for more efficient implementations. 

Note: It is best to treat the input to this function as immutable. Mutating the state during execution can cause unexpected results during testing because mutating the input can erase pairs of naked twins before they're discovered. 

---
**function** NakedTwins(_values_) **returns** a dict mapping from Sudoku box names to a list of feasible values  
&emsp;**inputs:**  
&emsp;&emsp;_values_, a dict mapping from Sudoku box names to a list of feasible values  
  
&emsp;_out_ <- **copy**(_values_)  /* make a deep copy */  
&emsp;**for each** _boxA_ in _values_ **do**  
&emsp;&emsp;**for each** _boxB_ of **PEERS**(_boxA_) **do**  
&emsp;&emsp;&emsp;**if** both _values_[_boxA_] and _values_[_boxB_] exactly match and have only two feasible digits **do**  
&emsp;&emsp;&emsp;&emsp;**for each** _peer_ of **INTERSECTION**(**PEERS**(_boxA_), **PEERS**(_boxB_)) **do**  
&emsp;&emsp;&emsp;&emsp;&emsp;**for each** _digit_ of _values_[_boxA_] **do**  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;remove digit _d_ from _out_[_peer_]  
&emsp;**return** _out_  

---
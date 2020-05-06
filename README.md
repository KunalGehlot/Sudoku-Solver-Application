# Sudoku Solver Application

This is the first exercise from Udacity's Artificial Intelligence Nanodegree course.

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
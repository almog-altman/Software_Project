# Software_Project

In this project we implemented a version of the Normalized Spectral Clustering algorithm.
The project is written both in C and in Python - the main user interface is via Python (a partial user interface via C),
and the implementation of the algorithm itself is via C.
The connection between the C code and the Python code is done in spkmeansmoudle.c

Executing the project:

Compile the project with the following commands:
1. python setup.py build_ext --inplace
2. bash comp.sh

Arguments for the python interface:

(a) k (int): Number of required clusters. If equal 0, uses heuristic to determine "best" k.

(b) goal (enum): Can get the following values:

	i. spk: Perform full spectral kmeans.
	ii. wam: Calculate and output the Weighted Adjacency Matrix.
	iii. ddg: Calculate and output the Diagonal Degree Matrix.
	iv. lnorm: Calculate and output the Normalized Graph Laplacian.
	v. jacobi: Calculate and output the eigenvalues and eigenvectors.
	
(c) file name (.txt or .csv): The path to the file that will contain N observations, the file extension is .txt or .csv.
Example:
python3 spkmeans.py 3 spk input.txt

Arguments for the partial C interface:

(a) goal (enum): Can get the following values:

	i. wam: Calculate and output the Weighted Adjacency Matrix.
	ii. ddg: Calculate and output the Diagonal Degree Matrix.
	iii. lnorm: Calculate and output the Normalized Graph Laplacian.
	iv. jacobi: Calculate and output the eigenvalues and eigenvectors.
	
(b) file name (.txt or .csv): The path to the file that will contain N observations, the file extension is .txt or .csv.
Example:
./spkmeans lnorm input.txt

NOTE:
For valid input you should use: (Else, the program prints "Invalid input!")
- Right number of command line arguments
- k < N and k > 1 (or you can use k == 0 if you wish to use the automatic heuristic)
  **If the heuristic chooses k to be 1, the program prints "An Error Has Occurred", because it is treated as invalid k.
- N > 1
- goal is one of the mentioned options
- The file with the observations is in the right format:
    1. Each observation coordinate is separated by a comma
    2. The observations are in different lines
    3. Empty line in the end of the file
    4. For Jacobi option – the file must contain a symmetric matrix
  **input_1.txt is an example for the valid format.

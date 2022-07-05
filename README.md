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

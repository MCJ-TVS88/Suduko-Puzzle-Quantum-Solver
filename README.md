# Sudoku-Puzzle-Quantum-Solver

Solving Sudoku puzzles with Grover's Search Algorithm - a mini-project for the Erdos Quantum Computing Boot Camp.

# $2 \times 2$ Sudoku

We begin by considering a simplified instance of the Sudoku puzzle consisting of a $2 \times 2$ grid:

$$
\left[\begin{array}{c|c}
a & b \\
\hline
c & d \\
\end{array}\right], 
\quad \{a, b, c, d\} \in \{0, 1\}.
$$

A configuration of this puzzle constitutes a valid solution if the following constraints are satisfied:

$$
a \neq b, \quad a \neq c, \quad b \neq d, \quad c \neq d.
$$

Under these conditions, there exist exactly two valid solutions:

$$
\left[\begin{array}{c|c}
0 & 1 \\
\hline
1 & 0 \\
\end{array}\right],
\quad
\left[\begin{array}{c|c}
1 & 0 \\
\hline
0 & 1 \\
\end{array}\right].
$$

Each configuration can be uniquely encoded as the binary representation of an integer between \(0\) and \(15\), defined by the tuple $(a\,b\,c\,d)_2$. Accordingly, the two valid solutions correspond to the binary states

$$
6 = (0110)_2, \quad 9 = (1001)_2.
$$

Grover’s search algorithm may be employed to identify these solutions through the following procedure:

1. **Initialization:** Prepare a register of four qubits in the uniform superposition state  

$$|s\rangle_4 = \mathcal{H}^{\otimes 4} \|0\rangle_4,$$

   representing all possible puzzle configurations.

2. **Oracle Application:** Implement a unitary operator \(U\) that evaluates the validity constraints and applies a phase factor of \(-1\) to the states corresponding to valid solutions.

3. **Amplitude Amplification:** Apply the Grover diffusion operator, which performs an inversion about the mean of the amplitude distribution, thereby amplifying the amplitudes of valid configurations while suppressing those of invalid ones.

4. **Iteration:** Repeat steps (2) and (3) an optimal number of times to maximize the measurement probability of a valid solution.

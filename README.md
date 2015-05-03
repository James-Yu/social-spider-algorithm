# Social Spider Algorithm

This is the source code repository of Social Spider Algorithm (SSA) [1]. The algorithm is implemented in multiple programming languages.

[1] James J.Q. Yu and Victor O.K. Li, "A Social Spider Algorithm for Global Optimization," Appl. Soft Comput., vol. 30, pp. 614–627, 2015.

## How to use

You may want to edit the source code to adapt the algorithm to solve your optimization problems.

### C++
    class MyProblem : public Problem {
    public:
        MyProblem(unsigned int dimension) : Problem(dimension) {
            // Your problem initialization.
        }
        double eval(const std::vector<double>& solution) {
            // Your objective function implementation.
            return 0.0;
        }
    };
	SSA ssa(new MyProblem(30), 30);
    ssa.run(10000, 1.0, 0.7, 0.1);

### Python

    def problem(x):
        # Your objective function implementation.
        return np.sum(x**2, 1)
    SSA(problem).run()
    
The Python implementation of SSA is vectorized. No loop is conducted on the python-level during each iteration of the algorithm. The objective function shall accept all solutions in the population per invoke.

### MATLAB

    func = @(x)sum(x.^2, 2);
    SSA(func, 30, 100, 10000, 25, 1, 0.7, 0.1);
    
The MATLAB implementation of SSA is a copy of the Python code. It is highly vectorized. The objective function shall accept all solutions in the population per invoke. The default matrix shape is popsize*dimension.

### More implementations TBD

* Java

## Difference

All SSA implementations are coded from the same pseudo-code. Programming language specific optimization is adopted. If significantly different results on a same problem are obtained from these implementations, the C++ one shall be regarded as a standard.

# License

All source codes are released under [MIT License](http://opensource.org/licenses/MIT).
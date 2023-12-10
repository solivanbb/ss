# numerical-analysiss
def bisection_method(func, a, b, tol=1e-6, max_iter=100):
    """
    Bisection method for finding the root of a function.

    Parameters:
    - func: The function for which we want to find the root.
    - a, b: The initial interval [a, b] where the root is expected to be.
    - tol: Tolerance, the algorithm stops when the interval size is less than tol.
    - max_iter: Maximum number of iterations.

    Returns:
    - root: Approximate root of the function.
    - iterations: Number of iterations performed.
    """
    if func(a) * func(b) > 0:
        raise ValueError("The function values at the interval endpoints must have different signs.")

    iteration = 0
    while (b - a) / 2 > tol and iteration < max_iter:
        midpoint = (a + b) / 2
        if func(midpoint) == 0:
            return midpoint, iteration
        elif func(midpoint) * func(a) < 0:
            b = midpoint
        else:
            a = midpoint
        iteration += 1

    root = (a + b) / 2
    return root, iteration

# Example usage:
if __name__ == "__main__":
    # Define the function for which you want to find the root
    def f(x):
        return x**2 - 4

    # Initial interval [a, b]
    a = 0
    b = 3

    # Find the root using the bisection method
    root, iterations = bisection_method(f, a, b)

    print(f"Approximate root: {root}")
    print(f"Iterations performed: {iterations}")

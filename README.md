# project_2
PI APPROX

"""Estimate the value of Pi with Monte Carlo simulation.
Author:  Justin Hatch C.S 2026
Credits:  TBD
"""
import random
import doctest
import points_plot

GOOD_PI = 3.141592653589793
SAMPLES = 100

def in_unit_circle(x: float, y: float) -> bool:
    """Returns True if and only if (x,y) lies within the circle
    with origin (0,0) and radius 1.0.
    
    >>> in_unit_circle(0.0, 0.0)
    True
    >>> in_unit_circle(1.0,1.0)
    False
    
    # You were wondering, weren't you? 
    >>> in_unit_circle(0.5, -0.5)
    True
    >>> in_unit_circle(-0.9, -0.5)
    False
    """
    result = ((x * x) + (y * y)) < 1
    
    return result

def  rand_point_unit_sq() -> tuple[float, float]:
    """Returns random x,y both in range 0..1.0, 0..1.0."""
    x = random.random()
    y = random.random()
    return x, y

def plot_random_points(n_points: int = SAMPLES):
    """Generate and plot n_points points
    in interval (0,0) to (1,1).
    Creates a window and prompts the user before
    closing it.
    """
    points_plot.init()
    points_total = 0
    points_in = 0
    
    for i in range(n_points):
        x, y = rand_point_unit_sq()
        if in_unit_circle(x , y):
            points_total += 1
            points_in += 1
            points_plot.plot(x, y, color_rgb=(255, 10, 10))
        else:
            points_total += 1
            points_plot.plot(x , y, color_rgb=(240, 240, 240))
            
    points_plot.wait_to_close()
    
    return (points_total , points_in)
    
def pi_approx() -> float:
    """Return an estimate of pi by sampling random points.
    >>> relative_error(pi_approx(), GOOD_PI) <= 0.01  # Within 1%
    True
    >>> relative_error(pi_approx(), GOOD_PI) <= 0.01  # Within 1%
    True
    >>> relative_error(pi_approx(), GOOD_PI) <= 0.01  # Within 1%
    True
    """
    points = plot_random_points(SAMPLES)
    
    hit = points[0]
    total = points[1]
    
    print(hit)
    print(total)
    
    return approx
    
def relative_error(est: float, expected: float) -> float:
    """Relative error of estimate (est) as non-negative fraction of expected value.
    
    
    Note estimate and expected are NOT interchangeable (see test cases).
    For example, if expected value is 5.0 but estimate is 3.0, the
    absolute error is -2.0, but the relative error is 2.0/5.0 = 0.4.
    If the expected value is 3.0 but the estimate is 5.0, the
    absolute error is 2.0, but the relative error is 2.0/3.0 = 0.66.
    >>> round(relative_error(3.0, 5.0), 2)
    0.4
    >>> round(relative_error(5.0, 3.0), 2)
    0.67
    """
    abs_error = est - expected
    rel_error = abs(abs_error / expected)
    return rel_error

#def main():
    #doctest.testmod()
    # Eyeball test of scattering points
    

#if __name__ == "__main__":
    print('Doc test complete')
    main()


pi_approx()

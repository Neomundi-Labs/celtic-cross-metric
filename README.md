import numpy as np

def celtic_cross(points=1000, radius=1.0):
    """
    Generate points forming a bounded orthogonal structure:
    two axes constrained within a circular boundary.
    """
    t = np.linspace(-radius, radius, points)

    vertical = np.array([(0, y) for y in t if abs(y) <= radius])
    horizontal = np.array([(x, 0) for x in t if abs(x) <= radius])

    cross = np.vstack((vertical, horizontal))

    # enforce circular boundary
    bounded = np.array([
        p for p in cross if np.linalg.norm(p) <= radius
    ])

    return bounded

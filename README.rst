gptools
=======

Gaussian processes with arbitrary derivative constraints and predictions.

`gptools` is a Python package that provides a convenient, powerful and extensible implementation of Gaussian process regression (GPR). Central to `gptool`'s implementation is support for derivatives and their variances. Furthermore, the implementation supports the incorporation of arbitrary linearly transformed quantities into the GP.

Developed and tested using Python 2.7 and scipy 0.14.0. May work with other versions, but it has not been tested under such configurations.

Full package documentation is located at http://gptools.readthedocs.org/

A printable PDF is available at https://media.readthedocs.org/pdf/gptools/latest/gptools.pdf

Releases are available in PyPI at https://pypi.python.org/pypi/gptools/

To install, simply execute::

    pip install gptools

(You must already have NumPy and Cython installed for this to work.)

If you find this software useful, please be sure to cite it:

M.A. Chilenski et al. 2015 Nucl. Fusion 55 023012

http://stacks.iop.org/0029-5515/55/023012



Notes on using the derivative option in ``add_data``
----------------------------------------------------
Taken from this discussion: https://github.com/markchil/gptools/issues/7

In the meantime, the ``n`` input is designed to let you make as general of a specification of inputs as possible. Essentially, it is asking you to unravel the Hessian. So, say you are working with a 2d process and you have the Hessian ``H=[[1, 2], [2, 3]]`` at point ``x = [0, 1]``. You then unravel H and you probably want to drop the redundant element(s). So, your inputs would be:

    y = [1, 2, 3]
    
    X = [[0, 1], [0, 1], [0, 1]]
    
    n = [[2, 0], [1, 1], [0, 2]]

You can then add these all at once with ``gp.add_data(X, y, n=n)``.

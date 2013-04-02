ipython
-------

_, __: most recent output
_N: output of line N
_iN: input of line N

%quickref

%magic

%hist

%logstart

%pdb: auto drop into pdb when exception occurs.

%xmode

%debug

%timeit

    %timeit x=10 # setup code, not counted in execution time.
    x ** 100


%time

%pycat

# %reset/%xdel - handy if large data, as not garbage collected due to 
#   input/output history.

%reset

%xdel

%page

%prun

%who

%who_ls

%whos



%paste
# prompts.
%cpaste

    # paste and run from clipboard.

%run
    # __name__ not set to '__main__' but filename w/out suffix.
    -n
    # run against ipython namespace, not empty one.
    -i
    # ignore sys.exit() calls.
    -e
    # print timing info at end.
    # -N<N> to run it N times.
    -t [-N<N>]
    # run under pdb, breakpoint on line 1.
    # -b<B> breakpoint line.
    -d [-b<B>]
    # run under profiler.
    -p
    # load module instead of run script.
    -m

matplotlib
---------

import matplotlib.pyplot as plt

plt.plot(x, y, 'o')

np.arange
-----------

    # interval [start, stop)
    np.arange(
        start, # (optional)
        stop,
        step, # (optional)
        # inferred if not given.
        dtype=None)


plt.ylim
--------

    # set/get range of y-axis.
    # set 
    # get
    ymin, ymax = plt.ylim()
    # set
    plt.ylim(
        ymin,
        ymax,
    )
        


np.linspace
------------

    # evenly spaced in interval [start, stop]
    np.linspace(
        start,
        stop,
        num=50,
        # include 'stop'?
        endpoint=True,
        # if True, return tuple. (array, spacing_between_samples)
        retstep=False)

I updated the source code by msilliac such that to use max sum algorithm.
[LBP-original.ipynb](LBP_original.ipynb) is the original source with sum product algorithm.  

[LBP_minsum.ipynb](LBP_minsum.ipynb) implements the max sum algorithm

![Comparison](/stereo.png)

Compare with the sum product algorithm which shows the blurring.  Max sum maintains the sharpness. 






Below is the original readme.md from the fork. 
-----------------

pyLBP - Loopy Belief Propagation for Python, using numpy.

copyright (c) 2014 Thomas Iorns - GPLv2+
    - this program is released under the terms of the
    - GNU General Public License version 2 or any later version

What is it?
-----------

This library provides a class representing a Markov Random Field,
with methods for applying Loopy Belief Propagation.

As input it takes an array specifying the relative probabilities
at each pixel of an image of some discrete set of beliefs,
and an array representing the relative similarity of the beliefs to each other.

A method may then be called to iteratively update the MRF according to the
sum-product Loopy Belief Propagation algorithm.

It uses numpy to do this in an efficient and brisk manner.

Variations of the algorithm may be included at some point,
such as max-product or min-sum,
perhaps even a GPU implementation,
but for now values are assumed to represent probabilities.

The MRF class will normalize arrays on input and iteration,
so the input arrays need only represent relative probabilities.


Usage
-----

put LBP.py in the same location as your Python script,
or interactive session is run from,
then:

    import LBP
    
    mrf = MRF(height, width, num_beliefs)
    mrf.init_base_belief(base_belief_array)
    mrf.init_smoothness(smoothness_array)
    
    for i in range(iterations):
        mrf.pass_messages()
        current_belief = mrf.calc_belief()

For a more in-depth example,
see the "looper.py" example script,
which performs depth-analysis on the tsukuba reference pair of stereo images.

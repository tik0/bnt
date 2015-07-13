## Why Matlab? ##


Matlab is an interactive, matrix-oriented programming language that
enables one to express one's (mathematical) ideas very concisely and directly,
without having to worry about annoying details like memory allocation
or type checking. This considerably reduces development time and
keeps code short, readable and fully portable.
Matlab has excellent built-in support for many data analysis and
visualization routines. In addition, there are many useful toolboxes, e.g., for
neural networks, signal and image processing.
The main disadvantages of Matlab are that it can be slow (which is why
we are currently rewriting parts of BNT in C), and that the commercial
license is expensive (although the student version is only $100 in the US).


Many people ask me why I did not use Octave, an open-source Matlab clone.
The reason is that, when I first wrote BNT,  Octave did not support multi-dimensional arrays,cell arrays, objects, etc. However, currently (Jan 2010) it does
support those thins, so it should be possible to run most of BNT in Octave.
# History of changes to BNT #

**09 May 2010 wsun**
  * Minor bug fixed about assertations. The latest version FullBNT-1.07 uploaded and installation tested without any error.

**07 May 2010 wsun**
  * Bug fixed in \BNT\inference\static\@jtree\_inf\_engine\jtree\_inf\_engine.m: It is proved that the last clique created in the elimination process is not necessarily to be a strong root for CLG model. Instead, we use a clique called interface clique, that contains all discrete parents and at least one continuous node from a connected continuous component, as a guaranteed strong root.

  * Added one function \graph\findroot.m: this is to find the interface clique with max number of discrete parent nodes as the guaranteed strong root.

**16 Feb 2010 mdunham**
  * Minor bug fixes to make Matlab 2009 compatible, e.g. replaced calls to deprecated finite function with isfinite, renamed custom assert, isscalar, and isvector functions assertBNT, isscalarBNT, isvectorBNT.

**28 Jan 2010 murphyk**
  * Matt Dunham helped me move the code and website to bnt.googlecode.com

**19 Oct 07 murphyk**

  * BNT\CPDs\@noisyor\_CPD\CPD\_to\_CPT.m: 2nd half of the file is a repeat of the first half and was deleted (thanks to Karl Kuschner)

  * KPMtools\myismember.m should return logical for use in "assert" so add line at end                 p=logical(p);  this prevents "assert" from failing on an integer input. (thanks to Karl Kuschner)



**17 Oct 07 murphyk**

  * Updated subv2ind and ind2subv in KPMtools to Tom Minka's implementation. His ind2subv is faster (vectorized), but I had to modify it so it matched the behavior of my version when called with siz=[.md](.md). His subv2inv is slightly simpler than mine because he does not treat the siz=[2 ... 2](2.md) case separately. Note: there is now no need to ever use the C versions of these functions (or any others, for that matter).

  * removed BNT/add\_BNT\_to\_path since no longer needed.

**4 Oct 07 murphyk**

  * moved code from sourceforge to UBC website, made version 1.0.4

  * @pearl\_inf\_engine/pearl\_inf\_engine line 24, default argument for protocol changed from [.md](.md) to 'parallel'. Also, changed private/parallel\_protocol so it doesn't write to an empty file id (Matlab 7 issue)

  * added foptions (Matlab 7 issue)

  * changed genpathKPM to exclude svn. Put it in toplevel directory to massively simplify the installation process.


## Sourceforge changelog ##


BNT was first ported to sourceforge on 28 July 2001 by yozhik.
BNT was removed from sourceforge on 4 October 2007 by Kevin Murphy;
that version is cached as [FullBNT-1.0.3.zip].
See  [Changelog from
sourceforge] for a history of that version of the code,
which formed the basis of the branch currently on Murphy's web page.



## Changes from August 1998 -- July 2004 ##


Kevin Murphy made the following changes to his own private copy.
(Other small changes were made between July 2004 and October 2007, but were
not documented.)
These may or may not be reflected in the sourceforge version of the
code (which was independently maintained).



**9 June 2004
  * Changed tabular\_CPD/learn\_params back to old syntax, to make it compatible with gaussian\_CPD/learn\_params (and re-enabled generic\_CPD/learn\_params). Modified learning/learn\_params.m and learning/score\_family appropriately. (In particular, I undid the change Sonia Leach had to make to score\_family to handle this asymmetry.) Added examples/static/gaussian2 to test this new functionality.
  * Added bp\_mrf2 (for generic pairwise MRFs) to inference/static/@bp\_belprop\_mrf2\_inf\_engine. [are not "officially" supported in BNT, so this code is just for expert hackers.](MRFs.md)
  * Added examples/static/nodeorderExample.m to illustrate importance of using topological ordering.
  * Ran dos2unix on all**.c files within BNT to eliminate compiler warnings.
  7 June 2004
  * Replaced normaliseC with normalise in HMM/fwdback, for maximum portability (and negligible loss in speed).
  * Ensured FullBNT versions of HMM, KPMstats etc were as up-to-date as stand-alone versions.
  * Changed add\_BNT\_to\_path so it no longer uses addpath(genpath()), which caused Old versions of files to mask new ones.
  18 February 2004
  * A few small bug fixes to BNT, as posted to the Yahoo group.
  * Several new functions added to KPMtools, KPMstats and Graphviz (none needed by BNT).
  * Added CVS to some of my toolboxes.
  30 July 2003
  * qian.diao fixed @mpot/set\_domain\_pot and @cgpot/set\_domain\_pot
  * Marco Grzegorczyk found, and Sonia Leach fixed, a bug in do\_removal inside learn\_struct\_mcmc
  28 July 2003
  * Sebastian Luehr provided 2 minor bug fixes, to HMM/fwdback (if any(scale==0)) and FullBNT\HMM\CPDs\@hhmmQ\_CPD\update\_ess.m (wrong transpose).
  8 July 2003
  * Removed buggy  BNT/examples/static/MRF2/Old/mk\_2D\_lattice.m which was masking correct graph/mk\_2D\_lattice.
  * Fixed bug in graph/mk\_2D\_lattice\_slow in the non-wrap-around case (line 78)
  2 July 2003
  * Sped up normalize(., 1) in KPMtools by avoiding general repmat
  * Added assign\_cols and marginalize\_table to KPMtools
  29 May 2003
  * Modified KPMstats/mixgauss\_Mstep so it repmats Sigma in the tied covariance case (bug found by galt@media.mit.edu).
  * Bob Welch found bug in gaussian\_CPDs/maximize\_params in the way cpsz was computed.
  * Added KPMstats/mixgauss\_em, because my code is easier to understand/modify than netlab's (at least for me!).
  * Modified BNT/examples/dynamic/viterbi1 to call multinomial\_prob instead of mk\_dhmm\_obs\_lik.
  * Moved parzen window and partitioned models code to KPMstats.
  * Rainer Deventer fixed some bugs in his scgpot code, as follows: 1. complement\_pot.m Problems occured for probabilities equal to zero. The result is an division by zero error.  2. normalize\_pot.m This function is used during the calculation of the log-likelihood. For a probability of zero a warning "log of zero" occurs. I have not realy fixed the bug. As a workaround I suggest to calculate the likelihhod based on realmin (the smallest real number) instead of zero.  3. recursive\_combine\_pots At the beginning of the function there was no test for the trivial case, which defines the combination of two potentials as equal to the direct combination. The result might be an infinite recursion which leads to a stack overflow in matlab.
  11 May 2003
  * Fixed bug in gaussian\_CPD/maximize\_params so it is compatible with the new clg\_Mstep routine
  * Modified KPMstats/cwr\_em to handle single cluster case separately.
  * Fixed bug in netlab/gmminit.
  * Added hash tables to KPMtools.
  4 May 2003
  * Renamed many functions in KPMstats so the name of the distribution/model type comes first, Mstep\_clg -> clg\_Mstep, Mstep\_cond\_gauss -> mixgauss\_Mstep. Also, renamed eval\_pdf\_xxx functions to xxx\_prob, e.g. eval\_pdf\_cond\_mixgauss -> mixgauss\_prob. This is simpler and shorter.
  * Renamed many functions in HMM toolbox so the name of the distribution/model type comes first, log\_lik\_mhmm -> mhmm\_logprob, etc. mk\_arhmm\_obs\_lik has finally been re-implemented in terms of clg\_prob and mixgauss\_prob (for slice 1). Removed the Demos directory, and put them in the main directory. This code is not backwards compatible.
  * Removed some of the my\_xxx functions from KPMstats (these were mostly copies of functions from the Mathworks stats toolbox).
  * Modified BNT to take into account changes to KPMstats and HMM toolboxes.
  * Fixed KPMstats/Mstep\_clg (now called clg\_Mstep) for spherical Gaussian case. (Trace was wrongly parenthesised, and I used YY instead of YTY. The spherical case now gives the same result as the full case for cwr\_demo.) Also, mixgauss\_Mstep now adds 0.01 to the ML estimate of Sigma, to act as a regularizer (it used to add 0.01 to  E[YY'], but this was ignored in the spherical case).
  * Added cluster weighted regression to KPMstats.
  * Added KPMtools/strmatch\_substr.
   28 Mar 03
  * Added mc\_stat\_distrib and eval\_pdf\_cond\_prod\_parzen to KPMstats
  * Fixed GraphViz/arrow.m incompatibility with matlab 6.5 (replace all NaN's with 0). Modified GraphViz/graph\_to\_dot so it also works on windows.
  * I removed dag\_to\_jtree and added graph\_to\_jtree to the graph toolbox; the latter expects an undirected graph as input.
  * I added triangulate\_2Dlattice\_demo.m to graph.
  * Rainer Deventer fixed the stable conditional Gaussian potential classes (scgpot and scgcpot) and inference engine (stab\_cond\_gauss\_inf\_engine).
  * Rainer Deventer added (stable) higher-order Markov models (see inference/dynamic/@stable\_ho\_inf\_engine).
  14 Feb 03
  * Simplified learning/learn\_params so it no longer returns BIC score. Also, simplified @tabular\_CPD/learn\_params so it only takes local evidence. Added learn\_params\_dbn, which does ML estimation of fully observed DBNs.
  * Vectorized KPMstats/eval\_pdf\_cond\_mixgauss for tied Sigma case (much faster!). Also, now works in log-domain to prevent underflow. eval\_pdf\_mixgauss now calls eval\_pdf\_cond\_mixgauss and inherits these benefits.
  * add\_BNT\_to\_path now calls genpath with 2 arguments if using matlab version 5.
   30 Jan 03
  * Vectorized KPMstats/eval\_pdf\_cond\_mixgauss for scalar Sigma case (much faster!)
  * Renamed mk\_dotfile\_from\_hmm to draw\_hmm and moved it to the GraphViz library.
  * Rewrote @gaussian\_CPD/maximize\_params.m so it calls KPMstats/Mstep\_clg. This fixes bug when using clamped means (found by Rainer Deventer and Victor Eruhimov) and a bug when using a Wishart prior (no gamma term in the denominator). It is also easier to read. I rewrote the technical report re-deriving all the equations in a clearer notation, making the solution to the bugs more obvious. (See www.ai.mit.edu/~murphyk/Papers/learncg.pdf) Modified Mstep\_cond\_gauss to handle priors.
  * Fixed bug reported by Ramgopal Mettu in which add\_BNT\_to\_path calls genpath with only 1 argument, whereas version 5 requires 2.
  * Fixed installC and uninstallC to search in FullBNT/BNT.
  24 Jan 03
  * Major simplification of HMM code. The API is not backwards compatible. No new functionality has been added, however. There is now only one fwdback function, instead of 7; different behaviors are controlled through optional arguments. I renamed 'evaluate observation likelihood' (local evidence) to 'evaluate conditional pdf', since this is more general. i.e., renamed mk\_dhmm\_obs\_lik to eval\_pdf\_cond\_multinomial, mk\_ghmm\_obs\_lik to eval\_pdf\_cond\_gauss, mk\_mhmm\_obs\_lik to eval\_pdf\_cond\_mog. These functions have been moved to KPMstats, so they can be used by other toolboxes. ghmm's have been eliminated, since they are just a special case of mhmm's with M=1 mixture component. mixgauss HMMs can now handle a different number of mixture components per state. init\_mhmm has been eliminated, and replaced with init\_cond\_mixgauss (in KPMstats) and mk\_leftright/rightleft\_transmat. learn\_dhmm can no longer handle inputs (although this is easy to add back).
  20 Jan 03
  * Added arrow.m to GraphViz directory, and commented out line 922, in response to a bug report.
  18 Jan 03
  * Major restructuring of BNT file structure: all code that is not specific to Bayes nets has been removed; these packages must be downloaded separately. (Or just download FullBNT.) This makes it easier to ensure different toolboxes are consistent. misc has been slimmed down and renamed KPMtools, so it can be shared by other toolboxes, such as HMM and Kalman; some of the code has been moved to BNT/general. The Graphics directory has been slimmed down and renamed GraphViz. The graph directory now has no dependence on BNT (dag\_to\_jtree has been renamed graph\_to\_jtree and has a new API). netlab2 no longer contains any netlab files, only netlab extensions. None of the functionality has changed.
  11 Jan 03
  * jtree\_dbn\_inf\_engine can now support soft evidence.
  * Rewrote graph/dfs to make it clearer. Return arguments have changed, as has mk\_rooted\_tree. The acyclicity check for large undirected graphs can cause a stack overflow. It turns out that this was not a bug, but is because Matlab's stack depth bound is very low by default.
  * Renamed examples/dynamic/filter2 to filter\_test1, so it does not conflict with the filter2 function in the image processing toolbox.
  * Ran test\_BNT on various versions of matlab to check compatibility. On matlab 6.5 ([r13](https://code.google.com/p/bnt/source/detail?r=13)), elapsed time = 211s, cpu time = 204s. On matlab 6.1 ([r12](https://code.google.com/p/bnt/source/detail?r=12)), elapsed time = 173s, cpu time = 164s. On matlab 5.3 ([r11](https://code.google.com/p/bnt/source/detail?r=11)), elapsed time = 116s, cpu time = 114s. So matlab is apparently getting slower with time!! (All results were with a linux PIII machine.)
  14 Nov 02
  * Removed all ndx inference routines, since they are only marginally faster on toy problems, and are slower on large problems due to having to store and lookup the indices (causes cache misses). In particular, I removed jtree\_ndx\_inf\_eng and jtree\_ndx\_dbn\_inf\_eng, all the **ndx** routines from potentials/Tables, and all the UID stuff from add\_BNT\_to\_path, thus simplifying the code. This required fixing hmm_(2TBN)_inf\_engine/marginal\_nodes\family, and updating installC.
  * Removed jtree\_C\_inf\_engine and jtree\_C\_dbn\_inf\_engine. The former is basically the same as using jtree\_inf\_engine with mutliply\_by\_table.c and marginalize\_table.c. The latter benefited slightly by assuming potentials were tables (arrays not objects), but these negligible savings don't justify the complexity and code duplication.
  * Removed stab\_cond\_gauss\_inf\_engine and scg\_unrolled\_dbn\_inf\_engine, written by shan.huang@intel.com, since the code was buggy.
  * Removed potential\_engine, which was only experimental anyway.
  13 Nov 02
  * **Released version 5**. The previous version, released on 7/28/02, is available [here](here.md).
  * Moved code and documentation to MIT.
  * Added repmat.c from Thomas Minka's lightspeed library. Modified it so it can return an empty matrix.
  * Tomas Kocka fixed bug in the BDeu option for tabular\_CPD, and contributed graph/dag\_to\_eg, to convert to essential graphs.
  * Modified definition of hhmmQ\_CPD, so that Qps can now accept parents in either the current or previous slice.
  * Added hhmm2Q\_CPD class, which is simpler than hhmmQ (no embedded sub CPDs, etc), and which allows the conditioning parents, Qps, to be before (in the topological ordering) the F or Q(t-1) nodes. See BNT/examples/dynamic/HHMM/Map/mk\_map\_hhmm for an example.
  7/28/02
  * Changed graph/best\_first\_elim\_order from min-fill to min-weight.
  * Ernest Chan fixed bug in Kalman/sample\_lds (G{i} becomes G{m} in line 61).
  * Tal Blum  fixed bug in HMM/init\_ghmm (Q becomes K, the number of states).  Fixed jtree\_2tbn\_inf\_engine/set\_fields so it correctly sets the maximize flag to 1 even in subengines.  Gary Bradksi did a simple mod to the PC struct learn alg so you can pass it an adjacency matrix as a constraint. Also, CovMat.m reads a file and produces a covariance matrix.  KNOWN BUG in CPDs/@hhmmQ\_CPD/update\_ess.m at line 72 caused by examples/dynamic/HHMM/Square/learn\_square\_hhmm\_cts.m at line 57.  The old version is available from www.cs.berkeley.edu/~murphyk/BNT.24june02.zip
  6/24/02
  * Renamed dag\_to\_dot as graph\_to\_dot and added support for undirected graphs.
  * Changed syntax for HHMM CPD constructors: no need to specify d/D anymore,so they can be used for more complex models.
  * Removed redundant first argument to mk\_isolated\_tabular\_CPD.
  6/19/02
  * Fixed most probable explanation code. Replaced calc\_mpe with find\_mpe, which is now a method of certain inference engines, e.g., jtree, belprop. calc\_mpe\_global has become the find\_mpe method of global\_joint. calc\_mpe\_bucket has become the find\_mpe method of var\_elim. calc\_mpe\_dbn has become the find\_mpe method of smoother. These routines now correctly find the jointly most probable explanation, instead of the marginally most probable assignments. See examples/static/mpe1\mpe2 and examples/dynamic/viterbi1 for examples. Removed maximize flag from constructor and enter\_evidence methods, since this no longer needs to be specified by the user.
  * Rainer Deventer fixed in a bug in CPDs/@gaussian\_CPD/udpate\_ess.m: now, hidden\_cps = any(hidden\_bitv(cps)), whereas it used to be hidden\_cps = all(hidden\_bitv(cps)).
  5/29/02
  * CPDs/@gaussian\_CPD/udpate\_ess.m fixed WX,WXX,WXY (thanks to Rainer Deventer and Yohsuke Minowa for spotting the bug). Does the C version work??
  * potentials/@cpot/mpot\_to\_cpot fixed K==0 case (thanks to Rainer Deventer).
  * CPDs/@gaussian\_CPD/log\_prob\_node now accepts non-cell array data on self (thanks to rishi  for catching this).
  5/19/02
  * Wei Hu made the following changes.
    * Memory leak repair:      a.  distribute\_evidence.c   in  static/@jtree\_C directory      b.  distribute\_evidence.c   in  static/@jtree\_ndx directory      c.  marg\_tablec.            in  Tables dir
    * Add "@jtree\_ndx\_2TBN\_inf\_engine"  in inference/online dir
    * Add "@jtree\_sparse\_inf\_engine"    in inference/static dir
    * Add "@jtree\_sparse\_2TBN\_inf\_engine"   in inference/online  dir
    * Modify "tabular\_CPD.m" in CPDs/@tabular\_CPD dir , used for sparse
    * In "@discrete\_CPD" dir:      a.  modify "convert\_to\_pot.m", used for sparse      b.  add "convert\_to\_sparse\_table.c"
    * In "potentials/@dpot" dir:      a.  remove "divide\_by\_pot.c" and "multiply\_by\_pot.c"      b.  add "divide\_by\_pot.m" and "multiply\_by\_pot.m"      c.  modify "dpot.m", "marginalize\_pot.m" and "normalize\_pot.m"
    * In "potentials/Tables" dir:      a.  modify mk\_ndxB.c;(for speedup)      b.  add "mult\_by\_table.m",              "divide\_by\_table.m",              "divide\_by\_table.c",              "marg\_sparse\_table.c",              "mult\_by\_sparse\_table.c",              "divide\_by\_sparse\_table.c".
    * Modify "normalise.c" in misc dir, used for sparse.
    * And, add discrete2, discrete3, filter2 and filter3 as test applications in test\_BNT.m Modify installC.m
  * 
  * Kevin made the following changes related to strong junction trees:
    * jtree\_inf\_engin line 75: engine.root\_clq = length(engine.cliques); the last clq is guaranteed to be a strong root
    * dag\_to\_jtree line 38: [jtree, root, B, w] = cliques\_to\_jtree(cliques, ns); never call cliques\_to\_strong\_jtree
    * strong\_elim\_order: use Ilya's code instead of topological sorting.
  * 
  * Kevin fixed CPDs/@generic\_CPD/learn\_params, so it always passes in the correct hidden\_bitv field to update\_params.
**.**  5/8/02
  * Jerod Weinman helped fix some bugs in HHMMQ\_CPD/maximize\_params.
  * Removed broken online inference from hmm\_inf\_engine. It has been replaced filter\_inf\_engine, which can take hmm\_inf\_engine as an argument.
  * Changed graph visualization function names. 'draw\_layout' is now 'draw\_graph', 'draw\_layout\_dbn' is now 'draw\_dbn', 'plotgraph' is now 'dag\_to\_dot', 'plothmm' is now 'hmm\_to\_dot', added 'dbn\_to\_dot', 'mkdot' no longer exists': its functioality has been subsumed by dag\_to\_dot. The dot functions now all take optional args in string/value format.
  4/1/02
  * Added online inference classes. See BNT/inference/online and BNT/examples/dynamic/filter1. This is work in progress.
  * Renamed cmp\_inference to cmp\_inference\_dbn, and made its     interface and behavior more similar to cmp\_inference\_static.
  * Added field rep\_of\_eclass to bnet and dbn, to simplify parameter tying (see ~murphyk/Bayes/param\_tieing.html).
  * Added gmux\_CPD (Gaussian mulitplexers). See BNT/examples/dynamic/SLAM/skf\_data\_assoc\_gmux for an example.
  * Modified the forwards sampling routines. general/sample\_dbn and sample\_bnet now take optional arguments as strings, and can sample with pre-specified evidence. sample\_bnet can only generate a single sample, and it is always a cell array. sample\_node can only generate a single sample, and it is always a scalar or vector. This eliminates the false impression that the function was ever vectorized (which was only true for tabular\_CPDs). (Calling sample\_bnet inside a for-loop is unlikely to be a bottleneck.)
  * Updated usage.html's description of CPDs (gmux) and inference (added gibbs\_sampling and modified the description of pearl).
  * Modified BNT/Kalman/kalman\_filter\smoother so they now optionally take an observed input (control) sequence. Also, optional arguments are now passed as strings.
  * Removed BNT/examples/static/uci\_data to save space.
  3/14/02
  * pearl\_inf\_engine now works for (vector) Gaussian nodes, as well as discrete. compute\_pi has been renamed CPD\_to\_pi. compute\_lambda\_msg     has been renamed CPD\_to\_lambda\_msg. These are now implemented for     the discrete\_CPD class instead of tabular\_CPD. noisyor and     Gaussian have their own private implemenations. Created examples/static/Belprop subdirectory.
  * Added examples/dynamic/HHMM/Motif.
  * Added Matt Brand's entropic prior code.
  * cmp\_inference\_static has changed. It no longer returns err. It     can check for convergence. It can accept 'observed'.
  3/4/02
  * Fixed HHMM code. Now BNT/examples/dynamic/HHMM/mk\_abcd\_hhmm implements the example in the NIPS paper. See also Square/sample\_square\_hhmm\_discrete and other files.
  * Included Bhaskara Marthi's gibbs\_sampling\_inf\_engine. Currently this only works if all CPDs are tabular and if you call installC.
  * Modified Kalman/tracking\_demo  so it calls plotgauss2d instead of     gaussplot.
  * Included Sonia Leach's speedup of mk\_rnd\_dag. My version created all NchooseK subsets, and then picked among them. Sonia reorders the possible parents randomly and choose the first k. This saves on having to enumerate the large number of possible subsets before picking from one.
  * Eliminated BNT/inference/static/Old, which contained some old .mexglx files which wasted space.
  2/15/02
  * Removed the netlab directory, since most of it was not being used, and it took up too much space (the goal is to have BNT.zip be less than 1.4MB, so if fits on a floppy). The required files have been copied into netlab2.
  2/14/02
  * Shan Huang fixed most (all?) of the bugs in his stable CG code. scg1-3 now work, but scg\_3node and scg\_unstable give different     behavior than that reported in the Cowell book.
  * I changed gaussplot so it plots an ellipse representing the     eigenvectors of the covariance matrix, rather than numerically     evaluating the density and using a contour plot; this     is much faster and gives better pictures. The new function is     called plotgauss2d in BNT/Graphics.
  * Joni Alon  fixed some small bugs:     mk\_dhmm\_obs\_lik called forwards with the wrong args, and     add\_BNT\_to\_path should quote filenames with spaces.   I added BNT/stats2/myunidrnd which is called by learn\_struct\_mcmc.   I changed BNT/potentials/@dpot/multiply\_by\_dpot so it now says Tbig.T(:) = Tbig.T(:) .**Ts(:);**
**2/6/02
  * Added hierarchical HMMs. See BNT/examples/dynamic/HHMM and CPDs/@hhmmQ\_CPD and @hhmmF\_CPD.
  * sample\_dbn can now sample until a certain condition is true.
  * Sonia Leach fixed learn\_struct\_mcmc and changed mk\_nbrs\_of\_digraph so it only returns DAGs. Click [here](here.md) for details of her changes.**
**2/4/02
  * Wei Hu fixed a bug in jtree\_ndx\_inf\_engine/collect\distribute\_evidence.c which failed when maximize=1.
  * I fixed various bugs to do with conditional Gaussians, so mixexp3 now works (thansk to Gerry Fung        for spotting the error). Specifically: Changed softmax\_CPD/convert\_to\_pot so it now puts cts nodes in cdom, and no longer inherits       this function from discrete\_CPD.      Changed root\_CPD/convert\_to\_put so it puts self in cdom.**
**1/31/02
  * Fixed log\_lik\_mhmm (thanks to ling chen  for spotting the typo)  Now many scripts in examples/static  call cmp\_inference\_static. Also, SCG scripts have been simplified (but still don't work!).  belprop and belprop\_fg enter\_evidence now returns [engine, ll,       niter], with ll=0, so the order of the arguments is compatible with other engines.  Ensured that all enter\_evidence methods support optional       arguments such as 'maximize', even if they ignore them.  Added Wei Hu's potentials/Tables/rep\_mult.c, which is used to       totally eliminate all repmats from gaussian\_CPD/update\_ess.**
**1/30/02
  * update\_ess now takes hidden\_bitv instead of hidden\_self and hidden\_ps. This allows gaussian\_CPD to distinguish hidden discrete and cts parents. Now learn\_params\_em, as well as learn\_params\_dbn\_em,     passes in this info, for speed.
  * gaussian\_CPD update\_ess is now vectorized for any case where all     the continuous nodes are observed (eg., Gaussian HMMs,  AR-HMMs).
  * mk\_dbn now automatically detects autoregressive nodes.
  * hmm\_inf\_engine now uses indexes in marginal\_nodes/family for     speed. Marginal\_ndoes can now only handle single nodes.    (SDndx is hard-coded, to avoid the overhead of using marg\_ndx,     which is slow because of the case and global statements.)
  * add\_ev\_to\_dmarginal now retains the domain field.
  * Wei Hu wrote potentials/Tables/repmat\_and\_mult.c, which is used to     avoid some of the repmat's in gaussian\_CPD/update\_ess.
  * installC now longer sets the global USEC, since USEC is set to 0     by add\_BNT\_to\_path, even if the C files have already been compiled     in a previous session. Instead, gaussian\_CPD checks to     see if repmat\_and\_mult exists, and (bat1, chmm1, water1, water2)     check to see if jtree\_C\_inf\_engine/collect\_evidence exists.     Note that checking if a file exists is slow, so we do the check     inside the gaussian\_CPD constructor, not inside update\_ess.
  * uninstallC now deletes both .mex and .dll files, just in case I     accidently ship a .zip file with binaries.  It also deletes mex    files from jtree\_C\_inf\_engine.
  * Now marginal\_family for both jtree\_limid\_inf\_engine and 	    global\_joint\_inf\_engine returns a marginal structure and 	    potential, as required by solve\_limid.     Other engines (eg. jtree\_ndx, hmm) are not required to return a potential.**
**1/22/02
  * Added an optional argument to mk\_bnet and mk\_dbn which lets you add names to nodes. This uses the new assoc\_array class.
  * Added Yimin Zhang's (unfinished) classification/regression tree code to CPDs/tree\_CPD.**
**1/14/02
  * Incorporated some of Shan Huang's (still broken) stable CG code.**
**1/9/02
  * Yimin Zhang vectorized @discrete\_CPD/prob\_node, which speeds up structure learning considerably. I fixed this to handle softmax CPDs.
  * Shan Huang changed the stable conditional Gaussian code to handle vector-valued nodes, but it is buggy.
  * I vectorized @gaussian\_CPD/update\_ess for a special case.
  * Removed denom=min(1, ... Z) from gaussian\_CPD/maximize\_params (added to cope with negative temperature for entropic prior), which gives wrong results on mhmm1.**
**1/7/02
  * Removed the 'xo' typo from mk\_qmr\_bnet.
  * convert\_dbn\_CPDs\_to\_tables has been vectorized; it is now substantially faster to compute the conditional likelihood for long sequences.
  * Simplified constructors for tabular\_CPD and gaussian\_CPD, so they now both only take the form CPD(bnet, i, ...) for named arguments - the CPD('self', i, ...) format is gone. Modified mk\_fgraph\_given\_ev to use mk\_isolated\_tabular\_CPD instead.
  * Added entropic prior to tabular and Gaussian nodes. For tabular\_CPD, changed name of arguments to the constructor to distinguish Dirichlet and entropic priors. In particular, tabular\_CPD(bnet, i, 'prior', 2) is now tabular\_CPD(bnet, i, 'prior\_type', 'dirichlet', 'dirichlet\_weight', 2).
  * Added deterministic annealing to learn\_params\_dbn\_em for use with entropic priors. The old format learn(engine, cases, max\_iter) has been replaced by learn(engine, cases, 'max\_iter', max\_iter).
  * Changed examples/dynamic/bat1 and kjaerulff1, since default equivalence classes have changed from untied to tied.**
**12/30/01
  * DBN default equivalence classes for slice 2 has changed, so that now parameters are tied for nodes with 'equivalent' parents in slices 1 and 2 (e.g., observed leaf nodes). This essentially makes passing in the eclass arguments redundant (hooray!).**
**12/20/01
  ***Released version 4**. Version 4 is considered a major new release since it is not completely backwards compatible with V3. Observed nodes are now specified when the bnet/dbn is created, not when the engine is created. This changes the interface to many of the engines, making the code no longer backwards compatible. Hence support for non-named optional arguments (BNT2 style) has also been removed; hence mk\_dbn etc. requires arguments to be passed by name.
  * Ilya Shpitser's C code for triangulation now compiles under Windows as well as Unix, thanks to Wei Hu.
  * All the ndx engines have been combined, and now take an optional argument specifying what kind of index to use.
  * learn\_params\_dbn\_em is now more efficient: @tabular\_CPD/update\_ess for nodes whose families are hidden does not need need to call add\_evidence\_to\_dmarginal, which is slow.
  * Wei Hu fixed bug in jtree\_ndxD, so now the matlab and C versions both work.
  * dhmm\_inf\_engine replaces hmm\_inf\_engine, since the former can handle any kind of topology and is slightly more efficient. dhmm is extended to handle Gaussian, as well as discrete, observed nodes. The new hmm\_inf\_engine no longer supports online inference (which was broken anyway).
  * Added autoregressive HMM special case to hmm\_inf\_engine for speed.
  * jtree\_ndxSD\_dbn\_inf\_engine now computes likelihood of the evidence in a vectorized manner, where possible, just like hmm\_inf\_engine.
  * Added mk\_limid, and hence simplified mk\_bnet and mk\_dbn.
  * Gaussian\_CPD now uses 0.01\*I prior on covariance matrix by default. To do ML estimation, set 'cov\_prior\_weight' to 0.
  * Gaussian\_CPD and tabular\_CPD optional binary arguments are now set using 0/1 rather no 'no'/'yes'.
  * Removed Shan Huang's PDAG and decomposable graph code, which will be put in a separate structure learning library.**
**12/11/01
  * Wei Hu fixed jtree\_ndx**_dbn\_inf\_engine and marg\_table.c.
  * Shan Huang contributed his implementation of stable conditional Gaussian code (Lauritzen 1999), and methods to search through the space of PDAGs (Markov equivalent DAGs) and undirected decomposable graphs. The latter is still under development.
  12/10/01
  * Included Wei Hu's new versions of the ndx**routines, which use integers instead of doubles. The new versions are about 5 times faster in C. In general, ndxSD is the best choice.
  * Fixed misc/add\_ev\_to\_dmarginal so it works with the ndx routines in bat1.
  * Added calc\_mpe\_dbn to do Viterbi parsing.
  * Updated dhmm\_inf\_engine so it computes marginals.**
**11/23/01
  * learn\_params now does MAP estimation (i.e., uses Dirichlet prior, if define). Thanks to Simon Keizer skeizer@cs.utwente.nl for spotting this.
  * Changed plotgraph so it calls ghostview with the output of dotty, instead of converting from .ps to .tif. The resulting image is much easier to read.
  * Fixed cgpot/multiply\_by\_pots.m.
  * Wei Hu fixed ind2subv.c.
  * Changed arguments to compute\_joint\_pot.**
**11/1/01
  * Changed sparse to dense in @dpot/multiply\_pots, because sparse arrays apparently cause a bug in the NT version of Matlab.
  * Fixed the bug in gaussian\_CPD/log\_prob\_node.m which incorrectly called the vectorized gaussian\_prob with different means when there were continuous parents and more than one case. (Thanks to Dave Andre for finding this.)
  * Fixed the bug in root\_CPD/convert\_to\_pot which did not check for pot\_type='g'. (Thanks to Dave Andre for finding this.)
  * Changed calc\_mpe and calc\_mpe\_global so they now return a cell array.
  * Combine pearl and loopy\_pearl into a single inference engine called 'pearl\_inf\_engine', which now takes optional arguments passed in using the name/value pair syntax. marginal\_nodes/family now takes the optional add\_ev argument (same as jtree), which is the opposite of the previous shrink argument.
  * Created pearl\_unrolled\_dbn\_inf\_engine and "resurrected" pearl\_dbn\_inf\_engine in a simplified (but still broken!) form.
  * Wei Hi fixed the bug in ind2subv.c, so now ndxSD works. He also made C versions of ndxSD and ndxB, and added (the unfinished) ndxD.**
**10/20/01
  * Removed the use\_ndx option from jtree\_inf, and created 2 new inference engines: jtree\_ndxSD\_inf\_engine and jtree\_ndxB\_inf\_engine. The former stores 2 sets of indices for the small and difference domains; the latter stores 1 set of indices for the big domain. In Matlab, the ndxB version is often significantly faster than ndxSD and regular jree, except when the clique size is large. When compiled to C, the difference between ndxB and ndxSD (in terms of speed) vanishes; again, both are faster than compiled jtree, except when the clique size is large. Note: ndxSD currently has a bug in it, so it gives the wrong results! (The DBN analogs are jtree\_dbn\_ndxSD\_inf\_engine and jtree\_dbn\_ndxB\_inf\_engine.)
  * Removed duplicate files from the HMM and Kalman subdirectories. e.g., normalise is now only in BNT/misc, so when compiled to C, it masks the unique copy of the Matlab version.**
**10/17/01
  * Fixed bugs introduced on 10/15: Renamed extract\_gaussian\_CPD\_params\_given\_ev\_on\_dps.m to gaussian\_CPD\_params\_given\_dps.m since Matlab can't cope with such long names (this caused cg1 to fail). Fixed bug in gaussian\_CPD/convert\_to\_pot, which now calls convert\_to\_table in the discrete case.
  * Fixed bug in bk\_inf\_engine/marginal\_nodes. The test 'if nodes < ss' is now 'if nodes <= ss' (bug fix due to Stephen seg\_ma@hotmail.com)
  * Simplified uninstallC.**
**10/15/01
  * Added use\_ndx option to jtree\_inf and jtree\_dbn\_inf. This pre-computes indices for multiplying, dividing and marginalizing discrete potentials. This is like the old jtree\_fast\_inf\_engine, but we use an extra level of indirection to reduce the number of indices needed (see uid\_generator object). Sometimes this is faster than the original way... This is work in progress.
  * The constructor for dpot no longer calls myreshape, which is very slow. But new dpots still must call myones. Hence discrete potentials are only sometimes 1D vectors (but should always be thought of as multi-D arrays). This is work in progress.**
**10/6/01
  * Fixed jtree\_dbn\_inf\_engine, and added kjaerulff1 to test this.
  * Added option to jtree\_inf\_engine/marginal\_nodes to return "full sized" marginals, even on observed nodes.
  * Clustered BK in examples/dynamic/bat1 seems to be broken, so it has been commented out. BK will be re-implemented on top of jtree\_dbn, which should much more efficient.**
**9/25/01
  * jtree\_dbn\_inf\_engine is now more efficient than calling BK with clusters = exact, since it only uses the interface nodes, instead of all of them, to maintain the belief state.
  * Uninstalled the broken C version of strong\_elim\_order.
  * Changed order of arguments to unroll\_dbn\_topology, so that intra1 is no longer required.
  * Eliminated jtree\_onepass, which can be simulated by calling collect\_evidence on jtree.
  * online1 is no longer in the test\_BNT suite, since there is some problem with online prediction with mixtures of Gaussians using BK. This functionality is no longer supported, since doing it properly is too much work.**
**9/7/01
  * Added Ilya Shpitser's C triangulation code (43x faster!). Currently this only compiles under linux; windows support is being added.**
**9/5/01
  * Fixed typo in CPDs/@tabular\_kernel/convert\_to\_table (thanks, Philippe!)
  * Fixed problems with clamping nodes in tabular\_CPD, learn\_params, learn\_params\_tabular, and bayes\_update\_params. See BNT/examples/static/learn1 for a demo.**
**9/3/01
  * Fixed typo on line 87 of gaussian\_CPD which caused error in cg1.m
  * Installed Wei Hu's latest version of jtree\_C\_inf\_engine, which can now compute marginals on any clique/cluster.
  * Added Yair Weiss's code to compute the Bethe free energy approximation to the log likelihood in loopy\_pearl (still need to add this to belprop). The return arguments are now: engine, loglik and niter, which is different than before.**
**8/30/01
  * Fixed bug in BNT/examples/static/id1 which passed hard-coded directory name to belprop\_inf\_engine.
  * Changed tabular\_CPD and gaussian\_CPD so they can now be created without having to pass in a bnet.
  * Finished mk\_fgraph\_given\_ev. See the fg** files in examples/static for demos of factor graphs (work in progress).
  8/22/01
  * Removed jtree\_compiled\_inf\_engine, since the C code it generated was so big that it would barf on large models.
  * Tidied up the potentials/Tables directory. Removed mk\_marg/mult\_ndx.c, which have been superceded by the much faster mk\_marg/mult\_index.c (written by Wei Hu). Renamed the Matlab versions mk\_marginalise/multiply\_table\_ndx.m to be mk\_marg/mult\_index.m to be compatible with the C versions. Note: nobody calls these routines anymore! (jtree\_C\_inf\_engine/enter\_softev.c has them built-in.) Removed mk\_ndx.c, which was only used by jtree\_compiled. Removed mk\_cluster\_clq\_ndx.m, mk\_CPD\_clq\_ndx, and marginalise\_table.m which were not used. Moved shrink\_obs\_dims\_in\_table.m to misc.
  * In potentials/@dpot directory: removed multiply\_by\_pot\_C\_old.c. Now marginalize\_pot.c can handle maximization, and divide\_by\_pot.c has been implmented. marginalize/multiply/divide\_by\_pot.m no longer have useC or genops options. (To get the C versions, use installC.m)
  * Removed useC and genops options from jtree\_inf\_engine.m To use the C versions, install the C code.
  * Updated BNT/installC.m.
  * Added fclose to @loopy\_pearl\_inf/enter\_evidence.
  * Changes to MPE routines in BNT/general. The maximize parameter is now specified inside enter\_evidence instead of when the engine is created. Renamed calc\_mpe\_given\_inf\_engine to just calc\_mpe. Added Ron Zohar's optional fix to handle the case of ties. Now returns log-likelihood instead of likelihood. Added calc\_mpe\_global. Removed references to genops in calc\_mpe\_bucket.m Test file is now called mpe1.m
  * For DBN inference, filter argument is now passed by name, as is maximize. This is NOT BACKWARDS COMPATIBLE.
  * Removed @loopy\_dbn\_inf\_engine, which will was too complicated. In the future, a new version, which applies static loopy to the unrolled DBN, will be provided.
  * discrete\_CPD class now contains the family sizes and supports the method dom\_sizes. This is because it could not access the child field CPD.sizes, and mysize(CPT) may give the wrong answer.
  * Removed all functions of the form CPD\_to\_xxx, where xxx = dpot, cpot, cgpot, table, tables.  These have been replaced by convert\_to\_pot, which takes a pot\_type argument. @discrete\_CPD calls convert\_to\_table to implement a default convert\_to\_pot. @discrete\_CPD calls CPD\_to\_CPT to implement a default convert\_to\_table. The convert\_to\_xxx routines take fewer arguments (no need to pass in the globals node\_sizes and cnodes!). Eventually, convert\_to\_xxx will be vectorized, so it will operate on all nodes in the same equivalence class "simultaneously", which should be significantly quicker, at least for Gaussians.
  * Changed discrete\_CPD/sample\_node and prob\_node to use convert\_to\_table, instead of CPD\_to\_CPT, so mlp/softmax nodes can benefit.
  * Removed @tabular\_CPD/compute\_lambda\_msg\_fast and private/prod\_CPD\_and\_pi\_msgs\_fast, since no one called them.
  * Renamed compute\_MLE to learn\_params, by analogy with bayes\_update\_params (also because it may compute an MAP estimate).
  * Renamed set\_params to set\_fields and get\_params to get\_field for CPD and dpot objects, to avoid confusion with the parameters of the CPD.
  * Removed inference/doc, which has been superceded by the web page.
  * Removed inference/static/@stab\_cond\_gauss\_inf\_engine, which is broken, and all references to stable CG.
  8/12/01
  * I removed potentials/@dpot/marginalize\_pot\_max. Now marginalize\_pot for all potential classes take an optional third argument, specifying whether to sum out or max out. The dpot class also takes in optional arguments specifying whether to use C or genops (the global variable USE\_GENOPS has been eliminated).
  * potentials/@dpot/marginalize\_pot has been simplified by assuming that 'onto' is always in ascending order (i.e., we remove Maynard-Reid's patch). This is to keep the code identical to the C version and the other class implementations.
  * Added Ron Zohar's general/calc\_mpe\_bucket function, and my general/calc\_mpe\_given\_inf\_engine, for calculating the most probable explanation.
  * Added Wei Hu's jtree\_C\_inf\_engine. enter\_softev.c is about 2 times faster than enter\_soft\_evidence.m.
  * Added the latest version of jtree\_compiled\_inf\_engine by Wei Hu. The 'C' ndx\_method now calls potentials/Tables/mk\_marg/mult\_index, and the 'oldC' ndx\_method calls potentials/Tables/mk\_marg/mult\_ndx.
  * Added potentials/@dpot/marginalize\_pot\_C.c and multiply\_by\_pot\_C.c by Wei Hu. These can be called by setting the 'useC' argument in jtree\_inf\_engine.
  * Added BNT/installC.m to compile all the mex files.
  * Renamed prob\_fully\_instantiated\_bnet to log\_lik\_complete.
  * Added Shan Huang's unfinished stable conditional Gaussian inference routines.
  7/13/01
  * Added the latest version of jtree\_compiled\_inf\_engine by Wei Hu.
  * Added the genops class by Doug Schwarz (see BNT/genopsfun/README). This provides a 1-2x speed-up of potentials/@dpot/multiply\_by\_pot and divide\_by\_pot.
  * The function BNT/examples/static/qmr\_compiled compares the performance gains of these new functions.
  7/6/01
  * Made bk\_inf\_engine use the name/value argument syntax. This can now do max-product (Viterbi) as well as sum-product (forward-backward).
  * Changed examples/static/mfa1 to use the new name/value argument syntax.
  6/28/01
  * **Released version 3**. Version 3 is considered a major new release since it is not completely backwards compatible with V2. V3 supports decision and utility nodes, loopy belief propagation on general graphs (including undirected), structure learning for non-tabular nodes, a simplified way of handling optional arguments to functions, and many other features which are described below. In addition, the documentation has been substantially rewritten.
  * The following functions can now take optional arguments specified as name/value pairs, instead of passing arguments in a fixed order: mk\_bnet, jtree\_inf\_engine, tabular\_CPD, gaussian\_CPD, softmax\_CPD, mlp\_CPD, enter\_evidence. This is very helpful if you want to use default values for most parameters. The functions remain backwards compatible with BNT2.
  * dsoftmax\_CPD has been renamed softmax\_CPD, replacing the older version of softmax. The directory netlab2 has been updated, and contains weighted versions of some of the learning routines in netlab. (This code is still being developed by P. Brutti.)
  * The "fast" versions of the inference engines, which generated matlab code, have been removed. @jtree\_compiled\_inf\_engine now generates C code. (This feature is currently being developed by Wei Hu of Intel (China), and is not yet ready for public use.)
  * CPD\_to\_dpot, CPD\_to\_cpot, CPD\_to\_cgpot and CPD\_to\_upot are in the process of being replaced by convert\_to\_pot.
  * determine\_pot\_type now takes as arguments (bnet, onodes) instead of (onodes, cnodes, dag), so it can detect the presence of utility nodes as well as continuous nodes. Hence this function is not backwards compatible with BNT2.
  * The structure learning code (K2, mcmc) now works with any node type, not just tabular. mk\_bnets\_tabular has been eliminated. bic\_score\_family and dirichlet\_score\_family will be replaced by score\_family. Note: learn\_struct\_mcmc has a new interface that is not backwards compatible with BNT2.
  * update\_params\_complete has been renamed bayes\_update\_params. Also, learn\_params\_tabular has been replaced by learn\_params, which works for any CPD type.
  * Added decision/utility nodes.
  6/6/01
  * Added soft evidence to jtree\_inf\_engine.
  * Changed the documentation slightly (added soft evidence and parameter tying, and separated parameter and structure learning).
  * Changed the parameters of determine\_pot\_type, so it no longer needs to be passed a DAG argument.
  * Fixed parameter tying in mk\_bnet (num. CPDs now equals num. equiv classes).
  * Made learn\_struct\_mcmc work in matlab version 5.2 (thanks to Nimrod Megiddo for finding this bug).
  * Made 'acyclic.m' work for undirected graphs.
  5/23/01
  * Added Tamar Kushnir's code for the IC**algorithm (learn\_struct\_pdag\_ic\_star). This learns the structure of a PDAG, and can identify the presence of latent variables.
  * Added Yair Weiss's code for computing the MAP assignment using junction tree (i.e., a new method called @dpot/marginalize\_pot\_max instead of marginalize\_pot.)
  * Added @discrete\_CPD/prob\_node in addition to log\_prob\_node to handle deterministic CPDs.**
**5/12/01
  * Pierpaolo Brutti updated his mlp and dsoftmax CPD classes, and improved the HME code.
  * HME example now added to web page. (The previous example was non-hierarchical.)
  * Philippe Leray (author of the French documentation for BNT) pointed out that I was including netlab.tar unnecessarily.**
**5/4/01
  * Added mlp\_CPD which defines a CPD as a (conditional) multi-layer perceptron. This class was written by Pierpaolo Brutti.
  * Added hierarchical mixtures of experts demo (due to Pierpaolo Brutti).
  * Fixed some bugs in dsoftmax\_CPD.
  * Now the BNT distribution includes the whole [Netlab](Netlab.md) library in a subdirectory. It also includes my HMM and Kalman filter toolboxes, instead of just fragments of them.**
**5/2/01
  * gaussian\_inf\_engine/enter\_evidence now correctly returns the loglik, even if all nodes are instantiated (bug fix due to Michael Robert James).
  * Added dsoftmax\_CPD which allows softmax nodes to have discrete and continuous parents; the discrete parents act as indices into the parameters for the continuous node, by analogy with conditional Gaussian nodes. This class was written by Pierpaolo Brutti.**
**3/27/01
  * learn\_struct\_mcmc  no longer returns sampled\_bitv.
  * Added mcmc\_sample\_to\_hist to post-process the set of samples.**
**3/21/01
  * Changed license from UC to GNU Library GPL.
  * Made all CPD constructors accept 0 arguments, so now bnets can be saved to and loaded from files.
  * Improved the implementation of sequential and batch Bayesian parameter learning for tabular CPDs with completely observed data (see log\_marg\_lik\_complete and update\_params\_complete). This code also handles interventional data.
  * Added MCMC structure learning for completely observed, discrete, static BNs.
  * Started implementing Bayesian estimation of linear Gaussian nodes. See root\_gaussian\_CPD and linear\_gaussian\_CPD. The old gaussian\_CPD class has not been changed.
  * Renamed evaluate\_CPD to log\_prob\_node, and simplified its arguments.
  * Renamed sample\_CPD to sample\_node, simplified its arguments, and vectorized it.
  * Renamed "learn\_params\_tabular" to "update\_params\_complete". This does Bayesian updating, but no longer computes the BIC score.
  * Made routines for completely observed networks (sampling, complete data likelihood, etc.) handle cell arrays or regular arrays, which are faster. If some nodes are not scalars, or are hidden, you must use cell arrays. You must convert to a cell array before passing to an inference routine.
  * Fixed bug in gaussian\_CPD constructor. When creating CPD with more than 1 discrete parent with random parameters, the matrices were the wrong shape (Bug fix due to Xuejing Sun).**
**11/24/00
  * Renamed learn\_params and learn\_params\_dbn to learn\_params\_em/ learn\_params\_dbn\_em. The return arguments are now [bnet, LLtrace, engine] instead of [engine, LLtrace].
  * Added structure learning code for static nets (K2, PC).
  * Renamed learn\_struct\_inter\_full\_obs as learn\_struct\_dbn\_reveal, and reimplemented it to make it simpler and faster.
  * Added sequential Bayesian parameter learning (learn\_params\_tabular).
  * Major rewrite of the documentation.**
**5/22/00
  * Added online filtering and prediction.
  * Added the factored frontier and loopy\_dbn algorithms.
  * Separated the online user manual into two, for static and dynamic networks.
  * Added a counter to the BNT web page.**
**4/27/00
  * Fixed the typo in bat1.m
  * Added preliminary code for online inference in DBNs
  * Added coupled HMM example**
**4/23/00
  * Fixed the bug in the fast inference routines where the indices are empty (arises in bat1.m).
  * Sped up marginal\_family for the fast engines by precomputing indices.**
**4/17/00
  * Simplified implementation of BK\_inf\_engine by using soft evidence.
  * Added jtree\_onepass\_inf\_engine (which computes a single marginal) and modified jtree\_dbn\_fast to use it.**
**4/14/00
  * Added fast versions of jtree and BK, which are designed for models where the division into hidden/observed is fixed, and all hidden variables are discrete. These routines are 2-3 times faster than their non-fast counterparts.
  * Added graph drawing code contributed by Ali Taylan Cemgil from the University of Nijmegen.**
**4/10/00
  * Distinguished cnodes and cnodes\_slice in DBNs so that kalman1 works with BK.
  * Removed dependence on cellfun (which only exists in matlab 5.3) by adding isemptycell. Now the code works in 5.2.
  * Changed the UC copyright notice.**
**3/29/00
  ***Released BNT 2.0**, now with objects! Here are the major changes.
  * There are now 3 classes of objects in BNT: Conditional Probability Distributions, potentials (for junction tree), and inference engines. Making an inference algorithm (junction tree, sampling, loopy belief propagation, etc.) an object might seem counter-intuitive, but in fact turns out to be a good idea, since the code and documentation can be made modular. (In Java, each algorithm would be a class that implements the inferenceEngine interface. Since Matlab doesn't support interfaces, inferenceEngine is an abstract (virtual) base class.)
  * In version 1, instead of Matlab's built-in objects, I used structs and a   simulated dispatch mechanism based on the type-tag system in the   classic textbook by Abelson   and Sussman ("Structure and Interpretation of Computer Programs",   MIT Press, 1985). This required editing the dispatcher every time a   new object type was added. It also required unique (and hence long)   names for each method, and allowed the user unrestricted access to   the internal state of objects.
  * The Bayes net itself is now a lightweight struct, and can be used to specify a model independently of the inference algorithm used to process it. In version 1, the inference engine was stored inside the Bayes net.**
**11/24/99
  * Added fixed lag smoothing, online EM and the ability to learn switching HMMs (POMDPs) to the HMM toolbox.
  * Renamed the HMM toolbox function 'mk\_dhmm\_obs\_mat' to 'mk\_dhmm\_obs\_lik', and similarly for ghmm and mhmm. Updated references to these functions in BNT.
  * Changed the order of return params from kalman\_filter to make it more natural. Updated references to this function in BNT.**
**10/27/99
  * Fixed line 42 of potential/cg/marginalize\_cgpot and lines 32-39 of bnet/add\_evidence\_to\_marginal (thanks to Rainer Deventer for spotting these bugs!)**
**10/21/99
  * Completely changed the blockmatrix class to make its semantics more sensible. The constructor is not backwards compatible!**
**10/6/99
  * Fixed all\_vals = cat(1, vals{:}) in user/enter\_evidence
  * Vectorized ind2subv and sub2indv and removed the C versions.
  * Made mk\_CPT\_from\_mux\_node much faster by having it call vectorized ind2subv
  * Added Sondhauss's bug fix to line 68 of bnet/add\_evidence\_to\_marginal
  * In dbn/update\_belief\_state, instead of adding eps to likelihood if 0, we leave it at 0, and set the scale factor to 0 instead of dividing.**
**8/19/99
  * Added Ghahramani's mfa code to examples directory to compare with fa1, which uses BNT
  * Changed all references of assoc to stringmatch (e.g., in examples/mk\_bat\_topology)**
**June 1999
  ***Released BNT 1.0**on the web.**
**August 1998
  ***Released BNT 0.0**via email.**
**October 1997
  * First started working on Matlab version of BNT.**
**Summer 1997
  * First started working on C++ version of BNT while working at DEC (now Compaq) CRL.**_

# Subset-Sum-Problem
Solving the subset-sum problem using Grover's Algorithm.

This notebook solves the subset-sum problem by combining a classical check with Grover-style quantum amplitude amplification.  
Given a set $S$ of cardinality $n \ge 0$ (given as a list), and target $t$, it first classically finds all subsets whose sum equals $t$ and encodes those solutions as bitstrings. 

The oracle circuit then marks the valid bitstrings by applying a phase flip, so “good” states are distinguishable in phase.

A diffuser circuit reflects amplitudes about the mean, which increases probability of marked states and suppresses unmarked ones.  

The algorithm prepares a uniform superposition over all subset bitstrings, then alternates oracle and diffuser for an approximately optimal number of iterations.  

That iteration count is computed from the standard Grover formula based on $N = 2^n$ search states.  

After amplification, the circuit is evaluated (statevector and/or sampled counts) to show which bitstrings are most likely outcomes.  

Those high-probability bitstrings are mapped back to actual subsets of S, giving the candidate solutions for the target sum.

The code also handles edge cases like empty input and provides outputs that make it easy to see both valid subsets and their quantum probabilities.

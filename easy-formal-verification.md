# Formal Verification Made Easy (and fast!) - Daniel Bristot de Oliveira, Red Hat

Linux is:

* critical
* complex

We need to be sure that Linux *behaves as expected*

## What do we expect?

* Documentation
* Lots of "ifs"

These things are good, but we need something more *robust*

E.g.:

* Is our reasoning right?
* Are our asserts contradictory?
* Are we covering all cases?

## How do we convince other communities of our properties?

What do computer scientists say about it?

* Formal methods

Some successful examples, but we need a more *generic* and *intuitive* way for modeling

## How to make easier?

We trace events!

While tracing we create state-machines

## Automata

* State-machines + FM = Automata!
* Using automata as a formal language
* Automata is a method to model *discrete event systems (DES)*
* Generators
* Sync of generators: All states & Events
* Specification
* Verification
* Sync of generators and specifications
* Why not just draw it?
  ** Linux is complex

`PREEMPT_RT` model:

* 9017 states
* 23103 transitions
* But:
  ** 12 generators
  ** 33 specifications
* During dev found 3 bugs not detectable by other tools

More complex case:

* process state
* Necessary conditions
* Properties
* Sufficient conditions
* Conclusion: `PREEMPT_RT` scheduler is deterministic

## Verifying system *behaves*?

Offline Run-time Verification

* Compare model with actual measurements
* Found logical correctness bugs

What can we do?

Code generation
  ** Transforms formal model into C code

Automaton in C

Processing one event

Verification: compile as kernel model

Error output

Practical example: bug in tracing system

Price is in the data structure

In practice we don't need full model to check certain properties

Efficiency in practice: a benchmark

* More overhead than no tracing, but
* Less overhead than tracing
* Efficient enough to verify in production

**Academically accepted!**

## Takeaways

## Next?

Better I/F

* perf / ebpf version of runtime verification
* ftrace-like interface
* ...

## What to model?

* Locking
* RCU
* Schedulers

## Worth mentioning

This is *not* the only *nor* the best way


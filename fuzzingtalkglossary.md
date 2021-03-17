## CS 669, Project 6: Research Presentation

_I often forget which term means which halfway into a talk and wish I had a term sheet or glossary to check. 
We'll try this out for this research presentation and see if this is useful to others._

## Fuzzing Glossary 
* Target program - program undergoing fuzz testing
* Driver - glue/translator program between the fuzzer and target program. Does not 'belong' to either the fuzzer or the target. There is an art to these.

* Iteration - a single repetition of the fuzzing algorithm
* Run - a series of iterations from start to finish
* Campaign - a series of identical fuzzing runs

* Seed - input to the target program
* Seed corpus - set of seeds in a context. For example, the seed corpus of the nth iteration or the overall seed corpus of the run.
* Initial seed corpus, initial corpus - seed corpus of the initial iteration. May be optional and/or supplied by the user.

* Mutational fuzzers - mutate promising old seeds into new seeds each iteration (AFL)
* Generational fuzzers - generate new seeds each iteration, usually ignoring prior seeds (Skyfire)
* Coverage-based fuzzers - define ‘interesting’ as an increase in fuzzers (AFL)
* Directed fuzzers - define ‘interesting’ as proximity to a desired point in the target program (AFLGo)

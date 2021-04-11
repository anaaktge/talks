## CS 669, Project 6: Research Presentation, Introduction to Fuzzing Talks

_I often forget which term means which halfway into a talk outside my area and wish I had a term sheet or glossary to check._

## Fuzzing Glossary

Fuzzing, also called Fuzz Testing, is a stochastic, dynamic software-testing technique. It tries to (intelligently) thoroughly explore the input space of a target program, searching for inputs to the program that cause it to exhibit ‘interesting’ behavior. Exactly what constitutes ‘interesting’ varies widely and is subject to interpretation.

### Programs Involved
* Target program - program undergoing fuzz testing. Sometimes called the victim program.
* Driver - optional glue/translator program between the fuzzer and target program. Does not 'belong' to either the fuzzer or the target. Also called a harness. There is an art to these.
* Fuzzer - program (may be several combined) responsible for fuzzing the target program.

### Repetitions
* Iteration - a single repetition of the fuzzing algorithm
* Run - a series of iterations from start to finish
* Campaign - a series of identical fuzzing runs

### Inputs to Target Programs
* Seed - input to the target program. Often one file = one input = one seed.
* Seed corpus - set of seeds in a context. For example, the seed corpus of the nth iteration or the overall seed corpus of the run.
* Initial seed corpus, initial corpus - seed corpus of the initial iteration. May be optional and is usually supplied by the user before the fuzzer starts.

### Fuzzing Taxnomy: What's this one do again? 
#### Where Seeds Originate 
* Not mutually exclusive. Some algorithms use a bit of everything.
* Mutational fuzzers - mutate promising old seeds from previous interation into new seeds for each new iteration.
* Generational fuzzers - generate new seeds each iteration, usually ignoring prior seeds. Grammar and protocol fuzzers often have generational components. 
* Naive, classic, random fuzzers - new seeds are pulled from random number generators, or dev/random. May be viewed as not having a seed corpus. 

#### Defining Interesting Behavior 
* Coverage-based fuzzers - define ‘interesting’ as an increase in code coverage, the amount of code exercised as measured by instrumented code points. Note that this may not include information on program flow. It can be thought of as a series of tuples, a graph, or a heatmap depending on the sophiscation of the code coverage algorithm. 
* Directed fuzzers - define ‘interesting’ as proximity to a desired point in the target program.
* Naive, classic, random fuzzers - use a source of randomness, such as a random number generator, to produce new values. 
* Crashes are generally considered interesting.
* Taint Analysis. Also called taint tracking or taint checking. When used in fuzzers, tries to figure out if a source (user controlled input) can reach a sink of sensitive data (such as a password or uid).

#### Knowledge of Target Program
* Whitebox - traditionally have source, which you can JIT/compile to graybox (greybox depending on your region) or black box if you have the source
* Graybox, Greybox - an instrumented binary. Usually requires access to the source since the insturmentation is generally not part of the usual compilation process. 
* Blackbox - no source, only a binary, which has usually been heavily optimized.  

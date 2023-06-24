Valgrind is a programming tool used for memory debugging, leak detection and profiling. 
The use of this tool is essential when working with large code bases.

# Some useful tools:
* Memcheck: memory error detector.
* Cachegrind: cache and branch-prediction profiler (Makes programs faster).
* Call grind: call-graph generating profiler (gathers some info cachegrind does not)
* Helgrind: thread error detector.
* DRD: thread error detector.
* Massif: heap profiler. Helps understand issues of block lifetimes, utilisation etc.
* DHAT: different heap profiler.
* BBV: experimental SimPoint basic block vector generator.

# Notes
Notes for technical issues

## 1. Stream
* Steams differ from collections:
  * Functional in nature. A stream is not a data structure that stores elements but doesn't modify its source.<br/>
    EX: filtering a stream obtained from a collection produces a new stream without the filtered elements, rather than removing elements.
  * Laziness-seeking.
* Can be obtained:
  * From a Collection via the stream() and paralleStram().
  * From an array via Arrays.stram(Object[]);
  * From static factory methods on the stram classes, such as Stream.of(Object[]).
  * The lines of a file can be obtained from BufferedReader.lines();
  * Numerous other stream-bearing methods in the JDK, including BitSet.stream(), Pattern.splitAsStream(java.lang.CharSequence), and JarFile.stream().
* Operations
  * Intermediate operations: <br/>
    EX: Stream.filter or Stream.map<br/>
    Return a new stream, lazy, executing an intermediate operation such as filter() does not actually perform any filtering, but instead creates a new stream that, when traversed, contains the elements of the initial stream that match the given predicate.<br/>
    *Traversal of the pipeline source does not begin until the terminal operation of the pipeline is executed.*
    * Stateless operations<br/>
    Pipelines containing exclusively stateless intermediate operations can be processed in a single pass.
    * Stateful operations
  * Terminal operations: <br/>
    EX: Stream.forEach or Stream.reduce<br/>
    Traverse the stream to produce a result or a side-effect.<br/>
    In almost all cases, terminal operations are eager, completing their traversal of the data source and processing of the pipeline before returning.
  * Processing streams lazily<br/>
    Operations can be fused into a single pass on the data, with minimal intermediate state.<br/>
    Allows avoiding examining all the data when it is not necessary.
* Parallelism
  All streams operations can execute either in serial or in parallel. The stream implementations in the JDK create serial streams unless parallelism is explicitly requested. <br/>
  Collection has methods Collection.stream() and Collection.parallelStream(), which produce sequential and parallel streams respectively.<br/>
  When the terminal operation is initiated, the stream pipeline is executed sequentially or in parallel depending on the mode of the stream on which it is invoked.

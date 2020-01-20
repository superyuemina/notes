## notes
Notes for technical issues

# 1. Stream
* Steams differ from collections:
  * Functional in nature. A stream is not a data structure that stores elements but doesn't modify its source.
    EX: filtering a stream obtained from a collection produces a new stream without the filtered elements, rather than removing elements.
  * Laziness-seeking.
* Can be obtained:
  * From a Collection via the stream() and paralleStram().
  * From an array via Arrays.stram(Object[]);


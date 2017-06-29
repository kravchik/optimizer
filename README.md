## Disclaimer
It is a library for automatic code optimization. Currently, it is best suited for math algorithm optimization: matrix, and vector math, for example. It can optimize Java and CSharp code and can easily be extended to any new language.

## Optimization
### write simple code -> run effective code

*TODO motivation*

For example, we have matrix multiplication. Straightforward mathematic algorithm independent of constants:
```java
    void multiply(int w, int h, float[] ab, float[] a, float[] b) {
        for (int i = 1; i <= w; i++) {
            for (int j = 1; j <= h; j++) {
                float r = 0;
                for (int k = 1; k <= h; k++) r += get(w, a, i, k) * get(w, b, k, j);
                set(w, ab, i, j, r);
            }
        }
    }
```
Then we want to use it:
```java
    void multiply33(float[] ab, float[] a, float[] b) {
        multiply(3, 3, ab, a, b);
    }
```
If we run optimization on it, we will get a highly optimized code, ready to be part of any utility library:
```java
    void multiply33Optimized(float[] ab, float[] a, float[] b) {
        ab[0] = a[0] * b[0] + a[1] * b[3] + a[2] * b[6];
        ab[1] = a[0] * b[1] + a[1] * b[4] + a[2] * b[7];
        ab[2] = a[0] * b[2] + a[1] * b[5] + a[2] * b[8];
        ab[3] = a[3] * b[0] + a[4] * b[3] + a[5] * b[6];
        ab[4] = a[3] * b[1] + a[4] * b[4] + a[5] * b[7];
        ab[5] = a[3] * b[2] + a[4] * b[5] + a[5] * b[8];
        ab[6] = a[6] * b[0] + a[7] * b[3] + a[8] * b[6];
        ab[7] = a[6] * b[1] + a[7] * b[4] + a[8] * b[7];
        ab[8] = a[6] * b[2] + a[7] * b[5] + a[8] * b[8];
    }
```

### object inline
In Java, you can have algorithms dependent on many small objects (Vectors, Matrices). Although there is a JIT, you can not always rely on it: it can miss some possible optimizations, it took time to warm up. So, in some cases (library methods, for example, or hot code) - you want just to make these optimizations in advance and leave JIT to deal with other parts of a code.
```java
  //TODO
```

## Current features
* Optimization of Java and CSarp code
  * constants calculation
  * cycle unroll
  * method inline
  * object inline
* Code conversion Java <-> CSarp

## Current plans/todos
- add support for all the rare features of Java and CSharp (i.e., features, and syntax I don't see in my current tasks)
- Python parser/generator (optimization/conversion toolset will be available automatically, as it's language independent)
- C++ code generator

## State of the project
It is currently in a dormant mode. I'm using it for my projects, and add features as needed. If you are interested in it - e-mail me.

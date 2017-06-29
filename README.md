## Welcome to GitHub Pages

## Disclaimer
Tool for automatic code optimization. Currently, it is best suited for math algorithm optimization: matrix, and vector math, for example.

## Optimization
### unroll cycles
   code examples
### calculate constants
   code examples
### inline methods, and objects
   code examples
### write simple code -> run effective code
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


## Current features
- Optimization of Java code
- Optimization of CSharp code
- Code conversion Java <-> CSarp

## Current plans/todos
- add support for all the rare features of Java and CSharp (i.e., features, and syntax I don't see in my current tasks)
- Python parser/generator (optimization/conversion toolset will be available automatically, as it's language independent)
- C++ code generator

## State of the project
It is currently in a dormant mode. I'm using it for my projects, and add features as needed. If you are interested in it - e-mail me.




# ========= TODO cut here ============

You can use the [editor on GitHub](https://github.com/kravchik/optimizer/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/kravchik/optimizer/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.

# Eigenvalues and Eigenvectors

So, when we talk about matrices, they represent linear transformations – things like rotations, scaling, or shearing of vectors.  
Think of it like stretching or twisting space. Now, eigenvectors are special vectors that don't change direction when this transformation happens; they only get scaled.

## Definition

### Eigenvectors: The Vectors That Don’t Rotate

An eigenvector is a vector that, after being transformed by a matrix, remains on the same line it started on. 
It just gets stretched or compressed.  It’s like a ‘special’ direction within the space that the transformation doesn't rotate.

### Eigenvalues: The Scaling Factor

The eigenvalue is the factor by which the eigenvector is scaled during the transformation. 
If the eigenvalue is **2**, the eigenvector gets stretched by a factor of **2**.  
If it’s **0.5**, it's compressed to half its original length.

### The Equation: How They Relate

The relationship between them is defined by this equation:

```
A * v = λ * v
```

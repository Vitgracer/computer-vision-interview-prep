# Self-Attention vs Cross-Attention

## Self-Attention
**Who looks at whom:** all tokens look at each other within the same set.  

**Input:** a single set of vectors (e.g., words in a sentence or frames in a video).  
The model learns to identify relationships between elements in one sequence.  

**Example:**  
You have the phrase “The cat eats fish.”  
Self-attention allows the word **“eats”** to look at **“cat”** and **“fish”** to understand the meaning.  

**Formula:**  
```
Q, K, V ← the same set of tokens
Attention = softmax(QKᵀ / √d) V
```

---

## Cross-Attention
**Who looks at whom:** tokens from one set (queries) look at tokens from another set (keys/values).  

**Input:** two different sets of vectors (e.g., text and image).  

Used to **mix information across modalities**.  

**Example:**  
You have the text “What is the cat doing?” and an image of a cat eating fish.  
Cross-attention allows text tokens to look at visual features from the image.  

**Formula:**  
```
Q ← tokens from set A (e.g., text)
K, V ← tokens from set B (e.g., image)
Attention = softmax(QKᵀ / √d) V
```
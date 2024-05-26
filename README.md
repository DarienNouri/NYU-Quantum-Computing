# Quantum Computing Project

Repo contains files related to Special Topics in Quantum Computing course.

## Files

- [elitzur-vaidman-bomb-detector.ipynb](elitzur-vaidman-bomb-detector.ipynb): This Jupyter notebook contains the implementation and explanation of the Elitzur-Vaidman bomb detector.

- [quantum-game-strategy.ipynb](quantum-game-strategy.ipynb): This Jupyter notebook explores strategies for quantum games.

- [basis-measurment-proofs.ipynb](basis-measurment-proofs.ipynb): This Jupyter notebook contains proofs related to basis measurements in quantum computing.



### Project Paper

The final project paper can be viewed [here](final_project_paper.pdf). 



### Proofs

Single Qubit Hadamard (Base Case):
$$H =  \frac{1}{\sqrt{2}} (|0\rangle\langle0| + |0\rangle\langle1| + |1\rangle\langle0| - |1\rangle\langle1|)$$

Inductive Hypothesis (n-1 qubits):

$$H^{\otimes (n-1)} = \frac{1}{\sqrt{2^{n-1}}} \sum_{x,y \in \{0,1\}^{n-1}} (-1)^{x \cdot y} |x\rangle\langle y|$$

Inductive Step (Expansion):

$$H^{\otimes n} = \frac{1}{\sqrt{2^{n}}} \sum_{x,y \in \{0,1\}^{n-1}} (-1)^{x \cdot y} [
     \\ (|x\rangle\otimes|0\rangle)\langle y|\otimes\langle0| + \\
     (|x\rangle\otimes|0\rangle)\langle y|\otimes\langle1| + \\
     (|x\rangle\otimes|1\rangle)\langle y|\otimes\langle0| - \\
     (|x\rangle\otimes|1\rangle)\langle y|\otimes\langle1| ]$$

Final Form (n qubits):
$$H^{\otimes n} = \frac{1}{\sqrt{2^n}} \sum_{x,y \in \{0,1\}^n} (-1)^{x \cdot y} |x\rangle\langle y|$$



## Proof of Orthonormal Basis for $C^{de}$

Here is a proof that for any orthonormal bases $\{\vert u_1 \rangle, \ldots, \vert u_d \rangle\}$ of $C^d$ and $\{\vert v_1 \rangle, \ldots, \vert v_e \rangle\}$ of $C^e$, the set $\{\vert u_i \rangle \otimes \vert v_j \rangle : i \in [d], j \in [e]\}$ is an orthonormal basis for $C^{de}$:

### Basis Span

**First**, we need to show that the set $\{\vert u_i \rangle \otimes \vert v_j \rangle : i \in [d], j \in [e]\}$ spans $C^{de}$. Any vector in $C^{de}$ can be written as a linear combination of basis vectors, i.e.,

$$
\vert \psi \rangle = \sum_{i,j} c_{ij} \vert u_i \rangle \otimes \vert v_j \rangle,
$$

where $c_{ij}$ are complex coefficients. To see this, note that any state in $C^{de}$ can be written as a linear combination of computational basis states,

$$
\vert \psi \rangle = \sum_{x,y} c_{xy} \vert x \rangle \otimes \vert y \rangle,
$$

where x and y range over all bit strings of length d and e, respectively. We can then rewrite each $\vert x \rangle \otimes \vert y \rangle$ as a linear combination of the basis vectors $\{\vert u_i \rangle \otimes \vert v_j \rangle\}$ using the following identity:

$$
\vert x \rangle \otimes \vert y \rangle = \left(\sum_i \alpha_i \vert u_i \rangle\right) \otimes \left(\sum_j \beta_j \vert v_j \rangle\right) = \sum_{i,j} \alpha_i \beta_j \vert u_i \rangle \otimes \vert v_j \rangle,
$$

where $\alpha_i$ and $\beta_j$ are complex coefficients determined by the bit strings x and y. This shows that any vector in $C^{de}$ can be expressed as a linear combination of $\{\vert u_i \rangle \otimes \vert v_j \rangle\}$ vectors, proving that the set spans $C^{de}$.

### Orthonormality

**Next**, we need to show that the basis vectors are orthonormal. For any two distinct basis vectors $\vert u_i \rangle \otimes \vert v_j \rangle$ and $\vert u_k \rangle \otimes \vert v_l \rangle$, their inner product is given by:

$$
\langle u_i \vert \otimes \langle v_j \vert (\vert u_k \rangle \otimes \vert v_l \rangle) = \langle u_i \vert u_k \rangle \langle v_j \vert v_l \rangle.
$$
Since
$\{\vert u_i \rangle\}$ and $\{\vert v_j \rangle\}$ are orthonormal bases, $\langle u_i \vert u_k \rangle = \delta_{ik}$ and $\langle v_j \vert v_l \rangle = \delta_{jl}$, where $\delta_{ij}$ is the Kronecker delta function. Therefore, the inner product becomes:


$$
\delta_{ik} \delta_{jl} =
\begin{cases}
1, & \text{if } i = k \text{ and } j = l, \\
0, & \text{otherwise}.
\end{cases}
$$

This shows that the basis vectors are orthonormal, as their inner product is 1 only when they are the same vector and 0 otherwise.

### Conclusion

We have shown that the set $\{\vert u_i \rangle \otimes \vert v_j \rangle : i \in [d], j \in [e]\}$ spans $C^{de}$ and that the basis vectors are orthonormal. Therefore, this set forms an orthonormal basis for $C^{de}$.

_Note: This proof relies on the properties of orthonormal bases, including the fact that they span the vector space and their inner product is 0 for distinct basis vectors. These properties are proven in standard linear algebra textbooks and are assumed to be known in this context._


## Theorem and Proof

### Theorem:

Let $\vert u_{\theta} \rangle = \frac{1}{\sqrt{2}}(\vert 0 \rangle + e^{i\theta}\vert 1 \rangle)$ for $\theta \in [0, 2\pi)$. There is a basis $\vert \uparrow \rangle, \vert \downarrow \rangle$ such that measuring the state $\vert u_{\theta} \rangle$ in this basis yields outcome $\uparrow$ with probability 1, and for any $\phi \neq \theta \in [0, 2\pi)$, measuring the state $\vert u_{\phi} \rangle$ in this basis yields outcome $\uparrow$ with probability strictly less than 1.

### Proof:

1. **Define the basis $\vert \uparrow \rangle, \vert \downarrow \rangle$:**
    - $\vert \uparrow \rangle = \frac{1}{\sqrt{2}}(\vert 0 \rangle + \vert 1 \rangle)$
    - $\vert \downarrow \rangle = \frac{1}{\sqrt{2}}(\vert 0 \rangle - \vert 1 \rangle)$

2. **Calculate the probability of measuring $\uparrow$ when the state is $\vert u_{\theta} \rangle$:**
    - $\langle u_{\theta} \vert \uparrow \rangle = \langle u_{\theta} \vert \frac{1}{\sqrt{2}}(\vert 0 \rangle + \vert 1 \rangle)$
    - $= \frac{1}{\sqrt{2}}(\langle 0 \vert u_{\theta} \rangle + \langle 1 \vert u_{\theta} \rangle)$
    - $= \frac{1}{\sqrt{2}}(e^{-i\theta}/\sqrt{2} + e^{-i\theta}/\sqrt{2})$
    - $= 1$

3. **Calculate the probability of measuring $\uparrow$ when the state is $\vert u_{\phi} \rangle$ for $\phi \neq \theta$:**
    - $\langle u_{\phi} \vert \uparrow \rangle = \langle u_{\phi} \vert \frac{1}{\sqrt{2}}(\vert 0 \rangle + \vert 1 \rangle)$
    - $= \frac{1}{\sqrt{2}}(\langle 0 \vert u_{\phi} \rangle + \langle 1 \vert u_{\phi} \rangle)$
    - $= \frac{1}{\sqrt{2}}(e^{-i\phi}/\sqrt{2} + e^{-i\phi}/\sqrt{2})$
    - $= \cos(\theta - \phi)/\sqrt{2}$

4. **Show that the probability of measuring $\uparrow$ is strictly less than 1 for $\phi \neq \theta$:**
    - Since $\theta$ and $\phi$ are in $[0, 2\pi)$, $\theta - \phi$ is also in $[0, 2\pi)$.
    - If $\theta - \phi = 0$, then $\cos(\theta - \phi) = 1$ and the probability of measuring $\uparrow$ is 1.
    - If $\theta - \phi \neq 0$, then $\cos(\theta - \phi) < 1$ and the probability of measuring $\uparrow$ is less than 1.

### Conclusion:

There is a basis $\vert \uparrow \rangle, \vert \downarrow \rangle$ such that measuring the state $\vert u_{\theta} \rangle$ in this basis yields outcome $\uparrow$ with probability 1, and for any $\phi \neq \theta \in [0, 2\pi)$, measuring the state $\vert u_{\phi} \rangle$ in this basis yields outcome $\uparrow$ with probability strictly less than 1.

# 3B


Rigorous Proof of Basis and Measurement Probability

Here is a more rigorous proof that there exists a basis $\vert \uparrow \rangle, \vert \downarrow \rangle$ such that measuring the state $\vert u_{\theta} \rangle$ in this basis yields outcome $\uparrow$ with probability 1, and for any $\phi \neq \theta \in [0, 2\pi]$, measuring the state $\vert u_{\phi} \rangle$ in this basis yields outcome $\uparrow$ with probability strictly less than 1:



### Proof:

#### Basis Construction:

We can construct the desired basis $\vert \uparrow \rangle, \vert \downarrow \rangle$ using the following steps:

1. Define $\vert \uparrow \rangle = \vert u_{\theta} \rangle$ (this is allowed as $\vert u_{\theta} \rangle$ is a normalized vector).
2. Define a vector $\vert v \rangle$ such that:

$$\vert v \rangle = e^{i\phi} \vert 0 \rangle + \vert 1 \rangle \quad (\text{where } \phi \neq \theta)$$

Note that $\vert v \rangle$ is also normalized:

$$\Vert v \Vert^2 = \vert e^{i\phi} \vert^2 + 1 = 1 + 1 = 2$$

#### Gram-Schmidt Orthogonalization:

Apply the Gram-Schmidt orthogonalization procedure to $\vert \uparrow \rangle$ and $\vert v \rangle$ to obtain an orthonormal basis:

1. **Step 1:** Project $\vert v \rangle$ onto $\vert \uparrow \rangle$.

$$\vert \text{proj}_{\uparrow}v \rangle = \langle \uparrow \vert v \rangle \vert \uparrow \rangle = (\langle u_{\theta} \vert (e^{i\phi} \vert 0 \rangle + \vert 1 \rangle)) \vert u_{\theta} \rangle = (e^{i\phi} + 1) \vert u_{\theta} \rangle$$

2. **Step 2:** Normalize the projection.

$$\vert \psi \rangle = \frac{\vert \text{proj}_{\uparrow}v \rangle}{\Vert \text{proj}_{\uparrow}v \Vert} = \frac{(e^{i\phi} + 1) \vert u_{\theta} \rangle}{\sqrt{1 + 2e^{i\phi} \cos(\theta - \phi) + 1}}$$

3. **Step 3:** Obtain the second basis vector.

$$\vert \downarrow \rangle = \vert v \rangle - \vert \text{proj}_{\uparrow}v \rangle = (e^{i\phi} \vert 0 \rangle + \vert 1 \rangle) - \left(\frac{(e^{i\phi} + 1) \vert u_{\theta} \rangle}{\sqrt{1 + 2e^{i\phi} \cos(\theta - \phi) + 1}}\right)$$

#### Probability Calculation:

- **Probability of outcome $\uparrow$:**

The probability of measuring outcome $\uparrow$ in the basis $\vert \uparrow \rangle, \vert \downarrow \rangle$ is equal to the absolute value squared of the projection of the state $\vert u_{\theta} \rangle$ onto $\vert \uparrow \rangle$. Since we defined $\vert \uparrow \rangle = \vert u_{\theta} \rangle$, this probability is:

$$P(\uparrow) = \Vert \uparrow \Vert^2 = 1$$

- **Probability of outcome $\downarrow$:**

The probability of measuring outcome $\downarrow$ is:

$$P(\downarrow) = 1 - P(\uparrow) = 1 - 1 = 0$$

Therefore, measuring $\vert u_{\theta} \rangle$ in the basis $\vert \uparrow \rangle, \vert \downarrow \rangle$ always yields outcome $\uparrow$

- **Case $\phi \neq \theta$:**
$x

**Case $\phi \neq \theta$:**

For any $\phi \neq \theta$, the basis vectors $\vert \uparrow \rangle$ and $\vert \downarrow \rangle$ will be different. The projection of $\vert u_{\phi} \rangle$ onto $\vert \uparrow \rangle$ will no longer be the entire vector itself, and the probability of outcome $\uparrow$ will be strictly less than 1.

### Conclusion:

We have constructed a basis $\vert \uparrow \rangle, \vert \downarrow \rangle$ such that measuring the state $\vert u_{\theta} \rangle$ in this basis yields outcome $\uparrow$ with probability 1. For any $\phi \neq \theta$, measuring the state $\vert u_{\phi} \rangle$ in this basis yields outcome $\uparrow$ with probability strictly less than 1. This demonstrates the effect of relative phase on the outcome probabilities in quantum mechanics.

_Note: This proof relies on the concepts of basis construction, Gram-Schmidt orthogonalization, and probability calculation in quantum mechanics._


## Theorem and Proof

### Theorem:

Let $\vert u_{\theta} \rangle = \frac{1}{\sqrt{2}}(\vert 0 \rangle + e^{i\theta}\vert 1 \rangle)$ for $\theta \in [0, 2\pi)$. There is a basis $\vert \uparrow \rangle, \vert \downarrow \rangle$ such that measuring the state $\vert u_{\theta} \rangle$ in this basis yields outcome $\uparrow$ with probability 1, and for any $\phi \neq \theta \in [0, 2\pi)$, measuring the state $\vert u_{\phi} \rangle$ in this basis yields outcome $\uparrow$ with probability strictly less than 1.


### Proof:

1. **Define the basis $\vert \uparrow \rangle, \vert \downarrow \rangle$:**
    - $\vert \uparrow \rangle = \frac{1}{\sqrt{2}}(\vert 0 \rangle + \vert 1 \rangle)$
    - $\vert \downarrow \rangle = \frac{1}{\sqrt{2}}(\vert 0 \rangle - \vert 1 \rangle)$

2. **Calculate the probability of measuring $\uparrow$ when the state is $\vert u_{\theta} \rangle$:**
    - $\langle u_{\theta} \vert \uparrow \rangle = \langle u_{\theta} \vert \frac{1}{\sqrt{2}}(\vert 0 \rangle + \vert 1 \rangle)$
    - $= \frac{1}{\sqrt{2}}(\langle 0 \vert u_{\theta} \rangle + \langle 1 \vert u_{\theta} \rangle)$
    - $= \frac{1}{\sqrt{2}}\left(\frac{e^{-i\theta}}{\sqrt{2}} + \frac{e^{-i\theta}}{\sqrt{2}}\right)$
    - $= 1$

3. **Calculate the probability of measuring $\uparrow$ when the state is $\vert u_{\phi} \rangle$ for $\phi \neq \theta$:**
    - $\langle u_{\phi} \vert \uparrow \rangle = \langle u_{\phi} \vert \frac{1}{\sqrt{2}}(\vert 0 \rangle + \vert 1 \rangle)$
    - $= \frac{1}{\sqrt{2}}(\langle 0 \vert u_{\phi} \rangle + \langle 1 \vert u_{\phi} \rangle)$
    - $= \frac{1}{\sqrt{2}}\left(\frac{e^{-i\phi}}{\sqrt{2}} + \frac{e^{-i\phi}}{\sqrt{2}}\right)$
    - $= \frac{\cos(\theta - \phi)}{\sqrt{2}}$


### Proof:

1. **Define the basis $\vert \uparrow \rangle, \vert \downarrow \rangle$:**
    - $\vert \uparrow \rangle = \frac{1}{\sqrt{2}}(\vert 0 \rangle + \vert 1 \rangle)$
    - $\vert \downarrow \rangle = \frac{1}{\sqrt{2}}(\vert 0 \rangle - \vert 1 \rangle)$

2. **Calculate the probability of measuring $\uparrow$ when the state is $\vert u_{\theta} \rangle$:**
    - $\langle u_{\theta} \vert \uparrow \rangle = \langle u_{\theta} \vert \frac{1}{\sqrt{2}}(\vert 0 \rangle + \vert 1 \rangle)$
    - $= \frac{1}{\sqrt{2}}(\langle 0 \vert u_{\theta} \rangle + \langle 1 \vert u_{\theta} \rangle)$
    - $= \frac{1}{\sqrt{2}}(e^{-i\theta}/\sqrt{2} + e^{-i\theta}/\sqrt{2})$
    - $= 1$

3. **Calculate the probability of measuring $\uparrow$ when the state is $\vert u_{\phi} \rangle$ for $\phi \neq \theta$:**
    - $\langle u_{\phi} \vert \uparrow \rangle = \langle u_{\phi} \vert \frac{1}{\sqrt{2}}(\vert 0 \rangle + \vert 1 \rangle)$
    - $= \frac{1}{\sqrt{2}}(\langle 0 \vert u_{\phi} \rangle + \langle 1 \vert u_{\phi} \rangle)$
    - $= \frac{1}{\sqrt{2}}(e^{-i\phi}/\sqrt{2} + e^{-i\phi}/\sqrt{2})$
    - $= \cos(\theta - \phi)/\sqrt{2}$

4. **Show that the probability of measuring $\uparrow$ is strictly less than 1 for $\phi \neq \theta$**
    - Since $\theta$ and $\phi$ are in $[0, 2\pi]$, $\theta - \phi$ is also in $[0, 2\pi]$.
    - If $\theta - \phi = 0$, then $\cos(\theta - \phi) = 1$ and the probability of measuring $\uparrow$ is 1.
    - If $\theta - \phi \neq 0$, then $\cos(\theta - \phi) < 1$ and the probability of measuring $\uparrow$ is less than 1.

### Conclusion:

There is a basis $\vert \uparrow \rangle, \vert \downarrow \rangle$ such that measuring the state $\vert u_{\theta} \rangle$ in this basis yields outcome $\uparrow$ with probability 1, and for any $\phi \neq \theta \in [0, 2\pi)$, measuring the state $\vert u_{\phi} \rangle$ in this basis yields outcome $\uparrow$ with probability strictly less than 1.









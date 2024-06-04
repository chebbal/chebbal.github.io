## A New Post

I believe performance imporvements due to Moore's law has made us programmers lazy about writing reliable performant code for the underlying hardware. Low-level programmers are an exception to this observation, as it's in their nature of work. As we move up the tech stack, we become less concerned about writing performant code thinking it's compilers or library implementers responsibility down the chain to make the code performant. But there is limit beyond which automatic optimization becomes infeasible and we need to enter the alley of code speed-ups at mathematical operator level. One such use-case is speeding-up operations that make up DNN(Deep Neural Nets). One operation that I think is interesting to explore is Convolutions, which involves matrix multiplications.

These are some of the efficient approaches that I have across during my readings:
1. Toeplitz transformations 
2. Strassen's matrix multiplication
3. Winograd's transform
4. FFT transform

(TBC)
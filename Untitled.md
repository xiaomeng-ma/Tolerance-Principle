### The skeleton idea of TP:
1. a rule is derived when it delivers more productive results

   How to define "more productive"?
3. Lexical retrieval time complexity --- the time cost to process the word list
4. aka A rule will be derived when it's faster to retrieve the word with a rules than without a rule
5. aka A rule will be derived when the total time complexity with rules smaller than without rules

### TP in practice:
1. Estimate total time complexity:

    p<sub>i</sub> as the probability for i_th ranked word in the list
    
    t<sub>i</sub> as the time complexitity for i_th ranked word in the list
    
    Total Time complexity no rules (T<sub>N</sub>): 
$$\displaystyle\sum_{i=1}^N p{_i} \cdot t{_i}$$ 

    Total Time complexity with rules with e exceptions(T<sub>e</sub>):
    $$\displaystyle\sum_{i=1}^e p{_i} \cdot t{_i} + (1-e/N) \cdot e$$ 
    
    If T<sub>N</sub> < T<sub>e</sub>, then TP is true

### Technical Details in TP:
1. How to estimate p<sub>i</sub>?

*Yang* ---- Zipfian f(x) = Cx<sup>(-s)</sup> , s = 1

*Me* ---- Power Law f(x) =Cx<sup>(-s)</sup>, s 

2. How to estimate t<sub>i</sub>?

*Yang* ---- t<sub>i</sub> = r<sub>i</sub>

*Me* ----- a lograthim relation to frequency t<sub>i</sub> = C - f<sup>(-k)</sup>



### Distribution Assumptions

Yang: naive Zipf: $$f(x) = C\cdot x^{-1}$$ 

Zipf: $$f(x) = C\cdot x^{-k}$$ 

Zipf-Mandelbrot:  $$f(x) = C\cdot (x+b)^{-k}$$ 

lognormal: $$f(x) = e^{d-m\cdot ln^2(x)}$$

might be something else ... 

### All about p

Yang:   $$p_i = 1/x\cdot H_N $$

Zipf: $$p_i =1/x^{k}\cdot H_{N,k}$$

Zipf-Mandelbrot: $$p_i =1/(x+b)^{k}\cdot H_{N,k,b}$$






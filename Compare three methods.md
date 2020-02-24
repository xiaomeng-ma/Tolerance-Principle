### Using Raw probability (exact estimate based on corpus)

S<sub>N</sub> as the tokens of all verbs, S<sub>e</sub> as tokens of all irregular verbs, S<sub>r<sub>i</sub></sub> as tokens for the i<sup>th</sup> ranked verb

$$T_N = \frac{S{r_1}}{S{_N}}\cdot 1+\frac{S{r_2}}{S{_N}} \cdot 2 +\frac{S{r_3}}{S{_N}}\cdot 3+...\frac{1}{S{_N}}\cdot N$$ = $$\displaystyle\sum_{i=1}^N p{_i} \cdot r{_i}$$ 
$$T_R = \frac{S{r_1}}{S{_e}}\cdot 1+\frac{S{r_2}}{S{_e}} \cdot 2 +\frac{S{r_3}}{S{_e}}\cdot 3+...\frac{S{r_e}}{S{_e}}\cdot e + (1-\frac{e}{N})\cdot e = \displaystyle\sum_{i=1}^e p_{i} \cdot r_{i} + (1-\frac{e}{N})\cdot e$$  

|         | S<sub>N</sub> | S<sub>e</sub> | N    | e    | T<sub>N</sub> | T<sub>R</sub> | T<sub>R</sub><T<sub>N</sub> |
| ------- | ------------- | ------------- | ---- | ---- | ------------- | ------------- | --------------------------- |
| Adam    | 6,747         | 3,632         | 270  | 62   | 33.80         | 58.78         | False                       |
| Eve     | 564           | 337           | 91   | 36   | 17.51         | 29.92         | False                       |
| Sarah   | 1,759         | 1,035         | 189  | 48   | 25.65         | 43.70         | False                       |
| Peter   | 7,532         | 3,647         | 424  | 67   | 43.82         | 64.80         | False                       |
| Naomi   | 1,240         | 757           | 128  | 43   | 19.63         | 36.54         | False                       |
| Allison | 612           | 335           | 88   | 36   | 18.24         | 29.71         | False                       |
| April   | 128           | 62            | 50   | 19   | 14.64         | 18.38         | False                       |
| Fraser  | 13,924        | 9,903         | 371  | 78   | 26.34         | 68.40         | False                       |

|                 | S<sub>N</sub> | S<sub>N</sub> | N    | e    | T<sub>N</sub> | T<sub>R</sub> | T<sub>R</sub><T<sub>N</sub> |
| --------------- | ------------- | ------------- | ---- | ---- | ------------- | ------------- | --------------------------- |
| Adam's input    | 4,670         | 2,863         | 297  | 70   | 35.27         | 64.93         | False                       |
| Eve's input     | 1,618         | 966           | 138  | 50   | 21.17         | 40.68         | False                       |
| Sarah's input   | 3,867         | 2,525         | 293  | 68   | 33.37         | 62.41         | False                       |
| Peter's input   | 15,573        | 8,466         | 633  | 83   | 47.19         | 82.86         | False                       |
| Naomi's input   | 1,463         | 945           | 174  | 59   | 27.12         | 49.36         | False                       |
| Allison's input | 1,453         | 936           | 140  | 44   | 21.32         | 38.37         | False                       |
| April's input   | 658           | 429           | 100  | 37   | 19.09         | 32.43         | False                       |
| Fraser's input  | 32,359        | 23,169        | 581  | 97   | 30.80         | 88.88         | False                       |

None of the children's data conformed to the TP's prediction



### Using my generalized TP 

$$T_N = {\displaystyle\sum_{k_1}^N(r_i\cdot p_i)}= {\displaystyle\sum_{k=1}^N(r_i\cdot\frac{1}{r_i^\alpha\cdot H_{N,\alpha}})}= \frac{H_{N,\alpha-1}}{H_{N,\alpha}}$$

$$T_R = {\displaystyle\sum_{k_1}^e (r_i\cdot p_i)} \cdot \frac{e}{N} + (1-\frac{e}{N}) \cdot e = \frac{H_{e,\beta-1}}{H_{e,\beta}}\cdot\frac{e}{N} + (1-\frac{e}{N})\cdot e$$ 

|         | T<sub>R</sub> | T<sub>N</sub> | T<sub>R</sub><T<sub>N</sub> |                 | T<sub>R</sub> | T<sub>N</sub> | T<sub>R</sub><T<sub>N</sub> |
| ------- | ------------- | ------------- | --------------------------- | --------------- | ------------- | ------------- | --------------------------- |
| Adam    | 52.53         | 78.07         | True                        | Adam's input    | 57.92         | 76.24         | True                        |
| Eve     | 26.27         | 22.55         | #False                      | Eve's input     | 37.66         | 36.94         | #False                      |
| Sarah   | 39.94         | 47.90         | True                        | Sarah's input   | 57.62         | 78.67         | True                        |
| Peter   | 60.18         | 115.04        | True                        | Peter's input   | 76.05         | 181.99        | True                        |
| Naomi   | 32.94         | 34.03         | True                        | Naomi's input   | 50.37         | 55.54         | True                        |
| Allison | 25.46         | 21.03         | #False                      | Allison's input | 34.65         | 36.42         | True                        |
| April   | 13.44         | 8.13          | #False                      | April's input   | 27.34         | 24.48         | #False                      |
| Fraser  | 67.27         | 110.64        | True                        | Fraser's input  | 86.71         | 181.58        | True                        |



### Using Yang's vanilla TP

$$T_N = \frac{N}{lnN}$$

$$T_R = \frac{e}{N}\cdot \frac{e}{lne} + (1-\frac{e}{N})\cdot e$$ 

$$\theta = \frac{N}{lnN}$$

|         | T_R   | T_N   | T_R < T_N |                 | T_R   | T_N   | T_R < T_N |
| ------- | ----- | ----- | --------- | --------------- | ----- | ----- | --------- |
| Adam    | 50.32 | 48.23 | False     | Adam's input    | 55.35 | 48.96 | False     |
| Eve     | 24.92 | 20.17 | False     | Eve's input     | 35.36 | 27.68 | False     |
| Sarah   | 38.14 | 36.06 | False     | Sarah's input   | 55.00 | 51.58 | False     |
| Peter   | 58.16 | 70.09 | #True     | Peter's input   | 73.80 | 98.13 | #True     |
| Naomi   | 31.53 | 26.38 | False     | Naomi's input   | 47.89 | 41.09 | False     |
| Allison | 24.56 | 19.65 | False     | Allison's input | 32.97 | 28.33 | False     |
| April   | 13.64 | 12.78 | False     | April's input   | 26.28 | 8.03  | False     |
| Fraser  | 63.90 | 13.26 | False     | Fraser's input  | 83.35 | 15.24 | False     |

|         | N    | e    | θ    | e ≤ θ |                 | N    | e    | θ    | e ≤ θ |
| ------- | ---- | ---- | ---- | ----- | --------------- | ---- | ---- | ---- | ----- |
| Adam    | 270  | 62   | ≈ 48 | False | Adam's input    | 275  | 70   | ≈ 56 | False |
| Eve     | 91   | 36   | ≈ 20 | False | Eve's input     | 136  | 50   | ≈ 28 | False |
| Sarah   | 189  | 48   | ≈ 36 | False | Sarah's input   | 293  | 68   | ≈ 52 | False |
| Peter   | 424  | 67   | ≈ 70 | #True | Peter's input   | 633  | 83   | ≈ 98 | #True |
| Naomi   | 128  | 43   | ≈ 26 | False | Naomi's input   | 222  | 62   | ≈ 41 | False |
| Allison | 88   | 36   | ≈ 20 | False | Allison's input | 140  | 44   | ≈ 28 | False |
| April   | 50   | 19   | ≈ 13 | False | April's input   | 100  | 37   | ≈ 22 | False |
| Fraser  | 371  | 78   | ≈ 61 | False | Fraser's input  | 566  | 97   | ≈ 92 | False |





Adam verbs p for #log normal# : 0.9; compare pl vs ln p_one_sided: 0.99

Eve verbs p for $log normal$  : 0.36, p for power law: 0.11, compare pl vs ln  p_one_sided:0.9754831

Fraser verbs p for log normal: 0.14, power law: 0.25, compare pl vs ln 0.699





换成log
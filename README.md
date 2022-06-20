# Conditional-Entropy-Based-Causal-Discovery
#This work aims to find the causal rules using conditional entropy in Cyberstalking data set. An algoritm (COJEC) is proposed to find the causal rules of this data set. For the proposed algorithm our inputs are the set of features of dataset i.e., F = {F1, F2, . . . , Ff } and the threshold value τ . Each feature i  contains different values denoted by V . Thus we can represent feature i is as Fi = {V1,Fi , V2,Fi , . . . , V|Fi|,Fi } where |Fi| denotes the number of values of feature i. For example, in the cyberstalking data set the third feature is "Age" where its has three 15, 16 and 17 values. Thus we can write this feature as F3 = {V(1,3), V(2,3), V(3,3)} = {15, 16, 17}. The out put will be the set of causal rules (X → Y) determined using the algorithm. This algorithm starts by determining all sub sets of F with m elements. This algorithm checks all the possible subsets of F by the end of the algorithm. After determining F^(m) which is all the subsets of F for a certain m starting from 1 to f − 1, selects each subset of it (F_s^(m)) and for each (F_s^(m)) computes the Cartesian product (F_C^(m)). Set of Cartesian product of sub set (F_s^(m)) are denoted as X = {X1, X2, . . . , Xm}. Then this process will be replicated for other subsets of features and Cartesian product of them will be done and denoted as Y = {Y1, Y2, . . . , Yn}. Now we haveX and Y sets. If X ∩ Y = ∅ and H(Y |X) ≤ τ  conditions are satisfied for X and Y ,  (X → Y ) will be considered as a causal rule  and will be adde to the output set of rules. Conditional entropy of H(Y |X) for X = {X1, X2, . . . , Xm} and Y = {Y1, Y2, . . . , Yn} is computed using the following formula:
H(Y│X)=P(X,Y)log (P(X,Y))/(P(X))=P(X={X_1,X_2,…,X_m },Y={Y_1,Y_2,…,Y_n })log P(X={X_1,X_2,…,X_m },Y={Y_1,Y_2,…,Y_n })/P(X={X_1,X_2,…,X_m }) 

# Algorithm:
ALGORITHM 1: COJEC - Conditional Joint Entropy based Casual rule discovery
INPUT: F,τ
F:  Feature’s set of f discrete features F={F_1,F_2,…,F_f }, where F_i={V_(1,Fi),V_(2,Fi),…,V_(|Fi|,Fi)}. F_i, st. 1≤i≤f
τ : a small threshold value
OUTPUT: W
W : the set of casual rules X->Y for which the conditional joint entropy is smaller than the threshold τ , i.e. H(Y|X)≤τ
1  for m=1 to f-1
2        F^((m))← allSubsetsOfF(F,m) 
3        foreach subset F_S^((m))  of F^((m))
4   	F_C^((m))←cartesianProductOfSubsetOfFeatures(F_S^((m) ) )
5 	foreach X={X_1,X_2,…,X_m }∈F_C^((m))
6                      for n=1 to f-1
7                             F^((n))← allSubsetsOfF(F,n) 
8                            foreach subset F_S^((n))  of F^((n))
9   	                      F_C^((n))←cartesianProductOfSubsetOfFeatures(F_S^((n) ) )
10                                 foreach Y={Y_1,Y_2,…,Y_n }∈F_C^((n))
11                                            if X∩Y=∅ and H(Y|X) ≤τ
12                                                  add the casual rule X→Y to W //X={X_1,X_2,…,X_m }→Y={Y_1,Y_2,…,Y_n }




13  return W     //the set of casual rules X->Y for which the conditional joint entropy is smaller than the threshold τ 
# Code of this algorithm can be found in COJEC.cpp file.

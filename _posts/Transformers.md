## Implement self attention in python

<br>1. Scale dot production</br>
Self attention can be expressed as follows:\
$score = softmax(\frac{qk^{T}}{\sqrt{d_k}})v$ (1)\
where the production is scaled by the dimention factor.

<br>2. Multi-head attention </br>
If q, k, v are in the size of (batch_size, seq_len, dim), suppose we let the number of head to be n_head,
q,k,v become three (batch_size, seq_len, n_head, emb_dim) vectors, where emb_dim = dim/n_head.
When computing attention score based on the equation (1), we first modify the order of seq_len and n_head.
(batch_size, n_head, seq_len, emb_dim) * (batch_size, n_head, emb_dim, seq_len))* 
The score should be in (batch_size, n_head, seq_len, emb_dim), we can concatenate n_head back together, 
thus the dimension of score is finally (batch_size, seq_len, dim) which seems no change in dimention to the orignal input q,k,v.

<br>3. mask </br>
We map mask some elements.

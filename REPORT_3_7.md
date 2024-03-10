# Records

## Methods

1. For case group: Select patient's records after diagnose AD date.
2. The weighted embedding process involves using the cosine similarity of each code with the AD code (PheCode: 290.11) to weight the code embedding
 
 ```math
tf_{i,j} = \text{Frequency of \(i^{th}\) code in \(j^{th}\) patient's record}
```
 ```math
idf_{i,i} = log(\# patient/ (1+ \# \text{patient with code i}))
```
 ```math
tf\_idf = tf*idf
```
 ```math
pt\_emb = tf\_idf*code\_emb
```
 ```math
pt\_emb\_wgt = tf\_idf*diag(weight)*code\_emb
```
3. We multiply the chart patient's embedding and the registry patient's embedding, select the biggest location to be the prediction of the registry-patients' prediction.
4. Supervise:
Forward:

 ```math
pt\_emb\_chart = pt\_emb\_chart *U + 1*b^T \text{(then row-normalize)}

pt\_emb\_registry = pt\_emb\_registry *U + 1*b^T \text{(then row-normalize)}

cos_similarity = pt\_emb\_registry * pt\_emb\_chart^T
```

In the loss function, we use the constractive learning. We divide the chart group into 3 parts: train, validation and test set (3:2:5). Then we use the labels in train set to train U and b.

 ```math
P_j = {5 codes with minimum cosine similarity of j}
N_j = {5 codes with maximun cosine similarity of j}
Loss_j = 1 / AA * torch.log(1+\sum_{i \in P_j} {exp(-AA*(x^i^Tx_j - \lambda))}) + 1 / BB * torch.log(1+\sum_{i \in N_j} {exp(BB*(x^i^Tx_j - \lambda))})
Loss = \sum_{j} Loss_j
```

## Calssifty Accuracy

| Metric        | UPMC  | MGB   |
|---------------|-------|-------|
| Before Supervised (Weighted) | 0.670 | 0.488 |
| Before Supervised (Non-weighted) | 0.655 | 0.450 |
| After Supervised (Weighted)| 0.728 | 0.625 |


## tsne  plot
### Before supervised
#### UPMC
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic/upmc_wgt.png" alt="UPMC_wgt" title="Weighted" width="400"/>
  <em>upmc weighted</em>
  &nbsp; &nbsp; &nbsp; &nbsp;
  <img src="https://github.com/TongHan96/Records/blob/main/pic/upmc.png" alt="UPMC" title="Origin" width="400"/>
  <em>upmc</em>
</p>

#### MGB
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic/mgb_wgt.png" alt="MGB_wgt" title="Weighted" width="400"/>
  <em>MGB weighted</em>
  &nbsp; &nbsp; &nbsp; &nbsp;
  <img src="https://github.com/TongHan96/Records/blob/main/pic/mgb.png" alt="MGB" title="Origin" width="400"/>
  <em>MGB</em>
</p>

### After supervised

<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic/supervised_mgb.png" alt="MGB" title="Weighted" width="400"/>
  <em>MGB</em>
  &nbsp; &nbsp; &nbsp; &nbsp;
  <img src="https://github.com/TongHan96/Records/blob/main/pic/supervised_upmc.png" alt="UPMC" title="Origin" width="400"/>
  <em>UPMC</em>
</p>


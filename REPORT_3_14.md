# Records

## Methods

1. Select patient's records after these codes ("PheCode:290.11" "PheCode:290.1"  "PheCode:290.12" "PheCode:290.13" "PheCode:290.3" ).
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
```
```math
pt\_emb\_registry = pt\_emb\_registry *U + 1*b^T \text{(then row-normalize)}
```
```math
cos_similarity = pt\_emb\_registry * pt\_emb\_chart^T
```

In the loss function, we use the constractive learning. We divide the chart group into 3 parts: train, validation and test set (3:2:5). Then we use the labels in train set to train U and b.

 ```math
P_j = \{\text{5 codes with minimum cosine similarity of j}\}
```
```math
N_j = \{\text{5 codes with maximun cosine similarity of j}\}
```
```math
Loss_j = \frac{1}{\alpha} \cdot \log\left(1 + \sum_{i \in P_j} \exp\left(-\alpha \cdot (x_i^T \cdot x_j - \lambda)\right)\right) + \frac{1}{\beta} \cdot \log\left(1 + \sum_{i \in N_j} \exp\left(\beta \cdot (x_i^T \cdot x_j - \lambda)\right)\right)
```
```math
Loss = \sum_{j} Loss_j
```

## Calssifty Accuracy
### Last Time:
| Metric        | UPMC  | MGB   |
|---------------|-------|-------|
| Before Supervised (Weighted) | 0.670 | 0.488 |
| Before Supervised (Non-weighted) | 0.655 | 0.450 |
| After Supervised (Weighted)| 0.728 | 0.625 |

### Now:
| Metric        | UPMC  | MGB   |
|---------------|-------|-------|
| Before Supervised (Weighted) | 0.586 | 0.563 |
| Before Supervised (Non-weighted) | 0.591 | 0.488 |

| Metric        | UPMC  | MGB   |
|---------------|-------|-------|
| Main Code Count | 0.753 | 0.821 |
| KOMAP | 0.777 | 0.493 |
| GAME | 0.777 | 0.493 |



## tsne  plot
### Before supervised
#### UPMC
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_new/upmc.weighted.png" alt="UPMC_wgt" title="Weighted" width="400"/>
  <em>upmc weighted</em>
  &nbsp; &nbsp; &nbsp; &nbsp;
  <img src="https://github.com/TongHan96/Records/blob/main/pic_new/upmc.png" alt="UPMC" title="Origin" width="400"/>
  <em>upmc</em>
</p>

#### MGB
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_new/mgb.weighted.png" alt="MGB_wgt" title="Weighted" width="400"/>
  <em>MGB weighted</em>
  &nbsp; &nbsp; &nbsp; &nbsp;
  <img src="https://github.com/TongHan96/Records/blob/main/pic_new/mgb.png" alt="MGB" title="Origin" width="400"/>
  <em>MGB</em>
</p>

#### Two institutions 

<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_new/upmc.mgb.wgt.upmc.png" alt="MGB" title="Weighted" width="400"/>
  <em>UPMC chart</em>
  &nbsp; &nbsp; &nbsp; &nbsp;
  <img src="https://github.com/TongHan96/Records/blob/main/pic_new/upmc.mgb.wgt.mgb.png" alt="UPMC" title="Origin" width="400"/>
  <em>MGB chart</em>
</p>
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_new/upmc.mgb.wgt.cc.png" alt="MGB" title="Weighted" width="400"/>
  <em>case&control</em>
  &nbsp; &nbsp; &nbsp; &nbsp;
  <img src="https://github.com/TongHan96/Records/blob/main/pic_new/upmc.mgb.wgt.inst.png" alt="UPMC" title="Origin" width="400"/>
  <em>2 inst</em>
</p>



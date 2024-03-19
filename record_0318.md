# Method
1. Log means log the count in tf. Normalization means mornalize every patient embedding.
2. 

# Results

# Main PheCode Count
| Method          |  AUC | Accuracy | MGB chart AUC | MGB chart Accuracy | UPMC chart AUC | UPMC chart Accuracy | UPMC reg AUC | UPMC reg Accuracy |
|-----------------|----------|--------|----------|--------|----------|--------|----------|--------|
| All | 0.751  | -  |  0.804  | -   |  0.728  | -   |  0.796  | -   |


# KOMAP

| Method          |  AUC | Accuracy | MGB chart AUC | MGB chart Accuracy | UPMC chart AUC | UPMC chart Accuracy | UPMC reg AUC | UPMC reg Accuracy |
|-----------------|----------|--------|----------|--------|----------|--------|----------|--------|
| feature(5%) by GAME by type  | 0.794  | 0.725   |  0.807  | 0.730   |  0.818  | 0.766   |  0.780  | 0.718   | 
| feature(5%) by GAME | 0.797  | 0.725   |  0.807  | 0.730   |  0.818  | 0.766   |  0.780  | 0.718   | 

# tf %*% wgt from KOMAP

## Log No Normalize 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P17.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

| Method          |  AUC | Accuracy | MGB chart AUC | MGB chart Accuracy | UPMC chart AUC | UPMC chart Accuracy | UPMC reg AUC | UPMC reg Accuracy | Param|
|-----------------|----------|--------|----------|--------|----------|--------|----------|--------|-------|
| GAME | 0.805  | 0.712   |  0.891  | 0.769   |  0.826  | 0.796   |  0.785  | 0.694   | (10,4)|

| Metric          | Data Source    | AUC | Accuracy |Param| 
|-----------------|----------------|----------|--------|-------|
|                 | UPMC Registry => UPMC Chart     |0.821  | 0.776   | (1e-2, 2)| 
|                 | UPMC Registry => MGB Chart      |0.789  | 0.824     | (10, 4) |
| GAME            | UPMC Registry  |0.811   |  0.767  | (1e+3, 768) |
|                 | UPMC Chart     |0.854  | 0.812   | (1e+3, 3) |
|                 | MGB Chart      |0.783  | 0.838     | (1, 4) |

## Log Normalize 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P18.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

| Method          |  AUC | Accuracy | MGB chart AUC | MGB chart Accuracy | UPMC chart AUC | UPMC chart Accuracy | UPMC reg AUC | UPMC reg Accuracy | Param|
|-----------------|----------|--------|----------|--------|----------|--------|----------|--------|-------|
| feature(5%) by GAME by type  | 0.766  | 0.788   |  0.737  | 0.707   |  0.85  | 0.802   |  0.743  | 0.791   | (10,2)|

| Metric          | Data Source    | AUC | Accuracy |Param| 
|-----------------|----------------|----------|--------|-------|
|                 | UPMC Registry => UPMC Chart     |0.794  | 0.766   | (1, 768)| 
|                 | UPMC Registry => MGB Chart      |0.778  | 0.757     | (0.1, 768) |
| GAME            | UPMC Registry  |0.754   |  0.793  | (1e-2, 768) |
|                 | UPMC Chart     |0.818  | 0.782   | (1, 3) |
|                 | MGB Chart      |0.865  | 0.811     | (1, 768) |

# tfidf %*% cosine^3
## No Log No Normalize 

<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P13.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

**The result is a little worse than tfidf %*% cosine.**

## Log No Normalize 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P14.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

| Metric          | Data Source    | AUC | Accuracy |Param| 
|-----------------|----------------|----------|--------|-------|
|                 | UPMC Registry => UPMC Chart     |0.775  | 0.761   | (1e-4, 768)| 
|                 | UPMC Registry => MGB Chart      |0.766  | 0.784     | (1e-5, 768) |
| GAME            | UPMC Registry  |0.842   |  0.726  | (1e-4, 768) |
|                 | UPMC Chart     |0.844  | 0.782   | (1e-2, 3) |
|                 | MGB Chart      |0.818  | 0.811     | (1, 768) |
## No Log Normalize 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P15.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

**The result is a little worse than tfidf %*% cosine.**

## Log Normalize 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P16.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

**The result is a little worse than tfidf %*% cosine.**

# tfidf %*% cosine^2
## No Log No Normalize 

<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P9.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

| Metric          | Data Source    | AUC | Accuracy | Param|
|-----------------|----------------|----------|--------|--------|
|                 | UPMC Registry => UPMC Chart     | 0.734|  0.726  |  (1e-6,3) |
|                 | UPMC Registry => MGB Chart      | 0.746 | 0.743  |  (1e-5, 768) |
| GAME            | UPMC Registry  |0.749   |  0.767  | (1e-2, 768)   |
|                 | UPMC Chart     |0.770  | 0.733   | (1e-4,768)  |
|                 | MGB Chart      |0.797  | 0.757     | (1,768) |

## Log No Normalize 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P10.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

| Metric          | Data Source    | AUC | Accuracy |Param| 
|-----------------|----------------|----------|--------|-------|
|                 | UPMC Registry => UPMC Chart     |0.775  | 0.751   | (1e-4, 768)| 
|                 | UPMC Registry => MGB Chart      |0.781  | 0.770     | (1e-5, 768) |
| GAME            | UPMC Registry  |0.821   |  0.801  | (1e-4, 768) |
|                 | UPMC Chart     |0.838  | 0.792   | (1e-3, 768) |
|                 | MGB Chart      |0.845  | 0.838     | (1, 768) |


## No Log Normalize 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P11.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

**The result is a little worse than tfidf %*% cosine.**

## Log Normalize 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P12.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

**The result is a little worse than tfidf %*% cosine.**

# tf %*% cosine

**The result is a little worse than tfidf %*% cosine.**

## No Log No Normalize 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P5.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

## Log No Normalize 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P6.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

## Log No Normalize 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P7.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

## Log Normalize 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P8.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

# tfidf %*% cosine

## No Log No Normalize 

<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P1.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

| Metric          | Data Source    | AUC | Accuracy | Param|
|-----------------|----------------|----------|--------|--------|
|                 | UPMC Registry => UPMC Chart     | 0.754|  0.682  |  (1e-6,4) |
|                 | UPMC Registry => MGB Chart      | 0.763 | 0.635  |  (1e-6, 768) |
| GAME            | UPMC Registry  |0.828   |  0.800  | (1e-5, 768)   |
|                 | UPMC Chart     |0.785  | 0.752   | (1e-5,3)  |
|                 | MGB Chart      |0.825  | 0.811     | (10,4) |



## Log No Normalize 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P2.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

| Metric          | Data Source    | AUC | Accuracy |Param| 
|-----------------|----------------|----------|--------|-------|
|                 | UPMC Registry => UPMC Chart     |0.760  | 0.721   | (1e-3, 768)| 
|                 | UPMC Registry => MGB Chart      |0.752  | 0.784     | (1e-3, 768) |
| GAME            | UPMC Registry  |0.791   |  0.770  | (1e-4, 768) |
|                 | UPMC Chart     |0.816  | 0.752   | (1e-3, 768) |
|                 | MGB Chart      |0.839  | 0.838     | (1e-1, 768) |


## No Log Normalize 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P3.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

| Metric          | Data Source    | AUC | Accuracy |Param| 
|-----------------|----------------|----------|--------|-------|
|                 | UPMC Registry => UPMC Chart     |0.752  | 0.711   | (1e-1, 768)| 
|                 | UPMC Registry => MGB Chart      |0.774  | 0.703    | (1e-2, 768) |
| GAME            | UPMC Registry  |0.813   |  0.797  | (1, 768) |
|                 | UPMC Chart     |0.816  | 0.752   | (1e-3, 768) |
|                 | MGB Chart      |0.839  | 0.838     | (1e-1, 768) |

## Log Normalize 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P4.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

| Metric          | Data Source    | AUC | Accuracy |Param| 
|-----------------|----------------|----------|--------|-------|
|                 | UPMC Registry => UPMC Chart     |0.750   |  0.721  | (1e-1, 768) |
|                 | UPMC Registry => MGB Chart      |0.766  | 0.716     | (1e-1, 768) |
| GAME            | UPMC Registry  |0.750   |  0.721  | (1e-4, 768) |
|                 | UPMC Chart     |0.777  | 0.733   | (10, 3) |
|                 | MGB Chart      |0.850  | 0.811     | (10, 4) |

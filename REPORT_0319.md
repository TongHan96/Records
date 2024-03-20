# Report
## Methods
1. "LOG" refers to taking the logarithm of the count in term frequency (tf).
2. "NOR" involves normalizing each patient's embedding.
3. The input for KOMAP includes using all patient data (after the first AD-related codes) from MGB and UPMC to build the training and validation covariance matrices. It selects codified features using the cosine similarity of GAME embeddings (top 5%), and performs a log(x+1) transformation of the count data.
4. The input for our method utilizes both chart and registry data (after the first AD-related codes) from MGB and UPMC. It explores different weights, clusters the points using SVM, and considers dimension reduction as a tunable parameter, which can be set to 2, 3, 4, 5, or 768.
## Tsne
### tf * KOMAP_wgt * GAME (LOG) 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P17.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

### tf * KOMAP_wgt * GAME (LOG NOR) 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P18.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

### tfidf * GAME_cosine * GAME (LOG)
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P2.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

### tfidf * GAME_cosine * GAME (LOG NOR)
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P4.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

### tfidf * GAME_cosine^2 * GAME (LOG) 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P10.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>

### tfidf * GAME_cosine^3 * GAME (LOG) 
<p align="center">
  <img src="https://github.com/TongHan96/Records/blob/main/pic_0318/P14.png" alt="no log no normalization" title="no log no normalization" width="1000"/>
</p>


## Results
|                  Method                  | MGB chart AUC | MGB chart Accuracy | UPMC chart AUC | UPMC chart Accuracy | UPMC reg AUC | UPMC reg Accuracy |
|:----------------------------------------:|:-------------:|:------------------:|:--------------:|:-------------------:|:------------:|:-----------------:|
|             Main PheCode Count           |     0.796     |         -          |      0.804     |          -          |    0.728     |         -         |
|                   KOMAP                  |     0.807     |       0.730        |      0.818     |        0.766        |    0.780     |       0.718       |
|    tf * KOMAP_wgt * GAME (LOG)           |     0.783     |     **0.838**      |    **0.854**   |      **0.812**      |    0.811     |       0.767       |
|    tf * KOMAP_wgt * GAME (LOG NOR)       |   **0.865**   |       0.811        |      0.818     |        0.782        |    0.754     |     0.793         |
|   tfidf * GAME_cosine * GAME (LOG)       |     0.839     |     **0.838**      |      0.829     |        0.792        |    0.791     |       0.770       |
| tfidf * GAME_cosine * GAME (LOG NOR)     |     0.850     |       0.811        |      0.777     |        0.733        |    0.750     |       0.721       |
| tfidf * GAME_cosine^2 * GAME (LOG)       |     0.853     |       0.811        |      0.838     |        0.802        |    0.821     |       **0.801**   |
| tfidf * GAME_cosine^3 * GAME (LOG)       |     0.818     |       0.811        |      0.844     |        0.782        |  **0.828**   |       0.751       |

|                  Method                  | MGB chart AUC | MGB chart Accuracy | UPMC chart AUC | UPMC chart Accuracy | UPMC reg AUC | UPMC reg Accuracy |
|:----------------------------------------:|:-------------:|:------------------:|:--------------:|:-------------------:|:------------:|:-----------------:|
|             Main PheCode Count           |     0.796     |         -          |      0.804     |          -          |    0.728     |         -         |
|                   KOMAP                  |     0.807     |       0.730        |      0.818     |        0.766        |    0.780     |       0.718       |
|    tf * KOMAP_wgt * GAME (LOG)  COSINE   |     0.817     |          -         |      0.816     |          -          |    0.732     |         -         |
|    tf * KOMAP_wgt * GAME (LOG)  L2       |     0.768     |          -         |      0.824     |          -          |    0.726     |         -         |
|    tf * KOMAP_wgt * GAME (LOG NOR)  COSINE   |     0.794     |          -         |      0.833     |          -          |    0.754     |         -         |
|    tf * KOMAP_wgt * GAME (LOG NOR)  L2       |     0.786     |          -         |      0.816     |          -          |    0.744     |         -         |
|    tf * KOMAP_wgt * GAME (LOG) KMeans        |     0.627     |          -         |      0.748     |          -          |    0.678     |         -         |
|    tf * KOMAP_wgt * GAME (LOG NOR) KMeans    |     0.717     |          -         |      0.743     |          -          |    0.675     |         -         |

# Report
## Methods
1. "LOG" refers to taking the logarithm of the count in term frequency (tf).
2. "NOR" involves normalizing each patient's embedding.

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
|    tf * KOMAP_wgt * GAME (LOG NOR)       |   **0.865**   |       0.811        |      0.818     |        0.782        |    0.754     |     **0.793**     |
|   tfidf * GAME_cosine * GAME (LOG)       |     0.839     |     **0.838**      |      0.829     |        0.792        |    0.791     |       0.770       |
| tfidf * GAME_cosine * GAME (LOG NOR)     |     0.850     |       0.811        |      0.777     |        0.733        |    0.750     |       0.721       |
| tfidf * GAME_cosine^2 * GAME (LOG)       |     0.797     |       0.757        |      0.770     |        0.733        |    0.749     |       0.767       |
| tfidf * GAME_cosine^3 * GAME (LOG)       |     0.818     |       0.811        |      0.844     |        0.782        |  **0.828**   |       0.751       |

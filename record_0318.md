# Results

| Metric          | Data Source    | AUC | Accuracy | Recall | Precision | F1 Score |
|-----------------|----------------|-----|----------|--------|-----------|----------|
| Main PheCode    | UPMC Registry  |     |          |        |           |          |
|                 | UPMC Chart     |     |          |        |           |          |
|                 | MGB Chart      |     |          |        |           |          |

| Metric          | Data Source    | AUC | Accuracy | Recall | Precision | F1 Score |
|-----------------|----------------|-----|----------|--------|-----------|----------|
| KOMAP           | UPMC Registry  |     |          |        |           |          |
|                 | UPMC Chart     |     |          |        |           |          |
|                 | MGB Chart      |     |          |        |           |          |


## No Log No Normalize 

| Metric          | Data Source    | AUC | Accuracy | Param|
|-----------------|----------------|----------|--------|--------|
|                 | UPMC Registry => UPMC Chart     | 0.754|  0.682  |  (1e-6,4) |
|                 | UPMC Registry => MGB Chart      | 0.763 | 0.635  |  (1e-6, 768) |
| GAME            | UPMC Registry  |0.828   |  0.800  | (1e-5, 768)   |
|                 | UPMC Chart     |0.785  | 0.752   | (1e-5,3)  |
|                 | MGB Chart      |0.825  | 0.811     | (10,4) |

## Log No Normalize 

| Metric          | Data Source    | AUC | Accuracy |Param| 
|-----------------|----------------|----------|--------|-------|
|                 | UPMC Registry => UPMC Chart     |0.760  | 0.721   | (1e-3, 768)| 
|                 | UPMC Registry => MGB Chart      |0.752  | 0.784     | (1e-3, 768) |
| GAME            | UPMC Registry  |0.791   |  0.770  | (1e-4, 768) |
|                 | UPMC Chart     |0.816  | 0.752   | (1e-3, 768) |
|                 | MGB Chart      |0.839  | 0.838     | (1e-1, 768) |

## No Log Normalize 

| Metric          | Data Source    | AUC | Accuracy |Param| 
|-----------------|----------------|----------|--------|-------|
|                 | UPMC Registry => UPMC Chart     |0.752  | 0.711   | (1e-1, 768)| 
|                 | UPMC Registry => MGB Chart      |0.774  | 0.703    | (1e-2, 768) |
| GAME            | UPMC Registry  |0.822   |  0.808  | (1, 768) |
|                 | UPMC Chart     |0.754  | 0.713   | (1e+2, 3) |
|                 | MGB Chart      |0.851  | 0.811     | (1e+2, 3) |

## Log Normalize 

| Metric          | Data Source    | AUC | Accuracy |Param| 
|-----------------|----------------|----------|--------|-------|
| GAME            | UPMC Registry  |0.791   |  0.770  | (1e-4, 768) |
|                 | UPMC Chart     |0.816  | 0.752   | (1e-3, 768) |
|                 | MGB Chart      |0.839  | 0.838     | (1e-1, 768) |
|                 | UPMC Registry => UPMC Chart     |0.760  | 0.721   | (1e-3, 768)| 
|                 | UPMC Registry => MGB Chart      |0.752  | 0.784     | (1e-3, 768) |


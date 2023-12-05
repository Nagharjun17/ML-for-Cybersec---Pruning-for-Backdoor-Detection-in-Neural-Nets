# ML-for-Cybersec---Pruning-for-Backdoor-Detection-in-Neural-Nets

## ECE-GY 9163 - ML for Cyber Security, Fall 2023

### Author
Nagharjun M (nm4074)

## Introduction

This report contains explanations for the findings in Lab 4 - Designing and Evaluating a Pruning-Based Backdoor Detector for Neural Networks. Pruning defence is applied to a compromised BadNet model trained on the YouTube Face dataset, aiming to disable the backdoor while preserving accuracy for clean inputs. Further findings, based on various pruning levels, provide insights into balancing network integrity with robustness against backdoor attacks.

## Dataset

The YouTube Face dataset is used in this experiment which is further divided into clean and poisoned subsets. I use clean validation and test sets (valid.h5 and test.h5) to fine-tune and assess the model. For backdoor simulation, poisoned datasets with a sunglasses trigger (bd\_valid.h5 and bd\_test.h5) are used to test the defence.

## Workflow

I implemented a pruning defense on a neural network, selectively removing channels based on activation levels until accuracy dropped by predefined thresholds (2\%, 4\%, 10\%). Using TensorFlow and Keras, I evaluated the pruned models against both original and poisoned data, classifying inputs as clean or backdoored based on model agreement. This approach aimed to balance accuracy with effective backdoor detection.

## Running the Code

To run this project, follow the steps below:

1. Upload the `lab4.ipynb` notebook to Google Colab or Jupyter Notebook environment.
2. Ensure the following data files are uploaded to your Google Drive:
    - BadNet weights file
    - Benign data content (`valid.h5` and `test.h5`)
    - Poisoned data content (`bd_valid.h5` and `bd_test.h5`)
3. Mount your Google Drive in the Colab notebook to access the datasets:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')

## Results

The following table shows the accuracy and attack rate of the repaired models at different pruning thresholds:

| Model         | Repaired Clean Accuracy | Attack Rate |
|---------------|-------------------------|-------------|
| 2% Repaired   | 95.7443                 | 100         |
| 4% Repaired   | 92.1278                 | 99.9844     |
| 10% Repaired  | 84.3336                 | 77.2097     |

![Comparison of Repaired Clean Accuracy and Attack Rate for each pruned model]([![image](https://github.com/Nagharjun17/ML-for-Cybersec---Pruning-for-Backdoor-Detection-in-Neural-Nets/assets/64778259/6cd6478e-9c26-4586-b497-858293110b59)](https://private-user-images.githubusercontent.com/64778259/287902948-d0c0d9a5-59ac-4021-8c84-e16937983b17.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTEiLCJleHAiOjE3MDE3NDUyMzgsIm5iZiI6MTcwMTc0NDkzOCwicGF0aCI6Ii82NDc3ODI1OS8yODc5MDI5NDgtZDBjMGQ5YTUtNTlhYy00MDIxLThjODQtZTE2OTM3OTgzYjE3LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFJV05KWUFYNENTVkVINTNBJTJGMjAyMzEyMDUlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjMxMjA1VDAyNTUzOFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTBiNjI0YTEzYmEwY2JlZjY2MzdjOTMwNGZlNzlkMzg0MDY3ODhiYjUwMzUyNDc4Njc1NzdjNTNkNTk1MzhkOGQmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.JrwwVjOny0ReD5FRThcambyt6ozR-JU16CqI7uHHrkI)https://private-user-images.githubusercontent.com/64778259/287902948-d0c0d9a5-59ac-4021-8c84-e16937983b17.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTEiLCJleHAiOjE3MDE3NDUyMzgsIm5iZiI6MTcwMTc0NDkzOCwicGF0aCI6Ii82NDc3ODI1OS8yODc5MDI5NDgtZDBjMGQ5YTUtNTlhYy00MDIxLThjODQtZTE2OTM3OTgzYjE3LnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFJV05KWUFYNENTVkVINTNBJTJGMjAyMzEyMDUlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjMxMjA1VDAyNTUzOFomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTBiNjI0YTEzYmEwY2JlZjY2MzdjOTMwNGZlNzlkMzg0MDY3ODhiYjUwMzUyNDc4Njc1NzdjNTNkNTk1MzhkOGQmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0JmFjdG9yX2lkPTAma2V5X2lkPTAmcmVwb19pZD0wIn0.JrwwVjOny0ReD5FRThcambyt6ozR-JU16CqI7uHHrkI)



*Figure: Comparison of Repaired Clean Accuracy and Attack Rate for each pruned model.*

The results show that as the pruning threshold increases from 2\% to 10\%, the repaired model's accuracy on clean validation data decreases. This shows that there is a trade-off between accuracy and removing the backdoor. So, the thresholding should be chosen properly.


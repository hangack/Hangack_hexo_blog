---
title: 평가지표 RMSE와 MAE, MSE
categories:
  - 빅데이터
  - 통계
tags:
  - 빅데이터
  - 수식
date: 2021-11-12 14:52:57
---
  
## DATA

Row(행)가 $n$개 있는 dataframe에서;
실측 값에 대한 dataframe의 column(열)을 $Y$로 봤을 때,

$Y$는 다음과 같은 원소의 집합이 된다.
$$
Y=
\begin{pmatrix}
    y_1 \\
    y_2\\
    \vdots\\
    y_n
\end{pmatrix}
$$

모델링 결과 등 $Y$에 대한 추정값의 집합이 $\hat{Y}$다.
$$
\hat Y=
\begin{pmatrix}
    \hat y_1 \\
    \hat y_2\\
    \vdots\\
    \hat y_n
\end{pmatrix}
$$

## 평가 지표

실측값$Y$와 추정값$\hat Y$가 있으니 두 값의 차이인 오차(error: $\Delta y_i = y_i-\hat{y_i}$)가 발생한다.
$\Delta y_i$를 여러 방식으로 가공해서 측정값의 신뢰도를 보여주는게 평가 지표다.

다양한 평가지표 중 RMSE에 관해 공부할 것이며, MSE, MAE는 RMSE와 매우 유사한 형태를 가진다.

### MAE(Mean Absolute Error): 평균 절대 오차

$$MAE=\sum_{i=1}^n\frac{\vert y_i-\hat{y_i}\vert}{n}$$

$\Delta y_i$의 절대값을 모두 더한 값의 평균이다.

### MSE(Mean Squared Error): 평균 제곱 오차

$$MSE=\sum_{i=1}^n\frac{(y_i-\hat{y_i})^2}{n}$$

$\Delta y_i$의 제곱을 모두 더한 값의 평균이다.

### RMSE(Root Mean Square Error): 평균 제곱근 오차

$$RMSE=\sqrt{\sum_{i=1}^n\frac{(y_i-\hat{y_i})^2}{n}}$$

$\Delta y_i$의 제곱을 모두 더한 값의 평균에 Root를 씌운 형태로 $\sqrt{MSE}=RMSE$다.


#### 특징

위 세 지표는 모두 오차 그 자체인 $y_i-\hat{y_i}$를 포함해 값이 낮을수록 좋은 추정모델임을 의미한다.
단, 실측값과 추정값의 차에 지나치게 의존하는 경향을 보여 $3-1=2$와 $100-102=2$ 모두 동일한 평가로 보여진다.

위 세 지표는 오차 자체에 의존하는 만큼 직관적인 지표가 나와 대중에게 설명하기 좋다.
MAE로 예를 들자면, 600과 620의 차는 20이므로 20의 예측 오류가 발생했다고 설명할 수 있다.

MSE의 경우 오차 제곱하기 때문에 $\vert error\vert<1$일 경우 error값은 작아지고 반대의 경우 커지는 왜곡이 발생한다.
RMSE에서는 MSE에 Root를 씌웠기 때문에 MSE만큼의 왜곡은 발생하지 않는다.


## python

간단한 예시로 아래의 $Y_1$과 $Y_2$ python 예제가 있다.

### MAE

```python
import numpy as np

def mean_absolute_error(y_true, y_pred):

    error = 0
    for yt, yp in zip(y_true, y_pred):
        error = error + np.abs(yt-yp)
  
    mae = error / len(y_true)
    return mae
```

### MSE

```python
import numpy as np

def mean_squared_error(y_true, y_pred):

    error = 0
    for yt, yp in zip(y_true, y_pred):
        error = error + (yt - yp) ** 2
  
    mse = error / len(y_true)
    return mse
```

### RMSE

```python
import numpy as np

def root_rmse_squared_error(y_true, y_pred):
    error = 0
  
    for yt, yp in zip(y_true, y_pred):
        error = error + (yt - yp) ** 2
  
    mse = error / len(y_true)
    rmse = np.round(np.sqrt(mse), 3)
    return rmse
```

```python
y1_true = [400, 300, 800]
y1_pred = [380, 320, 777]

y2_true = [400, 300, 800, 900]
y2_pred = [380, 320, 777, 600]
```

```python
print("MAE:", mean_absolute_error(y1_true, y1_pred))
print("MSE:", mean_squared_error(y1_true, y1_pred))
print("RMSE:", root_rmse_squared_error(y1_true, y1_pred))
```

    MAE: 21.0
    MSE: 443.0
    RMSE: 21.048
    


```python
print("MAE:", mean_absolute_error(y2_true, y2_pred))
print("MSE:", mean_squared_error(y2_true, y2_pred))
print("RMSE:", root_rmse_squared_error(y2_true, y2_pred))
```

    MAE: 90.75
    MSE: 22832.25
    RMSE: 151.103


오차값이 20~30 사이에서 놀다가 $\Delta y=300$인 이상값이 하나 들어가면서 지표가 지나치게 커짐을 확인할 수 있다.
마찬가지로 MSE와 RMSE의 왜곡 차이도 확연히 드러난다.
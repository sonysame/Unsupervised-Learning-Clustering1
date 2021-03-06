# Unsupervised-Learning-Clustering1

비지도학습 - 클러스터링(Clustering), 차원압축(Dimensionality Reduction), 이상감지(Anomaly Detection)

입력데이터 X를 사용하지만, 클래스 데이터 T는 사용하지 않는다.<br/>
#### 클러스터링: 클래스 정보 없이, 입력 데이터가 비슷한 것끼리 클래스로 나누는 것

지도 학습 문제는 클래스가 있는 데이터였고, 미지의 x에 대한 클래스를 예측하는 것이 목적이었다<br/>

클러스터링의 대표적인 알고리즘 -> **K-means 기법, 가우시안 혼합 모델**

## K-means 기법
### Step 0: 변수의 준비와 초기화
Mu: 클러스터의 중심 벡터, R: 각 데이터의 클래스 지시 변수

### *K-means.py*
![image](https://user-images.githubusercontent.com/24853452/103458098-2d6c7a00-4d48-11eb-88e2-060f4a6d0b06.png)

### Step 1: R의 갱신
각 데이터 점을 가장 중심이 가까운 클러스터에 넣어 R을 갱신
![image](https://user-images.githubusercontent.com/24853452/103458101-36f5e200-4d48-11eb-9890-832b408f528e.png) 

### Step 2: Mu의 갱신
각 클러스터에 속하는 데이터 점의 중심을 새로운 Mu로 갱신
![image](https://user-images.githubusercontent.com/24853452/103458256-a0c2bb80-4d49-11eb-995e-f5b9e9d9c8ad.png)

이후에는 Step 1과 Step 2의 절차를 반복하여 변수의 값이 변화하지 않으면 프로그램 종료 <br/>
이 경우, 총 6회 반복으로 변화하지 않게 되었다.

### *K-means-6times.py*
![image](https://user-images.githubusercontent.com/24853452/103458372-9654f180-4d4a-11eb-9c48-913047795baf.png)

### 왜곡척도(Distortion Measure)
K-means 기법의 경우, 데이터 점이 속한 클러스터의 중심까지의 제곱거리를 전체 데이터로 합한 것<br/>
[627.54  73.39  70.39  57.59  48.31  47.28  46.86  46.86  46.86  46.86] <br/>

Step 6에서 왜곡 척도의 값이 멈춘다. 이는 Mu와 R의 값이 변화하지 않는 것을 의미한다.<br/>

### *Distortion-Measure.py*
![image](https://user-images.githubusercontent.com/24853452/103458549-9950e180-4d4c-11eb-832e-bdbb4444d815.png)

## 가우시안 혼합 모델
### 확률적 클러스터링
K-means 기법은 데이터 점을 반드시 클러스터에 할당<br/> -> 클러스터 k에 속할 확률로 확장<br/>
**가우시안 혼합 모델** : 2차원 가우스 함수 여러 개를 합친 것
각각의 k에 대해 pi, mu, sigma

### *Gaussian-Mixture-Model.py*
![image](https://user-images.githubusercontent.com/24853452/103460965-13d62d00-4d5e-11eb-9f5b-c5080d84ba8b.png)

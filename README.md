r-misdemeanor :gun:
===
---

### 1. Subject
 범죄가 발생하는 원인을 파악해보고자 범죄를 경범죄와 중범죄로 나누어서 각각의 원인을 파악하고, <br>
 경범죄와 중범죄의 발생 원인을 비교해 보는 과정을 통하여 의미있는 결론을 도출하고자 함.

---

### 2. Data
다양한 성향을 가진 주들이 존재하고 원하는 모든 데이터를 얻을 수 있는 **미국의 주** 별 데이터 사용. 

표1)
feature name|contents|reference
:---:|:---:|:---:
area_police|주 별 경찰당 면적|
Penalty|경범죄 : 주별 평균 수감 기간 / 중범죄 : 주별 GDP 당 벌금|
Travel|여행으로인한 주 별 소비|
Temperature|주 별 평균 기온|
GDP|주 별 1인당 GDP|
MSA|주 별 인구의 도시 밀집도|
Happy|주 별 행복도|
Gun_ownership|주 별 가정에서 총기를 소유하는 평균 비율|
PCPI|주 별 개인당 수입|
Gender|주 별 여성의 비율|
Old_rate|주 별 65세 인구의 비율|
Education|주 별 학생 1명 당 공교육비|


<br>
표2)

feature name|contents|reference
:---:|:---:|:---:
Felony|주 별 중범죄 count|
Misdemeanor|주 별 경범죄 count|
Politics|주 별 정치적으로 지지하는 곳|
Region|주 별 위치하는 지역|
Gini_coff|주 별 사회적 불평등 지수|

---

### 3. File
파일 별 의미 대략 정리

+ **Misdemeanor.ipynb** : 표1의 features와 표2의 Misdemanor를 사용, LinearRegression을 이용하여 분석
+ **Misdemeanor(al,ha-x).ipynb** : alaska와 hawaii를 제거하고 위와 같이 분석
+ **GLM.ipynb** : 표1의 features와 표2의 Misdemanor를 사용, GLM을 이용하여 분석
+ **Misdemeanor_politics.ipynb** : 표2의 Misdemeanor와 politics 사용, LinearRegression을 이용하여 분석
+ **Misdemeanor_region.ipynb** : 표2의 Misdemeanor와 region 사용, LinearRegression을 이용하여 분석
+ **Felony.ipynb** : 표1의 features와 표2의 Felony를 사용, LinearRegression을 이용하여 분석
+ **Misdemeanor_Felony.ipynb** : Misdemeanor분석과 Felony분석을 비교
+ **logistic.ipynb** : 표1의 features와 표2의 Misdemanor, Felony를 사용, Logistic을 이용하여 분석
+ **Gini_coff.ipynb** : 표2의 Misdemanor, Felony, Gini_coff를 사용, LinearRegression을 이용하여 분석
+ **DecisionTree.ipynb** : Misdemeanor, Felony분석을 DeicisionTree를 사용하여 tree 분석

---
### 4. Model
##### 1) Regression
######  i. Linear : 종속 변수 y와 한 개 이상의 독립 변수 (또는 설명 변수) X와의 선형 상관 관계를 모델링하는 회귀분석 기법. 
![image](https://user-images.githubusercontent.com/55525705/136329638-f3a2cac1-875d-4cf6-aafa-d579b0d44d84.png)

<br>

######  ii. Logistic : 로지스틱 회귀의 목적은 일반적인 회귀 분석의 목표와 동일하게 종속 변수와 독립 변수간의 관계를 구체적인 함수로 나타내어 향후 예측 모델에 사용하는 것. 흔히 로지스틱 회귀는 종속변수가 이항형 문제(즉, 유효한 범주의 개수가 두개인 경우)를 지칭할 때 사용됨.
![image](https://user-images.githubusercontent.com/55525705/136330951-1e809cfa-b971-448d-81ff-25fe493b9803.png)

<br>

##### 2) DecisionTree : 결정 트리(Decision Tree, 의사결정트리, 의사결정나무라고도 함)는 분류(Classification)와 회귀(Regression) 모두 가능한 지도 학습 모델 중 하나. 이렇게 특정 기준(질문)에 따라 데이터를 구분하는 모델을 결정 트리 모델이라고 함.
![image](https://user-images.githubusercontent.com/55525705/136331693-c34eaf56-3ce4-4370-bbcb-5ebc8bf9d567.png)

<br>


---

### 5. Result
#### 1) 경범죄와 중범죄 사이의 차이가 존재함
![image](https://user-images.githubusercontent.com/55525705/136332129-5edd1a64-f24e-43e0-b85b-8debb9e269f1.png)

<br>

#### 2) regression을 이용하여 명확하게 두 범죄의 경향 차이 시각화 (target data 한 개당 feature data 한 개 사용)
ex) 행복도
![image](https://user-images.githubusercontent.com/55525705/136332382-93126137-ae3a-4d8f-b489-e29967089974.png)

<br>

전체 요소들의 correlation값 비교


![image](https://user-images.githubusercontent.com/55525705/136332471-7e614161-b851-4aa5-b0eb-05c2621a7845.png)

<br>

#### 3) decision tree를 이용해서 모든 feature를 사용했을 때와 한 개의 feature를 사용했을 때 차이 비교

<br>

![1](https://user-images.githubusercontent.com/55525705/142335544-99888e2e-53fd-413f-b91c-bec550620419.JPG)
오른쪽은 경범죄의 feature importance / 왼쪽은 중범죄의 feature importance


<br><br>

##### 주 별로 경범죄와 중범죄의 count를 그려보는 과정을 통하여 한 범죄의 발생 양상이 다른 범죄의 발생 양상을 따라가지는 않는 다는 것을 발견. 
##### 데이터를 수집한 12가지의 요소들을 이용하여 regression을 그리고 correlation을 구하는 과정을 통하여 각 범죄 별로 발생 원인을 파악하고 비교해 보고자 함.
##### 주 별 행복도와 총기 소지율이 반대되는 correlation을 가졌으며 면적 당 경찰 비율과 패널티 등등의 요소들이 correlation값이 큰 차이를 보임.
##### 이를 통하여 앞에서 언급한 요소들이 두 범죄의 발생 양상의 차이를 특징지을 수 있는 요소들임을 파악 가능.

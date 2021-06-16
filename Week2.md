# Deeplearning_Coursea
2021 하계 딥러닝

Binary Classification

- Output y 가 0 or 1 을 치역으로 가지는 판단 문제를 이야기한다.


이미지의 Classification

- 이미지는 어떤 형태의 데이터인가? 이번 수업에서는 64 X 64 크기의 이미지를 사용한다고 하자.
- 빛의 3원소는 빨, 녹, 청 이다. 보통 이미지는 64 X 64 Matrix 에, 3원소에 대한 각각의 가중치를 합쳐서 만들어진다.
- 그말인 즉슨 이미지를 구성하는 원본 소스는 64 X 64 X 3 의 크기를 가진다는 뜻 이다. (상기한 size 의 Matrix 3개에 해당하는)

- 우리는 따라서, 1개의 Dataset 은 여기서 64 X 64 X 3 = 12288 차원의 Input , 1 or 0 Output 을 지닌다고 정의할 수 있다.


Dataset

- X matrix 는 전체 Dataset 의 Input 을 모두 저장하는 Matrix 이다.
- 1열벡터씩 Data 가 쌓인다. 즉, N 차원 데이터 x 가 m 회차만큼 쌓인다.
- 따라서, X 의 크기는 N X m 이다.
- Y 의 경우, 1차원 데이터 y 가 m 회차 쌓이므로 1 X m 이다. 

- 한 Dataset 은 y = wx + b 와 같은 연산을 실시한다. 이때 우리의 목표는 w 와 b 를 최적화하는 것이다.
- W 는 N 차원 벡터 xi 와 조화되어 1차원 y 를 구성하므로 마찬가지로 N 차원 벡터인 것이 자명하다. 
- b 는 1차원 값에 대한 Linear 한 가중치 이므로 단순 스칼라인 것이 자명하다.



y' of Logistic Regression 

- y' 을 어떻게 정의할 것인가? 
- 익숙한 Linear Regression 문제에서는, y = wx + b 를 통해 y 를 추정하였었다.
- 이번 문제에서는 위의 식을 그대로 사용할 수 없다. y 의 범위가 사실상 실수 전체인데, 실제 문제는 1 또는 0 이기 떄문이다.


- Linear 가중치를 조정해 간다는 아이디어를 그대로 가져가되, 치역의 범위를 조정하고 싶다.
- 위 조건을 만족하는 함수가 Sigmoid 함수이다.
- Sigmoid 는 다음과 같은 특성들을 지닌다 : 치역이 0~1 사이이다 / 평균이 0.5 이다 / 정의역이 실수 전체이다.

- Linear Regression 의 추정 공식을 Sigmoid 에 얻음으로써 Logistic Regression 에 사용할 y' 공식을 얻는다. 



Cost & Loss Function 

- Linear Regression 에서는, y - y' 을 제곱함으로써 Cost 를 얻은 바 있었다.
- 이번에 새로 정의한 y' 에서는 결론부터 말하자면 그 방법을 사용할 수 없다.
- Cost Function 의 개형이 Convex( = 위 또는 아래로 볼록한 2차원 함수) 형태로 얻어지지 않기 때문이다.
- Optimized 한 해석을 찾기 위해, Convex 한 Cost 를 얻기 위한 수식을 새로이 설계하여야 한다.

- 그렇게 설계된 Loss Function 의 구조는 다음과 같다()
- 이렇게 되면 y 와 y' 가 다르면 다를수록 Loss 가 극한까지 커지고, 같으면 같을수록 Loss 가 점점 0으로 수렴한다.

- 이러한 Loss 는 개별적인 Dataset 회차들에 대하여 정의된다.
- m 개의 Dataset에 대하여 Linear 하게 Loss 를 평균낸 것이 곧 Cost Function 이 된다.


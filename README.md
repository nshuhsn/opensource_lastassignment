# opensource_lastassignment
## SVM(Support Vector Machine)을 이용한 학습
1.SVM을 사용하여  진행한 이유는 분류과제를 수행해야 했기 때문이고, 분류과제를 위한 대부분의 모델을 사용해본 결과 SVM이 정확도가 가장 높게 나왔기 때문입니다.
2.SVM은 분류를 위한 기준 선을 정의하는 모델입니다. 새로운 점이 나타나면 그어진 경계의 어느쪽에 속하는지를 분류합니다. 이때 경계는 어떻게 정의할까요?
  경계는 일반적으로 데이터 군으로 부터 최대한 멀리 떨어져 있어야 합니다. 이때 그 거리를 뜻하는 마진이 최대화가 되는 경계를 결정 경계로 정의합니다.
  만약 점들 중에 혼자서 데이터 군으로 부터 떨어진 이상치가 존재할때, 이 것들을 허용하지 않고 기준을 까다롭게 만든다면 이것을 하드 마진이라고 부르고,
  너무 심할 결우 오버피팅이 발생합니다. 만약 이상치를 너무 너그럽게 잡을 경우 소프트 마진이라고 하고 이것은 언더피팅을 유발할 수 있습니다.
  이를 위해 파라미터 c가 존재하는데 여러가지 값을 대입해본 결과 10일때 최대의 정확성을 보여주어 따로 바꾸진 않았습니다. tol의 경우에는 기본값은 1e-3 이지만 0.1로 바꾸어 주었을때 가장 정확
  성이 높기에 0.1로 설정해 주었습니다. 우리가 분류하는 데이터는 충분히 선형으로 결정 경계를 생성할 수 있기에 linear로 커널을 설정했습니다. gamma의 경우에는 default일때의 정확도도 같지만 
  C를 설정하면서 같이 해보았습니다.
```
SvcLearning = SVC(kernel="linear" ,C = 10, gamma=0.01, tol = 0.1)
SvcLearning.fit(X_train, y_train)
y_pred = SvcLearning.predict(X_test)
```
첫번째 줄에서 위에서 말한 매개변수들로 설정하고,
두번째 줄에서 X_train과 y_train에 따라 SVM 모델을 피팅하고
세번째 줄에서 X의 샘플에 대한 분류를 수행합니다.

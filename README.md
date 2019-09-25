# 초기값이란

초기값 설정이란 딥러닝 모델에서 가중치를 학습시킬 때 처음 들어가는 가중치를 말하며 초기값 설정에 대해 알려진 사실 중 하나는 초기값을 모두 똑같은 상수로 하거나 0으로 설정하면 안된다는 것이다. 초기값을 모두 똑같은 상수로 설정하면 신경망에 있는 모든 노드(node)들은 같은 신호 값을 받게 된다. 이에 따라 각 출력 노드의 출력 값 역시 똑같은 값으로 나오게 된다. 또한 오차를 역전파(backpropagation)함으로써 가중치를 업데이트하는 과정에서 오차는 모두 같은 값으로 나뉘어 전파되고 결국 동일한 가중치 업데이트로 이어지게 된다. 이는 또다시 동일한 값을 가지는 가중치라는 결과로 이어지게 된다. 보통 동일한 가중치를 가지는 것을 대칭이라고 표현한다. 결국 같은 입력에 대해 동일하거나 대칭적인 가중치로 초기값을 설정하면 활성화 함수를 거치면서 같은 방향으로 계속 집중될 수밖에 없고 결국 동일한 계산을 수행하며 네트워크 전체를 대칭으로 만들게 되는 것이다 

# 기존 초기값방법

|  Popular initialization methods  | Feature | 
|:--------|:--------:|
| LeCun(Uniform) | 상한과 하한의 값에 따라 분포 변화가 가능하고 초기값이 모두 똑같은 상수로 설정되는 것을 제한할 수 있음 | 
| LeCun(Normal)| 평균과 분산 값에 따라 분포 변화가 가능하고 초기값은 주로 평균값 0 주위에서 많이 설정되도록 할 수 있음   | 
| Truncated normal| 작은 확률이지만 정규분포의 꼬리 부분에서 큰 초기값이 뽑힐 수 있기 때문에 양쪽 꼬리를 절단시킴으로써 큰 초기값이 나오는 것을 제한함 | 
| Xavier | 각층의 입력과 출력에 대한 분산값을 동일하게 함으로써 포화 현상을 방지할 수 있고 활성화 함수 sigmoid, tanh에서 효과적 | 
| He |활성화 함수 relu를 제안하면서 relu가 음수 쪽 신호를 완전히 없애 버린다는 것에서 착안해 분산을 두배 해줌으로써 분산을 유지 시켜준 relu에 최적화된 초기값 설정 방법 | 

# 새로운 초기값 설정방법
초기값을 설정하는 분포로 절단된 정규분포와 절단된 코쉬 분포를 고려하였다. 코쉬 분포는 정규분포보다 0에 더 몰려있고 양쪽 꼬리가 더 얇기 때문에양쪽 끝을 절단할 경우 초기치가 0 근처에서 뽑힐 확률이 더 높을 수 있다. 절단된 정규분포와 절단된 코쉬 분포를 각각 Xavier initialization 방법에 적용
후 초기값을 설정한다면 기존의 한계점을 보완하고 좋은 성능을 보임

# 데이터 
![대체 텍스트(alternative text)를 입력하세요!](http://www.gstatic.com/webp/gallery/5.jpg "링크 설명(title)을 작성하세요."

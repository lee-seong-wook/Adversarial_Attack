### 적대적 공격이란?

적대적 공격(Adversarial Attack)은 기계 학습 모델을 속이기 위해 설계된 입력 데이터의 수정입니다. 이러한 수정은 인간이나 다른 기계 학습 모델에는 거의 눈에 띄지 않지만, 목표 모델에 대해 잘못된 예측을 유도하거나 원하는 출력을 얻기 위해 조작됩니다.

### FGSM (Fast Gradient Sign Method)

FGSM은 적대적 공격의 간단하면서도 효과적인 기법 중 하나입니다. 다음과 같은 단계로 작동합니다:

1. **기울기 계산:** 목표 모델에서 입력 이미지의 손실 함수를 통해 기울기를 계산합니다.
   
2. **기울기의 부호 활용:** 입력 이미지의 각 픽셀에 대해 기울기의 부호를 이용하여 방향을 설정합니다. 목표는 손실을 최대화하도록 이미지를 조정하는 것입니다.
   
3. **입력 이미지 조정:** 설정된 방향으로 이미지를 작은 양의 엡실론(epsilon) 값으로 조정하여 적대적 예제를 생성합니다.
   
4. **클리핑:** 생성된 적대적 예제는 픽셀 값이 허용 범위를 초과하지 않도록 클리핑하여 이미지의 자연스러움을 유지합니다.

### 사용 방법

1. **설치 및 준비:**
   - 이 저장소를 로컬 머신에 클론합니다.
   - 필요한 라이브러리 (`torch`, `torchvision`, `matplotlib`, `requests`, `PIL`)가 설치되어 있는지 확인합니다.

2. **적대적 공격 실행:**
   - 대상 이미지를 지정된 디렉토리에 넣습니다 (예: `path_your_img.jpg`).
   - 스크립트를 실행하기 위해 `python adversarial_attack.py`를 실행합니다.

3. **설명:**
   - 스크립트는 ImageNet에서 사전 학습된 ResNet-18 모델을 사용하여 분류를 수행합니다.
   - 이미지를 로드하고, 모델에 적합한 텐서로 전처리한 후 출력을 계산합니다.
   - FGSM을 사용하여 손실을 최대화하기 위해 이미지를 왜곡합니다 (정확한 클래스에 대한 신뢰도를 낮춤).
   - 생성된 적대적 이미지를 다시 분류하여 모델의 견고성을 관찰합니다.

### 예시

  ![Adversarial Image](https://github.com/lee-seong-wook/Adversarial_Attack/assets/130055880/75be9070-7eee-4650-82ea-a2589e9e542d)

### 참고 사항

- `epsilon` 값을 조정하여 왜곡의 크기를 제어할 수 있습니다. 높은 값은 적대적 이미지에서 더 큰 변화를 초래할 수 있습니다.
- 응용 프로그램에서 원본 데이터셋과 모델 소스에 대한 적절한 어트리뷰션을 보장하세요.

더 많은 모델, 데이터셋 또는 공격 전략을 실험하고 수정하는 것에 자유롭게 도전해 보세요. FGSM 기법과 그 영향에 대한 자세한 내용은 [Goodfellow et al., 2014](https://arxiv.org/abs/1412.6572)를 참조하세요.

### 추가 정보

#### 기능 설명

이 저장소의 주요 기능은 다음과 같습니다:

- **모델 설정:** ImageNet에서 사전 학습된 ResNet-18 모델을 사용하여 이미지 분류를 수행합니다.
- **적대적 공격 생성:** FGSM 기법을 활용하여 원본 이미지를 왜곡시켜 적대적 예제를 생성합니다.
- **시각화:** 생성된 적대적 이미지와 원본 이미지를 비교하여 시각적으로 확인할 수 있는 기능을 제공합니다.

#### 사용자 정의
![96018f12-68a1-428d-823c-c43c4a96ee84]

사용자는 다음과 같은 방식으로 이 저장소를 활용할 수 있습니다:

- 새로운 이미지를 추가하고, 해당 이미지에 대해 적대적 공격을 실행하여 모델의 강건성을 테스트할 수 있습니다.
- 다양한 모델을 시도하거나 다른 데이터셋에 대해 같은 접근 방식을 적용하여 비교 및 분석을 수행할 수 있습니다.
- 코드를 수정하여 다른 공격 기법을 구현하거나 추가적인 시각화 기능을 개발할 수 있습니다.





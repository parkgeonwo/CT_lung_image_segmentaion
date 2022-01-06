# CT_lung_image_segmentaion
using CNN-Encoder-Decoder model / CT_lung_image_segmentaion

### 목표 : CT 이미지 (인풋)에서 폐 영역 마스크 (아웃풋)을 예측해내는 인공지능 모델 만들기

<img width="40%" src="https://user-images.githubusercontent.com/87109907/148348520-e0ba1a93-cb89-433d-be37-4004eeb11e46.png"/>

### dataset

https://www.kaggle.com/kmader/finding-lungs-in-ct-data?select=2d_images.zip

왜 폐 영역을 분리하는 문제를 풀어야 하는가 ?

폐결핵, 폐암, 폐렴을 인공지능이 진단하기 위해서는 우선 폐영역을 정확히 분리해낼 필요가 있다.

1. 폐가 어딨는지 알아낸다.
2. 폐 영역안에서 폐렴, 폐암 등의 가능성을 검토한다.

### 모델 설명

<img width="40%" src="https://user-images.githubusercontent.com/87109907/148348734-ae3cc642-74fc-495c-9610-020c99801596.png"/>

CNN으로 이루어진 Convolutional encoder-decoder

encoder : 차원을 축소해서 핵심 요소만 뽑아낸다.

decoder : 압축된 정보로부터 차원 확장을 통해 원하는 정보를 복원한다.

input은 ct사진 output은 0과 1로 폐와 폐가아닌 부분으로 나눈다.

Downsampling은 MaxPooling2D을 사용

Upsampling은 UpsamPling2D을 사용

마지막엔 시그모이드 계층이 0과 1로 나눠준다.

upsampling이 뭐냐 ?

<img width="40%" src="https://user-images.githubusercontent.com/87109907/148348775-b4c6ca02-4f65-4e65-a567-b4c917f9e79f.png"/>

목표 : 

차원을 줄여서 핵심정보만 뽑아낸다음에 다시 차원을 늘려서 마스크를 뽑아낼것이다.

사용 기술 :

training:

- Python
- numpy
- keras
- matplotlib

preprocessing :

- skimage
- sklearn
- pandas

참고 사이트 :

youtube :
https://www.youtube.com/watch?v=z8lK69BQ0VE

skimage 설명 :
https://aciddust.github.io/blog/post/scikit-Python-%EC%9D%B4%EB%AF%B8%EC%A7%80-%EC%B2%98%EB%A6%AC-%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC/
https://runebook.dev/ko/docs/scikit_image/api/skimage.transform![image](https://user-images.githubusercontent.com/87109907/148348926-1a15edcf-176b-4940-af87-43da34ef2512.png)











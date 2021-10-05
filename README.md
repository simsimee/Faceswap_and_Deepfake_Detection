# Faceswap_and_Deepfake_Detection

## 딥페이크 구현과 탐지

### 프로젝트 기획
딥페이크 기술이 발전함에 따라 딥페이크 기술을 악용하는 사례가 증가하고있다.
그에 따라 일반 사람들도 자신이 보는 영상이 딥페이크인지 아닌지 탐지할 수 있는 프로젝트를 기획하게 되었다.

### 딥페이크 구현 (Face_swap)

### 사용한 라이브러리, 툴
- Pytorch
- pretrained model (Voxceleb dataset으로 학습된 모델)
- 논문 저자 공식 Repository 의 part_swap.py 의 함수 이용

### 방법론

![image](https://user-images.githubusercontent.com/75903850/134393978-46113f0f-809d-4430-b4d1-236fddf945b8.png)

타겟 비디오의 프레임에 segmentation을 진행하고, 소스 프레임의 segment를 이용하여 타겟 비디오 프레임을 reconstruct 하는 방식으로 결과물을 도출할 수 있다. 타겟 프레임의 모션을 유지하면서 소스 프레임의 정체성을 가져오는 것이 특징이다.


![입술 변형](https://user-images.githubusercontent.com/75903850/134393672-02cc0293-e63b-41a3-80fb-57b46461dcd9.png)
![머리 변형](https://user-images.githubusercontent.com/75903850/134393930-c055f5ce-1084-4399-b93c-cd3b1c9c9f41.png)
![얼굴 변형](https://user-images.githubusercontent.com/75903850/134395532-10b2951e-b009-46ba-bf93-ca31bc5abd4b.png)

위 예시처럼 소스 비디오(왼쪽)의 특징(ex. 입술, 헤어스타일)을 타겟 비디오(가운데)에 적용하여 결과(오른쪽)를 만들어 낼 수 있다.
 
#### 참고 논문 
- [Motion-supervised Co-Part Segmentation](https://arxiv.org/abs/2004.03234)

#### 참고 Repository
- https://github.com/deepfakes/faceswap
- [Motion-supervised Co-Part Segmentation 저자의 공식 Repository](https://github.com/AliaksandrSiarohin/motion-cosegmentation)

### 딥페이크 탐지 (FaceForensics++)

### 사용한 라이브러리, 툴
- Pytorch
- xception pretrained model
- dlib (detection library)
- opencv2

### 방법론
![image](https://user-images.githubusercontent.com/75903850/134397425-10566442-5671-4311-9b06-82348f5308de.png)
![image](https://user-images.githubusercontent.com/75903850/135982383-20b5a2a2-1ec5-45df-bd86-a27c29e43b73.png)

참고한 FaceForensic++ 논문(아래 첨부)에 따라 성능이 가장 높았던 XceptionNet 분류 모델을 이용하였다.

### 진행 순서
영상의 프레임 간단하게 전처리 -> dlib 를 이용하여 얼굴 탐지 -> 탐지된 얼굴에 width, height를 추가로 주어 bounding box 그리기 -> 예측. 각 프레임 별 Fake일 확률을 최종적으로 평균내어 영상의 Deep Fake 확률 도출

### 분석한 영상
![image](https://user-images.githubusercontent.com/75903850/135982953-5b6c9c04-f801-464f-8822-077250304259.png)

아까 진행했던 Face swap 결과와 AI hub의 딥페이크 영상을 탐지해본 결과 각각 약 49, 53, 96% 로 DeepFake 확률이 도출되었다.

### 개선점

사전학습모델을 사용할 뿐아니라 추가적으로 학습하여 성능을 높히고, 누구나 사용할 수 있도록 간단한 웹 어플을 제작 및  

#### 참고 논문
- [FaceForensics++](https://arxiv.org/abs/1901.08971)

#### 참고 Repository
- [FaceForensics++ 저자의 공식 Repository](https://github.com/ondyari/FaceForensics)

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


#### 참고 논문
- [FaceForensics++](https://arxiv.org/abs/1901.08971)

#### 참고 Repository
- [FaceForensics++ 저자의 공식 Repository](https://github.com/ondyari/FaceForensics)

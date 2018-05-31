## Google Cloud Platform with GPUs
for studying cs231n class.

### 순서
- google 로그인 & google cloud platform 설정
- 언어 변경
- quota 변경 요청
- (image 설정)
- 새로운 instance 생성
￼- ssh를 통해 vm에 연결
- 프레임워크 설치
- jupyter notebook 설정
****
#### 0. google 로그인 & google cloud platform 설정
구글에 로그인은 알아서 하기 바람.
****
![enter the GCP](/gcp-img/0-1.PNG)

로그인 후 google cloud platform을 들어가면 초기에 setting 창이 뜸.
각자 알아서 읽어보고 마지막 agrre만 하면 됨.

![rename project](/gcp-img/0-2.PNG)

default로 설정되어 있는 프로젝트 이름을 'Go to project settings'로 가면 바꿀 수 있음.

#### 1. 언어 변경
![change the language](/gcp-img/1-1.PNG)

언어를 한국어에서 영어로 변경.\
(언어 변경 은 상단의 search bar에서 검색하면 쉽게 이동할 수 있다.)

#### 2. quota 변경 요청
```diff
- 이때 만약 화면 상단에 계정 업그레이드가 팝업으로 뜬다면, 업그레이드를 우선적으로 진행할 것.
```
![move to quotas setting](/gcp-img/2-1.PNG)

언어를 변경했다면, menu bar를 눌러서 'IAM & admin' 섹션의 quotas를 클릭한다.

![set quotas](/gcp-img/2-2.PNG)

내가 앞으로 쓸 서버와 GPU에 해당하는 quotas를 찾자.
- Service : Compute Engine API
- Metric : NVIDIA K80 GPUs
- Location : us-west1

![edit quotas](/gcp-img/2-3.PNG)

그다음 'EDIT QUITAS'를 누르고, 해당 service의 check box를 누른다.

![submit quotas](/gcp-img/2-4.PNG)

그러면 오른쪽 화면과 같이 New quota limit과 Description을 작성하는 popup이 생성된다.
다음과 같이 작성하자.
- New quota limit : 1 (숫자 1만 빈칸에 쓰면 됨)
- Description : I want to train and test machine learning models using Tensorflow framework.(그냥 예시일 뿐 맘대로 써도 됨.)
다 작성하였으면 Submit request를 누르면 끝.
****
```diff
+> 이 과정은, google에서 gpu 할당을 원하는 사람한테만 해주므로, 1개 gpu할당해 달라고 요청하는 작업.
```
****
![get Email](/gcp-img/2-5.PNG)

2-3 Business days 후에 다음

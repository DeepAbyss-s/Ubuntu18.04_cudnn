# Ubuntu18.04_cuDNN
- NVIDIA CUDA Deep Neural Network

cuDNN은 GPU가속화를 활용한 신경망 라이브러리

딥러닝을 하기에는 필수설치요소중 하나입니다.

GPU연산을 하기 위한 기반으로써 NVIDIA의 그래픽카드를 딥러닝에 사용할 때 성능 향상을 가져옵니다.

특히 Tensorflow와 Caffe2 를 포함한 주로 사용되는 심층 학습 프레임워크를 가속화 시킬수있습니다.

# 우분투 버전
- Ubuntu 18.04.4.LTS AMD64 버전

# 권장사양
엔비디아 홈페이지 계정

[Nvidia cuDNN 다운로드 링크](https://developer.nvidia.com/rdp/form/cudnn-download-survey)

Cuda 10.1또는 그 이상버전 정상적으로 설치된 Ubuntu 18.04 시스템.

# 설치방법
#### ※ 순서대로 따라해주셔야지 정상적으로 설치가 가능합니다!!
#### ※ 엔비디아 개발자 페이지에 로그인을 해야되고, 사용자의 쿠다버전에 따라 압축파일, 폴더명, 파일명이 달라질 가능성이 있어서 Readme의 설명으로 대체합니다.

Nvidia cuDNN 다운로드 링크로 접속하여 로그인 또는 엔비디아 개발자 회원가입을 진행하여 다운로드 페이지로 이동합니다.

동의를 진행하면 아래에 버전별로 지원하는 cuDNN을 받으실 수 있습니다.

저희는 쿠다 10.1 버전을 받아서 진행을 해야됩니다.

- cuDNN Library for Linux 버전을 다운받으셔야됩니다.

다운로드가 완료된 후에 다운로드가 된 폴더로 이동 후 그 폴더에서 마우스 오른쪽을 클릭하여 터미널창을 실행시켜주셔야됩니다.

파일을 어드민폴더 안에 있는 쿠다폴더로 옮겨야되기 때문에 터미널 창을 실행시킨 후 슈퍼유저(sudo -E su)로 로그인해줍니다.

이제 받은 파일의 압축을 터미널창에서 코드로 풀어줍니다.

> tar -zxvf cudnn (Tab 키를 누르면 자동완성)

압축 풀기가 완료된 후에는

> cd cuda

를 사용하여 터미널창에서 폴더로 들어가줍니다.

터미널 창에서 파일을 쿠다 라이브러리 폴더로 옮겨주어야 됩니다. 이때 꼭 슈퍼유저가 되어있어야지 오류없이 이동이 됩니다!

> sudo cp lib64/lib* /usr/local/cuda/lib64

> sudo cp include/cudnn.h /usr/local/cuda/include

이 코드를 이용하면 쿠다폴더로 무사히 옮겨집니다. 그리고 쿠다 라이브러리 폴더로 이동합니다.

> cd /usr/local/cuda/lib64

여기서 터미널창에 l 키를 입력하면 폴더 안에 있는 리스트들을 확인 할 수 있습니다.

_2020.07.09 테스트기준 7.6.5버전을 설치하였습니다._

이제 cudnn 라이브러리를 읽을수 있도록 권한을 부여합니다.

> sudo chmod +r libcudnn.so.7.6.5

권한이 부여가 되었을 때 심볼릭 링크를 사용하여 경로를 지정해줍니다.

> sudo ln -sf libcudnn.so.7.6.5 libcudnn.so.7

> sudo ln -sf libcudnn.so.7 libcudnn.so

> sudo ldconfig

여기까지 오류메시지 없이 잘 되었다면 cuDNN은 설치가 무사히 완료되었습니다.

> sudo reboot 

이제 재부팅을 하시면 마무리가 됩니다.

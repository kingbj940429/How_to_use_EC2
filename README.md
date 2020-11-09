# EC2 사용방법
window 환경에서 EC2로 Node.js 배포하는 방법입니다. (2020년11월09일 기준)

## AWS 사이트에서
### 1) 
AWS EC2에 접속하셔서 _**인스턴스 시작**_ 을 눌러줍니다.

![aws_사용법_01](https://user-images.githubusercontent.com/63000843/98460752-7097ea00-21ea-11eb-8d6b-f9b788ebe2d8.PNG)
### 2) 
_**우분투**_ 를 선택해줍니다.

![aws_사용법_02](https://user-images.githubusercontent.com/63000843/98460753-7261ad80-21ea-11eb-9e16-34630c56fb6f.PNG)
### 3) 
_**프리티어의 유형**_ 을 선택해줍니다.

 ![aws_사용법_03](https://user-images.githubusercontent.com/63000843/98460754-7392da80-21ea-11eb-968b-80358beef045.PNG)
### 4) 
_**시작하기**_ 를 선택해줍니다

 ![aws_사용법_04](https://user-images.githubusercontent.com/63000843/98460755-742b7100-21ea-11eb-9858-4c4a6381cc76.PNG)

### 5) 
7단계 : 인스턴스 시작 검토 화면에서 _**새 키 페어 생성**_ 을 선택하고 _**키 페어 이름**_ 을 임의로 작성해주고 _**키 페어 다운로드**_ 를 꼭 해줍니다.

* __**다운 받은 키 페어의 위치**__ 를 꼭 기억해줍니다.
 
 ![aws_사용법_06](https://user-images.githubusercontent.com/63000843/98460757-768dcb00-21ea-11eb-8369-146cb2e350bd.PNG)
### 6) 
상태 검사가 사진과 같이 바뀔때 까지 기달려줍니다. 몇분 소요될 수 있습니다. 

 ![aws_사용법_05](https://user-images.githubusercontent.com/63000843/98460756-75f53480-21ea-11eb-832a-d539e7c3cab7.PNG)

## 우분투에서
### 1) 
_**연결**_ 를 선택해줍니다.

![0번_aws_연결](https://user-images.githubusercontent.com/63000843/98461109-f321a900-21ec-11eb-95aa-1a231d52be07.PNG)
### 2)
4번째 항목의 _**ssh -i**_ 로 시작하는 명령어를 복사해줍니다.

 ![0번_1_ssh 관련](https://user-images.githubusercontent.com/63000843/98461108-f1f07c00-21ec-11eb-845f-412707fbf0be.PNG)
### 3)
터미널을 실행시키고 아까 다운 받았던 키페어가 있는 곳으로 디렉터리를 설정해줍니다.

* **만약 C:\User\bjpearl에 있다면 cd C:\User\bjpearl 해줍니다. 여기서 주의할점은 C:\에 키 페어를 저장하면** 

* **접근 권한 문제가 생길수 있으니 사용자안에 다운 받아줍니다.**

* **윈도우 환경에서는 ssh를 사용할 수 없으니 google에 윈도우에서 ssh를 사용할 수 있는 방법을 검색 후 설정을 해줍니다.**

* 디렉터리를 키 페어가 있는 곳을 설정해줬다면 아까 복사했던 __**ssh -i 명령어**__ 를 실행시켜줍니다.

[윈도우에서 ssh 설정](https://amorfati-1000.tistory.com/50)
![1번_ssh_접속](https://user-images.githubusercontent.com/63000843/98461110-f321a900-21ec-11eb-82b4-3da0d0342a5c.PNG)
### 4)
사진과 같이 __**sudo apt update**__ , __**sudo apt install npm**__ , __**sudo apt install nodejs**__ 를 해줍니다.
![2번_update](https://user-images.githubusercontent.com/63000843/98461111-f3ba3f80-21ec-11eb-938f-614ada35af5a.PNG)
![3번_node_npm 설치](https://user-images.githubusercontent.com/63000843/98461112-f3ba3f80-21ec-11eb-8808-6726db1b61bc.PNG)
![4번_nodejs](https://user-images.githubusercontent.com/63000843/98461113-f452d600-21ec-11eb-9a28-59f7bc0288d3.PNG)

### 5)
gitclone할 폴더를 __**mkdir**__ 를 이용하여 폴더를 생성해주고 gitclone을 해줍니다.

일부러 gitclone 실패를 한 사진을 가져왔습니다. 성공했다면 성공했다는 문구가 보여집니다.
![5번_gitclone](https://user-images.githubusercontent.com/63000843/98461114-f452d600-21ec-11eb-9471-ec9ba56bb9ec.PNG)

### 6)
__**pwd**__ 를 이용해 현 디렉터리를 확인하고 __**ls**__ 를 이용하여 현 디렉터리에 있는 파일 목록을 불러옵니다.

디렉터리 문제가 없으면 __**npm i**__ 를 하여 기존 nodejs 파일에 있던 npm들을 설치해줍니다.

nodemon 같은 경우 npm start를 해주면 로컬에서와 마찬가지로 실행됩니다.

* **pwd** : 현 디렉터리 위치를 표시해줍니다.

* **ls** : 현 디렉터리에 있는 폴더들을 표시해줍니다.

![6번_파일 실행](https://user-images.githubusercontent.com/63000843/98461118-f74dc680-21ec-11eb-9d5e-43ab2507bdf4.PNG)

## 보안그룹
아마 위 같이 실행시켜도 퍼블릭 ip로 접속할수 없습니다. 보안그룹이 설정되지 않아서 그런겁니다.

따라서 보안 그룹 설정을 해주어야 합니다. EC2를  대부분 AWS 클라우드 서비스는 보안그룹 설정을 해주야 합니다.

### 1)
인스턴스 화면에서 __**보안 그룹 이름**__ 을 확인해줍니다. 
![보안그룹_01](https://user-images.githubusercontent.com/63000843/98461500-e94d7500-21ef-11eb-970a-2c4f8b846677.PNG)
### 2)
__**보안 그룹**__ 으로 이동 후 아까 확인한 __**보안 그룹 이름**__ 을 클릭합니다.
![보안그룹_02](https://user-images.githubusercontent.com/63000843/98461502-e9e60b80-21ef-11eb-9aa1-c57aa73610ca.PNG)
### 3)
__**보안 그룹 이름**__ 으로 이동 후 __**인바운드 규칙 편집**__ 을 클릭합니다.
![보안그룹_03](https://user-images.githubusercontent.com/63000843/98461504-ea7ea200-21ef-11eb-9340-15b62578af99.PNG)
### 4)
이미지처럼 __**Nodejs가 실행될 포트**__ 를 지정해줍니다.
![보안그룹_04](https://user-images.githubusercontent.com/63000843/98461505-eb173880-21ef-11eb-8576-e28051b7a1b9.PNG)

### 나를 위한 EC2 사용 방법 끝 :)






  


# CPU 작동원리

## 명령어 세트란?
CPU가 실행할 명령어의 집합
- 연산 코드(Operation Code) : 실행할 연산
    - 연산, 제어, 데이터 전달, 입출력 기능을 가짐
- 피연산자(Operand) : 필요한 데이터 or 저장 위치
    - 주소, 숫자/문자, 논리 데이터 등을 저장

## 명령어 사이클
cpu는 메모리에서 명령어나 데이터를 읽는다.
<img align="center" width="800" alt="image" src="https://user-images.githubusercontent.com/80687913/201073242-8675d5e2-3971-4b43-8a42-f2ee9045af16.png">

2 와 3을 더해서 저장해
-> 10번지와 11번지를 더해서 12번지에 저장해
-> 프로세스

<img width="800" alt="image" src="https://user-images.githubusercontent.com/80687913/202429843-40a087a5-a0c2-411c-93b3-2aae1124c522.png">

CPU는 프로그램 실행하기 위해 주기억장치에서 명령어를 순차적으로 인출하여 해독하고 실행하는 과정을 반복함

- 범용 레지스터 : 연산에 필요한 데이터나 연산 결과를 임시로 저장
- 특수목적 레지스터 : 특별한 용도로 사용하는 레지스터

특수목적 레지스터
- PC(프로그램 카운터) : 다음에 수행할 명령어 주소 저장
- MAR(메모리 주소 레지스터) : 프로그램 카운터에서 수행할 주소를 넘겨받은 다음 그 주소를 찾아가 데이터를 가져온다.
- MBR(메모리 버퍼 레지스터) : 메모리 주소 레지스터가 가져온 데이터들을 일시적으로 저장한다.
- IR(명령어 레지스터) : 명령을 받아 현재 실행 중인 명령어 저장
- AC(누산기) :
연산에 사용될 데이터를 받아 연산 결과값, 중간 값, 임시 저장 
- 제어장치 :
명령어 레지스터에 있는 명령어를 받아 해석하고 해석된 명령어를 실행할 시스템에 지시한다.
- ALU : 산술 논리 연산을 실행한다.
<img width="800" alt="Screen Shot 2022-11-17 at 8 18 39 PM" src="https://user-images.githubusercontent.com/80687913/202432938-fcef9b21-3380-48df-a3fe-f0eccaf88849.png">
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80687913/202434769-c355a2cf-8dc5-410c-a120-175536660232.png">

- 인출
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80687913/202435287-3f0d9766-bf0b-4d3d-994d-e68b15faf1bd.png">
- 해석
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80687913/202435629-76ede0c4-1456-4166-98e2-b30700836619.png">
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80687913/202436061-6e2d578d-eb66-4f81-8775-b34d7b7a4171.png">

- 실행
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80687913/202436803-5df5dd59-64f3-4b17-a415-069c336baacb.png">

- 저장
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80687913/202436593-4e720b49-90c0-4218-8de6-6ef2e2c0c637.png">

## 쓰레드
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80687913/202429843-40a087a5-a0c2-411c-93b3-2aae1124c522.png">

## 아키텍처
<img width="800" alt="image" src="https://user-images.githubusercontent.com/80687913/202430852-5eacd1d3-d17d-44ee-bb1f-c3b823ad3f63.png">
구조 설계
(펜티엄, 커피레이크, 타이거 레이크)

[참고한 사이트]
https://www.youtube.com/watch?v=Fg00LN30Ezg
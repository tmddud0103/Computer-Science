# CH2 System Structure & Program Execution

## 컴퓨터 시스템의 구조

![image-20210905142428486](photo/image-20210905142428486.png)

I/O = input & output 

![image-20210905142846175](photo/image-20210905142846175.png)

메모리 = cpu의 작업 공간

CPU = 매 순간 메모리에서 기계어를 읽어서 작업을 실행

local buffer = IO 디바이스들의 작은 작업 공간

registers = 메모리보다 빠르고, 정보를 저장할 수 있는 CPU 내부의 공간

CPU => 디바이스 컨트롤러로 정보 요청(CPU가 직접적으로 일을 하지 않음)

#### Mode bit

메모리에서 읽은 정보가 OS인지 사용자 프로그램인지 판단

![image-20210905144449705](photo/image-20210905144449705.png)

#### Timer

하드웨어, 특정 프로그램이 CPU를 독점하지 않기 위해 시간 값을 설정

![image-20210905144531868](photo/image-20210905144531868.png)

#### Device controller

각각 I/O 디바이스를 전담하는 작은 CPU

![image-20210905144607204](photo/image-20210905144607204.png)

#### 입출력(I/O)의 수행

![image-20210905145201722](photo/image-20210905145201722.png)

### Interrupt

interrupt line = CPU는 일반적으로 메모하고만 일한다. I/O 디바이스에서 정보를 전달할 때 사용, 

​							들어오는 순간 CPU의 제어권은 OS로 넘어가게 된다

![image-20210905145321561](photo/image-20210905145321561.png)

IO에 요청을 할 때에는 소프트웨어 인터럽트를 통해 요청

IO가 처리를 끝났으면 하드웨어인터럽트를 통해 정보를 받음

![image-20210905145542567](photo/image-20210905145542567.png)

타이머가 인터럽트를 하는 경우

![image-20210905145553421](photo/image-20210905145553421.png)

IO 컨트롤러가 인터럽트를 하는 경우

#### 현대의 운영체제는 인터럽트에 의해 구동됨

### 시스템 콜(System Call)

![image-20210905145734787](photo/image-20210905145734787.png)


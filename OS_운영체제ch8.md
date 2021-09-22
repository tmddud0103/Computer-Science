# CH8 Memory Management

>  메모리 관리

### Logical address(=virtual address 가상 주소)

논리적인 주소

- 프로세스마다 독립적으로 가지는 주소 공간
- 각 프로세스마다 0번지부터 시작
- **CPU가 보는 주소는 Logical address임**

### Physical address

물리적인 주소

- 메모리에 실제 올라가는 위치



## 주소 바인딩(Address Binding)

#### 주소를 결정하는 것

Symbolic Address => Logical Address => Physical Address 

#### Symbolic Address

프로그래머가 프로그래밍을 할 때 메모리에 이름을 가지고 심볼로 된 주소를 사용한다.

숫자가 아닌 심볼로 된 address를 사용하고 그것이 논리적인 주소로 바뀐다

### Compile time binding

- 물리적 메모리 주소(physical address)가 컴파일 시 알려짐
- 시작 위치 변경시 재컴파일
- 컴파일러는 절대 코드(absolute) 생성

### Load time binding

- Loader의 책임하에 물리적 메모리 주소 부여
- 컴파일러가 재배치가능코드(relocatable code)를 생성한 경우 가능

### Execution time binding (=Run time binding)

- 수행이 시작된 이후에도 프로세스의 메모리 상 위치를 옮길 수 있음
- CPU가 주소를 참조할 때마다 binding을 점검 (address mapping table)
- **하드웨어적인 지원이 필요**  
  - (e.g. base and limit registers, MMU(하드웨어))

![image-20210922211756089](photo/image-20210922211756089.png)



### Memory-Management Unit (MMU 하드웨어)

- #### MMU(Memory-Management Unit)

  - logical address를 physical address로 매핑해주는 Hardware device

- MMU scheme

  - 사용자 프로세스가 CPU에서 수행되며 생성해내는 모든 주소값에 대해 basse register(=relocation register)의 값을 더한다

- user program

  - logical address만을 다룬다
  - 실제 physical address를 볼 수 없으며 알 필요가 없다

![image-20210922212941448](photo/image-20210922212941448.png)

![image-20210922213116104](photo/image-20210922213116104.png)



## Some terminologies

> Dynamic Loading
>
> Dynamic Linking
>
> Overlays
>
> Swapping

### Dynamic Loading

- 프로세스 전체를 메모리에 미리 다 올리는 것이 아니라 해당 루틴이 불려질 때 메모리에 load하는 것
- memory utilization의 향상
- 가끔씩 사용되는 많은 양의 코드의 경우 유용
  - 예) 오류 처리 루틴
- 운영체제의 특별한 지원 없이 프로그램 자체에서 구현 가능(OS는 라이브러리를 통해 지원 가능)

- loading = 메모리로 올리는 것

### Dynamic Linking

- #### Linking을 실행 시간(execution time)까지 미루는 기법

- #### Static linking

  - 라이브러리가 프로그램의 실행 파일 코드에 포함됨
  - 실행 파일의 크기가 커짐
  - 동일한 라이브러리를 각각의 프로세스가 메모리에 올리므로 메모리 낭비
    - (eg. printf 함수의 라이브러리 코드)

- #### Dynamic linking

  - 라이브러리가 실행시 연결(link)됨
  - 라이브러리 호출 부분에 라이브러리 루틴의 위치를 찾기 위한 stub이라는 작은 코드를 둠
  - 라이브러리가 이미 메모리에 있으면 그 루틴의 주소로 가고 없으면 디스크에서 읽어옴
  - 운영체제의 도움이 필요

### Overlays

- 메모리에 프로세스의 부분 중 실제 필요한 정보만을 올림 (dynamic loading와 큰 자이 없음)
- 프로세스의 크기가 메모리보다 클 때 유용
- 운영체제의 지원없이 사용자에 의해 구현
- 작업 공간의 메모리를 사용하던 초창기 시스템에서 수작업으로 프로그래머가 구현
  - Manual Overlay
  - 프로그래밍이 매우 복잡

### Swapping

- #### Swapping

  - 프로세스를 일시적으로 메모리에서 backing store로 쫒아내는 것

- #### Backing store(=swap area)

  - 디스크
    - 많은 사용자의 프로세스 이미지를 담을 만큼 충분히 빠르고 큰 저장 공간

- #### Swap in / Swap out

  - 일반적으로 중기 스케줄러(swapper)에 의해 swap out 시킬 프로세스 선정
  - priorty-based CPU scheduling algorithm
    - priority가 낮은 프로세스를 swapped out 시킴
    - priority가 높은 프로세스를 메모리에 올려놓음
  - Compile time 혹은 load time binding 에서는 원래 메모리 위치로 swap in 해야 함
  - Execution time binding에서는 추후 빈 메모리 영역 아무 곳에나 올릴 수 있음
  - swap time은 대부분 transfer time (swap되는 양에 비례하는 시간)임

![image-20210922214707216](photo/image-20210922214707216.png)



## Allocation of Physical Memory 물리적 메모리의 영역

- ### 메모리는 일반적으로 두 영역으로 나뉘어 사용

  - #### OC 상주 영역

    - interrupt vector와 함께 낮은 주소 영역 사용

  - #### 사용자 프로세스 영역

    - 높은 주소 영역 사용

![image-20210922215310249](photo/image-20210922215310249.png)

- ### 사용자 프로세스 영역의 할당 방법

  - #### Contiguous allocation 연속 할당

    : 각각의 프로세스가 메모리의 연속적인 공간에 적재되도록 하는 것

    - ##### Fixed partition allocation 고정 분할 방식

    - ##### Variable partition allocation 가변 분할 방식

  - #### Noncontiguous allocation 불연속 할당 (현대의 시스템)

    : 하나의 프로세스가 메모리의 여러 영역에 분산되어 올라갈 수 있음

    - ##### Paging

    - ##### Segmentation 

      - 코드, 데이터, 스택 세그먼트로 잘라서 필요시에 물리적 메모리(다른 위치에)에 올려놓을 수 있게 하는 방법
      - 의미 단위로 자르기 때문에 코드가 균일하지 않음

    - ##### Paged Segmentation



## Contiguous allocation 연속 할당

- #### Fixed partition allocation 고정 분할 방식

  - 물리적 메모리를 몇 개의 영구적 분할(partition)로 나눔
  - 분할의 크기가 모두 동일한 방식과 서로 다른 방식이 존재
  - 분할당 하나의 프로그램 적재
  - 융통성이 없음
    - 동시에 메모리에 load되는 프로그램의 수가 고정됨
    - 최대 수행 가능 프로그램 크기 제한
  - internal fragmentation 발생 (external fragmentation도 발생)

- #### Variable partition allocation 가변 분할 방식

  - 프로그램의 크기를 고려해서 할당
  - 분할의 크기, 개수가 동적으로 변함
  - 기술적 관리 기법 필요
  - External fragmentation 발생

![image-20210922215643651](photo/image-20210922215643651.png)

#### External fragmentation 외부 조각

- 프로그램 크기보다 분할의 크기가 작은 경우
- 아무 프로그램에도 배정되지 않은 빈 곳인데도 프로그램이 올라갈 수 없는 작은 분할

#### Ixternal fragmentation 내부 조각

- 프로그갬의 크기보다 분할의 크기가 큰 경우
- 하나의 분할 내부에서 발생하는 사용되지 않는 메모리 조각
- 특정 프로그램에 배정되었지만 사용되지 않는 공간

![image-20210922220159559](photo/image-20210922220159559.png)

![image-20210922220211839](photo/image-20210922220211839.png)

![image-20210922220404063](photo/image-20210922220404063.png)

 => 디스크 조각 모음(호락호락한 방법은 아님(비용이 많이 든다))



## Noncontiguous allocation 불연속 할당

### Paging

![image-20210922220902292](photo/image-20210922220902292.png)
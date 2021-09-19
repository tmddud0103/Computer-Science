# CH5 CPU Scheduling

## CPU ans I/O Bursts in Program Execution

<img src="photo/image-20210912135344792.png" alt="image-20210912135344792" style="zoom: 80%;" />



## CPU-burst Time 분포

![image-20210912135602326](photo/image-20210912135602326.png)

CPU는 '일반적으로' CPU bound job를 많이 쓰지만, I/O bound job의 경우 빈도가 높아 frequency가 높다



## 프로세스의 특성 분류

![image-20210912135850398](photo/image-20210912135850398.png)



## CPU Scheduler & Dispather

두 가지 모두 소프트웨어의 종류

![image-20210912135925394](photo/image-20210912135925394.png)

비선점형 nonpreemptive

선점형    preemptive 

## 성능 척도 Scheduling Criteria

![image-20210912155211967](photo/image-20210912155211967.png)





## Scheduling Algorithm

![image-20210912160500061](photo/image-20210912160500061.png)

### FCFS (First-Come First-Served)

![image-20210912160517252](photo/image-20210912160517252.png)

![image-20210912160536819](photo/image-20210912160536819.png)

### SFJ (Shortest-Job-First)

![image-20210912160601828](photo/image-20210912160601828.png)

![image-20210912160613435](photo/image-20210912160613435.png)

![image-20210912160644325](photo/image-20210912160644325.png)

![image-20210912160700704](photo/image-20210912160700704.png)

![image-20210912160712100](photo/image-20210912160712100.png)

### Property Scheduling

![image-20210912160721215](photo/image-20210912160721215.png)

### RR (Round Robin)

![image-20210912160437765](photo/image-20210912160437765.png)

응답시간이 빨라진다

![image-20210912160804907](photo/image-20210912160804907.png)

![image-20210912160910595](photo/image-20210912160910595.png)

### Multilevel Queue

![image-20210912160942059](photo/image-20210912160942059.png)

![image-20210912161101719](photo/image-20210912161101719.png)

### Multilevel Feedback Queue

![image-20210912161142927](photo/image-20210912161142927.png)

![image-20210912161149103](photo/image-20210912161149103.png)

![image-20210912161211219](photo/image-20210912161211219.png)



## Scheduling

### CPU가 여러개인 경우의 스케줄링

![image-20210912161223488](photo/image-20210912161223488.png)



### Real-Time Scheduling

=> deadline이 존재하는 경우 

deadline을 보장받아야한다

![image-20210912161343845](photo/image-20210912161343845.png)



### Thread Scheduling

![image-20210912161438863](photo/image-20210912161438863.png)





## Algorithm Evaluation 알고리즘 성능 척도

![image-20210912161524374](photo/image-20210912161524374.png)



## 이권희 포트폴리오
 
## 1. 기술 스택

| **Backend**   | **ORM**       | **SQL** | **Cloud** | **Front**     |
|---------------|---------------|---------|-----------|---------------|
| Spring        | JPA           | MySQL   | AWS       | HTML          |
| Spring Boot   | QueryDSL      | -       | Docker    | JavaScript    |
| -             | MyBatis       | -       | Raspberry | -             |

## 2. 소개
현재에 살고 지금 내가 할 수 있는 최선을 다하자!  
지금 배울 수 있는 최대한을 배우고 현재 갈 수 있는 최고의 길을 가기 위해 노력하자!

## 3. 프로젝트 (포트 폴리오)
## 1. 질문 하나, 마음속에 남는 [여운](https://github.com/Yeoun-project)  
소개 : 사용자 주도 자기성찰 Q&A 서비스  
개발 기간 : 2025/02 ~ 2025/05 (2달) / 2025/06(user test)  
인원 : 기획자1, 디자이너1, backend2, front2  
역할 : backend  
  
### 구현한 주요 기능 : login, security, 게시판 댓글 추가 수정, 오늘의 질문, 실시간 알림 서비스  
> 1. login, security : google social login, security, jwt token 구현  
> 2. 실시간 알림 서비스 구현 : 단방향 socket Server Sent Emitter socket을 사용한 실시간 알림 서비스 구현  
> 3. 게시판 댓글 추가 수정

### 문제 해결  
#### 1. 비회원 로직
기획 : 모든 비회원에게 같은 오늘의 질문이 아닌 각자 다른 오늘의 질문을 렌더링해주세요!  
문제점 : 모든 비회원을 server에서 관리해야 한다  

| ** 해경 방안 ** | ** 해결 방법 ** |
| --- | --- |
| 1. redis 도입  | 기존 회원과 비회원을 완전히 분리하고 redis를 사용하여 비회원을 관리한다 |
| 2. 기존 회원 통합 | 기존 회원의 무결성을 조금 풀고 모든 비회원에게 비회원 token을 발금해서 db를 통해 관리한다 |

최종 해결 방안 = 2. 기존 회원 통합  
비회원의 정보 또한 휘발성이 되어서는 안된다.  
aws성능과 개발 기간을 고려했을 때 redis도입은 어렵다.  

### 2. 배포 환경에서의 socket 관리
기획 : 실시간 알림 기능을 만들어 주세요!
도입 기술 : SSE Socket (단방향 Server Sent Event Socket)
| ** 문제점 ** | ** 해결 방안 ** |
| 네트워크 문제로 socket이 끊어진 경우 | front에서 socket이 끊어진 경우 5초 후에 다시 연결하는 로직 구현 |
| 네트워크 문제로 쌓여진 무수한 socket 요청이 backend에 도착할 경우 server 의 부담 | server의 socket이 남아 있는 경우 해당 socket을 다시 반환|
최종 : 대부분의 네트워크 상황에 대비한 socket 기능 구현 완료

<p align="center">
 <img width="45%" height="500" alt="image" src="https://github.com/user-attachments/assets/4e860990-5589-42cd-b435-afb99799bb76" />
 <img width="45%" height="500" alt="image" src="https://github.com/user-attachments/assets/b0a29f4d-407d-4a2e-9819-c994de8c48b8" />
</p>

### 2. 펀딩 플랫폼 [with U](https://github.com/DMU-NextLevel)
소개 : 
개발 기간 : 2025/04 ~ (진행 중)  
인원 : frontend3, backend1  
역할 : backend  
     
구현한 주요 기능 : aws 배포, login, toss 결제, img  
> 1. aws 배포 : Git CI,CD / Docker 를 사용한 aws 배포  
> 2. login 기능 : email login, social login, security jwt 보안과 인증 기능 구현  
> 3. toss 결제 시스템 : toss 결제 api를 사용한 결제 시스템 구현 (test용 구현, 실제 결제X)  
> 4. img service : back 서버 내에 img 파일을 저장하고 nginx 서빙 (aop를 사용한 img file rollback 구현)

문제 해결


<p align="center">
 <img width="45%" height="500" alt="image" src="https://github.com/user-attachments/assets/f553717e-77c6-4423-8680-556df1b72c2c" />
 <img width="45%" height="500" alt="image" src="https://github.com/user-attachments/assets/468329a5-7216-440c-bbd5-8cabae476b33" />
</p>

## 4. 대외 활동 / 수상경력
> 1. 2024/12 전국 창의코딩 경진대회 참여

## 5. 자격증
> 1. sqld
> 2. 프로그래머스 PCCE Lv.4

## 6. 학위
> 1. 동양미래 대학교 (3년)

### Contact
이메일 : lkh8033@gmail.com  
[velog : https://velog.io/@lkh8033/series](https://velog.io/@lkh8033/series)

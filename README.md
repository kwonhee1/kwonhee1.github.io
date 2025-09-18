
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
### 1. 질문 하나, 마음속에 남는 [여운](https://github.com/Yeoun-project)  

| **소개** | 사용자 주도 자기성찰 Q&A 서비스 |
| --- | --- |
| **개발 기간** | 2025/02 ~ 2025/05 (2달) / 2025/06(user test) |
| **인원** | 기획자1, 디자이너1, backend2, front2 |
| **역할** | backend |
  
#### 구현한 주요 기능  
| **구현한 주요 기능** | **구현 기술** |
| --- | --- |
| login, security | jwt token, spring security, google social login |
| 실시간 알림 서비스 | SSE Socket (Server Sent Event Socket) |
| 게시판 댓글 추가/수정 | spring boot, jpa |

### 문제 해결  

<table>
  <tr>
    <td>
      <b>비회원 로직</b>
      <table>
        <tr>
          <th>고민한 해결 방안</th>
          <th>해결 방법</th>
        </tr>
        <tr>
          <td>1. redis 도입</td>
          <td>redis을 도입해서 비회원을 관리한다</td>
        </tr>
        <tr>
          <td>2. 기존 회원 통합</td>
          <td>모든 비회원에게 비회원 token을 발급해서 DB로 관리</td>
        </tr>
      </table>
      <p><b>최종 선택:</b> 기존 회원 통합 방식</p>
    </td>
    <td>
      <b>배포 환경에서의 socket 관리</b>
      <table>
        <tr>
          <th>문제점</th>
          <th>해결 방안</th>
        </tr>
        <tr>
          <td>네트워크 문제로 socket이 끊어진 경우</td>
          <td>front에서 socket 끊어지면 5초 후 재연결</td>
        </tr>
        <tr>
          <td>무수한 socket 요청이 backend에 도착</td>
          <td>server의 socket 남아있으면 반환</td>
        </tr>
      </table>
      <p><b>최종 해결:</b> 대부분의 네트워크 상황에 대비한 socket 기능 구현 완료</p>
    </td>
  </tr>
</table>


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


## 이권희 포트폴리오
 
## 1. 기술 스택

| **Backend**   | **ORM**       | **SQL** | **Cloud** | **Front**     |
|---------------|---------------|---------|-----------|---------------|
| Spring        | JPA           | MySQL   | AWS       | HTML          |
| Spring Boot   | QueryDSL      | -       | Docker    | JavaScript    |
| -             | MyBatis       | -       | Raspberry | -             |

## 2. 소개
현재에 살고 지금 내가 할 수 있는 최선을 다하자!
고등학교 때 The Present라는 책에서 읽은 명언입니다. 과거의 후회와 미래의 걱정보다는 현재에서 내가 할 수 있는 최고를 찾고 내가 할 수 있는 최선을 다하는 것이 제 목표입니다.
언제나 어제보다 한 발자국 더 나아지기 위해 발버둥 치는 개발자가 되겠습니다! 감사합니다!

## 3. 프로젝트 (포트 폴리오)
### 1. 펀딩 플랫폼 [with U](https://github.com/DMU-NextLevel)

| **소개** | **펀딩 플렛폼**|
| --- | --- |
| 개발 기간 | 2025/04 ~ (진행 중) |
| 인원 | frontend3, backend1 |
| 역학 | backend |
     
#### -- 구현한 주요 기능
| **구현한 주요 기능** | **구현 방식** |
| --- | --- |
| 배포 자동화 | Git CI,CD / Docker |
| toss 결제 | toss 결제 api를 사용한 결제 시스템 구현 |
| img service | 서버에 img저장, nginx 서빙 / Aop img rollback 구현 |
| login 기능 | jwt token, spring security, OAuth2 |
| 이외 기능 | -- |

#### -- 문제 해결

<table>
 <tr>
  <td>
    <b>문제 1. img transaction</b>
    <p><b>문제점 :</b> db transaction에 img 파일이 rollback되지 않음</p>
    <table>
      <tr>
       <th>고민한 해결 방안</th>
       <th>해결 방법</th>
      </tr>
      <tr>
        <td>1. Spring TransactionSynchronization</td>
        <td>afterCommit, beforeCommit함수 사용</td>
      </tr>
      <tr>
        <td>2. Aop를 사용한 Custom Transaction 구현</td>
        <td>Aop를 사용해서 저장된 Img들의 Path를 저장하고 Exception발생시 img파일 rollback</td>
      </tr>
    </table>
    <p><b>최종 선택 : </b>2. Aop를 사용한 Custom Transaction 구현 <br>
    @ImgTransaction <br>
    Img관련 함수에서 img 저정 할 때 저장된 Path를 저장하고 Exception발생 시 Path의 img 파일들을 지움
    </p>
  </td>
 </tr>
 <tr>
  <td>
    <b>문제 2. Service Layer 의존성 관리</b>
    <p><b>문제점 :</b> service layer가 다른 service를 의존하면서 발생한 Circular References</p>
    <table>
     <tr>
      <th>이전 방식</th>               <th>개선 방식</th>
     </tr>
     <tr>
      <td>domain별 한개의 service</td> <td>기능 별 service 분리</td>
     </tr>
     <tr>
      <td>단일 service layer</td>      <td>service layer, module service layer 분리</td>
     </tr>
    </table>
    <p><b>결론</b><br> 1. 기능 별 service 분리 <br>
        2. service layer(module service layer의존)/module service layer(repository의존) 분리
    </p>
  </td>
 </tr>
</table>

<p align="center">
 <img width="45%" height="500" alt="image" src="https://github.com/user-attachments/assets/f553717e-77c6-4423-8680-556df1b72c2c" />
 <img width="45%" height="500" alt="image" src="https://github.com/user-attachments/assets/468329a5-7216-440c-bbd5-8cabae476b33" />
</p>

### 2. 질문 하나, 마음속에 남는 [여운](https://github.com/Yeoun-project)  

| **소개** | 사용자 주도 자기성찰 Q&A 서비스 |
| --- | --- |
| **개발 기간** | 2025/02 ~ 2025/05 (2달) / 2025/06(user test) |
| **인원** | 기획자1, 디자이너1, backend2, front2 |
| **역할** | backend |
  
#### -- 구현한 주요 기능  
| **구현한 주요 기능** | **구현 기술** |
| --- | --- |
| login, security | jwt token, spring security, google social login |
| 실시간 알림 서비스 | SSE Socket (Server Sent Event Socket) |
| 게시판 댓글 추가/수정 | spring boot, jpa |

#### -- 문제 해결  

<table>
  <tr>
    <td>
      <b>문제 1. 비회원 로직</b>
      <p>기획: 모든 비회원에게 같은 오늘의 질문이 아닌 각자 다른 오늘의 질문을 렌더링해주세요! <br>
      문제점: 모든 비회원을 server에서 관리해야 함</p>
      <table>
        <tr>
          <th>고민한 해결 방안</th>
          <th>해결 방법</th>
        </tr>
        <tr>
          <td>1. redis 도입</td>
          <td>redis을 도입해서 비회원을 관리</td>
        </tr>
        <tr>
          <td>2. 기존 회원 통합</td>
          <td>모든 비회원에게 비회원 token을 발금해서 db를 통해 관리한다</td>
        </tr>
      </table>
      <p><b>최종 선택:</b> 기존 회원 통합 방식</p>
      <p>비회원의 정보 또한 휘발성이 되어서는 안된다.<br>
      aws성능과 개발 기간을 고려했을 때 redis도입은 어렵다.</p>
    </td>
  </tr>
  <tr>
    <td>
      <b>문제 2. 배포 환경에서의 socket 관리</b>
      <p>기획: 실시간 알림 기능을 만들어 주세요!<br>
      도입 기술: SSE Socket (단방향 Server Sent Event Socket)</p>
      <table>
        <tr>
          <th>문제점</th>
          <th>해결 방안</th>
        </tr>
        <tr>
          <td>네트워크 문제로 socket 끊어진 경</td>
          <td>front에서 socket이 끊어진 경우 5초 후에 다시 연결하는 로직 구현</td>
        </tr>
        <tr>
          <td>네트워크 문제로 쌓여진 무수한 socket 요청이 backend에 도착할 경우 server 의 부담</td>
          <td>server의 socket이 남아 있는 경우 해당 socket을 다시 반환</td>
        </tr>
      </table>
      <p><b>최종 해결: </b>대부분의 네트워크 상황에 대비한 socket 기능 구현 완료</p>
    </td>
  </tr>
</table>


<p align="center">
 <img width="45%" height="500" alt="image" src="https://github.com/user-attachments/assets/4e860990-5589-42cd-b435-afb99799bb76" />
 <img width="45%" height="500" alt="image" src="https://github.com/user-attachments/assets/b0a29f4d-407d-4a2e-9819-c994de8c48b8" />
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

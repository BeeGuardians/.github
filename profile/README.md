# 우리FISA 4기 최종 프로젝트 🏆우수상 수상팀 - BeeGuardians
<br>

### "배우고 도전하고 성장하세요. 당신의 실력을 수호하는 공간, 가디언즈."


모의해킹 문제와 실시간 환경 배포가 결합된 워게임 플랫폼을 개발했습니다. <br>BeeGuardians는 별도의 설치 없이, 웹에서 바로 실습하고 실력을 시각화하며 성장할 수 있습니다.

<br><br>

## ▾ Team 꿀벌 방범대 소개  
<br>

우리FISA 4기 클라우드 엔지니어링 과정 수강생 5명으로 구성된 팀입니다. <br>
웹 애플리케이션 개발과 운영 및 배포(DevOps) 전반을 함께 다루며<br>
약 2개월간 협업을 통해 BeeGuardians 프로젝트를 완성했습니다.

|<img src="https://avatars.githubusercontent.com/u/71498489?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/95984922?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/150774446?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/153366521?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/127267532?v=4" width="150" height="150"/>|
|:-:|:-:|:-:|:-:|:-:|
|[PM] 한정현<br/>[@letsgojh0810](https://github.com/letsgojh0810)|[PL] 나홍찬<br/>[@HongChan1412](https://github.com/HongChan1412)|김예진<br/>[@yeejkim](https://github.com/yeejkim)|박지혜<br/>[@parkjhhh](https://github.com/parkjhhh)|석혜진<br/>[@HyeJinSeok](https://github.com/HyeJinSeok)|

<br><br>

## ▾ 프로젝트 기간
### 📆 2025.04.18 ~ 2025.06.10

<br><br>

## ▾ 마일스톤
<br>

  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/milestone.jpg" alt="마일스톤" width="800"/>

<br><br>

## ▾ Git Branch 전략
<br>

기능 및 페이지 개발은 dev 브랜치에서 일괄 통합한 뒤, 테스트를 거쳐 <br> 최종적으로 main 브랜치에 병합하여 운영 환경에 배포했습니다.

  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/git_branch.png" alt="마일스톤" width="800"/>

<br><br>

## ▾ Overview
<br>

아래 순서로 BeeGuardians 프로젝트의 주요 내용을 소개합니다 : <br>
### [1. 프로젝트 개요](#1-프로젝트-개요)  
### [2. 프로젝트 소개](#2-프로젝트-소개)  
### [3. 기술 스택](#3-기술-스택)
### [4. 아키텍처](#4-아키텍처)
### [5. 프론트엔드](#5-프론트엔드)
### [6. 백엔드 및 DB](#6-백엔드-및-db)  
### [7. 인프라](#7-인프라)  
### [8. 트러블 슈팅](#8-트러블-슈팅)  
### [9. 회고](#9-회고)

<br><br>

<br>

# 1. 프로젝트 개요
<br>

### 🌍 도입 배경
- 세계경제포럼(WEF)이 발표한 「글로벌 사이버보안 전망 2025」보고서에 따르면, 전 세계적으로 사이버 보안 인력이 400만 명이 부족하여 인재 유치가 시급한 상황임

- 최근 국내 대형 통신사를 시작으로 많은 기업들에서 해킹 사고가 잇따라 발생하면서 보안의 중요성이 대두되고 있음

<br>

### 🎯 문제 인식
- 보안이나 해킹 관련 실습을 해보려면 가상머신(VM) 설정, 각종 도구 설치 등 **복잡한 환경 구성**이 선행되어야 함

- 이 경우 실습 환경이 무겁고 개인별로 **독립된 실습 공간**을 확보하기 어려움

- 여러 사용자가 동일한 환경을 공유할 경우 충돌이나 오류가 발생할 수 있음

- 실습 플랫폼 자체도 부족하거나, 유료 플랫폼이 많아 자유로운 접근이 어려움

<br>

### 💡 해결 방안
- 보안이나 해킹 실습 문제를 쉽고 빠르게 수행할 수 있도록 **Kubernetes 기반으로 실습 환경(pod)** 을 자동 생성하는 구조를 설계함

- 사용자는 버튼 클릭만으로 개인별 **격리된 실습 공간**에 접근 가능하며, 별도의 환경 설정이나 복잡한 설치 없이 실습이 가능함

- 실습 환경은 사용자마다 분리되므로 충돌 없이 안정적인 실습이 가능함

- 전체 과정은 웹에서 이루어지며 접근성과 반복 학습 효율이 높음

<br>

> [!NOTE]
> pod는 Kubernetes에서 가장 작은 배포 단위로, 하나 이상의 컨테이너를 포함할 수 있는 격리된 실행 환경입니다. <br> 전통적인 가상머신(VM)은 각 인스턴스마다 전체 운영체제를 포함해 무겁고 부팅시간이 오래 걸리는 반면, <br> pod는 호스트 OS를 공유하면서 필요한 애플리케이션만 실행하기 때문에 <br> 리소스 사용이 효율적이고 배포 속도가 빠르다는 장점을 가지고 있습니다. 

<br><br>

---

<br>

# 2. 프로젝트 소개
<br>

### 🖥️ Kubernetes 기반 모의해킹 트레이닝 플랫폼 - “Guardians”


- 보안 위협에 실질적으로 대응할 수 있도록 누구나 쉽게 실습 가능한 모의해킹 훈련 플랫폼

- 워게임별로 pod가 자동 생성되어 격리된 환경에서 모의해킹 기법 실습 가능

- 사용자의 워게임 관리, 활동 기록, 성과 분석 등이 유기적으로 반영되는 서비스 구조

<br>

### 🚩 모의해킹 실습 환경 - 워게임이란?


- 다양한 해킹 관련 문제를 풀어보며 보안 기술을 연습하는 실습 콘텐츠

- 사용자는 웹 해킹/포렌식/리버싱 등 여러 분야의 문제를 해결해나가며 **각 문제에 숨겨진 문자열인 ‘flag’를 찾아내는 방식**으로 진행됨

- flag는 문제해결 과정 중에 발견할 수 있도록 설계되어 있어,
실제 보안 취약점을 분석하고 추적하는 연습에 적합함

<img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/wargame_flow.jpg" alt="유저 다이어그램" width="800"/>

<br>

### 🎲 워게임 pod 생성 요약도 

<img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/pod_flow.png" alt="POD요약도" width="800"/>

```
1. React (프론트엔드)  
   → 사용자는 웹 UI를 통해 워게임을 선택  

2. Spring Boot (백엔드)  
   → 요청된 워게임에 맞는 컨테이너 환경을 설정하고, 생성할 pod의 세부 스펙을 정의  

3. Fabric8 라이브러리  
   → Spring 내부에서 Kubernetes 클러스터와 직접 통신하며 pod 생성 명령을 전달  

4. Kubernetes Pod  
   → 워게임 환경 컨테이너 실행  

5. Amazon ECR  
   → 워게임 Docker 이미지를 저장해두는 컨테이너 이미지 저장소  
   → 워게임 생성 시 해당 이미지를 기반으로 pod가 생성됨
```
<br>

> [!IMPORTANT]
> Fabric8은 Java 기반 애플리케이션에서 K8s 리소스를 코드로 생성·관리할 수 있도록 해주는 오픈소스 라이브러리입니다. <br> 이를 통해 yaml 파일 없이 Java 코드로 Deployment, Pod, Service 등을 정의할 수 있습니다. <br><br> Amazon ECR은 Elastic Container Registry의 약자로, AWS에서 제공하는 완전관리형 Docker 이미지 저장소입니다. <br> 이를 통해 K8s 클러스터에서 이미지 pull 시 빠르고 안정적인 접근이 가능합니다.

<br><br>

### 📋 서비스 주요 기능

| 기능 영역         | 설명                                                                 |
|------------------|----------------------------------------------------------------------|
| 워게임 실습      | 다양한 난이도의 워게임 선택 및 격리된 실습 환경(Pod) 자동 생성         |
| 채점 시스템       | 사용자 Flag 제출 시 자동 채점 및 정답 여부 실시간 확인                  |
| 랭킹 시스템       | 사용자 점수를 기준으로 순위를 산정하고 랭킹 페이지에서 확인 가능         |
| 대시보드    | 획득한 뱃지, 역량 진단표, 타임라인 등 사용자의 종합 활동 리포트 시각화                 |
| 커리어            | 보안 분야 채용공고 목록 및 상세정보 확인, 필터링 검색           |
| 커뮤니티    | Q&A, 관리자에게 문의, 스터디 모집 등 게시글 작성 및 댓글 기능         |
| 마이페이지        | 내 정보 수정, 내가 쓴 게시글 및 내가 쓴 워게임 리뷰 확인                 |
| 관리자 기능       | 워게임/채용공고 등록 및 관리, 사용자 목록 확인 및 삭제           |

  <br><br>

  ### 📋 인프라 주요 기능
| 기능 영역         | 설명 |
|------------------|------|
| CI/CD 파이프라인  | Jenkins와 GitHub Actions를 활용한 자동 빌드 및 배포 |
| 보안 스캔        | Trivy로 이미지 보안 취약점 검사 수행 |
| 이미지 저장소     | Harbor로 내부 이미지 저장, DockerHub 대체 |
| 시크릿 관리       | Vault를 이용한 인증정보 및 환경변수 안전 저장 |
| 모니터링          | Prometheus + Grafana로 메트릭 수집 및 시각화 |
| 로그 수집         | Loki + Promtail로 시스템 로그 수집 및 분석 |
| 스토리지          | Rook-Ceph 기반 PVC 및 Amazon S3 활용 |
| 고가용성 구성     | 2개 AZ 기반 Master/Worker 분산 배치 |
| 네트워크 보안     | Bastion 서버, Public/Private 서브넷 분리 및 접근 제어 |
| 도메인 관리       | Route 53을 통한 도메인 라우팅 설정 |

<br><br>

---

<br>

# 3. 기술 스택

<br>

### < 인프라 >

<img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/techStack/infra_stack.png" alt="인프라 기술스택" width="800"/>

<br>

### < 백엔드 >

<img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/techStack/back_stack.png" alt="인프라 기술스택" width="500"/>

<br>

### < 프론트엔드 >

<img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/techStack/front_stack.png" alt="인프라 기술스택" width="500"/>

<br>

### < DB >

<img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/techStack/db_stack.png" alt="DB 기술스택" width="500"/>

<br><br>

---

<br>

# 4. 아키텍처

<br>

### 1) 온프레미스 - 클라우드 연동형 k8s 인프라 구조

<img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/techStack/infra_arch.png" alt="인프라 아키텍처" width="1000"/>

<br>

[ 온프레미스 노드 구성 및 사양 ]

<img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/techStack/onpre_table.png" alt="온프레 테이블" width="500"/>

<br>

[ 클라우드 노드 구성 및 사양 ]

<img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/techStack/cloud_table.png" alt="온프레 테이블" width="500"/>

<br>

> [!TIP]
> 프로젝트 초기에는 AWS 비용을 절감하기 위해 온프레미스 자원을 우선적으로 활용해 인프라를 구성했습니다. <br> 이후 트래픽 증가와 서비스 안정성 확보를 위해 클라우드 기반 리소스를 구성했습니다.<br><br> 온프레미스에는 1대의 Master와 5대의 일반 Worker, 1대의 고사양 Worker 노드로 구성되었으며 <br> 클라우드 환경은 2개의 AZ를 활용해 Master/Worker 노드를 고가용성 구조로 분산 배치했습니다. <br> 또한 각 AZ에는 Bastion 서버를 별도로 두어 보안성과 접근 통제를 강화했습니다.


<br><br>

### 2) 전체 인프라 아키텍처

<br>

<img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/techStack/infra.png" alt="인프라 아키텍처" width="1000"/>

<br>

<img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/infra_description.png" alt="인프라 아키텍처" width="1000"/>

<br><br>


### 3) 애플리케이션 아키텍처

<br>

 - 3-Tier 아키텍처

<img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/techStack/app_arch.png" alt="앱 아키텍처" width="800"/>

•  Presentation Tier :<br>
  사용자와 직접 상호작용하는 웹 UI 구성, 요청을 백엔드로 전달하고 응답 결과를 화면에 표시
  
•  Application Tier :<br>
  비즈니스 로직 처리, 인증 및 데이터 접근 수행
  
•  Data Tier :<br>
  세션 캐싱(Redis), 파일 저장(S3), 관계형 데이터 관리(PostgreSQL) 등 각종 데이터를 저장하고 관리하는 역할 담당

<br><br>

- MVC 모델

<img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/techStack/mvc.png" alt="mvc 모델" width="800"/>

•  View :<br>
  기능별 UI 구조(pages) + 컴포넌트 단위 구성(components)으로 나뉘며 라우팅과 마운트는 App.tsx, main.tsx에서 처리
  
•  Controller :<br>
  요청을 받아 각 도메인의 서비스로 위임, 응답을 적절한 DTO로 변환해 반환
  
•  Model :<br>
  서비스 로직(service), DB 처리(repository), 엔티티(entity), 요청/응답 DTO(dto) 분리

<br><br>

---

<br>

# 5. 프론트엔드
<br><br>

<img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/menu_flow.png" alt="메뉴 흐름 요약도" width="800"/>


<br><br>

## ① 메인 화면 : 플랫폼의 핵심 가치와 방향성을 전달
<br>

<div style="display: flex; align-items: flex-start; gap: 16px;">
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front0.png" alt="프론트0" style="height: 300px, width: 300px;" />
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front00.png" alt="프론트00" style="height: 300px, width: 300px;" />
</div>

<br>

📌 기능 목록

```
•  상단 내비게이션 바(Navbar) : 로그인 버튼 / 워게임 / 랭킹 / 커뮤니티 / 커리어 / 대시보드 (로그인 시)

•  플랫폼 소개 영역 : 플랫폼명(가디언즈) 및 핵심 슬로건 소개

•  이용자 공감 문구

•  이모지 & 캐릭터 삽화 : 사용자의 고민을 시각적으로 전달

•  하단 후기 영역 (슬라이드 형태)

•  CTA(Call To Action) 버튼 : '회원가입하고 시작하기' 버튼 (로그인한 경우 '대시보드로 이동'으로 변경됨)
```

<br><br>

<br>

## ② 로그인 및 회원가입 : 사용자 인증 및 신규 사용자 등록
<br>

<div style="display: flex; align-items: flex-start; gap: 20px;">
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front1.jpg" alt="프론트1" style="height: 300px;" />
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front2.png" alt="프론트2" style="height: 300px;" />
</div>

<br>

📌 기능 목록

```
•  로그인 폼 : 이메일 + 비밀번호 입력 → 로그인 버튼 클릭 시 인증

•  회원가입 진입 버튼 : 로그인 화면 하단 이메일 회원가입 버튼을 통해 회원가입 화면으로 이동

•  비밀번호 찾기 : 로그인 화면 하단 링크로 비밀번호 재설정 페이지로 이동

•  회원가입 폼 : 이메일 인증, 닉네임 입력, 비밀번호 2회 입력

•  이용약관 동의 : 전체 동의 / 이용약관 동의 / 개인정보 수집 및 이용 동의 체크박스

•  회원가입 완료 버튼 : 모든 항목 입력 및 동의 시 버튼 활성화됨 
```

<br><br>

<br>

## ③ 워게임 : 해킹 실습 기반의 문제 풀이 플랫폼
<br>

<div style="display: flex; align-items: flex-start; gap: 16px;">
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front3.png" alt="프론트3" style="height: 300px, width: 300px;" />
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front4.png" alt="프론트4" style="height: 300px, width: 300px;" />
</div>

<br>

📌 기능 목록
```
•  워게임 검색 필터 : 카테고리 선택 / 난이도 선택 / 해결 여부 선택 / 즐겨찾기한 문제만 보기 토글 (내 북마크)

•  인기 워게임 추천 영역 : 사용자가 많이 푼 인기 워게임이 카드 형태로 좌우 슬라이드

•  워게임 목록 테이블 : 컬럼 - 제목, 카테고리, 난이도, 배점 (클릭 시 상세 페이지로 이동)

•  사용자 정보 카드 (우측) : 유저 정보 표시
```
<br><br>

<div style="display: flex; align-items: flex-start; gap: 16px;">
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front5.png" alt="프론트5" style="height: 300px, width: 300px;" />
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front6.png" alt="프론트6" style="height: 300px, width: 300px;" />
</div>

<br>

📌 기능 목록
```
•  워게임 정보 카드 : 제목 / 카테고리 / 난이도 / 배점 / 북마크 및 좋아요 버튼 (클릭 가능)

•  문제 파일 다운로드 : 문제 관련 .zip, .py, Dockerfile 등 분석 파일을 내려받을 수 있는 기능

•  해킹 실습 환경 : 웹 기반으로 접속 가능한 칼리 리눅스 GUI 환경 실행 (워게임 Pod와는 별개로, 문제해결을 위한 분석 및 테스트 도구가 내장됨)

•  워게임 인스턴스 : 시작 버튼 클릭 시 Pod의 URL을 자동 할당하여 사용자에게 접속 환경 제공

•  플래그 제출 영역 : 문제를 풀고 얻은 flag를 입력 / 정답 여부에 따라 메시지 출력

•  Q&A 영역 : 사용자들이 남긴 질문들을 확인 가능 / 질문 등록 버튼
```

<br><br> 

<br>

## ④ 랭킹 : 전체 사용자 순위 조회 및 검색
<br>

<div style="display: flex; align-items: flex-start; gap: 16px;">
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front7.png" alt="프론트7" style="height: 300px, width: 300px;" />
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front8.png" alt="프론트8" style="height: 300px, width: 300px;" />
</div>

<br>

📌 기능 목록
```
•  상위 TOP 3 프로필 카드 : 닉네임, 프로필 사진, 총 점수, 푼 문제 수 표시

•  닉네임 검색 기능 : 검색창을 통해 특정 사용자의 닉네임을 입력

•  전체 유저 순위 테이블 : 표 형태로 나열
```

<br><br>

<br>

## ⑤ 커뮤니티 : 사용자 간 정보 공유를 위한 공간
<br>

<div style="display: flex; align-items: flex-start; gap: 16px;">
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front9.png" alt="프론트9" style="height: 300px, width: 300px;" />
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front10.png" alt="프론트10" style="height: 300px, width: 300px;" />
</div>

<br>

📌 기능 목록
```
•  좌측 카테고리 메뉴 : 전체 게시판 / 핫 게시판 / 워게임 Q&A / 자유 게시판 / 스터디 모집 / 문의 게시판

•  각 카드에는 최신 글 몇 개가 리스트로 표시되며 “더보기” 버튼으로 특정 게시판 전체 보기로 이동 가능

•  상단 입력창 : 제목 및 내용으로 빠르게 검색 가능

•  질문하기 버튼 : 버튼 클릭 시, 새 질문 작성 페이지로 이동 (게시글 작성)
```

<br><br>

<br>

## ⑥ 커리어 : 보안 관련 채용 정보 제공 페이지
<br>

<div style="display: flex; align-items: flex-start; gap: 16px;">
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front11.png" alt="프론트11" style="height: 300px, width: 300px;" />
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front12.png" alt="프론트12" style="height: 300px, width: 300px;" />
</div>

<br>

📌 기능 목록
```
•  채용공고 필터 기능 : 회사명 키워드로 검색 가능 (지원 유형 선택 / 근로기간 선택 / 지역 선택 필터링)

•  채용 카드 리스트 : 클릭 시 해당 공고의 상세 페이지로 이동

•  채용 상세 페이지 : 채용 포지션 및 업무 소개
```

<br><br>

<br>

## ⑦ 대시보드 : 내가 푼 워게임 기반의 시각화된 피드백 제공
<br>

<div style="display: flex; align-items: flex-start; gap: 16px;">
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front13.png" alt="프론트13" style="height: 300px, width: 300px;" />
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front14.png" alt="프론트14" style="height: 300px, width: 300px;" />
</div>

<br>

📌 기능 목록
```
•  유저 활동 개요 영역 : 내 정보 및 뱃지 획득 현황

•  종합 활동 리포트 영역 : 역량 진단표 (Radar Chart) / 내가 푼 문제 수 (요일별 그래프) / 일별 점수 기록 (막대 그래프) / 풀이 타임라인
```

<br><br>

<br>

## ⑧ 관리자 전용 페이지 : 사용자 관리 및 워게임/채용공고 등록 및 삭제
<br>

<div style="display: flex; align-items: flex-start; gap: 16px;">
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front15.png" alt="프론트15" style="height: 300px, width: 300px;" />
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/front16.png" alt="프론트16" style="height: 300px, width: 300px;" />
</div>

<br>

📌 기능 목록
```
•  DevOps 관리 현황 모니터링 : 배포 및 인프라 관리 도구의 페이지로 접근 기능 

•  관리자 메뉴 : 대시보드 / 워게임 관리 / 커리어 관리 / 회원 관리

•  회원 관리 기능 : 관리자 그룹과 일반 사용자 그룹을 나눠서 표시 (권한, 삭제 버튼 포함)
```

<br><br>

---

<br>

# 6. 백엔드 및 DB

<br>

### < 패키지 다이어그램 >
<br>

  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/package_diagram.png" alt="패키지 다이어그램" width="700"/>

> [!NOTE]
> 이 패키지 다이어그램은 백엔드 전체 구조의 의존 관계를 시각화한 것입니다. <br>
<br> 요청은 controller → service → domain.repository → domain.entity 흐름으로 전달되며 <br>
dto는 계층 간 데이터 전달을, exception은 공통 예외 처리를 담당합니다. <br>
config는 전역 설정, 보안, CORS 등의 환경 구성을 포함합니다. <br><br>
전체 애플리케이션의 계층적 책임 분리를 통해 유지보수성과 확장성을 확보했습니다.


  <br><br>

### < 주요 기능별 클래스 흐름 >
<br>
  <img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/function_flow.png" alt="기능별 클래스 흐름" width="1000"/>

<br><br>

### < ERD >

<img src="https://raw.githubusercontent.com/BeeGuardians/bee-assets/main/images/ERD.png" alt="ERD" width="1000"/>


- users 테이블 : 사용자 기반의 모든 기능과 연동되는 플랫폼의 중심 테이블

- wargames 테이블 : 워게임 실습 환경의 Docker URL을 담고 있는 콘텐츠 중심 테이블

- 위 두 테이블을 중심으로, 사용자 활동과 워게임 콘텐츠를 둘러싼 대부분의 기능 테이블이 유기적으로 확장되며 ERD가 전개됨
  <br><br>

  ---

  <br>

  # 7. 인프라

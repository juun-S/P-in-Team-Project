# P-in-Team-Project

<a href="https://hits.seeyoufarm.com">
    <img src="https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Fjuun-S%2FP-in-TeamPJ_Java&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false" alt="Hit Counter for P-in-TeamPJ_Java"/>
</a>

## 네이버 클라우드 DevOps 10기 미니 프로젝트
---
## 👨‍🏫 프로젝트 소개
* **볼링장에서 음식 주문 및 직원 호출을 위해 사용하는 키오스크에 나만의 기록을 관리하고 사용자들의 랭킹을 보여주는 키오스크**
  이 프로젝트는 **Java Swing**을 사용한 **데스크탑 애플리케이션**으로, **멀티스레드 기반의 채팅 서버**와 **MySQL** 데이터베이스를 활용하여 데이터 관리와 실시간 통신을 처리합니다.

## ⏲️ 개발 기간
- 2024.03.25(월) ~ 2024.04.22(월)
- 04.19 : 프로젝트 마감
- 04.22 : 프로젝트 발표
- ### 1주차 : 프로젝트 주제 선정 및 데이터 모델링
- ### 2주차 : UI 설계 및 기능 구현
- ### 3주차 : Front + Back
- ### 4주차 : 최종 오류 수정 및 테스트 / 발표 준비

## 🧑‍🤝‍🧑 개발자 소개
- **김승민**(팀장), **최시호**, **강현욱**, **손유정**, **강보현**, **송예준**

## 💻 개발환경
<img src='https://img.shields.io/badge/Java%2017-%23ED8B00.svg?style=for-the-badge&logo=java&logoColor=white' alt='Java 17'/> <img src='https://img.shields.io/badge/IntelliJIDEA-000000.svg?style=for-the-badge&logo=intellij-idea&logoColor=white' alt='IntelliJ IDEA'/> <img src="https://img.shields.io/badge/mysql-4479A1.svg?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL"/>
- **Version** : Java 17
- **IDE** : IntelliJ
- **DB** : MySQL

## 📌 주요 기능 기획
- 기존 키오스크 기능
  - 사용자가 키오스크의 음식들을 클릭하면 그 음식에 해당되는 정보들이 장바구니 테이블로 옮겨진다.
  - 사용자가 결제를 클릭하게 되면 장바구니에 있는 값들의 결제 내역을 화면에 보여주고 장바구니 테이블을 삭제된다.
  - 삭제된 값들은 주문내역 테이블로 옮겨져 사용자는 결제한 내역(=주문내역)을 확인할 수 있다.
  - 직원 호출을 하게 되면 사용자는 호출할 항목을 선택하게 되고 선택 후에는 간단한 메세지를 띄어준다
- 나만의 기록 관리
  - 실제 볼링을 할 수 없는 관계로 간단한 볼링 알고리즘을 서치해서 볼링 게임 시뮬레이션을 진행한다.
  - 게임이 끝나면 게임의 기록들이 기록용 테이블, 집계용 테이블로 각각 들어가게 된다.
  - 사용자는 기록용 테이블을 통해 이전에 본인이 진행했던 게임의 기록들을 확인할 수 있다.
- 랭킹 조회
  - 집계용 테이블에 들어간 게임중 가장 점수가 높은 게임을 랭킹 테이블로 가져온다.
  - 랭킹 테이블에 점수값을 기준으로 순위를 매겨 사용자에게 순위표를 보여준다.

---

## 📝 이름 선정 규칙
1. 변수명은 최대한 직관적으로 알아볼 수 있게!!
2. 변수앞 태그는 테이블 필드값을 보면서 할것 (ex. 변수 : 사용자 이름 -> u_name)

## P-in 프로젝트 DB 테이블
- 사용자(user)
  - userid(유저아이디)      varchar()       not null
  - username(유저이름)      varchar()
  - pw(유저 비밀번호)       varchar()

- 게임(game)
  - game_code               int
  - point(게임당 점수)       int
  - game_date               date

- 게임기록(game_record)
  - game_code               int
  - point(게임당 점수)       int
  - game_date               date

- 음식(food)
  - food_no(음식 번호)          int
  - food_name(음식 이름)        varchar()
  - food_price(음식 가격)       int
  - food_image(음식 이미지)      blob
  - food_etc (음식 수량)         boolean
  - food_code(0,1)               int

- 장바구니(cart)
  - c_no(주문번호)                int        null
  - c_name(주문 상품 이름)        varchar()  null
  - c_ea(주문 수량)               int        null
  - c_price(주문 가격)            int        null
  - c_time(주문한 시간)           date       null

- 랭킹(rank)
  - userid                       varchar()
  - game_point                   int

## 프로젝트 구조

```
src/
│
├── naver/
│   └── pin_project/
│       ├── data/                   # 데이터 모델 클래스 정의 (User, Food, OrderInfo 등)
│       ├── db/                     # MySQL 데이터베이스 연결 및 SQL 처리
│       ├── game_feature/           # 게임 관련 기능 (랭킹 및 기록 조회)
│       ├── main/                   # 애플리케이션 진입점 (PinApp.java)
│       ├── view/                   # 사용자 인터페이스 (UI) 클래스
│       └── viewmodel/              # 비즈니스 로직 및 데이터 처리
│
└── lib/                            # 외부 라이브러리 (폰트, 이미지 등)
```

### 주요 패키지 설명

- **data**: 애플리케이션에서 사용되는 데이터 모델 정의. 예: `User`, `Food`, `OrderInfo`, `Ranking` 등이 포함됩니다.
- **db**: MySQL 데이터베이스와의 연결 및 쿼리 처리를 담당하는 패키지. `OjdbcConnection` 클래스를 통해 연결을 관리합니다.
- **game_feature**: 게임과 관련된 기능 (게임 기록 및 랭킹 관리).
- **view**: 사용자 인터페이스(UI) 관련 클래스. Java Swing 기반의 다양한 화면과 컴포넌트를 정의합니다.
- **viewmodel**: UI와 데이터 간의 비즈니스 로직을 처리하는 클래스. 로그인, 회원가입, 음식 주문 처리, 랭킹 계산 등.

## 주요 기능

### 1. **로그인 및 회원가입**

- **로그인**: 사용자는 MySQL 데이터베이스에 저장된 계정 정보를 기반으로 로그인할 수 있습니다. `Login_ViewModel`에서 SQL 쿼리를 실행해 사용자의 아이디와 비밀번호를 확인하고, 성공적으로 로그인하면 메인 화면으로 이동합니다.
- **회원가입**: 사용자는 `SignUp_ViewModel`을 통해 새로운 계정을 생성할 수 있습니다. 사용자의 아이디, 비밀번호, 전화번호 등 정보를 입력하고, 중복된 아이디를 확인한 후 저장됩니다.

### 2. **음식 주문 및 장바구니**

- **음식 메뉴 조회**: 사용자는 `FoodOrderScreen`에서 MySQL 데이터베이스에 저장된 음식 메뉴를 조회하고, 각 음식의 수량을 선택하여 장바구니에 추가할 수 있습니다.
- **장바구니 관리**: 선택한 음식은 장바구니에 저장되며, 사용자는 장바구니에서 주문 내역을 확인하고 결제 화면으로 이동할 수 있습니다. `FoodOrder_ViewModel`에서 음식 메뉴 데이터를 DB로부터 불러옵니다.

### 3. **결제 시스템**

- **결제 방식 선택**: 사용자는 `PaymentScreen`을 통해 카드 또는 현금 결제를 선택할 수 있습니다. 결제가 완료되면 주문 정보는 데이터베이스에 저장되고, 장바구니가 초기화됩니다.
- **주문 내역 저장**: 결제 완료 후 사용자의 주문 내역은 `OrderInfo` 데이터 모델로 관리되며, DB에 저장되어 추후 주문 기록으로 조회할 수 있습니다.

### 4. **직원 호출 및 채팅 기능**

- **직원 호출**: 사용자는 `StaffCallScreen`을 통해 특정 요청 사항(예: 핀 리셋, 공이 나오지 않음 등)을 직원에게 전달할 수 있습니다.
- **실시간 채팅**: `Chat_ViewModel`을 통해 클라이언트와 서버 간 실시간 채팅이 가능하며, 직원과의 채팅을 통해 문제 해결을 요청할 수 있습니다. 채팅 서버는 **멀티스레드**로 동작하여 다중 클라이언트의 요청을 처리합니다.

### 5. **실시간 및 월별 랭킹**

- **실시간 랭킹**: 사용자가 기록한 점수를 기반으로 실시간 랭킹을 조회할 수 있습니다. `Ranking_ViewModel`에서 DB에 저장된 게임 기록을 불러와 사용자들의 점수를 비교해 실시간으로 랭킹을 갱신합니다.
- **월별 랭킹**: 월별 게임 기록을 조회하여 상위 점수를 기록한 사용자들의 랭킹을 보여줍니다.

### 6. **마이페이지**

- **사용자 정보 수정 및 삭제**: `MyPage_ViewModel`을 통해 로그인한 사용자는 자신의 개인정보를 수정할 수 있으며, 필요 시 계정을 삭제할 수 있습니다. 삭제된 계정은  데이터베이스에서 제거됩니다.

### 7. **주문 내역 조회**

- 사용자는 `OrderListScreen`을 통해 과거 주문 내역을 확인할 수 있습니다. MySQL 데이터베이스에서 해당 사용자의 주문 기록을 불러와 테이블 형식으로 화면에 출력하며, 주문 시간, 음식명, 수량, 총 금액 등의 세부 정보를 확인할 수 있습니다.

## 기술 스택

### 1. **프로그래밍 언어 및 프레임워크**

<img src='https://img.shields.io/badge/Java%208-%23ED8B00.svg?style=for-the-badge&logo=java&logoColor=white' alt='Java 8 (Application Logic)'/> <img src='https://img.shields.io/badge/Java%20Swing-%236DB33F.svg?style=for-the-badge&logo=java&logoColor=white' alt='Java Swing (UI Implementation)'/> <img src='https://img.shields.io/badge/JDBC-%23007396.svg?style=for-the-badge&logo=java&logoColor=white' alt='JDBC (Database Integration)'/> <img src='https://img.shields.io/badge/멀티스레딩-%23FFCA28.svg?style=for-the-badge&logo=parallel&logoColor=black' alt='Multithreading (Concurrency for Chat Server)'/>
- **Java 8**: 주요 애플리케이션 로직 개발
- **Java Swing**: 사용자 인터페이스(UI) 구현
- **JDBC**: 데이터베이스 통합 및 SQL 처리
- **멀티스레딩**: 채팅 서버의 동시성 처리

### 2. **데이터베이스**
- **MySQL**: 사용자 정보, 음식 메뉴, 게임 기록, 주문 내역 등을 관리. `OjdbcConnection` 클래스를 통해 MySQL과 연결되며, SQL 쿼리를 사용하여 데이터 삽입, 조회, 수정, 삭제 기능을 수행합니다.

### 3. **멀티스레드 서버**
- **Java Thread**: 채팅 서버는 다중 클라이언트를 처리하기 위해 멀티스레드로 구현되었습니다. 서버는 클라이언트의 연결 요청을 대기하고, 새로운 클라이언트가 접속할 때마다 독립된 스레드에서 요청을 처리합니다.

## 메뉴 주문 시스템 [본인기여부분]

사용자가 음식 메뉴를 조회하고, 선택한 음식을 장바구니에 추가한 후 결제할 수 있는 시스템입니다.

### 주요 기능
1. 음식 메뉴 조회 및 선택
   메인 화면에서 데이터베이스에 저장된 음식 목록을 조회하고, 사용자는 음식을 선택하여 수량을 조절할 수 있습니다.
   선택된 음식은 장바구니에 저장되며, 장바구니 화면을 통해 주문 내역을 확인할 수 있습니다.
2. 결제 기능
   결제 화면에서 사용자는 카드 또는 현금 결제 방식을 선택할 수 있습니다.
   결제 완료 후, 주문 내역은 MySQL 데이터베이스에 저장되며 장바구니가 초기화됩니다.
3. 장바구니 및 주문 내역
   사용자는 장바구니에 추가한 음식 목록을 조회하고, 결제를 진행하거나 수정할 수 있습니다.
   주문 내역은 주문 정보를 기반으로 관리되며, 사용자는 추후 주문 내역을 조회할 수 있습니다.
###   로직 다이어그램

```mermaid
graph TD;
A[사용자] --> B[FoodOrderScreen]
B --> C{음식 선택}
C -->|음식 선택 및 수량 입력| D[장바구니에 추가]
D --> E[결제 화면으로 이동]
E -->|카드 결제| F[결제 처리 및 주문 내역 저장]
E -->|현금 결제| F[결제 처리 및 주문 내역 저장]
F --> G[장바구니 초기화]
G --> H[주문 완료 화면]
```

---

#### 설명:
* 사용자는 FoodOrderScreen에서 음식을 선택하고, 선택한 음식을 장바구니에 추가합니다.
* 장바구니에 추가된 후 결제 화면으로 이동합니다.
* 결제 화면에서 카드 결제 또는 현금 결제를 선택하여 결제를 진행합니다.
* 결제가 완료되면 주문 내역이 MySQL에 저장되고, 장바구니는 초기화됩니다.
* 마지막으로 주문 완료 화면이 표시됩니다.


## 라이선스

이 프로젝트는 **MIT 라이선스**에 따라 배포됩니다. 자세한 내용은 [LICENSE](LICENSE) 파일을 참조하세요.

--- 

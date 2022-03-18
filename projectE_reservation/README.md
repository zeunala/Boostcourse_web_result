# Project E: 예약관리 시스템 - 예약하기

### 개요

- 실제 네이버에서 운영하는 예약 시스템과 유사한 서비스를 만드는 것이 최종적인 목표로, Project E에서는 전체 예약서비스 중에 예약하기와 나의 예약 내역확인 기능을 구현한다.

## 기획서
### (1) 예약 화면
![E1](https://user-images.githubusercontent.com/79515820/154669034-e3d23600-5ce6-4bbc-bb22-16b8378741d2.png)

1. 상품정보
2. 티켓 수 선택
	- +, - 를 누르면 아래의 변화가 생긴다.
		- 숫자가 증가 또는 감소한다.
		- 금액이 변경된다.
		- 0명이면 - 버튼이 disabled된다.
3. 예매자 정보
	- 필수 정보는 입력돼야 한다.
	- 총매수는 예약상황을 합쳐서 개수가 변경될때 바로바로 변경되어 노출된다.
	- 연락처 정보는 전화번호 포맷(형식)만 입력이 가능해야 한다. 그 외의 값이 입력되면 입력된 값의 형식이 틀렸다는 메시지를 자유롭게 만들어서 화면에 노출해야 한다.
	- 예매내용내의 예매일은 웹프론트엔드에서 사용자가 선택하거나 입력해서 얻어지는 정보가 아니고, 서버에서 다음의 규칙으로 생성해서 내려준다.  (예매일생성 규칙 : 예매일 기준 오늘포함해서 1-5일 랜덤값으로 서버에서 생성)
4. 약관 동의 영역
	- 약관은 접기/보기로 토글된다.
	- 약관정보 동의에 체크하면 활성화된 상태로 보여진다.
	- 예매갯수가 1개이상, 예매자입력,연락처입력,약관동의 된 상태라면 모든 값이 유효한상태이다.
	- 모든 정보가 유효하다면 ‘예약하기' 버튼이 활성화된 상태로 노출된다.
5. 예약하기 버튼

### (2) 비회원 예약확인 화면
![E2](https://user-images.githubusercontent.com/79515820/154669036-d9c1300b-cdd1-45da-bb37-6e85777259cb.png)
- 모든 페이지의 ‘예약확인'을 누르면 비회원예약 확인 창이 노출된다.
- 별도의 비밀번호 인증없이 ‘예약자 이메일’만으로 조회가 가능하다.
- ‘내 예약확인' 을 버튼을 누르면 나의 예매내역 확인 페이지로 이동한다.

### (3) 나의 예매내역 확인 페이지
![E3](https://user-images.githubusercontent.com/79515820/154669039-3e0b7c22-2386-4bf8-8386-cb8fb4e5652a.png)

1. 나의 예약 요약정보
	- 요약된 나의 예약 정보가 노출된다.
2. 예약확정 리스트
	- 예약한 상품정보가 노출되고, ‘취소' 버튼이 있다.
	- 취소를 누르면 취소하겠냐는 메시지 레이어가 화면 가운데 뜨고 확인/취소를 통해 즉시 반영된다.
	- 취소된 이후에는 ‘취소된 예약’ 으로 새롭게 화면에 결과가 나온다. (4)
3. 예약상품 리스트
	- 이용완료 리스트가 노출된다.


## 웹프론트엔드 기술요구사항

- 자주 사용되는 함수를 객체형태로 묶어서 사용해야 한다.
- form에 입력된 값을 체크를 할 때는 값의 유효성(validation)을 체크해야 하며, 정규표현식을 사용해서 구현해야 한다.
- UI 별로 기능을 묶어서 객체화된 모듈을 만들어야 하며, prototype 방식을 적용해야 한다.
- 이전 프로젝트와 같이 클린코드의 규칙대로 코드를 구현한다.

## 웹백엔드 기술요구사항

- 예매확인을 위해 이메일을 입력 후 예약확인을 눌렀을 때 예매 내역이 있다면 이메일 정보를 세션에 저장한다.
- 메인화면의 경우 세션에 이메일 정보가 있을 경우 예매 확인 버튼 대신 이메일을 보여주고, 이메일을 클릭하면 해당 이메일로 예약된 예매 내역이 보이도록 한다.

## 구현을 위한 학습 내용
### Back-End
- Maven
- SQL
- Spring Core
- Spring MVC
- Spring JDBC
- Web API(post, put)
- Argument Resolver

### Front-End
- 생성자패턴
- 정규표현식
- form 유효성 검증과 전송

## ER 다이어그램
![ER](https://user-images.githubusercontent.com/79515820/150718045-886fcb1f-cf4a-42ef-8553-f22021db2895.png)

## 프로젝트 구성
![E4](https://user-images.githubusercontent.com/79515820/154790487-9b62ee33-b244-4d43-a4c3-ab894c54c415.png)

- org.boostcourse.reservation.controller: 프로젝트의 Controller 클래스 파일들을 담고 있는 패키지
	- ProductApiController.java (변경)
		- 현재 작품의 예약 가능일을 반환하는 메서드를 추가하였다. (오늘을 포함해서 1~5일의 무작위 값을 반환한다)
	- ReservationController.java (변경)
		- URL요청을 View와 연결해주는 컨트롤러로 /reserve, /bookinglogin, /myreservation 페이지를 추가하였으므로 관련된 코드를 추가하였다.
		- /myreservation페이지는 현재 로그인되어 있을 경우에만(세션 확인) 진입가능하도록 한다.
	- ReservationApiController.java
		- 지정된 API요청들이 들어올 때 그에 맞는 응답을 하는 역할을 하며, 예약정보 확인(GET), 예약하기(POST), 예약취소(PUT) 요청에 대해 처리하고 응답을 하도록 한다. 
- org.boostcourse.reservation.dto: 프로젝트에서 사용하는 DTO들을 담고 있는 패키지
	- AllCategories.java (변경)
	- AllPromotions.java (변경)
	- ProductByDisplayInfoId.java (변경)
	- SomeProducts.java (변경)
		- 기존 api.dto 패키지에 있던 파일 4개를 dto패키지에 병합하였다.
	- Reservation.java
		- 예약 하나하나와 관련된 DTO이다. 다음과 같은 멤버 변수들로 구성된다.
		- boolean cancelYn
		- String createDate
		- Integer displayInfoId
		- String modifyDate
		- Integer productId
		- String reservationDate
		- String reservationEmail
		- Integer reservationInfoId
		- String reservationName
		- String reservationTelephone
		- Integer totalPrice
	- ReservationByEmail.java
		- 특정 예약자 이메일에 대한 예약들의 리스트와 개수를 나타낼 때 사용하는 DTO이다. 다음과 같은 멤버 변수들로 구성된다.
		- List\<Reservation\> reservations
		- Integer size
	- ReservationParam.java
		- 예약하기 과정에서 클라이언트가 서버에게 파라미터를 넘겨줄 때 사용하는 DTO이다. 다음과 같은 멤버 변수들로 구성된다.
		- Integer displayInfoId
		- List\<ReservationPrice\> prices
		- Integer productId
		- String reservationEmail
		- String reservationName
		- String reservationTelephone
		- String reservationYearMonthDay
	- ReservationPrice.java
		- ReservationParam.java에서 사용하는 클래스로이다.
		- Integer count
		- Integer productPriceId
		- Integer reservationInfoId
		- Integer reservationInfoPriceId
			- 위 두 개의 멤버변수는 클라이언트에서 넘겨준값과 무관하게 DB에서 auto increment로 자동으로 설정되어 그 결과가 ReservationResult에 담긴다.
	- ReservationResult.java
		- 예약하기 과정 후 서버가 클라이언트에게 예약결과를 반환할 때 사용하는 DTO이다. 다음과 같은 멤버 변수들로 구성된다.
		- boolean cancelYn
		- String createDate
		- Integer displayInfoId
		- String modifyDate
		- List\<ReservationPrice\> prices
		- Integer productId
		- String reservationDate
		- String reservationEmail
		- Integer reservationInfoId
		- String reservationName
		- String reservationTelephone
- org.boostcourse.reservation.dao: 프로젝트에서 사용하는 DAO들을 담고 있는 패키지
	- ReservationDao.java
	- ReservationDaoSqls.java
		- Reservation와 관련된 DAO와 SQL문을 저장하는 클래스이다.
		- List\<Reservation\> selectReservations(String reservationEmail): reservationEmail에 해당하는 이메일로 예약한 모든 Reservation 목록을 가져온다.
		- int addReservation(ReservationParam reservationParam): reservationParam으로 넘어온 정보에 따라 DB에 추가한다.
		- int cancelReservation(Integer reservationId): DB에서 reservationId에 해당하는 예약의 cancel_flag을 1로 만들어 예약을 취소시킨다.
	- ReservationPriceDao.java
	- ReservationPriceDaoSqls.java
		- ReservationPrice와 관련된 DAO와 SQL문을 저장하는 클래스이다.
		- List\<ReservationPrice\> selectReservationPrices(Integer reservationId): reservationId에 해당하는 예약의 ReservationPrice 목록을 가져온다.
	- ReservationResultDao.java
	- ReservationResultDaoSqls.java
		- ReservationResult와 관련된 DAO와 SQL문을 저장하는 클래스이다.
		- ReservationResult selectReservationResult(Integer reservationId): reservationId에 해당하는 예약의 ReservationResult 정보를 가져온다.
- org.boostcourse.reservation.service: 프로젝트의 Service의 인터페이스들을 담고 있는 패키지
	- ReservationService.java
		- Reservation과 관련된 Service의 인터페이스이다.
- org.boostcourse.reservation.service.impl: 프로젝트의 Service의 실제 구현체들을 담고 있는 패키지
	- ReservationServiceImpl.java
		- Reservation과 관련된 Service의 실제 구현체로, @Autowired로 자동주입된 reservationDao(displayInfoDao 포함), reservationPriceDao, reservationResultDao 객체를 멤버 변수로 가진다.
		- boolean checkReservationValid(ReservationParam reservationParam): Reservation을 Dao로 추가하기 전 서버에서 한 번 더 유효성 검사를 하기 위해 만들어졌다.
		- ReservationResult getReservationResult(Integer reservationId): ReservationResultDao 객체의 selectReservationResult와ReservationPriceDao 객체의 selectReservationPrices를 호출한다.
		- List\<Reservation\> getReservations(String reservationEmail): ReservationDao 객체의 selectReservations를 호출하고 각 Reservation에 대해 DisplayInfoDao 객체의 selectDisplayInfo를 호출한다.
		- ReservationResult addReservation(ReservationParam reservationParam): 유효성 검사를 한 후 ReservationDao 객체의 addReservation를 호출하고 getReservationResult 메서드의 결과를 반환한다.
		- ReservationResult cancelReservation(Integer reservationId): ReservationDao 객체의 cancelReservation를 호출하고 getReservationResult 메서드의 결과를 반환한다.
- webapp/WEB-INF/views: jsp파일들을 담고 있는 폴더
	- mainpage.jsp (변경)
	- datail.jsp (변경)
		- 공통적으로 세션에 로그인된 이미지 정보가 있을 때 예약확인 대신 로그인된 이메일 정보가 나타나게 한다. 또한 클릭했을 때 로그인이 되지 않은 상태라면 비회원 예약확인 화면으로, 로그인된 상태라면 나의 예매내역 확인 페이지로 이동하도록 한다.
	- reserve.jsp: 웹 페이지의 예약 화면이다(reserve.png에 대응). 상세 페이지에서 '예매하기'를 눌렀을 때 이 화면으로 넘어와 해당 상품의 예약할 수 있도록 한다.
	- bookinglogin.jsp: 웹 페이지의 비회원 예약확인 화면이다(bookinglogin.png에 대응). 로그인 되지 않았을 때 '예약확인' 버튼을 눌렀을 때 여기로 이동하며, 이메일을 입력하면 로그인 후 예매내역을 확인할 수 있다.
	- myreservation.jsp: 웹 페이지의 나의 예매내역 확인 페이지이다(myreservation.png에 대응). 로그인된 상태에서 이동할 수 있으며, 로그인된 이메일로 예약된 상품들을 확인할 수 있다.
- webapp/js: js파일들을 담고 있는 폴더
	- detail.js (변경): detail.jsp에서 사용하는 자바스크립트 파일이다. 상세 페이지에서 '예매하기' 버튼을 눌렀을 때 현재 페이지에 해당하는 예약 화면으로 넘어갈 수 있도록 코드를 추가하였다.
	- reserve.js: reserve.jsp에서 사용하는 자바스크립트 파일이다. 먼저 상품가격을 포함한 예매에 필요한 정보들을 Ajax로 가져온다. 사용자가 티켓 수를 선택하면 그에 따라 가격 정보가 출력되도록 하고, 약관에 동의하면 예약하기 버튼이 활성화된다. 올바른 필수입력 정보를 입력하고 약관에 동의했을 때 예약하기 버튼이 동작하여 서버에게 데이터를 전송하는 역할 등을 수행한다.
	- bookinglogin.js: bookinglogin.jsp에서 사용하는 자바스크립트 파일이다. 이메일을 잘못된 형식으로 입력하지 않았는지 확인하는 역할을 한다.
	- myreservation.js: myreservation.jsp에서 사용하는 자바스크립트 파일이다. 먼저 현재 로그인된 이메일로 예약된 예약정보들을 Ajax로 가져온다. 사용자가 탭을 눌렀을 때 각 상태에 해당하는 예약들만 노출되도록 한다. 또한 취소버튼을 눌렀을 때 취소확인 문구가 일차적으로 뜨고 확인을 누르면 Ajax로 취소내용이 즉시 반영되도록 한다.


## Back-End 리뷰
### 리뷰 결과
![E5](https://user-images.githubusercontent.com/79515820/154791291-5602c62d-faf6-4e70-a6a0-4a8e8f71bd2c.png)

### 주요 코드 리뷰 반영사항
![E6](https://user-images.githubusercontent.com/79515820/154791292-47a8d3bc-7b81-4d88-bce6-e4eaf67d809d.png)
- ReservationDao.java에서 DB에 데이터를 삽입할 때 기존에는 INSERT문을 만들어서 실행하는 식으로 하였으나, SimpleJdbcInsert를 이용하여 쿼리문을 별도로 만들 필요 없이 삽입할 수 있도록 수정함

![E7](https://user-images.githubusercontent.com/79515820/154791293-f4105299-505f-4f4e-954a-ca3b9e8f6018.png)
- 예약취소를 구현할 때 기존에는 cancel_flag를 1로 만드는 UPDATE문, modify_date를 현재시점으로 수정하는 UPDATE문, 총 두 개를 만들었으나, 이를 하나의 쿼리문으로 합쳐 불필요한 부분을 제거함

## Front-End 리뷰
### 리뷰 결과
![E8](https://user-images.githubusercontent.com/79515820/154791294-8ea57652-c534-4fa6-8871-da7f71f8230a.png)

### 주요 코드 리뷰 반영사항
![E9](https://user-images.githubusercontent.com/79515820/154791295-23778806-a83d-45c1-949d-e460eb149b5e.png)
- 프론트엔드는 개발자도구를 이용해서 악의적인 사용자가 원하는대로 바꿀 수 있다는 취약점이 있기에, 이메일 형식 체크 등을 프론트엔드뿐만 아니라 백엔드에서도 이중으로 체크하도록 수정함

![E10](https://user-images.githubusercontent.com/79515820/154791290-0c6accb4-1ece-4df9-bd49-590e63e43e6a.png)
- 사용자 경험 측면을 고려하여, placeholder를 통하여 사용자가 정확히 어떤 형식을 입력해야 하는지 알 수 있도록 수정함
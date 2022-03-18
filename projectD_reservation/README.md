# Project D: 예약관리 시스템 - 상세 페이지 개발

### 개요

- 실제 네이버에서 운영하는 예약 시스템과 유사한 서비스를 만드는 것이 최종적인 목표로, Project D에서는 전체 예약서비스 중에 '상세 페이지'를 구성한다.

## 기획서
### (1) 상세 페이지 전체 구성

![D1](https://user-images.githubusercontent.com/79515820/153696438-6016044e-1875-49b8-8b7d-6720161dca06.png)


### (2) 상세 페이지 상단영역

![D2](https://user-images.githubusercontent.com/79515820/153696440-ead34b49-d6ca-4088-9192-9720f242376d.png)

1. 타이틀
	- (1.1) 홈 버튼
		-  클릭시 예약홈(메인페이지)으로 이동한다.
	- (1.2) 나의 예약
		- 클릭시 나의 예약 페이지로 이동한다. (프로젝트 E에서 관련 내용 구현)
	- (1.3) 배경사진의 번호
		-  1.5 네비버튼을 눌러 네비게이션을 할 때 해당 번호로 노출된다.
		-  최대로 노출해야 하는 개수는 1개 또는 2개이다. (기타이미지 존재시 2개노출)
	- (1.4) 배경영역
		- 서버에서 생성한 메인이미지가 노출된다.
	- (1.5) 네비버튼
		- 네비버튼은 메인이미지 (type = ‘ma’) 이외에 기타이미지 (type = ‘et’) 가 존재할 때만 노출된다.
		- 따라서 상세페이지가 로딩된 후 Ajax를 통해서 기타이미지가 있는지 확인해야 한다.
		- 기타이미지가 여러개 API에 존재하더라도, 실제로는 한 개만 더 화면에 노출한다.
		- 터치이벤트 발생시 슬라이딩 애니메이션 되며 다른 사진을 노출한다.
	- (1.6) 타이틀(제목)
		- 전시타이틀이 화면 가운데 텍스트로 노출되도록 해야 한다.
2. 펼쳐보기
	- 펼쳐보기를 누르면 펼쳐져서 보인다.
	- 다시 누르면 접기가 된다.
3. 이벤트정보
	- 클릭시 별도의 반응은 없다.
4. 예매하기  
	- 클릭시 예매페이지로 이동한다. (프로젝트 E에서 관련 내용 구현)

### (3) 상세 페이지 하단영역(예매자 한줄평)
![D3](https://user-images.githubusercontent.com/79515820/153696442-79fa6b59-5690-43d6-8d45-4707f3990fbc.png)

5. 상세설명 영역
	- (5.1) 한줄평 요약
		- 5.0만점의 평균과 총 건수를 표시한다.
	- (5.2) 한줄평 내용
		- 이미지는 한 장 노출된다.
		- 하단에 평점, 이메일, 방문날짜가 표시된다.
		- 이미지는 클릭시 반응이 없다.
	- (5.3) 더보기
		- 리스트는 3개까지만 노출하고 그 이상은 ‘더보기'버튼을 눌러서 전체 한줄평 노출 페이지로 이동한다.

### (4) 전체 한줄평 노출 페이지
![D4](https://user-images.githubusercontent.com/79515820/153696444-0c38302d-6ff5-4c7a-a0af-234b0fcaacfe.png)
- 상세페이지 하단의 ‘더보기'를 누르면 전체 한줄평 리스트 화면이 우측처럼 노출된다.

### (5) 상세 페이지 하단영역(상세설명)
![D5](https://user-images.githubusercontent.com/79515820/153696445-1d392ee0-4d50-4fcc-a097-acda737f0378.png)

6. 상세설명/오시는 길
	- (6.1) 상세정보와 오시는길
		- 탭으로 전환되며, 오시는 길을 누르면 6.4 콘텐츠가 노출된다.
	- (6.2) 공지사항(또는 상세사진) 이미지 노출
		- 공지사항은 이미지로 노출된다. (모든 아이템이 같은 이미지를 쓴다)
	- (6.3) TOP
		- 선택시 상단으로 이동한다.
	- (6.4) 오시는 길
		- 전시타이틀/새주소/지번주소/세부주소/전화번호가 노출된다.
		- 길찾기/네비게이션은 클릭시 반응이 없다.
		- 지도는 동일한 내용의 지도이미지를 노출한다.

## 웹프론트엔드 기술요구사항

- 전체 코드는 객체리터럴 패턴으로 구현해야 하고, 더불어 전역변수를 최소화해야 한다.
- 한 개 이상 객체리터럴을 사용할 수 있다.
- 상단 타이틀 이미지 영역의 애니메이션은 CSS3의 transition과 transform을 활용해서 구현해야 한다.
- 상단에 추가로 노출해야 하는 기타 이미지는 Ajax요청을 통해 가져온다.
- DOMContentloaded 이후에 모든 자바스크립트 로직이 동작하게 한다.
- Event delegation으로 처리할 수 있는 영역은 최대한 delegation방법으로 처리한다.
- Templating 작업은 handlebar 라이브러리를 사용해서 구현해야 한다.  
- 함수 하나에 여러 개의 기능을 넣지 않고, 함수를 여러 개로 분리한다.
- 중복코드를 제거하고 공통부분은 공통함수로 만든다.
- 변수와 함수 이름은 본인이 정한 코딩컨벤션을 최대한 지킨다.
- 접기/펼치기 기능은 jQuery 라이브러리를 사용할 수 있다.

## 웹백엔드 기술요구사항

- controller, service, dao로 레이어드 아키텍쳐를 구성한다.
- spring JDBC를 이용하여 주어진 테이블로부터 입력, 수정, 삭제, 조회하는 DAO와 DTO를 작성한다.
- 서비스 인터페이스를 작성하고 해당 인터페이스에 비지니스 메소드를 추가한다.
- 서비스 인터페이스를 구현하는 클래스를 작성하고 클래스 내 메소드에 적절한 트랜잭션에 관련된 어노테이션을 사용한다.
- 클라이언트에게 Web API를 제공하기 위해 RestController를 작성한다.

## 구현을 위한 학습 내용
### Back-End
- Maven
- SQL
- Spring Core
- Spring MVC
- Spring JDBC
- Web API(get)
- Logging

### Front-End
- 배열의 higher order fuctions
- 객체리터럴, this, bind
- handlebar 기반 templating
- 클린코드

## ER 다이어그램
![ER](https://user-images.githubusercontent.com/79515820/150718045-886fcb1f-cf4a-42ef-8553-f22021db2895.png)

## 프로젝트 구성
![D6](https://user-images.githubusercontent.com/79515820/153698163-8749db1c-b64f-46f2-970c-17f4daf193a8.png)

- org.boostcourse.reservation.api.dto: 클라이언트에게 Web API를 제공할 때 필요한 DTO를 담고 있는 패키지
	- 프로젝트 C에서는 DTO를 만들지 않고 ReservationApiController.java 하나의 파일에서 모두 해결하였지만, 유지보수의 용이성 등을 위하여 ApiController에서 리턴할 내용들을 DTO로 정의하였다.
	- AllCategories.java: List\<Category\> items를 멤버변수로 가지는 DTO이다.
	- AllPromotions.java: List\<Promotion\> items를 멤버변수로 가지는 DTO이다.
	- ProductByDisplayInfoId.java
		- 상품의 전시 정보 관련 API에서 사용하는 DTO이다. 다음과 같은 멤버 변수들로 구성된다.
		- Double averageScore: 해당 상품에 대한 한줄평들의 평균점수에 해당한다.
		- List\<Comment\> comments: 해당 상품에 대한 한줄평들의 목록에 해당한다.
		- DisplayInfo displayInfo: 해당 상품의 카테고리, 제목, 설명, 장소 등이 들어간다.
		- DisplayInfoImage displayInfoImage: 해당 상품에 대한 지도 이미지와 관련된 정보들이 들어간다.
		- List\<ProductImage\> productImages: 해당 상품에 대한 메인 이미지, 기타 이미지에 대한 정보들이 들어간다.
		- List\<ProductPrice\> productPrices: 해당 상품의 가격 정보들이 들어간다. List의 각 요소에는 좌석의 종류와 가격 등의 정보가 들어간다.
	- SomeProducts.java: List\<Category\> items와 Integer totalCount를 멤버변수로 가지는 DTO이다. 지정한 카테고리에 대해 최대 4개 상품에 대한 Product 정보와 해당 카테고리의 총 상품 수에 대한 정보가 담긴다.
- org.boostcourse.reservation.controller:
	- CategoryApiController.java
	- ProductApiController.java
	- PromotionApiController.java
		- 프로젝트 C의 ReservationApiController.java를 사용하는 기능들에 따라 세 개의 클래스로 분리하였다. 각 파일들은 그에 대응하는 @Autowired로 자동주입된 Service 객체들을 멤버 변수로 가진다. 
	- ReservationController.java (변경): URL요청을 View와 연결해주는 컨트롤러로 /detail 페이지와 /review 페이지를 추가하였으므로 관련된 코드를 추가하였다.
- org.boostcourse.reservation.dto: 프로젝트에서 사용하는 DTO들을 담고 있는 패키지
	- Comment.java
		- 한줄평 하나하나와 관련된 DTO이다. 다음과 같은 멤버 변수들로 구성된다.
		- String comment
		- Integer commentId
		- List\<CommentImage\> commentImages
		- String createDate
		- String modifyDate
		- Integer productId
		- String reservationDate
		- String reservationEmail
		- Integer reservationInfoId
		- String reservationName
		- String reservationTelephone
		- Double score
	- CommentImage.java
		- 한줄평에 첨부된 이미지와 관련된 DTO이다. 다음과 같은 멤버 변수들로 구성된다.
		- String contentType
		- String createDate
		- boolean deleteFlag
		- Integer fileId
		- String fileName
		- Integer imageId
		- String modifyDate
		- Integer reservationInfoId
		- Integer reservationUserCommentId
		- String saveFileName
	- DisplayInfo.java
		- 전시상품 하나하나와 관련된 DTO이다. 다음과 같은 멤버 변수들로 구성된다.
		- Integer categoryId
		- String categoryName
		- String createDate
		- Integer displayInfoId
		- String email
		- String homepage
		- String modifyDate
		- String openingHours
		- String placeLot
		- String placeName
		- String placeStreet
		- String productContent
		- String productDescription
		- String productEvent
		- Integer productId
		- String telephone
	- DisplayInfoImage.java
		- 전시상품에 대한 지도 이미지와 관련된 DTO이다. 다음과 같은 멤버 변수들로 구성된다.
		- String contentType
		- String createDate
		- boolean deleteFlag
		- Integer displayInfoId
		- Integer displayInfoImageId
		- Integer fileId
		- String fileName
		- String modifyDate
		- String saveFileName
	- ProductImage.java
		- 전시상품에 대한 메인 이미지, 기타 이미지와 관련된 DTO이다. 다음과 같은 멤버 변수들로 구성된다.
		- String contentType
		- String createDate
		- boolean deleteFlag
		- Integer fileInfoId
		- String fileName
		- String modifyDate
		- Integer productId
		- Integer productImageId
		- String saveFileName
		- String type
	- ProductPrice.java
		- 전시 상품의 각각의 좌석에 대한 가격 정보들이 들어가는 DTO이다. 다음과 같은 멤버 변수들로 구성된다.
		- String createDate
		- Double discountRate
		- String modifyDate
		- Integer price
		- String priceTypeName
		- Integer productId
		- Integer productPriceId
- org.boostcourse.reservation.dao: 프로젝트에서 사용하는 DAO들을 담고 있는 패키지
	- CommentDao.java
	- CommentDaoSqls.java
		- Comment와 관련된 DAO와 SQL문을 저장하는 클래스이다.
		- List\<Comment\> selectComments(Integer displayInfoId): displayInfoId에 해당하는 상품의 Comment 목록을 가져온다.
		- double selectAverageScore(Integer displayInfoId): displayInfoId에 해당하는 상품의 한줄평 점수 평균을 가져온다.
	- CommentImageDao.java
	- CommentImageDaoSqls.java
		- CommentImage와 관련된 DAO와 SQL문을 저장하는 클래스이다.
		- List\<CommentImage\> selectCommentImages(Integer commentId): commentId에 해당하는 한줄평에서 첨부된 이미지에 대한 CommentImage 리스트를 가져온다.
	- DisplayInfoDao.java
	- DisplayInfoDaoSqls.java
		- DisplayInfo와 관련된 DAO와 SQL문을 저장하는 클래스이다.
		- DisplayInfo selectDisplayInfo(Integer displayInfoId): displayInfoId에 해당하는 상품의 DisplayInfo 정보를 가져온다.
	- DisplayInfoImageDao.java
	- DisplayInfoImageDaoSqls.java
		- DisplayInfoImage와 관련된 DAO와 SQL문을 저장하는 클래스이다.
		- DisplayInfoImage selectDisplayInfoImage(Integer displayInfoId): displayInfoId에 해당하는 상품의 DisplayInfoImage 정보를 가져온다.
	- ProductImageDao.java
	- ProductImageDaoSqls.java
		- ProductImage와 관련된 DAO와 SQL문을 저장하는 클래스이다.
		- List\<ProductImage\> selectProductImages(Integer displayInfoId): displayInfoId에 해당하는 상품의 ProductImage 목록을 가져온다.
	- ProductPriceDao.java
	- ProductPriceDaoSqls.java
		- ProductPrice와 관련된 DAO와 SQL문을 저장하는 클래스이다.
		- List\<ProductPrice\> selectProductPrices(Integer displayInfoId): displayInfoId에 해당하는 상품의 ProductPrice 목록을 가져온다.
- org.boostcourse.reservation.service: 프로젝트의 Service의 인터페이스들을 담고 있는 패키지
	- CategoryService.java (변경)
	- ProductService.java (변경)
	- PromotionService.java (변경)
		- 프로젝트 C에서의 OOOService.java 파일들을 인터페이스와 실제 구현체로 분리하였다.
- org.boostcourse.reservation.service.impl: 프로젝트의 Service의 실제 구현체들을 담고 있는 패키지
	- CategoryServiceImpl.java
	- ProductServiceImpl.java
	- PromotionServiceImpl.java
		- 프로젝트 C에서의 OOOService.java 파일들의 기존 내용들을 OOOServiceImpl.java로 이동하였다. 또한 프로젝트 D에서 추가된 DAO객체들의 메서드를 호출하는 함수들을 추가한다.
- webapp/WEB-INF/views: jsp파일들을 담고 있는 폴더
	- mainpage.jsp (변경): 웹 페이지의 메인 화면이다. 상세 페이지를 만들었으므로 각각의 상품을 클릭하면 관련 상품의 상세 페이지 화면으로 이동하도록 수정하였다.
	- detail.jsp: 웹 페이지의 상세페이지 화면이다(detail.png에 대응). 메인 화면에서 상품을 클릭하면 이 화면으로 넘어와 해당 상품의 이미지/정보들을 보여준다.
	- review.jsp: 전체 한줄평 노출 페이지이다(review.png에 대응). 상세페이지 하단의 '더보기'를 눌렀을 때 이 화면으로 넘어와 해당 상품의 전체 한줄평 목록들을 보여준다.
- webapp/js: js파일들을 담고 있는 폴더
	- mainpage.js (변경): mainpage.jsp에서 사용하는 자바스크립트 파일이다. 프로젝트 C에서는 단순히 함수들을 나열했다면, 프로젝트 D에서는 객체리터럴 패턴을 이용하도록 변경하여 함수들의 기능에 따라 ProductObj, PromotionObj, EventObj의 객체안에 위치하도록 수정하였다.
	- common.js: 여러 페이지에 공통적으로 사용되는 자바스크립트 파일이다. TOP 버튼 클릭시 스크롤 처리와 같은 작업들이 여기에 위치한다.
	- detail.js: detail.jsp에서 사용하는 자바스크립트 파일이다. 먼저 상품과 관련된 정보들을 Ajax로 가져와서 보여준다. 사용자가 네비버튼을 눌렀을 때 메인 이미지를 슬라이딩 시키는 역할을 하며, 펼쳐보기를 누르면 생략된 전시상품 설명이 펼쳐지도록 한다. 또한 상세페이지 하단의 상세정보/오시는길 탭을 눌렀을 때 탭이 전환되며 관련 콘텐츠가 노출되도록 하는 역할 등을 수행한다.
	- review.js: review.jsp에서 사용하는 자바스크립트 파일이다. 상품의 전체 한줄평 정보를 가져와서 사용자에게 보여주는 역할을 수행한다.


## Back-End 리뷰
### 리뷰 결과
![D7](https://user-images.githubusercontent.com/79515820/153702337-61a056f6-1b28-4b50-8b0a-63b73b6c7238.png)

### 주요 코드 리뷰 반영사항
![D8](https://user-images.githubusercontent.com/79515820/153702339-93336109-ae6b-46cf-b5be-bf894c770f30.png)
- 기존에는 api Controller를 ReservationApiController라는 하나의 클래스 파일에서 모두 처리하였으나, 역할에 맞게 CategoryApiController, ProductApiController, PromotionApiController로 나누어 향후 확장 및 유지보수가 용이하도록 변경함

![D9](https://user-images.githubusercontent.com/79515820/153702340-10dd4822-64fb-4e12-8dae-ea5a7457a3d5.png)
- ApiController에서 리턴할 내용들을 DTO로 만들어 정의하도록 수정함

![D10](https://user-images.githubusercontent.com/79515820/153702341-c5ae0a5a-3376-4729-a0c2-c7b00c302fac.png)
- 코드의 가독성 향상 등의 목적을 위하여 기존에 IF문을 이용해 값이 없으면 0으로 설정한 부분을 IFNULL을 이용하도록 수정함

![D11](https://user-images.githubusercontent.com/79515820/153702343-55aade2c-8741-482e-a83b-5574f5d68c27.png)
- 기존에는 각 JOIN별 성능의 차이를 고려하지 않고 일괄적으로 LEFT JOIN을 사용하여 테이블을 JOIN하도록 하였으나, INNER JOIN을 사용할 수 있는 부분들은 INNER JOIN을 이용하도록 변경해서 이후 데이터가 많아졌을 때 성능 문제가 발생하지 않도록 개선함


## Front-End 리뷰
### 리뷰 결과
![D12](https://user-images.githubusercontent.com/79515820/153702345-a136ab5f-07f9-483c-83dc-b4aa05c3a918.png)

### 주요 코드 리뷰 반영사항

![D13](https://user-images.githubusercontent.com/79515820/153702346-d51df638-2d39-41e3-89b2-6e8ae348978e.png)
- 자바스크립트에서 관습적으로 사용하는 표기법, 특히 다른 언어에서의 private 접근지정자 개념을 언더바 표기법을 이용하여 관습적으로 명명한다는 것을 알게 되었으며, 이에 맞도록 객체/필드/메서드 명들을 수정함

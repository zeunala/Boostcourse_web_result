# Project C: 예약관리 시스템 - 메인 화면 개발

### 개요

- 실제 네이버에서 운영하는 예약 시스템과 유사한 서비스를 만드는 것이 최종적인 목표로, Project C에서는 전체 예약서비스 중에 '메인 화면'을 구성한다.

## 기획서
### (1) 메인 화면

![C1](https://user-images.githubusercontent.com/79515820/150627476-7714be66-f401-4c5f-98d3-d3edf9ae0991.png)

1. GNB 영역
	- 예약이미지를 클릭하면 아무반응이 없다.
	- 모든 하위페이지에서 동일하게 적용한다.
	- 비회원로그인 된 이메일정보를 보여준다.
	- 클릭 시 나의예약확인 페이지로 이동한다.
	- 로그인 안된 상태라면, ‘예약확인'으로 노출한다.
2. 프로모션 영역
	- 슬라이딩 기능을 구현한다.
		- 이미지 (type = 'th')를 순차적으로 노출한다.
		- 자동슬라이딩되며 끝까지 가면 다시 되돌아와서 처음 내용이 노출된다.
		-  슬라이딩은 좌측으로 이동하며, 이동되는 것이 보인다.
3. 카테고리 영역
	- 화면이 노출될때 처음엔 ‘전체리스트' 항목이 노출된다.
	- 노출되는 아이템 개수는 기본 4개이다. 
	- 카테고리내 장르를 선택하면 화면이동 없이 해당 장르 결과가 5번 영역에  노출된다.
	- 선택된 장르 메뉴는 녹색으로 하이라이트 된다.
4. 총 개수표시 영역
	- 장르별 노출가능한 아이템 총 개수를 노출한다.
5. 상품리스트
	- 선택된 장르에 맞는 결과를 노출한다.
	- 각 아이템별로 썸네일이미지 (type = ‘th’), 제목, 장소, 설명을 노출한다.
	- 아이템을 선택하면(클릭) 상세페이지로 이동한다.
6. 더보기 영역
	- 더보기를 누르면 4개씩 추가 데이터를 가져오고 그 결과가 화면에 노출된다.
	- 추가로 보여줄 데이터가 없다면 더보기UI는 사라진다.
7. TOP
	- TOP영역이 선택되면, 화면 맨 위로 이동한다.

## 웹프론트엔드 기술요구사항

- DOMContentloaded 이후에 모든 자바스크립트 로직이 동작하게 한다.
- 상단영역의 애니메이션은 CSS3의 transition과 transform 속성을 활용해서 구현한다.
- TABUI로 구성되는 카테고리 아이템이 노출되는 영역의 HTML은 카테고리별로 각각 만들지 않고 하나로 만들어 재사용한다.
- 카테고리 탭을 선택할 때마다, Ajax 요청을 해서 데이터를 가져온다.
- 탭 메뉴 (전시/뮤지컬/콘서트 등)는 Event delegation으로 구현한다.
- Template 코드를 javascript 함수 안에 보관하지 않고, 별도 분리시켜서 사용해야 한다. (HTML에 script태그 안에 보관하는 등)
- 함수 하나에 여러 개의 기능을 넣지 않고, 함수를 여러 개로 분리해야 한다.


## 웹백엔드 기술요구사항

- 제공된 SQL을 이용해서 테이블을 생성하고, 샘플데이터를 입력한다.
- maven을 이용해서 웹 어플리케이션 프로젝트를 작성한다.
- controller, service, dao로 레이어드 아키텍쳐를 구성한다.
- spring JDBC를 이용하여 주어진 테이블로부터 입력, 수정, 삭제, 조회하는 DAO와 DTO를 작성한다.
- 서비스 인터페이스를 작성하고 해당 서비스 인터페이스에 비지니스 메소드를 작성한다.
- 서비스 인터페이스를 구현하는 클래스를 작성한다.
- 해당 구현 클래스의 메소드에 적절한 트랜잭션에 관련된 어노테이션을 사용한다.
- 클라이언트에게 Web API를 제공하기 위해 RestController를 작성한다.

## 구현을 위한 학습 내용
### Back-End
- Maven
- SQL
- Spring Core
- Spring MVC
- Spring JDBC
- Web API(get)

### Front-End
- 자바스크립트 자료구조
- DOM APIs
- JSON과 Ajax 응답 처리
- 웹 애니메이션
- event delegation
- vanilla HTML templating

## ER 다이어그램
![C2](https://user-images.githubusercontent.com/79515820/150718045-886fcb1f-cf4a-42ef-8553-f22021db2895.png)

## 프로젝트 구성
![C3](https://user-images.githubusercontent.com/79515820/150718041-7700b527-61bd-4558-977e-923f482fa53a.png)
- org.boostcourse.reservation.config: 프로젝트 설정과 관련된 클래스 파일들을 담고 있는 패키지
	- WebMvcContextConfiguration.java
		- DispatcherServlet의 설정을 담당하는 클래스이다.
		- controller 패키지를 대상으로 ComponentScan을 하며, 기본으로 보여줄 뷰를 세팅하고 뷰의 이름을 가지고 실제 어떤 뷰에 대응하는지 찾아내는 등의 역할을 수행한다.
	- DBConfig.java
		- 데이터베이스의 관련된 설정을 해주는 클래스이다.
		-  사용자 간의 트랜잭션 처리를 위해서, @EnableTransactionManagement 어노테이션과 함께 TransactionManagementConfigurer 구현 후 annotationDrivenTransactionManager를 오버라이딩하였다.
	- ApplicationConfig.java
		- DAO와 Service 객체들의 설정을 담당하는 클래스이다.
		- dao패키지와 service패키지를 대상으로 @ComponentScan을 하여 컴포넌트 들을 읽어오고, DBConfig.class를 대상으로 @Import한다.
- org.boostcourse.reservation.dto: 프로젝트에서 사용하는 DTO들을 담고 있는 패키지
	- Category.java
		- 카테고리 하나하나와 관련된 DTO이다. 다음과 같은 멤버 변수들로 구성된다.
		- Integer count: 카테고리에 속한 전시상품 수에 해당한다.
		- Integer id: 카테고리 ID에 해당한다.
		- String name: 카테고리 이름에 해당한다. 
	- Product.java
		- 각각의 전시 상품과 관련된 DTO이다. 다음과 같은 멤버 변수들로 구성된다.
		- Integer displayInfoId: 전시 ID에 해당한다.
		- String placeName: 전시 장소명에 해당한다.
		- String productContent: 상품 상세 설명에 해당한다.
		- String productDescription: 상품 설명에 해당한다.
		- Integer productId: 상품 ID에 해당한다.
		- String productImageUrl: 상품 썸네일 이미지 URL에 해당한다.
	- Promotion.java
		- 프로모션 영역에 나오는 각각의 상품들과 관련된 DTO이다. 다음과 같은 멤버 변수들로 구성된다.
		- Integer id
		- Integer productId
		- String productImageUrl
- org.boostcourse.reservation.dao: 프로젝트에서 사용하는 DAO들을 담고 있는 패키지
	- CategoryDao.java
	- CategoryDaoSqls.java
		- Category와 관련된 DAO와 SQL문을 저장하는 클래스이다.
		- List\<Category\> selectAll(): 각 category별로 상품의 개수를 포함한 전체 category 목록을 가져온다.
	- ProductDao.java
	- ProductDaoSqls.java
		- Product와 관련된 DAO와 SQL문을 저장하는 클래스이다.
		- List\<Product\> selectSome(Integer start, Integer count): display_info의 id를 기준으로 start번부터 count개까지의 Product 목록을 가져온다.
		- List\<Product\> selectSomeByCategory(Integer category, Integer start, Integer count): selectSome과 유사하나 추가적으로 category를 지정한다.
		- int selectCount()
			- display_info의 전체 행 개수를 리턴한다.
		- int selectCountByCategory(Integer category)
			- 지정한 category를 조건으로 하는  전체 display_info 개수를 리턴한다.
	- PromotionDao.java
	- PromotionDaoSqls.java
		- Promotion와 관련된 DAO와 SQL문을 저장하는 클래스이다.
		- List\<Promotion\> selectAll(): promotion 테이블에 있는 id와 product_id, 그리고 해당 product_id에 대응하는 이미지파일 주소를 product_img 테이블에서 가져온다.
- org.boostcourse.reservation.service: 프로젝트의 Service 클래스 파일들을 담고 있는 패키지
	- CategoryService.java
		- Category와 관련된 Service 클래스로, @Autowired로 자동주입된 CategoryDao 객체를 멤버 변수로 가진다.
		- List\<Category\> getAllCategories(): CategoryDao 객체의 selectAll을 호출한다.
	- ProductService.java
		- Product와 관련된 Service 클래스로, @Autowired로 자동주입된 ProductDao 객체를 멤버 변수로 가진다.
		- List\<Product\> getSomeProducts(Integer start): ProductDao 객체의 selectSome을 호출한다.
		- List\<Product\> getSomeProductsByCategory(Integer category, Integer start): ProductDao 객체의 selectSomeByCategory를 호출한다.
		- Integer getCount(): ProductDao 객체의 selectCount를 호출한다.
		- Integer getCountByCategory(Integer category): ProductDao객체의 selectCountByCategory를 호출한다.
	- PromotionService.java
		- Promotion와 관련된 Service 클래스로, @Autowired로 자동주입된 PromotionDao 객체를 멤버 변수로 가진다.
		- List\<Promotion\> getAllPromotions(): PromotionDao객체의 selectAll을 호출한다.
- org.boostcourse.reservation.controller: 프로젝트의 Controller 클래스 파일들을 담고 있는 패키지
	- ReservationController.java: URL요청을 View와 연결해주는 컨트롤러이다.
	- ReservationApiController.java: 지정된 API요청들이 들어올 때 그에 맞는 응답을 하는 역할을 한다. @Autowired로 자동주입된 Service 객체들을 멤버 변수로 가진다. 
- webapp/WEB-INF/views: jsp파일들을 담고 있는 폴더
	- index.jsp: mainpage로 리다이렉트 한다.
	- mainpage.jsp: 웹 페이지의 메인 화면 (main.png에 대응)
- webapp/css: css파일들을 담고 있는 폴더
	- bookinglogin.css
	- reservation.css
	- style.css
- webapp/js: js파일들을 담고 있는 폴더
	- mainpage.js: mainpage.jsp에서 사용하는 자바스크립트 파일이다. 먼저 프로모션 영역과 관련된 정보들과 상품 리스트 중 첫 4개에 대한 정보를 Ajax로 가져와서 보여주고, 더보기를 누르거나 탭을 바꿀 때 추가적으로 정보를 Ajax로 가져와서 사용자에게 보여주는 역할을 한다. 또한 프로모션 영역의 이미지들이 자동으로 슬라이딩 하도록 만들어주는 역할 등을 수행한다.

## Back-End 리뷰
### 리뷰 결과
![C4](https://user-images.githubusercontent.com/79515820/151942816-a8bda1ab-e7d3-4341-9874-0cd86a305726.png)

### 주요 코드 리뷰 반영사항
![C5](https://user-images.githubusercontent.com/79515820/151942826-907f3a65-aa84-404b-8c1f-a4911b74030b.png)
- @RequestParam 어노테이션에서 생략해도 무방한 정보들을 생략함

![C6](https://user-images.githubusercontent.com/79515820/151942827-7bcc8630-da89-46b4-b836-504e293b08b3.png)
- 기존에는 ReservationService라는 클래스 하나만 두어 Service 역할을 하도록 했으나, 각각의 책임에 맞게 CategoryService, ProductService, PromotionService로 나누어 SRP가 지켜지도록 수정함

![C7](https://user-images.githubusercontent.com/79515820/151942830-3e09c61a-05e4-46d5-8eec-2d60a2f91663.png)
- 클래스에서 상수, 멤버 변수, 생성자, 메서드 순으로 나타나도록 순서를 변경함

## Front-End 리뷰
### 리뷰 결과
![C8](https://user-images.githubusercontent.com/79515820/151942832-d7a66997-0243-4b65-9427-c844ddeb430d.png)

### 주요 코드 리뷰 반영사항

![C9](https://user-images.githubusercontent.com/79515820/151942833-7d6ec2ab-3627-49b4-8564-714ba982cc55.png)
- 기존에는 script태그를 body태그 최하단에 두었으나, defer 속성을 이용하여 head태그 안에 두면서도 html parsing이 끝난 후에 script가 실행되도록 변경함

![C10](https://user-images.githubusercontent.com/79515820/151942834-7b3866f6-55d9-4d41-9a7a-7dc3dda282c4.png)
- 기존에는 TOP버튼을 클릭했을 때 바로 화면의 최상단으로 이동하게 하였으나, 자바스크립트를 이용해 화면이 좀 더 부드럽게 이동하도록 수정함

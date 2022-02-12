# 부스트코스 웹 프로그래밍 프로젝트
네이버 커넥트 재단의 부스트코스에서 웹 프로그래밍 과정을 수행하는 중에 진행한 프로젝트로, 다양한 웹 페이지를 만들어보는 것을 목표로 한다.

- 부스트코스 규정상 소스코드는 공개하지 않습니다.
- 프로젝트 결과물의 캡쳐본과 구현 영상 파일은 각 프로젝트 폴더에 있습니다.
- 개발 환경
	- Eclipse IDE
	- Java 8, HTML5, CSS3, JavaScript(ES6)
	- Java Servlet (v3.1.0)
	- Apache Tomcat (v8.5)
	- Spring Framework (v5.3.9)
	- MySQL (v8.0.25)
- 프로젝트 목록
	 - Project A: 자기소개 홈페이지
	 - Project B: To Do 웹 애플리케이션
	 - Project C-F: 예약관리 시스템 만들기
- 수료증
	![1](https://user-images.githubusercontent.com/79515820/149649841-23e3760d-43e3-433c-a73d-81805795fcf8.jpg)



## Project A: 자기소개 홈페이지 만들기

### 개요

- 나를 소개하는 웹페이지를 만드는 것이 목표이다.
- HTML페이지 3개와 서블릿 1개를 Tomcat 서버 위에서 동작하도록 만든다.

### 웹프론트엔드 기술요구사항

-  html layout tag를 사용한다.
-  classname은 일정한 컨벤션을 유지한다.
-  의미에 맞는 tag를 최대한 사용한다. (div 사용은 최대한 자제)
-  position속성과 float를 사용해서 element를 배치한다.
-  id와 class등의 다양한 selector문법을 잘 활용한다.

### 웹백엔드 기술요구사항

-  톰캣서버를 통해서 자기소개 페이지가 동작하도록 한다.
-  서블릿페이지하나를 생성해서, url을 입력했을 때 시간데이터가 화면에 노출되도록 한다.

### 구현을 위한 학습 내용
#### Back-End
- Servlet, JSP

#### Front-End
- HTTP 와 웹동작원리
- browser 렌더링 원리
- HTML 구조화 설계
- CSS 스타일링 및 UI 레이아웃 구성
- HTML, CSS 디버깅

### 프로젝트 구성
![A1](https://user-images.githubusercontent.com/79515820/149650651-0740356d-809a-4021-85fb-477c0456d1bb.png)
- index.html: 웹 페이지의 첫 화면. (index.png에 대응)
- aboutme.html: 자기소개 버튼을 눌렀을 때 나오는 자기소개 화면 (aboutme.png에 대응)
- photo.html: 내사진 버튼을 눌렀을 때 나오는 내사진 화면 (photo.png에 대응)
- TodayServlet.java: 몇시예요 버튼을 눌렀을 때 나오는 현재시간 화면의 서블릿 (today.png에 대응)
- reset.css: 리셋역할을 하는 css코드
- style.css: html문서에서 사용하는 외부 스타일시트

### Back-End 리뷰
#### 리뷰 결과
![A2](https://user-images.githubusercontent.com/79515820/149651512-0594586e-ab26-47f5-b837-b98b6b4dbc6b.png)

#### 주요 코드 리뷰 반영사항
![A3](https://user-images.githubusercontent.com/79515820/149651513-299e3ca9-ce5b-4b4b-960b-88cad93b4331.png)
- serialVersionUID값을 유니크한 값으로 생성하도록 변경함

![A4](https://user-images.githubusercontent.com/79515820/149651514-525d1558-456b-48b6-953c-7dbf5a35ebae.png)
- 들여쓰기 기준을 tab 단위로 하도록 통일함

![A5](https://user-images.githubusercontent.com/79515820/149651510-0a89f7fb-cd9e-4d00-9ab4-e4904f66b40d.png)
- 오버라이드 된 메소드들에 대해 @Override 어노테이션을 붙이도록 변경함

### Front-End 리뷰
#### 리뷰 결과
![A6](https://user-images.githubusercontent.com/79515820/149652591-0739ea6f-0565-4192-928d-1ad9096c17b1.png)

#### 주요 코드 리뷰 반영사항
![A7](https://user-images.githubusercontent.com/79515820/149652764-3ff4efdb-ce83-4865-9cc7-2d10d21270f4.png)
- 에릭 마이어의 reset.css를 이용하여 브라우저 별로 다른 스타일들을 통일시켜 주도록 변경함

![A8](https://user-images.githubusercontent.com/79515820/149652765-e36ac383-d3ea-456f-8e6a-98751890faf1.png)
- style.css의 외부 스타일 시트를 이용하여 중복 되는 css 코드들을 제거할 수 있도록 함

![A9](https://user-images.githubusercontent.com/79515820/149652766-68688be0-c760-4921-81b5-e417c54829dc.png)
- 기존에 카멜 표기법으로 사용했던 class 이름들을 스네이크 표기법을 사용하도록 변경함

![A10](https://user-images.githubusercontent.com/79515820/149652767-299e5fed-1889-48d4-8b1e-48fd335875f6.png)
- 줄 간격 조정을 br태그를 이용하기 보다는 margin, padding을 사용하여 조정을 하도록 변경함

![A11](https://user-images.githubusercontent.com/79515820/149652768-cbebfbc4-1edc-4497-98f5-5e60271424c7.png)
- 웹 접근성을 위하여 img태그에 alt속성을 추가하도록 변경함

![A12](https://user-images.githubusercontent.com/79515820/149652761-28576bb5-af5b-4ec9-b2ef-8de3a1b3dd3c.png)
- 기존에 프로젝트 코드와 동일한 경로에 놓이게 했던 이미지 파일들을 resource/img 폴더에 위치하도록 변경함

## Project B: To Do 웹 애플리케이션

### 개요

- 해야 할 일, 하고 있는 일, 한 일을 웹 브라우저에서 확인할 수 있는 웹 어플리케이션을 만드는 것이 목표이다. 

### 기획서
(1) 메인 화면
![B1](https://user-images.githubusercontent.com/79515820/149660217-f9b0ba3e-05ec-426e-9c74-32609d748fb0.png)
- TODO, DOING, DONE 3가지 상태로 구분한다.
- 간격은 위/아래 모두 동일한 margin으로 유지하도록 한다.
- 새로운 카드(할 일)가 추가되면 아래에 동일한 카드가 추가되며, 카드의 개수는 계속 증가할 수 있도록 한다.
- 각 카드에는 할 일제목/등록날짜/담당자/우선순위를 표현한다.
- 먼저 등록한 카드(할 일)가 위에 노출되고, 나중에 등록한 카드는 아래에 추가되도록 한다.
- 각 카드에서 오른쪽 화살표를 누르면 오른쪽 상태로 이동시킨다. 예를 들어 TODO에서 각 카드의 화살표를 누르면 Doing으로 이동된다. done상태로가면 오른쪽 화살표가 사라지도록 한다.

(2) 할 일 등록 화면
![B2](https://user-images.githubusercontent.com/79515820/149660220-9ae12f04-9731-4119-b0e3-2debf3e7f50d.png)
- 할 일 제목, 담당자, 우선순위를 입력하게 한다.
- 할 일 제목은 24자까지 입력가능하도록 한다.
- 제출버튼을 누르면 서버로 데이터가 전송되며, 이후 메인페이지에 등록한 내용이 함께 노출된다.
- 내용지우기버튼을 누르면 현재 입력중인 모든 내용이 초기화되도록 한다.
- 이전버튼을 누르면 메인페이지로 돌아가게 한다.
- 3가지 항목은 모두 필수로 입력되도록 해야한다.

### 웹프론트엔드 기술요구사항

- 총 2개의 화면이 존재한다.
	- 할 일 목록 화면 (리스트)
	- 할 일 등록 화면 (쓰기)
- CSS는 기획서와 동일한 수준으로 만들어야 한다.
- HTML 엘리먼트간의 배치와 간격은 일정하고 반듯해야 한다.
- 글자의 크기는 일정한 수준을 유지해야 한다.
- CSS는 외부 라이브러리(부트스트랩)을 사용하지 않는다.
- jQuery를 사용하지 않고, querySelector, addEventListener, innerHTML을 사용해서 DOM, EVENT 처리를 한다.
- Ajax는 XMLHTTPRequest를 사용한다.


### 웹백엔드 기술요구사항

- 프로젝트는 maven프로젝트로 생성한다.
- 제공된 테이블 생성 SQL을 이용해서 테이블을 생성한다.
- TodoDto 클래스와 TodoDao클래스를 주어진 스펙에 맞게 작성한다.
- 메인화면을 보여주기 위한 MainServlet과 main.jsp를 작성한다.
- MainServlet은 TodoDao를 이용해 결과를 조회해서 main.jsp 에 전달한다.
- 새로운 todo등록 버튼을 클릭하면 해당 요청을 서블릿이 받아서 jsp로 포워딩하여 할 일 등록 화면을 보여주도록 한다.
- 할 일 등록폼에서 값을 입력하고 제출 버튼을 누르면 post 방식으로 요청하게 한다.
- 해당 요청을 서블릿이 받아서 처리하게하고, 요청에 대한 모든 일이 끝나면 메인화면으로 리다이렉트 한다.
- 메인화면에서 todo 상태변경 버튼(->)을 클릭하여 요청을 보낼 때, Todo 의 Id와 상태값을 전달하여 다음 상태로 (현재 상태가 Todo라면 doing으로 doing 이라면 done) 상태를 나타내는 컬럼값을 변경하고 응답결과로 "success"를 보낸다.

### 구현을 위한 학습 내용
#### Back-End
- Maven
- SQL
- JDBC
- MySQL
- Servlet & JSP
- JSTL & EL

#### Front-End
- 자바스크립트 문법 (ES 2015이상)
- DOM
- Ajax 통신
- JavaScript 디버깅

### 프로젝트 구성
![B3](https://user-images.githubusercontent.com/79515820/149660825-c5115389-e98a-4700-b758-fdf89a30d6ca.png)
- MainServlet.java, main.jsp: 웹 페이지의 메인 화면 (main.png에 대응). MainServlet.java에서는 DB에서 데이터를 불러와 main.jsp에게 포워딩시키고, main.jsp에서는 그 정보를 토대로 화면에 할 일 목록을 보여준다.
- TodoFormServlet.java, todoForm.jsp: 할 일 등록 화면 (form.png에 대응)
- main.js: 메인 화면에서 사용하는 자바스크립트 파일. 사용자가 메인 화면에서 화살표를 눌렀을 때 Ajax로 TodoTypeServlet.java에게 해당 항목의 type값(TODO/DOING/DONE)을 바꾸도록 한 후 화면에 변경사항을 반영하는 역할을 한다.
- reset.css: 리셋역할을 하는 css코드
- style_common.css, style_form.css, style_main.css: jsp에서 사용하는 외부 스타일시트
- TodoDto.java: 할 일 목록 하나하나에 관련된 DTO이다. 다음과 같은 멤버 변수들로 구성된다.
	- Long id: PK값에 해당한다.
	- String name: 누가 할 일인지 이름을 표시한다.
	- String regDate: 등록 날짜에 해당한다.
	- Integer sequence: 우선순위에 해당한다.
	- String title: 할 일 제목에 해당한다.
	- String type: TODO, DOING, DONE 중 어떤 것인지를 나타낸다.
- TodoDao.java: TodoDto를 이용하여 MySQL의 DB에 접근하는 DAO이다. 다음과 같은 멤버 메서드들로 구성된다.
	- int addToDo(TodoDto dto): INSERT문으로 DB에 할 일 목록을 추가한다.
	- List\<TodoDto\> getTodos(): SELECT문으로 DB에 있는 전체 할 일 목록을 등록 날짜 순으로 가져온다.
	- int updateTodo(TodoDto todo): TodoDto객체를 인자로 받아 인자의 id에 해당하는 레코드의 type을 인자의 것으로 바꾼다.
- TodoAddServlet.java:  할 일 등록 화면에서 제출 버튼을 클릭했을 때 그에 맞는 TodoDto객체를 만들어 TodoDao의 addToDo 메서드를 호출하는 역할을 한다.
- TodoTypeServlet.java: 메인 화면에서 화살표 버튼을 클릭했을 때 그에 맞는 TodoDto객체를 만들어 TodoDao의 updateTodo 메서드를 호출하는 역할을 한다.
	
### Back-End 리뷰
#### 리뷰 결과
![B4](https://user-images.githubusercontent.com/79515820/149667942-83000472-0304-4422-92b6-30ba60c536c4.png)

#### 주요 코드 리뷰 반영사항
![B5](https://user-images.githubusercontent.com/79515820/149667943-d3b88b86-f52f-4a43-b312-838f2864e613.png)
- 기존에는 모든 클래스들을 projectB라는 패키지에 넣었으나 이들을 분리하여 같은 성격의 클래스끼리 패키지로 묶도록 변경함

![B6](https://user-images.githubusercontent.com/79515820/149667944-b1c751c2-3193-4a2c-84f6-b49005854331.png)
- DB 접속 정보를 final로 선언하여 변경하지 못하도록 함

![B7](https://user-images.githubusercontent.com/79515820/149667945-d08ff5ba-db74-48a4-88c7-d1a678ce42fa.png)
- 기존에 JDBC 드라이버를 로드할 때 TodoDao의 각 메서드 시작부분에 하도록 하였으나   TodoDao의 static에서 한 번만 로드하도록 변경함

![B8](https://user-images.githubusercontent.com/79515820/149667948-0031a8a7-5536-4315-a044-087a0f9404ab.png)
- jsp파일들을 WEB-INF 디렉토리에 넣어 직접 접근하지 못하도록 변경함

### Front-End 리뷰
#### 리뷰 결과
![B9](https://user-images.githubusercontent.com/79515820/149667950-5303ad37-012f-40c1-9101-e3371d376e16.png)

#### 주요 코드 리뷰 반영사항
![B10](https://user-images.githubusercontent.com/79515820/149667940-9ea08a44-f7bb-4ebb-9c70-a6b38d30fe33.png)
- 악의적인 사용자가 개발자 도구 등을 이용해서 잘못된 값을 제출하는 경우를 대비하여 백엔드에서 한 번 더 값을 검증하도록 변경함

## Project C: 예약관리 시스템 - 메인 화면 개발

### 개요

- 실제 네이버에서 운영하는 예약 시스템과 유사한 서비스를 만드는 것이 최종적인 목표로, Project C에서는 전체 예약서비스 중에 '메인 화면'을 구성한다.

### 기획서
(1) 메인 화면

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

### 웹프론트엔드 기술요구사항

- DOMContentloaded 이후에 모든 자바스크립트 로직이 동작하게 한다.
- 상단영역의 애니메이션은 CSS3의 transition과 transform 속성을 활용해서 구현한다.
- TABUI로 구성되는 카테고리 아이템이 노출되는 영역의 HTML은 카테고리별로 각각 만들지 않고 하나로 만들어 재사용한다.
- 카테고리 탭을 선택할 때마다, Ajax 요청을 해서 데이터를 가져온다.
- 탭 메뉴 (전시/뮤지컬/콘서트 등)는 Event delegation으로 구현한다.
- Template 코드를 javascript 함수 안에 보관하지 않고, 별도 분리시켜서 사용해야 한다. (HTML에 script태그 안에 보관하는 등)
- 함수 하나에 여러 개의 기능을 넣지 않고, 함수를 여러 개로 분리해야 한다.


### 웹백엔드 기술요구사항

- 제공된 SQL을 이용해서 테이블을 생성하고, 샘플데이터를 입력한다.
- maven을 이용해서 웹 어플리케이션 프로젝트를 작성한다.
- controller, service, dao로 레이어드 아키텍쳐를 구성한다.
- spring JDBC를 이용하여 주어진 테이블로부터 입력, 수정, 삭제, 조회하는 DAO와 DTO를 작성한다.
- 서비스 인터페이스를 작성하고 해당 서비스 인터페이스에 비지니스 메소드를 작성한다.
- 서비스 인터페이스를 구현하는 클래스를 작성한다.
- 해당 구현 클래스의 메소드에 적절한 트랜잭션에 관련된 어노테이션을 사용한다.
- 클라이언트에게 Web API를 제공하기 위해 RestController를 작성한다.

### 구현을 위한 학습 내용
#### Back-End
- Maven
- SQL
- Spring Core
- Spring MVC
- Spring JDBC
- Web API(get)

#### Front-End
- 자바스크립트 자료구조
- DOM APIs
- JSON과 Ajax 응답 처리
- 웹 애니메이션
- event delegation
- vanilla HTML templating

### ER 다이어그램
![C2](https://user-images.githubusercontent.com/79515820/150718045-886fcb1f-cf4a-42ef-8553-f22021db2895.png)

### 프로젝트 구성
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

### Back-End 리뷰
#### 리뷰 결과
![C4](https://user-images.githubusercontent.com/79515820/151942816-a8bda1ab-e7d3-4341-9874-0cd86a305726.png)

#### 주요 코드 리뷰 반영사항
![C5](https://user-images.githubusercontent.com/79515820/151942826-907f3a65-aa84-404b-8c1f-a4911b74030b.png)
- @RequestParam 어노테이션에서 생략해도 무방한 정보들을 생략함

![C6](https://user-images.githubusercontent.com/79515820/151942827-7bcc8630-da89-46b4-b836-504e293b08b3.png)
- 기존에는 ReservationService라는 클래스 하나만 두어 Service 역할을 하도록 했으나, 각각의 책임에 맞게 CategoryService, ProductService, PromotionService로 나누어 SRP가 지켜지도록 수정함

![C7](https://user-images.githubusercontent.com/79515820/151942830-3e09c61a-05e4-46d5-8eec-2d60a2f91663.png)
- 클래스에서 상수, 멤버 변수, 생성자, 메서드 순으로 나타나도록 순서를 변경함

### Front-End 리뷰
#### 리뷰 결과
![C8](https://user-images.githubusercontent.com/79515820/151942832-d7a66997-0243-4b65-9427-c844ddeb430d.png)

#### 주요 코드 리뷰 반영사항

![C9](https://user-images.githubusercontent.com/79515820/151942833-7d6ec2ab-3627-49b4-8564-714ba982cc55.png)
- 기존에는 script태그를 body태그 최하단에 두었으나, defer 속성을 이용하여 head태그 안에 두면서도 html parsing이 끝난 후에 script가 실행되도록 변경함

![C10](https://user-images.githubusercontent.com/79515820/151942834-7b3866f6-55d9-4d41-9a7a-7dc3dda282c4.png)
- 기존에는 TOP버튼을 클릭했을 때 바로 화면의 최상단으로 이동하게 하였으나, 자바스크립트를 이용해 화면이 좀 더 부드럽게 이동하도록 수정함

## Project D: 예약관리 시스템 - 상세 페이지 개발

### 개요

- 실제 네이버에서 운영하는 예약 시스템과 유사한 서비스를 만드는 것이 최종적인 목표로, Project D에서는 전체 예약서비스 중에 '상세 페이지'를 구성한다.

### 기획서
(1) 상세 페이지 전체 구성

![D1](https://user-images.githubusercontent.com/79515820/153696438-6016044e-1875-49b8-8b7d-6720161dca06.png)


(2) 상세 페이지 상단영역

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

(3) 상세 페이지 하단영역(예매자 한줄평)
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

(4) 전체 한줄평 노출 페이지
![D4](https://user-images.githubusercontent.com/79515820/153696444-0c38302d-6ff5-4c7a-a0af-234b0fcaacfe.png)
- 상세페이지 하단의 ‘더보기'를 누르면 전체 한줄평 리스트 화면이 우측처럼 노출된다.

(5) 상세 페이지 하단영역(상세설명)
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

### 웹프론트엔드 기술요구사항

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

### 웹백엔드 기술요구사항

- controller, service, dao로 레이어드 아키텍쳐를 구성한다.
- spring JDBC를 이용하여 주어진 테이블로부터 입력, 수정, 삭제, 조회하는 DAO와 DTO를 작성한다.
- 서비스 인터페이스를 작성하고 해당 인터페이스에 비지니스 메소드를 추가한다.
- 서비스 인터페이스를 구현하는 클래스를 작성하고 클래스 내 메소드에 적절한 트랜잭션에 관련된 어노테이션을 사용한다.
- 클라이언트에게 Web API를 제공하기 위해 RestController를 작성한다.

### 구현을 위한 학습 내용
#### Back-End
- Maven
- SQL
- Spring Core
- Spring MVC
- Spring JDBC
- Web API(get)
- Logging

#### Front-End
- 배열의 higher order fuctions
- 객체리터럴, this, bind
- handlebar 기반 templating
- 클린코드

### 프로젝트 구성
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
	- review.jsp: 전체 한줄평 노출 페이지이다(review.png)에 대응). 상세페이지 하단의 '더보기'를 눌렀을 때 이 화면으로 넘어와 해당 상품의 전체 한줄평 목록들을 보여준다.
- webapp/js: js파일들을 담고 있는 폴더
	- mainpage.js (변경): mainpage.jsp에서 사용하는 자바스크립트 파일이다. 프로젝트 C에서는 단순히 함수들을 나열했다면, 프로젝트 D에서는 객체리터럴 패턴을 이용하도록 변경하여 함수들의 기능에 따라 ProductObj, PromotionObj, EventObj의 객체안에 위치하도록 수정하였다.
	- common.js: 여러 페이지에 공통적으로 사용되는 자바스크립트 파일이다. TOP 버튼 클릭시 스크롤 처리와 같은 작업들이 여기에 위치한다.
	- detail.js: detail.jsp에서 사용하는 자바스크립트 파일이다. 먼저 상품과 관련된 정보들을 Ajax로 가져와서 보여준다. 사용자가 네비버튼을 눌렀을 때 메인 이미지를 슬라이딩 시키는 역할을 하며, 펼쳐보기를 누르면 생략된 전시상품 설명이 펼쳐지도록 한다. 또한 상세페이지 하단의 상세정보/오시는길 탭을 눌렀을 때 탭이 전환되며 관련 콘텐츠가 노출되도록 하는 역할 등을 수행한다.
	- review.js: review.jsp에서 사용하는 자바스크립트 파일이다. 상품의 전체 한줄평 정보를 가져와서 사용자에게 보여주는 역할을 수행한다.


### Back-End 리뷰
#### 리뷰 결과
![D7](https://user-images.githubusercontent.com/79515820/153702337-61a056f6-1b28-4b50-8b0a-63b73b6c7238.png)

#### 주요 코드 리뷰 반영사항
![D8](https://user-images.githubusercontent.com/79515820/153702339-93336109-ae6b-46cf-b5be-bf894c770f30.png)
- 기존에는 api Controller를 ReservationApiController라는 하나의 클래스 파일에서 모두 처리하였으나, 역할에 맞게 CategoryApiController, ProductApiController, PromotionApiController로 나누어 향후 확장 및 유지보수가 용이하도록 변경함

![D9](https://user-images.githubusercontent.com/79515820/153702340-10dd4822-64fb-4e12-8dae-ea5a7457a3d5.png)
- ApiController에서 리턴할 내용들을 DTO로 만들어 정의하도록 수정함

![D10](https://user-images.githubusercontent.com/79515820/153702341-c5ae0a5a-3376-4729-a0c2-c7b00c302fac.png)
- 코드의 가독성 향상 등의 목적을 위하여 기존에 IF문을 이용해 값이 없으면 0으로 설정한 부분을 IFNULL을 이용하도록 수정함

![D11](https://user-images.githubusercontent.com/79515820/153702343-55aade2c-8741-482e-a83b-5574f5d68c27.png)
- 기존에는 각 JOIN별 성능의 차이를 고려하지 않고 일괄적으로 LEFT JOIN을 사용하여 테이블을 JOIN하도록 하였으나, INNER JOIN을 사용할 수 있는 부분들은 INNER JOIN을 이용하도록 변경해서 이후 데이터가 많아졌을 때 성능 문제가 발생하지 않도록 개선함


### Front-End 리뷰
#### 리뷰 결과
![D12](https://user-images.githubusercontent.com/79515820/153702345-a136ab5f-07f9-483c-83dc-b4aa05c3a918.png)

#### 주요 코드 리뷰 반영사항

![D13](https://user-images.githubusercontent.com/79515820/153702346-d51df638-2d39-41e3-89b2-6e8ae348978e.png)
- 자바스크립트에서 관습적으로 사용하는 표기법, 특히 다른 언어에서의 private 접근지정자 개념을 언더바 표기법을 이용하여 관습적으로 명명한다는 것을 알게 되었으며, 이에 맞도록 객체/필드/메서드 명들을 수정함
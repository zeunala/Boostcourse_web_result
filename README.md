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
	 - Project A: 나를 소개하는 웹페이지 만들기
	 - Project B: TO-DO List 구현하기
	 - Project C-F: 네이버 예약관리 시스템 만들기
- 수료증
	![1](https://user-images.githubusercontent.com/79515820/149649841-23e3760d-43e3-433c-a73d-81805795fcf8.jpg)



## Project A: 나를 소개하는 웹페이지 만들기

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

## Project B: TO-DO List 구현하기

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
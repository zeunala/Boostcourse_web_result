# Project B: To Do 웹 애플리케이션

### 개요

- 해야 할 일, 하고 있는 일, 한 일을 웹 브라우저에서 확인할 수 있는 웹 어플리케이션을 만드는 것이 목표이다. 

## 기획서
### (1) 메인 화면
![B1](https://user-images.githubusercontent.com/79515820/149660217-f9b0ba3e-05ec-426e-9c74-32609d748fb0.png)
- TODO, DOING, DONE 3가지 상태로 구분한다.
- 간격은 위/아래 모두 동일한 margin으로 유지하도록 한다.
- 새로운 카드(할 일)가 추가되면 아래에 동일한 카드가 추가되며, 카드의 개수는 계속 증가할 수 있도록 한다.
- 각 카드에는 할 일제목/등록날짜/담당자/우선순위를 표현한다.
- 먼저 등록한 카드(할 일)가 위에 노출되고, 나중에 등록한 카드는 아래에 추가되도록 한다.
- 각 카드에서 오른쪽 화살표를 누르면 오른쪽 상태로 이동시킨다. 예를 들어 TODO에서 각 카드의 화살표를 누르면 Doing으로 이동된다. done상태로가면 오른쪽 화살표가 사라지도록 한다.

### (2) 할 일 등록 화면
![B2](https://user-images.githubusercontent.com/79515820/149660220-9ae12f04-9731-4119-b0e3-2debf3e7f50d.png)
- 할 일 제목, 담당자, 우선순위를 입력하게 한다.
- 할 일 제목은 24자까지 입력가능하도록 한다.
- 제출버튼을 누르면 서버로 데이터가 전송되며, 이후 메인페이지에 등록한 내용이 함께 노출된다.
- 내용지우기버튼을 누르면 현재 입력중인 모든 내용이 초기화되도록 한다.
- 이전버튼을 누르면 메인페이지로 돌아가게 한다.
- 3가지 항목은 모두 필수로 입력되도록 해야한다.

## 웹프론트엔드 기술요구사항

- 총 2개의 화면이 존재한다.
	- 할 일 목록 화면 (리스트)
	- 할 일 등록 화면 (쓰기)
- CSS는 기획서와 동일한 수준으로 만들어야 한다.
- HTML 엘리먼트간의 배치와 간격은 일정하고 반듯해야 한다.
- 글자의 크기는 일정한 수준을 유지해야 한다.
- CSS는 외부 라이브러리(부트스트랩)을 사용하지 않는다.
- jQuery를 사용하지 않고, querySelector, addEventListener, innerHTML을 사용해서 DOM, EVENT 처리를 한다.
- Ajax는 XMLHTTPRequest를 사용한다.


## 웹백엔드 기술요구사항

- 프로젝트는 maven프로젝트로 생성한다.
- 제공된 테이블 생성 SQL을 이용해서 테이블을 생성한다.
- TodoDto 클래스와 TodoDao클래스를 주어진 스펙에 맞게 작성한다.
- 메인화면을 보여주기 위한 MainServlet과 main.jsp를 작성한다.
- MainServlet은 TodoDao를 이용해 결과를 조회해서 main.jsp 에 전달한다.
- 새로운 todo등록 버튼을 클릭하면 해당 요청을 서블릿이 받아서 jsp로 포워딩하여 할 일 등록 화면을 보여주도록 한다.
- 할 일 등록폼에서 값을 입력하고 제출 버튼을 누르면 post 방식으로 요청하게 한다.
- 해당 요청을 서블릿이 받아서 처리하게하고, 요청에 대한 모든 일이 끝나면 메인화면으로 리다이렉트 한다.
- 메인화면에서 todo 상태변경 버튼(->)을 클릭하여 요청을 보낼 때, Todo 의 Id와 상태값을 전달하여 다음 상태로 (현재 상태가 Todo라면 doing으로 doing 이라면 done) 상태를 나타내는 컬럼값을 변경하고 응답결과로 "success"를 보낸다.

## 구현을 위한 학습 내용
### Back-End
- Maven
- SQL
- JDBC
- MySQL
- Servlet & JSP
- JSTL & EL

### Front-End
- 자바스크립트 문법 (ES 2015이상)
- DOM
- Ajax 통신
- JavaScript 디버깅

## 프로젝트 구성
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
	
## Back-End 리뷰
### 리뷰 결과
![B4](https://user-images.githubusercontent.com/79515820/149667942-83000472-0304-4422-92b6-30ba60c536c4.png)

### 주요 코드 리뷰 반영사항
![B5](https://user-images.githubusercontent.com/79515820/149667943-d3b88b86-f52f-4a43-b312-838f2864e613.png)
- 기존에는 모든 클래스들을 projectB라는 패키지에 넣었으나 이들을 분리하여 같은 성격의 클래스끼리 패키지로 묶도록 변경함

![B6](https://user-images.githubusercontent.com/79515820/149667944-b1c751c2-3193-4a2c-84f6-b49005854331.png)
- DB 접속 정보를 final로 선언하여 변경하지 못하도록 함

![B7](https://user-images.githubusercontent.com/79515820/149667945-d08ff5ba-db74-48a4-88c7-d1a678ce42fa.png)
- 기존에 JDBC 드라이버를 로드할 때 TodoDao의 각 메서드 시작부분에 하도록 하였으나   TodoDao의 static에서 한 번만 로드하도록 변경함

![B8](https://user-images.githubusercontent.com/79515820/149667948-0031a8a7-5536-4315-a044-087a0f9404ab.png)
- jsp파일들을 WEB-INF 디렉토리에 넣어 직접 접근하지 못하도록 변경함

## Front-End 리뷰
### 리뷰 결과
![B9](https://user-images.githubusercontent.com/79515820/149667950-5303ad37-012f-40c1-9101-e3371d376e16.png)

#### 주요 코드 리뷰 반영사항
![B10](https://user-images.githubusercontent.com/79515820/149667940-9ea08a44-f7bb-4ebb-9c70-a6b38d30fe33.png)
- 악의적인 사용자가 개발자 도구 등을 이용해서 잘못된 값을 제출하는 경우를 대비하여 백엔드에서 한 번 더 값을 검증하도록 변경함
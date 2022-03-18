# Project F: 예약관리 시스템 - 예약 한줄평

### 개요

- 실제 네이버에서 운영하는 예약 시스템과 유사한 서비스를 만드는 것이 최종적인 목표로, Project F에서는 전체 예약서비스 중에 한줄평 등록 기능을 구현한다.

## 기획서
### (1) 한줄평 등록 화면
![F1](https://user-images.githubusercontent.com/79515820/154792335-2d53769e-1ae6-40ec-8de7-c201ec83b87a.png)

1. 별점
	- 별점을 1~5점까지 선택할 수 있다.
	- 별점을 선택하면 좌측별점도 하이라이트 된다. 예를 들어 3번째 별점을 선택하면 1,2,3번째 별에 하이라이트가 된다.
	- 우측에 선택한 별 개수 만큼 숫자로 점수가 노출된다.
2. 리뷰입력
	- 글자가 최소 5자에서 최대 400자까지 등록할 수 있다.
	- 400자를 넘어가면 더 이상 글자를 쓸 수 없다.
	- 선택을 하면(포커스를 주면) 입력창(textarea)이 노출된다.
	- 입력을 하지 않고 입력창에서 포커스를 나가면 다시 원래의 콘텐츠가 노출된다.
3. 사진
	- 사진은 한 장만 등록할 수 있다.
	- jpg, png만 등록 가능하다.
4. 리뷰등록
	- 리뷰등록 이후에는 ‘나의 예매내역 확인' 페이지로 이동된다.

## 웹프론트엔드 기술요구사항

- 리뷰 쓰기의 별점 기능은 별도의 별점 컴포넌트로 개발(prototype 방식의 클래스로 작성)해야 한다.
- form입력 값은 유효성 검증을 정규표현식을 사용해서 체크해야 한다.
- file upload시 이미지 파일의 확장자 체크는 자바스크립트로 체크 해야 한다.
- 썸네일 이미지 미리보기도 자바스크립트를 사용해서 구현해야 한다.
- 작은 단위의 함수로 구현하려고 하고, 스스로 필요한 리팩토링요소를 개선하려고 노력해야 한다.

## 웹백엔드 기술요구사항

- 기존 샘플 이미지가 저장되어 있는 img, img_map 폴더를 브라우저에서 바로 접근할 수 없는 경로로 이동시킨다. (예 : c:/tmp, /tmp)
- reservation_user_comment_image 테이블의 id를 파라미터로 받아, 이미지를 보여주는(다운로드하는) 컨트롤러를 작성해야 한다.
- webapp 아래의 img, img_map폴더를 외부에서 접근할 수 없는 경로로 이동을 하면, 기존에 보이던 이미지는 보이지 않게 되므로, 위에서 작성한 컨트롤러를 이용하여 이미지를 보여주도록 기존 코드를 수정해야 한다.
- 웹 브라우저에서 요청이 올 때마다, 요청 URL, 시간, 클라이언트 ip주소에 대한 로그를 인터셉터를 이용하여 콘솔에 남기도록 한다.

## 구현을 위한 학습 내용
### Back-End
- Maven
- SQL
- Spring Core
- Spring MVC
- Spring JDBC
- Web API( post, get)
- File Upload & Download
- Interceptor

### Front-End
- file upload(multipart)
- prototype & ES Classes
- UI 컴포넌트 개발

## ER 다이어그램
![ER](https://user-images.githubusercontent.com/79515820/150718045-886fcb1f-cf4a-42ef-8553-f22021db2895.png)

## 프로젝트 구성
![F2](https://user-images.githubusercontent.com/79515820/158966575-ba565bb8-9fb6-4ca3-9974-d187388dd84c.png)
- org.boostcourse.reservation.config: 프로젝트 설정과 관련된 클래스 파일들을 담고 있는 패키지
	- WebMvcContextConfiguration.java (변경)
		- DispatcherServlet의 설정을 담당하는 클래스이다.
		- DispatcherServlet에게 멀티파트 요청이 올경우 파일 업로드가 될 수 있도록 MultipartResolver 객체를 @Bean으로 등록하였다.
		- 또한 웹 브라우저 요청이 올 때마다 로그를 인터셉터를 이용해서 남기도록 addinterceptors() 메서드를 추가하였다.
- org.boostcourse.reservation.controller: 프로젝트의 Controller 클래스 파일들을 담고 있는 패키지
	- ReservationController.java (변경)
		- URL요청을 View와 연결해주는 컨트롤러로 /review_write 페이지를 추가하였으므로 관련된 코드를 추가하였다.
		- 세션을 확인하여 현재 로그인되어 있을 경우에만 /review_write 페이지로 진입가능하도록 하며, 로그인상태인데 예약이력이 없는 상품의 리뷰를 작성하려 할 경우 비정상접근으로 간주해 mainpage로 돌려보낸다.
	- ReservationApiController.java (변경)
		- 지정된 API요청들이 들어올 때 그에 맞는 응답을 하는 역할을 하며, 한줄평(POST) 요청에 대한 처리를 추가하였다.
	- ImageDownloadController.java
		- 파일의 id나 파일명을 파라미터로 받아 이미지를 보여주는 컨트롤러이다.
- org.boostcourse.reservation.dto: 프로젝트에서 사용하는 DTO들을 담고 있는 패키지
	- CommentResult.java
		- 한줄평 등록 과정 후 서버가 클라이언트에게 한줄평 등록 결과를 반환할 때 사용하는 DTO이다. 다음과 같은 멤버변수들로 구성된다.
		- String comment
		- Integer commentId
		- CommentImage commentImage
		- String createDate
		- String modifyDate
		- Integer productId
		- Double score
- org.boostcourse.reservation.dao: 프로젝트에서 사용하는 DAO들을 담고 있는 패키지
	- CommentDao.java (변경)
		- Comment와 연관된 DAO로, 한줄평 등록 기능을 추가하기 위해 다음과 같이 메서드들을 추가하였다.
		- int addComment(Integer reservationInfoId, String comment, Integer productId, Double score): DB의 reservation_user_comment 테이블에 관련 정보들을 추가한다.
		- int addFileInfo(String fileName): DB의 file_info 테이블에 관련 정보들을 추가한다.
		- int addCommentImage(Integer reservationInfoId, Integer commentId, Integer fileId): DB의 reservation_user_comment_image 테이블에 관련 정보들을 추가한다.
	- CommentImageDao.java (변경)
		- CommentImage와 관련된 DAO와 SQL문을 저장하는 클래스로, 기존 List\<CommentImage\>를 반환하는 selectCommentImages 메서드 뿐만 아니라 CommentImage 하나만을 반환하는 selectCommentImage 메서드를 추가하였다.
	- ProductDaoSqls.java (변경)
	- PromotionDaoSqls.java (변경)
		- 파일 url이 변경된 것에 맞춰 SQL문을 수정하였다.
	- CommentResultDao.java
	- CommentResultDaoSqls.java
		- CommentResult와 관련된 DAO와 SQL문을 저장하는 클래스이다.
		- CommentResult selectCommentResult(Integer commentId): commentId에 해당하는 한줄평의 CommentResult 정보를 가져온다.
	- FileInfoDao.java
	- FileInfoDaoSqls.java
		- 파일정보와 관련된 DAO와 SQL문을 저장하는 클래스이다.
		- String selectSaveFileNameById(Integer fileInfoId): fileInfoId에 해당하는 파일의 경로를 문자열로 가져온다.
- org.boostcourse.reservation.interceptor: 프로젝트에서 사용하는 인터셉터들을 담고 있는 패키지
	- LogInterceptor.java
		- API 호출 요청이 발생할 때마다 호출 메서드와 ip주소, 요청 URL 정보를 로그로 남긴다.
- org.boostcourse.reservation.service: 프로젝트의 Service의 인터페이스들을 담고 있는 패키지
	- ReservationService.java (변경)
		- Reservation과 관련된 Service의 인터페이스로, addComment 메서드를 추가하였다.
	- FileService.java
		- File과 관련된 Service의 인터페이스이다.
- org.boostcourse.reservation.service.impl: 프로젝트의 Service의 실제 구현체들을 담고 있는 패키지
	- ReservationServiceImpl.java (변경)
		- Reservation과 관련된 Service의 실제 구현체로, @Autowired로 자동주입된 CommentDao, CommentImageDao, CommentResultDao 객체를 멤버 변수로 추가하였다.
		- CommentResult addComment(Integer reservationId, String comment, Integer productId, Double score, String imageFileName): 한줄평 내용과 첨부 이미지를 추가하고, 추가된 한줄평에 대한 CommentResult객체를 반환하는 역할을 한다. 여러 DAO들의 메서드를 호출하고 중간에 끊기면 안되기에 @Transactional 선언을 하였다.
	- FileServiceImpl.java
		- String getSaveFileName(Integer fileInfoId): FileInfoDao 객체의 selectSaveFileNameById를 호출한다.
- src/main/resources: 프로젝트에서 사용하는 리소스 파일들을 담고 있는 패키지
	- logback.xml
		- logback의 설정을 담고 있는 파일이다. 출력 로그의 포맷, 로그 레벨 등의 설정을 한다.
- webapp/WEB-INF/views: jsp파일들을 담고 있는 폴더
	- detail.jsp (변경)
	- review.jsp (변경)
		- 이미지를 컨트롤러를 이용해서 가져오도록 변경하도록 수정한 것에 맞춰 관련 내용들을 수정하였다.
	- myreservation.jsp (변경)
		- '예매자 리뷰 남기기' 버튼을 눌렀을 때 한줄평 등록 화면으로 이동하도록 추가하였다. 이 때 백엔드에서 리뷰를 작성할 수 있는 상태인지 한 번 더 체크하도록 하기 위해 관련 정보도 넘기도록 한다.
	- reviewWrite.jsp: 웹 페이지의 한줄평 등록 화면이다(reviewwrite.png에 대응). 나의 예매내역 확인 페이지에서 '예매자 리뷰 남기기'를 눌렀을 때 이 화면으로 넘어와 한줄평을 작성할 수 있도록 한다.
- webapp/js: js파일들을 담고 있는 폴더
	- detail.js (변경)
	- reserve.js (변경)
	- review.js (변경)
		- 이미지를 컨트롤러를 이용해서 가져오도록 변경하도록 수정한 것에 맞춰 관련 코드들을 수정하였다.
	- reviewWrite.js: reviewWrite.jsp에서 사용하는 자바스크립트 파일이다. 별을 클릭했을 때 별점을 표시하는 기능, 이미지 등록/삭제 기능, '리뷰 등록' 버튼을 눌렀을 때 조건을 체크한 후 서버로 전송하는 역할 등을 수행한다.


## Back-End 리뷰
### 리뷰 결과
![F3](https://user-images.githubusercontent.com/79515820/158966579-83e0709f-d816-4be8-b23a-2b5dcfc8c200.png)

#### 주요 코드 리뷰 반영사항
![F4](https://user-images.githubusercontent.com/79515820/158966583-d86ade3c-6f88-44e1-b2e2-becf84871628.png)
- 윈도우 뿐 아니라 모든 OS에서 동작하도록 이미지를 저장하는 파일 경로를 수정함

![F5](https://user-images.githubusercontent.com/79515820/158967002-38cd475a-93f2-46e4-8bf4-6b05e2645c3a.png)
- 파일 경로와 같이 중복되는 부분들을 상수로 추출하여 중복을 제거하도록 리팩토링함

## Front-End 리뷰
### 리뷰 결과
![F6](https://user-images.githubusercontent.com/79515820/158967004-08b86271-01e1-41d0-a247-89fba09779ad.png)

#### 주요 코드 리뷰 반영사항
![F7](https://user-images.githubusercontent.com/79515820/158967006-b50de24a-c035-4747-be45-2a24b9e5bb3b.png)
- ReservationApiController.java의 addComment 메서드에서 score, comment 길이에 대한 유효성을 검사해서 비정상접근을 막도록 함

![F8](https://user-images.githubusercontent.com/79515820/158966997-af8983c5-0ca2-4647-8fc7-3cddec9f5523.png)
- 마찬가지로 개발자도구를 수정하는 등의 비정상적인 방법으로 jpg/png파일이 아닌 다른 파일을 업로드하는 것을 방지하기 위해 addComment 메서드에서 다시 한 번 확장자를 체크하도록 함
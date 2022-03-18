# Project A: 자기소개 홈페이지 만들기

### 개요

- 나를 소개하는 웹페이지를 만드는 것이 목표이다.
- HTML페이지 3개와 서블릿 1개를 Tomcat 서버 위에서 동작하도록 만든다.

## 웹프론트엔드 기술요구사항

-  html layout tag를 사용한다.
-  classname은 일정한 컨벤션을 유지한다.
-  의미에 맞는 tag를 최대한 사용한다. (div 사용은 최대한 자제)
-  position속성과 float를 사용해서 element를 배치한다.
-  id와 class등의 다양한 selector문법을 잘 활용한다.

## 웹백엔드 기술요구사항

-  톰캣서버를 통해서 자기소개 페이지가 동작하도록 한다.
-  서블릿페이지하나를 생성해서, url을 입력했을 때 시간데이터가 화면에 노출되도록 한다.

## 구현을 위한 학습 내용
### Back-End
- Servlet, JSP

### Front-End
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

## Back-End 리뷰
### 리뷰 결과
![A2](https://user-images.githubusercontent.com/79515820/149651512-0594586e-ab26-47f5-b837-b98b6b4dbc6b.png)

### 주요 코드 리뷰 반영사항
![A3](https://user-images.githubusercontent.com/79515820/149651513-299e3ca9-ce5b-4b4b-960b-88cad93b4331.png)
- serialVersionUID값을 유니크한 값으로 생성하도록 변경함

![A4](https://user-images.githubusercontent.com/79515820/149651514-525d1558-456b-48b6-953c-7dbf5a35ebae.png)
- 들여쓰기 기준을 tab 단위로 하도록 통일함

![A5](https://user-images.githubusercontent.com/79515820/149651510-0a89f7fb-cd9e-4d00-9ab4-e4904f66b40d.png)
- 오버라이드 된 메소드들에 대해 @Override 어노테이션을 붙이도록 변경함

## Front-End 리뷰
### 리뷰 결과
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
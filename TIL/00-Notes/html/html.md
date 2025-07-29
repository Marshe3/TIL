## HTML
<br/>

### HTTP(Hyper Text Transfer Protocol)
 - 인터넷에서 하이퍼텍스트문서를 교환하기 위하여 사용되는 통신규약
<br/>
<br/>

### HTML(Hyper Text MarkUp Language)
- 웹 페이지에 정보를 담아 표시하기 위한 마크업 언어

<br/>
<br/>

### Hyper Text
- 현재 문서에서 다른 문서로 즉시 접근할 수 있는 텍스트
<br/>
<br/>
<br/>

### HTML의 구성요소

```html
<p>Hyper Text Markup Language</p>
```
\<p> : Element(요소) 시작태그  
Hyper Text Markup Language : Content(내용)  
\</p> : Element(요소) 끝태그

<br/>
<br/>

```html
<p align = "center">Hello, World!</p>
```
align : attribute(속성)  
"center" : value(값)

<br/>
<br/>


```html
<!DOCTYPE html> <!-- 문서 형태를 정의하는 코드-->
<html lang="en">
<head> <!-- HTML 문서의 머릿글 절정 부분 -->
    <meta charset="UTF-8"> <!-- HTML 문서의 정보 정의-->
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>나만의 페이지</title> <!-- HTML 문서의 제목 -->
</head>
<body>
    
    오늘은 즐거운 HTML 시간 입니다! <!-- HTML문서 내용(텍스트,이미지,내용 등) -->
    
</body>
</html>
```
<br/>
<br/>
<br/>

---

### 태그
<br/>
  
#### h(header) 태그
- 제목 태그
- 크기, 굵기를 숫자에 따라 지정해서 쓰는 태그
- \<h1>\</h1> ~ \<h6>\</h6>
```html
<h1>제목</h1>
```
<br/>
<br/>

#### p 태그
- 다락으로 표현되기 때문에 가로 한줄을 통으로 차지하는 태그
- 작성이후 개행 자업으로 보임
```html
<p>내용1</p>
<p>내용2</p>
```
- 출력  
내용1  
내용2  

<br/>
<br/>

#### span 태그
- 하나의 문장으로 표현 되기 때문에 넣은 text 만큼만 영역으로 사용
- 이후에 오는 내용들은 가로로 이어서 배치
```html
<span>내용1</span>
<span>내용2</span>
```
- 출력  
내용1내용2

<br/>
<br/>

#### br 태그
```html
<span>내용1</span>
<br>
<span>내용2</span>
```
- 출력  
내용1  
내용2

<br/>
<br/>

#### b 태그
- 시각적으로 굵기를 강조하는 태그
```html
<b>b 태그</b>
```
<br/>
<br/>

#### strong 태그
- 의미 자체를 강조하는 태그

```html
<strong>strong 태그</strong>
 ```
# 1.뷰 CLI를 이용한 프로젝트 생성
- 원하는 위치에 새로운 폴더 `vue-todo`를 생성하고 `vue-todo`폴더 내에서 cmd창을 열어 뷰 CLI로 프로젝트를 생성한다.
- 자세한 내용은 **[뷰 프로젝트 구성 방법](https://github.com/ahn-sujin/TIL/blob/main/vue/vue04.md)** 를 참고해 주세요

<br>


# 2. 프로젝트 초기 설정
* 프로젝트에 반응형 웹 디자인 태그와 이후에 사용할 아이콘 CSS를 설정해 준다. 

<br>

## 2-1. 반응형 웹 디자인 태그 설정

##### index.html
```html
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>vue-todo1</title>
</head>
```

<br>

## 2-2. 어썸 아이콘 CSS 설정

##### index.html
```html
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css">
    <title>vue-todo1</title>
</head>
```

- 폰트 어썸 아이콘 공식 사이트 [바로가기](https://fontawesome.com/)

<br>

## 2-3. 폰트와 파비콘 설정

##### index.html
```html
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css">
    <link rel="shortcut icon" href="src/assets/favicon.ico" type="image/x-icon">
    <link rel="icon" href="src/assets/favicon.ico" type="image/x-icon">
    <link href="https://fonts.googleapis.com/css?family=Ubuntu" rel="stylesheet">
    <title>vue-todo1</title>
</head>
```

- favicon generator [바로가기](https://www.favicon-generator.org/)
- google font [바로가기](https://fonts.google.com/?subset=korean) 

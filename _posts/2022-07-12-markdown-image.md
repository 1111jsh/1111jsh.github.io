---
layout : single
title : "마크다운 이미지"

categories :
  - markdown
tags:
  - markdown
toc: true
toc_sticky: true
published: true
---

## 이미지

이미지를 추가하려면 느낌표( !)를 추가하고 대괄호 안에 대체 텍스트를 추가하고 괄호 안에 이미지의 경로 또는 URL을 추가합니다. 선택적으로 경로 또는 URL 뒤에 따옴표로 묶인 제목을 추가할 수 있습니다.

```
![image](https://github.com/1111jsh/image_repo/blob/upload/img/image.png?raw=true
```

## 이미지 캡션

Markdown은 기본적으로 이미지 캡션을 지원하지 않지만 두 가지 가능한 해결 방법이 있습니다.

1. Markdown 애플리케이션이 HTML`figure` 을 지원하는 경우 HTML 태그  `figcaption`을 사용 하여 이미지에 캡션을 추가할 수 있습니다.

```html
<figure>
    <div><img src="https://github.com/1111jsh/image_repo/blob/upload/img/icon_3.png?raw=true" alt="icon_3"/>
    <figcaption>고양이에요</figcaption></div>
</figure>
```

<figure>
    <div><img src="https://github.com/1111jsh/image_repo/blob/upload/img/icon_3.png?raw=true" alt="icon_3"/>
    <figcaption>고양이에요</figcaption></div>
</figure>

​     2.Markdown 애플리케이션이 HTML을 지원하지 않을경우 이미지 바로 아래에 캡션을 배치하여 강조를(\**) 사용해 볼수 있습니다.

```html
![icon_3](https://github.com/1111jsh/image_repo/blob/upload/img/icon_3.png?raw=true)
*고양이에요*
```

![icon_3](https://github.com/1111jsh/image_repo/blob/upload/img/icon_3.png?raw=true)

*고양이에요*

## 이미지 크기

이미지에 대한 Markdown 구문에서는 이미지의 너비와 높이를 지정할 수 없습니다. 이미지 크기를 조정해야 하고 Markdown 애플리케이션이 HTML 을 지원하는 경우 및 속성 `img`과 함께 HTML 태그를 사용 하여 이미지 크기를 픽셀 단위로 설정할 수 있습니다.

```html
<img src=image_path/img.png width="200" height="200"/>     <!--사진1-->

![img](image_path/img.png){: width="100px", height="100px"}        <!--사진2-->
```

<img src="https://github.com/1111jsh/image_repo/blob/upload/img/icon_3.png?raw=true" alt="icon_3" width="200" height="200"/>

*사진1*

<img title="" src="https://github.com/1111jsh/image_repo/blob/upload/img/icon_3.png?raw=true" alt="icon_3" data-align="inline">{: width="100px", height=100px"}

*사진2*

## 이미지 정렬

이미지 정렬 또한 HTML을 이용하여 지정 할 수 있습니다.

```html
<div style="text-align: center;"><img src=image_path/img.png/></div>    <!--사진3-->

![img](image_path/img.png){: .align-right}        <!--사진4-->
```

<div style="text-align: center;">
    <img src="https://github.com/1111jsh/image_repo/blob/upload/img/icon_3.png?raw=true" alt="icon_3"/><p style="text-align: center;">
    사진3</p></div>
1
![icon_3](https://github.com/1111jsh/image_repo/blob/upload/img/icon_3.png?raw=true)


<p style="text-align: right;">사진4</p>

<br>

> Reference
> 
> [markdownguide.org](https://www.markdownguide.org/basic-syntax/#images-1)
> 
> [HTML figure Tag](https://www.w3schools.com/tags/tag_figure.asp)

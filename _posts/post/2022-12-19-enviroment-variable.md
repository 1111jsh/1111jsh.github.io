---
layout: single
title: "환경변수"
categories:
  - post
tags:
  - export
published: true
toc: true
toc_sticky: true
---
----

## 환경변수
- 환경에 따라 프로그램의 동작에 영향을 줄 수 있는 값들을 환경변수라고 한다
- Linux 기반의 운영체제에서는 시스템 자체에 전역변수를 설정할 수 있다
- 시스템에 설정한 전역변수를 환경변수라고 한다

## Linux & Mac OS 환경변수 설정
- 운영체제와 관계없이 환경변수는 지역 환경변수와 전역 환경변수로 분류
- Linux와 Mac OS에서는 환경변수를 임시적으로 적용하거나, 영구적으로 적용할 수 있다

### 환경변수 임시 적용하기

##### 지역 환경변수
- **지역 환경변수**는 환경변수를 생성한 특정 사용자만 사용할 수 있는 환경변수
- **전역 환경변수**는 모든 사용자가 사용할 수 있는 환경변수
- `hello=codestates` 같이 등호 표시를 사용해서 지역 환경변수 임시 적용 공백이 없어야 하며 저장하고자 하는 변수에 공백이 존재할 경우 따옴표 `("")` 를 사용해 감싸야 한다

##### 전역 환경변수
- 명령어 `export`를 이용해서 전역 환경변수 설정
- `export urclass="is good"`

##### 환경변수의 개별 값 확인하기
- 환경변수 앞에 `$`를 입력하면 `$`뒤의 문자열이 환경변수라는 의미를 터미널에 전달

### 환경변수 영구 적용하기

##### 지역 환경변수 영구 적용하기
1. `cd ~`를 입력 홈 디렉토리로 이동 `ls -al`을 통해 모든 파일과 디렉토리 조회
2. 조회 결과에 따라 아래 명령어를 입력
	- 목록에 `.zshrc`가 있으면 `nano .zshrc`를 입력
	- 목록에 `.bashrc`가 있으면 `nano .bashrc`를 입력
3. 파일의 맨 아래로 이동한 다음, 설정하고자 하는 환경변수를 작성하고 저장
4. `source .zshrc` or `source .bashrc`를 입력하여 변경 내용을 적용한다

##### 전역 환경변수 영구 적용하기
1. 변경하고자 하는 파일의 권한을 수정
	- 환경변수를 저장하고자 하는 파일은 루트 디렉토리의 `/etc/profile` 라는 파일의 권한을 변경
2. `nano /etc/profile`을 입력
3. 파일의 맨 아래로 이동한 다음, 설정하고자 하는 환경변수를 작성하고 저장
4. `source /etc/profile` 입력하여 변경 내용을 적용한다

##### export
- 터미널에 명령어 `export`를 입력하면 운영체제 내에 이미 설정되어져 있는 환경변수 및 `export` 키워드를 통해 설정한 환경 변수들의 목록을 확인할 수 있다


##### Windows에서 환경변수 설정하기
- Window에서는 환경변수를 영구적으로만 설정 가능  
- **환경변수 설정창 열기**
	1. 환경 변수를 검색 '시스템 환경 변수 편집'을 열기
	2. 환경 변수에 들어가면 이 곳에서 환경변수를 설정
	3. User에 대한 사용자 변수는 지역 환경변수이며, 시스템 변수는 전역 환경변수
---
layout : post
title:  "OOXML(Office Open XML)"
excerpt: "OOXML구조에 대해서 알아보자"

categories:
  - File Format
tags:
  - [File Format, OOXML, Office Open XML]
 
date: 2021-01-21
last_modified_at: 2021-01-21
---
분석하고자(공부하고자) 하는 악성코드가 Office의 Word문서이다. 그래서 Office의 구조에 대해서 먼저 간략하게 공부를 하고 분석을 시작하는게 좋을 것 같아서 이 포스트에 정리하고자 한다.

***

### OOXML(Office Open XML)
OOXML(Office Open XML) 파일 포맷은 ZIP 형태로 압축되어 있는 XML 기반의 파일 포맷이다. MS Office(docx, .xls, .ppt  등등)의 기본형식이다.
해당 포스터는 아무 내용이 없는 word파일(a.docx)을 기반으로 정리하였다.

### Package Structure
xlsx, pptx, docx파일은 UTF-8이나 UTF-16으로 인코딩된 여러 파트 또는 XML 파일들을 담고 있는 zip파일이다.
파일의 확장자 **zip**으로 변경한 다음, 압축해제하여 폴더 내부를 보면 다음과 같은 구조를 볼 수 있다.
![폴더](/img/20210121103958.png)

### Content Types
모든 패키지에는 [Content_Types].xml이 있다. 해당 파일은 root Diretory에 존재하고 있으며, 패키지의 Part의 content type의 목록을 가지고 있다. 모든 part와 type은 반드시 이 파일에 기록되어 있어야 한다. 
![Content_Types.xml](/img/20210121105205.png)

### Relationships
모든 패키지는 Relationships 파트를 가지고 있으며, 다른 Part 또는 다른 패키지의 리소스 간의 관계를 정의한다. 
_rels 폴더 내에 패키지의 시작부분을 구별하는 .rels 파일이 존재한다. 
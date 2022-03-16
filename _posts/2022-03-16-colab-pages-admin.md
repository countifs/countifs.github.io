---
layout: single
title:  "Colab으로 GitHub pages 작성 Source code"
categories : [Colab]
tag : [Colab, GitHub Pages]
toc: false
toc_sticky : true
toc_label: " "
toc_icon: "file" 
author_profile: true
search : true 
---

### **📌 Colab으로 GitHub pages 작성 Source Code**

<a href="https://colab.research.google.com/drive/1vJrptCaNj7j2sLc_ce3ZlhVXkz5QB58e?usp=sharing" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

##### 👉 코랩 숏컷 단축키 사용방법 : 크롬 확장팩 ["Magical"](https://www.getmagical.com/change-log) 설치 

---

#### 1. 코랩 구글드라이브에 마운트하기 (shortcut → z;1)

```python
#구글드라이브 마운트하기
from google.colab import drive
drive.mount('/content/drive')
```

#### 2. 구글드라이브 공유파일 이미지 태그 만들기 (shortcut → z;2)

```python
# 구글드라이브 공유파일 이미지 태그 만들기
url=input("공유파일 이미지 링크 입력 : ")
path='https://drive.google.com/uc?export=download&id='+url.split('/')[-2]
size="width=\"\" "+"height =\"\" "
tag="<img src='"+path+"' "+size+"/><br>"
print('\n',tag)
```

#### 3. 구글드라이브 로컬폴더 공유파일의 이미지 태그 만들기 (shortcut → z;3)

```python
# 구글드라이브 로컬폴더 공유파일의 이미지 태그 만들기
url=input("공유파일 이미지 링크 입력 : ")
url_split=url.split('=')[1]
url_replace=url_split.replace('&authuser',"")
path='https://drive.google.com/uc?export=download&id='+url_replace
size="width=\"\" "+"height =\"\" "
tag="<img src='"+path+"' "+size+"/><br>"
print('\n',tag)
```

#### 4. 구글드라이브 csv 공유파일 불러오기 (shortcut → z;4)

```python
# 구글드라이브 csv 공유파일 불러오기 (z;4)
import pandas as pd
url=input("▶ 공유파일 csv 링크 입력 : ")
path='https://drive.google.com/uc?id='+url.split('/')[-2]
print("▶ 공유파일 링크변환 경로명 : ", path)
df=pd.read_csv(path)
df.head()
```

#### 5. 구글드라이브 로컬폴더의 csv 공유파일 불러오기 (shortcut → z;5)

```python
# 구글드라이브 로컬폴더의 csv 공유파일 불러오기 (z;5)
import pandas as pd
url=input("▶ 공유파일 csv 링크 입력 : ")
url_split=url.split('=')[1]
url_replace=url_split.replace('&authuser',"")
path='https://drive.google.com/uc?export=download&id='+url_replace
print("▶ 공유파일 링크변환 경로명 : ", path)
df=pd.read_csv(path)
df.head()
```

#### 6. Colab ipynb 노트북 파일을 html 파일로 변환 (shortcut → z;6)

```python
# Colab ipynb 노트북 파일을 html 파일로 변환
!jupyter nbconvert --to html "/path/"
```

#### 7. Colab ipynb 노트북 파일을 markdown 파일로 변환 (shortcut → z;7)

```python
# Colab ipynb 노트북 파일을 markdown파일로 변환
!jupyter nbconvert --to markdown "/path/"
```

#### 8. GitHub Pages 작성 레이아웃 (shortcut → z;8)

```markdown
---
layout: single
title:  " "
categories : [ ]
tag : [ ]
toc: false
toc_sticky : true
toc_label: " "
toc_icon: "file"  
author_profile: true
search : true 
---
```

#### 9. GitHub Pages 작성 레이아웃 (shortcut → z;9)
<a href="link" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>

```html
<a href="link" target="_parent"><img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/></a>
```

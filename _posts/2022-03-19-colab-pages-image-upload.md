---
layout: single
title:  "코랩(Colab) & 주피터(Jupyter) 노트북에 이미지 업로드 하기"
categories : [Colab]
tag : [Colab, Images Upload, Images insert, Google Drive ]
toc: false
toc_sticky : true
toc_label: " "
toc_icon: "file"  
author_profile: true
search : true
---

# 📌 **코랩(Colab) & 주피터(Jupyter) 노트북에 구글 드라이브 공유 이미지 링크 업로드**

오늘은 구글 코랩(Colab) 또는 주피터(Jupyter) 노트북 파일에 

**구글 드라이브로 공유하여 링크를 생성한 이미지 파일을 업로드** 하는 방법에 대해 설명하고자 한다.

먼저 해당 방법을 찾으면서 참고했던 내용인데 워낙 정리를 잘해주신 분이라서 참고하면 좋을 것 같다.

- [SOMANET'S DEV ARCHIVE](https://www.somanet.xyz/2017/06/blog-post_21.html) 님의 개발 블로그 "구글 드라이브를 외부 이미지 링크 저장소로 사용하기" 편

코랩이나 주피터 노트북을 사용할 때 로컬에 있는 파일을 사용해서 작업을 하고, 

이를 그대로 외부사용자에게 공유를 해주는 경우가 있다.

이 때  외부사용자가 실수로라도 코드를 실행하버리는 경우 공유되었던 결과들이 손상되어 

다시 새로 파일을 열어야 하는 경우를 나같은 초보자들은 많이 경험해보았을 것 같다.

그래서 내가 공유한 노트북 파일을 누구든지 바로 실행해볼 수 있고, 

오류가 없도록 하기위해 가급적이면 이미지든 데이터셋이든 

구글 드라이브로 공유링크를 만들고 사용해보면 좋을 것 같다는 생각을 하였고, 

지금 포스팅을 하는 이미지 공유하는 방법이 그 과정 중에 첫번째라고 보면 될 것 같다.

우선 코랩이나 주피터 노트북에서 사용하는 IPYNB (IPython Notebooks)  파일에서 

꼭 구글이미지가 아니라도 기본적인 이미지를 업로드 하는 방법에는 

크게 두가지가 있을 것이다.

1️⃣ 첫번째, 마크다운 셀에 이미지를 업로드 하는 방법<br>

2️⃣ 두번째, 코드셀에 이미지를 업로드 하는 방법<br>

두가지 방법 모두 검색을 해보면 쉽게 찾을 수 있는데, 

내가 이번에 포스팅 할 내용은 

**구글 드라이브로 외부로 공유할 이미지의  링크주소를 만들면, 그것을 노트북 파일에 업로드하여 출력하는 방법이다.**

이 방법은 구글 드라이브를 서버 외부 저장소처럼 사용하는 방법으로 보아도 될 것 같다.

## **1. 마크다운셀에 구글드라이브 공유링크 이미지 출력하기**

### **1.1 구글드라이브 이미지 공유링크 생성하는 방법**

우선 구글 드라이브에 이미지 파일 하나를 미리 업로드 하였다.

<img src='https://drive.google.com/uc?export=download&id=1lyFpGsZGf5EssK9rVWGWyRk0V7C67RW1' width="" height ="" /><br>

해당 이미지를 우클릭 하면 메뉴창이 뜨는데 `링크 생성` 버튼을 클릭하면 공유파일 링크가 생성된다.

<img src='https://drive.google.com/uc?export=download&id=1m0oaS-Z53KaP-PWgwxDSOkoCxibZ0BV_' width="" height ="" /><br>

우선 나는 링크를 제한된 사용자가 아닌 모든 사용자에게 공개되도록 설정하였고, 
링크복사 버튼을 눌러서 링크주소를 복사하였다.

<img src='https://drive.google.com/uc?export=download&id=1m1lROU14KuTdjy5LClsjeJB4Is0kBqVU' width="" height ="" /><br>

생성된 링크주소는 아래와 같다.

```https://drive.google.com/file/d/1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn/view?usp=sharing```


생성된 링크를 크롬 url 입력창에 그대로 입력하거나 위 링크를 그대로 클릭하면 아래 이미지와 같이 화면에 나타나는데,
이미지 화면이 바로 출력되거나, 다운받을 수 있는 것이 아니라,
구글드라이브의 미리보기 화면창으로 결과물이 표시되는 것을 볼 수 있다. 때문에 이 링크 주소를 마크다운셀이나 코드셀에 그대로 사용하는 경우는 에러가 발생될 수 있고, 이 링크를 사용할 수 있도록 간단하게 변경해 주는 작업이 필요하다.

<img src='https://drive.google.com/uc?export=download&id=1m2gCYknkgd5LGdkd-pYoYGbjywoh4dEd' width="" height ="" /><br>

### **1.2 구글드라이브 이미지 공유링크 마크다운 태그 만들기**

구글드라이브 이미지를 마크다운 태그로 만드는 코드는 다음과 같다

```python
#구글드라이브 공유파일 이미지 태그 만들기 

url="link" #link 부분을 구글 드라이브에서 생성한 공유 링크로 변경해주면 된다.
path='https://drive.google.com/uc?export=download&id='+url.split('/')[-2]
size="width=\"\" "+"height =\"\" "
tag="<img src='"+path+"' "+size+"/><br>"
print(" ▶ Path : ", path)
print('\n',"▶ Tag : ", tag)
```

우선 원리는 간단한데 먼저 위에서 생성된 구글 링크주소를 url 값에 변수로 선언해준다 <br>
 그 다음 url값을 "/" 기준으로 split을 해서 리스트를 만들고 맨뒤에서 2번째 값인 파일 고유키만 가져오면 된다.


```python
url = "https://drive.google.com/file/d/1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn/view?usp=sharing"
url.split('/')
```




    ['https:',
     '',
     'drive.google.com',
     'file',
     'd',
     '1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn',
     'view?usp=sharing']




```python
path='https://drive.google.com/uc?export=download&id='+url.split('/')[-2]
print(" ▶ Path : ", path)
```

     ▶ Path :  https://drive.google.com/uc?export=download&id=1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn


그럼 url값을 구글드라이브 이미지에서 가져온 공유링크 주소로 변경한 뒤에 코드를 실행해 보도록 하겠다.


```python
url="https://drive.google.com/file/d/1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn/view?usp=sharing" 
path='https://drive.google.com/uc?export=download&id='+url.split('/')[-2]
size="width=\"\" "+"height =\"\" "
tag="<img src='"+path+"' "+size+"/><br>"
print(" ▶ Path : ", path)
print('\n',"▶ Tag : ", tag)
```

     ▶ Path :  https://drive.google.com/uc?export=download&id=1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn
    
     ▶ Tag :  <img src='https://drive.google.com/uc?export=download&id=1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn' width="" height ="" /><br>


출력된 Path는 구글 드라이브 링크를 바로 볼 수 있도록 변환한 값인데,
자세히 보면 "uc?export=download&id" 뒤에 url링크에서 파일 고유키가 추가된 형태로 보면된다. 

Tag값은 Path값을 이용해 이미지가 출력되도록 변환해준 값이고
이 값을 복사해서 마크다운 셀에 입력하면 구글 드라이브로 공유된 이미지 파일이 출력되는 것을 확인할 수 있다.


<img src='https://drive.google.com/uc?export=download&id=1m6b2UsIntKSSsjsrE6FzUjfQ9cQeB6t0' width="" height ="" /><br>

그럼 태그 부분을 복사해서 아래와 같이 마크다운셀에 입력만 해주면 그림을 출력해 줄 수 있다.

<img src='https://drive.google.com/uc?export=download&id=1m9dyhyFTwitz2Jj4IrUAC6Y2ILDwa_Zp' width="" height ="" /><br>


```python
그럼 아래와 같이 이미지가 잘 출력되는 것을 확인할 수 있다.
```

 <img src='https://drive.google.com/uc?export=download&id=1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn' width="" height ="" /><br>

### **1.3 이미지 크기 변경하기**

이미지 크기를 조정하고 싶다면 태그를 복사한 뒤 "width" 또는 "height" 값에 원하는 이미지 크기를 입력해주면 된다.

```markdown
<img src='https://drive.google.com/uc?export=download&id=1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn' width="200" height ="" /><br>
```

<img src='https://drive.google.com/uc?export=download&id=1mFp4YO7mgrYRjRq2-D7DQjZLNrBiE0AM' width="" height ="" /><br>

출력해보면 입력한 값에 따라서 이미지 크기가 변경되는 것을 확인할 수 있다.

<img src='https://drive.google.com/uc?export=download&id=1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn' width="200" height ="" /><br>

<br>

---

<br>

## **2. 코드셀에서 구글드라이브 공유링크 이미지 출력하기**

### **2.1 구글드라이브 이미지 공유링크 코드셀에서 출력하기**

다음은 마크다운셀이 아닌 코드셀에서도 구글 드라이브 공유링크 이미지를 출력하는 방법이다.

코드는 아래와 같이 입력하면 되고, image모듈과 request 모듈을 import 해주면 된다.

그리고 1.2에서와 마찬가지로 <br>
공유링크 이미지 주소를 url에 변수선언해주고 <br>
path 링크로만 변경해 주면 된다. <br>
마지막으로 urlopen 함수를 통해서 image를 출력만 해주면 끝난다.

```python
# 코드셀에서 url 이미지 출력하기 
from IPython.display import Image
from urlib import request

url="link" #link 부분을 구글 드라이브에서 생성한 공유 링크로 변경해주면 된다
path='https://drive.google.com/uc?export=download&id='+url.split('/')[-2] 

res = request.urlopen(path).read()
img = images(res) # width = , height = 
img
```

실제로 url 링크주소를 입력하여 코드를 실행해보면 다음과 같이 출력되는 것을 확인할 수 있다.


```python
from IPython.display import Image
from urllib import request

url="https://drive.google.com/file/d/1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn/view?usp=sharing" #link 부분을 구글 드라이브에서 생성한 공유 링크로 변경해주면 된다.
path='https://drive.google.com/uc?export=download&id='+url.split('/')[-2] 

res = request.urlopen(path).read()  #path값
img = Image(res, width='', height='') #이미지 크기 변경필요시 width 또는 height에 값을 입력
img
```




![png](2022-03-19-colab-pages-image-upload_files/2022-03-19-colab-pages-image-upload_49_0.png)



### **2.2 이미지 크기 변경하기**

이미지 크기 변경이 필요하면 아래와 같이 width 또는 height 값을 조정해주면 된다.


```python
res = request.urlopen(path).read()  #path값
img = Image(res, width='200', height='') #이미지 크기 변경필요시 width 또는 height에 값을 입력
img
```




![png](2022-03-19-colab-pages-image-upload_files/2022-03-19-colab-pages-image-upload_52_0.png)



## **번외. pc로컬폴더에서 구글드라이브 공유링크를 생성시**

만약 구글드라이브를 자주 사용하는 사람중에서 다음과 같이 클립보드로 링크를 복사하는게 편한 사람이 있을 수 있다.

<img src='https://drive.google.com/uc?export=download&id=1mlrtYx834-9sH1n8A9Frk-bj5E1gahYy' width="" height ="900" /><br>

✔️ 웹에서 링크생성 :  ```https://drive.google.com/file/d/1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn/view?usp=sharing ```

✔️ **로컬에서 링크생성 ``` https://drive.google.com/open?id=1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn&authuser=userid%40gmail.com&usp=drive_fs```**

이럴 경우는 위에서 생성되는 구글드라이브에서 생성한 링크주소와는 조금 다른 형태로 생성되는데 그럴 경우는 아래의 코드를 사용하면 된다.


```python
# 구글드라이브 로컬폴더 공유파일의 이미지 태그 만들기 (
url="https://drive.google.com/open?id=1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn&authuser=userid%40gmail.com&usp=drive_fs" #로컬에서 생성된 링크 입력
url_split=url.split('=')[1]
url_replace=url_split.replace('&authuser',"")
path='https://drive.google.com/uc?export=download&id='+url_replace
size="width=\"\" "+"height =\"\" "
tag="<img src='"+path+"' "+size+"/><br>"
print(" ▶ Path : ", path)
print('\n',"▶ Tag : ", tag)
```

     ▶ Path :  https://drive.google.com/uc?export=download&id=1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn
    
     ▶ Tag :  <img src='https://drive.google.com/uc?export=download&id=1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn' width="" height ="" /><br>


마찬가지로 Tag값을 복사해서 마크다운 셀에 붙이면 출력이 잘 되는 것을 확인할 수 있다.

 <img src='https://drive.google.com/uc?export=download&id=1lsgC54AC8z8TqjvJ9X-VE7qpf27Gpubn' width="" height ="" /><br>

---
layout: single
title:  "코랩(Colab)에서 구글드라이브(Google Drive) 연동"
categories :
- Colab
tag : [Colab, Google Drive]
toc: false
toc_sticky : true
toc_label: "--"
toc_icon: "file"  # corresponding Font Awesome icon name (without fa prefix)
author_profile: true
search : true
---


## 📌 **코랩(Colab)에서 구글드라이브(Google Drive) 연동하기**

#### 구글 코랩에서 구글 드라이브에 연동하는 방법은 크게 두가지가 있다.

#### 1️⃣ 버튼을 클릭해서 드라이브에 연결하는 방법 <br>

#### 2️⃣ 코드셀에 드라이브 마운트를 연결하는 코드를 입력하고 실행하는 방법

---

####  **1️⃣ 버튼을 클릭해서 드라이브에 연결하는 방법** <br>

##### **1.1 코랩 왼쪽 가장자리를 보면 파일 버튼이 보이는데, 파일 버튼을 클릭하면 현재 구글 코랩에서사용하고 있는 탐색창이 보인다.**

<img src='http://drive.google.com/uc?export=view&id=1V_kyLMWz0l4awWGznlj7gPjd_qZaGvt-' /><br>

**1.2 좌측 상단에 있는 구글드라이브 버튼을 클릭한다.**

<img src='http://drive.google.com/uc?export=view&id=1LEQ4BW4yWuUKOD0kqYdvpN0TkgIb7flN' /><br>

**1.3 구글드라이브에 연결하는 엑세스 창이 나오는데 `Google Drive`에 연결 버튼을 클릭한다.**

 <img src='https://drive.google.com/uc?export=download&id=1PxTqQa-MEmk1hHQvXUxcaU3g3U4iMt-z'/><br>

**1.4 구글드라이브에 연결할 계정을 선택한다.**

 <img src='https://drive.google.com/uc?export=download&id=1Q7XHqDA0QgsU3zdKD3MUbp5gUTkhMNpG'/><br>

**1.5 엑세스 확인창이 나오면 `허용`을 선택하면 된다.**

 <img src='https://drive.google.com/uc?export=download&id=1Q8pqOfPSXp9tqpUAEw3C0n_krR7bxMzN'/><br>

**1.6 드라이브에 마운트 되면 탐색창에 보이지 않았던 `dirve`폴더가 생성되었음을 확인할 수 있다.**

 <img src='https://drive.google.com/uc?export=download&id=1QhFjly9BjDKKS45G2GS7kTPKtH3qSUGZ'/><br>

**Othercomputer는 구글드라이브와 PC가 동기화된 공유폴더가 있으면 나타나고,**<br>
**shareddrives 다른 멤버들과 공유된 드라이브시 나타난다.**
<br>
**개인적으로 팀프로젝트를 진행할 때 함께 공유하는 노트북이라면 공유드라이브 위치를**
<br> **파일경로로 설정해주면 다같이 노트북을 편리하게 사용할 수 있다.** 

---

####  **2️⃣ 코드셀에 드라이브 마운트를 연결하는 코드를 입력하고 실행하는 방법**


**코드셀에 코드를 입력하여 드라이브에 연결하는 방법도 간단하며, 그냥
아래 코드를 코드셀에 입력하고 실행하면 된다.**

```python
from google.colab import drive
drive.mount('/content/drive') 
```

**drive.mount('content/<u>drive</u>')를 아래처럼 <u>gdrive</u>로 바꿔도 연결된다.**

```python
from google.colab import drive
drive.mount('/content/gdrive')
```

1️⃣**에서 나온 엑세스 허용과정은 동일하게 진행해주면 된다.**

<img src='https://drive.google.com/uc?export=download&id=1QAQAIGddm6OZAhairYiL0R5J7Urqq5Co'/><br>

**마운트가 완료되면 코드 실행결과창과 탐색창에서 드라이브가 정상적으로 연결되었음을 확인할 수 있다.**

**첫 포스팅을 작성해 보았는데 가급적 구글 코랩에서 모든 노트를 작성하고 있다.😊😊😊<br>**
**이미지는 typora를 사용해서 클립보드를 붙여넣으면 자동으로 구글드라이브에 저장되도록 하였고,**<br>
**구글드라이브에 있는 이미지 파일을 공유한 뒤 공유링크를 코랩 노트북에 붙여넣으면서  작성하였다.**<br>

**이와 관련해서도 포스팅을 통해 공유해보도록 하겠다.**🖐️🖐️

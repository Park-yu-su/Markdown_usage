Markdown_usage
===============


## **GitHub Flavered Markdown (GFM)**
위 문서는 Markdown의 추가적인 문법 중 하나인 GFM 중 기존의 Markdown 문법 외에 추가된 내용을 다루는 문서입니다.

### 1) **테이블(Table)**

---

- **테이블(Table)** 은 GFM에서 제공하는 표의 형태의 리프 블록이다.
- 각 칸은 파이프 ( `|` )로 구분되며, 각 행은 inline으로 구분된다.
- 행 단위로 값을 입력하며, 분리 행에는 **헤더 행의 칸만큼 행 전체를 뺴기( `-` )로 채우거나 콜론을 앞, 뒤, 양 옆에 붙인다.( `:-:` )**

```
<입력>

| one | two | three |
| --- | :-: | --: |
| seven | eight | nine |
| ten | eleven | twelve |

```
> <출력>
>
> | one | two | three |
> | --- | :-: | --: |
> | seven | eight | nine |
> | ten | eleven | twelve |

#### 1.2) **주의할 점**

---

**1. 테이블의 맨 처음, 맨 끝의 파이프는 항상 입력하지 않아도 되며, 빼기( `-` )역시 행에 맞추지 않아도 된다.**

```
<입력>

| one | two | three |
------ | :-: | :-------------
five | six | seven
```

> <출력>
>
> | one | two | three |
> ------ | :-: | :-------------
> five | six | seven

위와 같이 표현해도 정상적으로 출력되지만 코드의 수정을 대비해 가독성을 높이도록 작성하는 습관을 기르도록 하자!

**2. 이스케이프 문자( `\` )를 통해서 파이프를 삽입할 수 있다.**

```
<입력>

| he\|\|o |
| --------- |
| N\|CE |
```

> <출력>
>
> | he\|\|o |
> | --------- |
> | N\|CE |

**3. 테이블은 첫 빈 줄이 오거나 다른 코드 구조가 오면 끝이 난다.**

```
<입력>

| one | two |
| --- | --- |
| three | four |
> five

| one | two |
| --- | --- |
| three | four |
five

six
```

> <출력>
>
> | one | two |
> | --- | --- |
> | three | four |
>> five
> 
> | one | two |
> | --- | --- |
> | three | four |
> five
>
> six

**4. 맨 처음 행(헤더 행)은 분리 행(| --- |)과 개수가 일치해야 한다.**

```
<입력>

| one | two |
| ----------|      <- 헤더 행은 2칸인데, 분리 행은 1칸이다.
| three | four |
```

> <출력>
>
> | one | two |
> | ----------|
> | three |
> 
> 위와 같이 테이블이 생성되지 않는다.

**5.** 헤더 행과 분리 행 이후, 행이 적으면 **공백** 으로 채워지지만 행이 초과되면 **초과된 칸은 무시된다.**

```
<입력>

| one | two |
| --- | --- |
| three |
| four | five | six |
```

> <출력>
> 
> | one | two |
> | --- | --- |
> | three |
> | four | five | six |

**6. 만약 분리 행 이후에 행이 없으면 헤더 행만 출력된다.**
```
<입력>

| one | two |
| --- | --- |
```

> <출력>
> 
> | one | two |
> | --- | --- |
 

### 2) **작업 목록 항목(Task list items)**

---

- **작업 목록 항목** 은 GFM에서 제공하는 구문이다.
- 목록 항목에서 사용할 수 있기 때문에 항상 **대시( `-` )를 붙인 뒤** 사용한다.
- 대쉬 뒤에 **대괄호( `[ ]` )**를 붙이고, 선택적으로 괄호 안에 **소문자 x, 대문자 X**를 넣는다.
- 괄호 안의 X의 여부에 따라 출력된 확인란에 체크 표시 유무가 달라진다.
```
<입력>

[ ] zero      <- 목록에서 사용하지 않은 경우
 - [ ] one  
 - [x] two  
```

> <출력>
>
> [ ] zero
>  - [ ] one  
>  - [x] two  
>  위와 같이 목록 형태로 사용하지 않으면 정상적으로 출력되지 않는다.

- 작업 목록 항목은 기존 목록 사용과 같이 탭을 이용해 중첩할 수 있다.
```
<입력>

- [ ] one
  - [ ] one-one
  - [x] one-two
- [X] two
```

> <출력>
> - [ ] one
>   - [ ] one-one
>   - [x] one-two
> - [X] two

### 3) **취소선(Strikethrough)**

---

- **취소선**은 GFM에 추가된 강조하기 기능 중 하나이다.
- 물결표 2개( `~~` )로 취소하고 싶은 문장을 묶으면 된다.

```
<입력>

잘못된 코드를 지우고 다시 입력했습니다.  
~~print("Hello world!\n")~~  
printf("Hello world!\n");
```

> <출력>
> 
> 잘못된 코드를 지우고 다시 입력했습니다.  
> ~~print("Hello world!\n")~~  
> printf("Hello world!\n");

#### 3.1) **주의할 점**

---

- 다른 강조하기 코드와 같이 단락이 새로 바뀌면 취소선은 중단된다.

```
<입력>

This ~~is a

new paragraph~~.
```

> <출력>
> 
> This ~~is a
> 
> new paragraph~~.

### 4) **자동 링크(Autolinks)**

---

- **자동 링크**는 GFM에서 제공하는 구문으로, **더 많은 조건에서 링크가 인식**되는 기능을 제공한다.

www.commonmark.org  
Visit www.commonmark.org/help for more information.  
Visit www.commonmark.org.  

Visit www.commonmark.org/a.b.  
www.google.com/search?q=Markup+(business)

www.google.com/search?q=Markup+(business)))

(www.google.com/search?q=Markup+(business))

(www.google.com/search?q=Markup+(business)  
www.google.com/search?q=(business))+ok  
www.google.com/search?q=commonmark&hl=en

www.google.com/search?q=commonmark&hl;  
www.commonmark.org/he<lp  

http://commonmark.org

(Visit https://encrypted.google.com/search?q=Markup+(business))

a.b-c_d@a.b

a.b-c_d@a.b.

a.b-c_d@a.b-

a.b-c_d@a.b_

hello@mail+xyz.example isn't valid, but hello+xyz@mail.example is.  





### 5) **허용되지 않는 HTML 구문**

---



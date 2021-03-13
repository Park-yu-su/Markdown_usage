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
- 하지만 일반적인 링크 사용에 비해 **제약점이 존재하기 때문에 신중하게 사용**해야 한다.

```
<입력>

www.commonmark.org
```

> <출력>
> 
> www.commonmark.org
 
- 자동 링크 앞, 뒤에는 문장이 올 수 있습니다.

```
<입력>

Visit www.commonmark.org/help for more informaion!
```

> <출력>
>
> Visit www.commonmark.org/help for more informaion!

#### 4.1) **자동 링크 경로 유효성 확인 (주의할 점)**

---

아래 서술되는 내용은 자동 링크를 사용하는 경우, **링크 유효성 판단에 영향을 주는 요소**들이다. 

**1. 자동 링크 바로 뒤에 문장부호( `?`, `!`, `.`, `,`, `:`, `*`, `_`, `-`, `/` 등)를 붙이면, 링크에 영향을 줄 수 있다.**

```
<입력>

Visit www.commonmark.org       <- 원본 
Visit www.commonmark.org.  
Visit www.commonmark.org?a.b.  
```

> <출력>
> 
> Visit www.commonmark.org  
> Visit www.commonmark.org.  
> Visit www.commonmark.org?a.b.  
> - 위와 같이 자동 링크가 달라지는 모습을 볼 수 있다.
 
**2. 자동 링크가 닫는 괄호( `)` )로 끝나는 경우 전체 괄호 개수를 계산한다. 닫는 괄호 개수가 여는 괄호보다 많은 경우 자동 링크와 일치하지 않는 괄호는 무시된다.**

```
<입력>

www.google.com/search?q=Markup+(business)      <- 괄호 수 정상
www.google.com/search?q=Markup+(business)))    <- 닫는 괄호가 2개 초과
(www.google.com/search?q=Markup+(business))    <- 닫는 괄호가 1개 초과
(www.google.com/search?q=Markup+(business)     <- 닫는 괄호가 1개 부족
```

> <입력>
>
> www.google.com/search?q=Markup+(business)  
> www.google.com/search?q=Markup+(business)))  
> (www.google.com/search?q=Markup+(business))  
> (www.google.com/search?q=Markup+(business)  
> - 위와 같이 닫는 괄호가 남으면 그냥 둔다. (닫는 괄호가 부족해도 그냥 링크가 된다.)

**단 이 규칙은 자동 링크가 닫는 괄호( `)` )로 끝나지 않으면 적용되지 않는다. (그냥 링크된다)** 

```
<입력>

www.google.com/search?q=(business))+ok     <- 닫는 괄호가 1개 초과
```

> <출력>
> 
> www.google.com/search?q=(business))+ok
 
**3. 자동 링크가 세미콜론( `;` )으로 끝나면 자동으로 확인 작업을 거친다.**

- 세미콜론으로 끝난 링크 중 **`&` 뒤에 하나 이상의 영어나 숫자가 오는 경우**, 이 부분은 자동 링크에서 **제외**된다.

```
<입력>

www.google.com/search?q=commonmark&hl=en      <- 세미콜론(;) 없으니 정상 링크
www.google.com/search?q=commonmark&hl;        <- 세미콜론으로 끝남 + & 뒤에 hl이 붙음
```

> <출력>
> 
> www.google.com/search?q=commonmark&hl=en  
> www.google.com/search?q=commonmark&hl;  

**4. 자동 링크 중에 여는 꺽쇠( `<` )가 있는 경우 즉시 자동 링크가 종료된다.
```
<입력>

www.commonmark.org/he<lp    <- 여는 꺽쇠 삽입(<)
www.commonmark.org/he>lp    <- 닫는 꺽쇠 삽입(>)
```

> <출력>
> 
> www.commonmark.org/he<lp  
> www.commonmark.org/he>lp  

#### 4.2) **확장된 자동 링크 경로 유효성 확인**

---

- 확장된 자동 링크는 `http://``, 또는 ``https://``로 된 링크를 말한다.
- 이 링크 역시 4.1절에서 서술된 링크 경로 유효성 확인 작업을 거친다.

```
<입력>

http://commonmark.org                                        <- 기본 사용
Visit http://commonmark.org to get information!              <- 문장 중간에 사용
http://commonmark.org.123                                    <- 규칙1 (문장부호 영향)
(https://encrypted.google.com/search?q=Markup+(business)))   <- 규칙2 (닫는 괄호 개수)
https://commonmark.org&help/;                                <- 규칙3 (세미콜론과 &)
http://commonmark.o<rg                                       <- 규칙4 (< 시 바로 링크 종료)
```

> <출력>
>
> http://commonmark.org  
> Visit http://commonmark.org to get information!  
> http://commonmark.org.123   
> (https://encrypted.google.com/search?q=Markup+(business)))  
> https://commonmark.org&help;  
> http://commonmark.o<rg    


#### 4.3) **자동 링크 경로 유효성 확인 (주의할 점)**

---

### 5) **허용되지 않는 HTML 구문**

---



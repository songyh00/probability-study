# 파이썬 프로그래밍 중간고사 완전 대비 — 4~7장 개념·확인문제·코딩 서술형

> **시험:** 2026년 10월 22일(목) 오후 6시 · 성결관 B101호  
> **범위:** 4~7장 · 객관식/단답형/서술형 필기 · **터틀그래픽 제외**  
> **출제 공지:** 교재 확인문제·연습문제 기반 60~70%, 그 외 30~40%.  
> **구성:** ① 전 범위 개념 ② 수업 PDF에 실제 실린 확인문제 ③ 부족한 영역의 예상문제 ④ 종이에 직접 쓰는 코딩 연습 ⑤ 마지막에 정답·예시 답안.

## 수업자료와 작성 기준

| 교재 장 | 기반 수업자료 | 분량 |
|---|---|---:|
| 4장 데이터와 변수 | `2주차_데이터와_변수.pdf` | 9쪽 |
| 5장 연산자 | `3주차_연산자.pdf` | 30쪽 |
| 5장 조건 표현식·모듈 | `4주차_연산자(2).pdf` | 5쪽 |
| 6장 조건문 | `4주차_조건문.pdf` | 14쪽 |
| 7장 반복문 | `5주차_반복문(최종).pdf` | 23쪽 |

**총 81쪽**의 강의자료를 순서대로 정리했다. 각 절에는 개념 → 실행 가능한 예제 → 실행 결과 또는 해석 → 주의사항을 담았다. **[강의자료 실습]**은 원본의 목적과 로직을 유지하되 PDF에서 줄바꿈·들여쓰기 등이 손상된 코드를 실행 가능하도록 정리한 것이다. **[보충]**은 수업자료의 정확한 이해를 위해 추가한 내용이다. 원본의 설명 또는 코드가 실제 Python 동작과 다른 부분은 **[원본 주의]**로 구분했다.



## 이 파일을 사용하는 방법

1. **1회독:** Part I(4~7장 개념)을 읽으며 `input → 처리 → print`의 흐름을 이해한다.
2. **2회독:** Part II의 **[수업 PDF 확인문제]**를 답을 가리고 푼다. 출처가 없는 문제는 **[추가 예상문제]**로 표시했다.
3. **필기 연습:** Part III 문제만 보고 Python 코드를 종이에 직접 적는다. 코드를 보며 필사하는 것은 서술형 연습으로 세지 않는다.
4. **셀프 채점:** 맨 뒤 Part IV에서 정답과 대표 코드를 확인하고, 틀린 문제의 해당 장으로 돌아간다.

> **출처 구분:** `[수업 PDF 확인문제]`는 업로드된 슬라이드에 문항 내용이 있는 문제를 기준으로 옮기거나 표현을 다듬은 것이다. `[수업자료 실습 기반]`은 수업에 나온 예제를 문제 형식으로 변환했다. `[추가 예상문제]`는 출제 범위를 연습하기 위해 새로 만든 문제다. PDF만으로 확인할 수 없는 **별도 교재의 장말 연습문제 전체를 수록했다고 주장하지 않는다.**

---

# Part I. 개념과 수업 실습

# 4장. 데이터와 변수

## 4-1. 데이터와 정보, 메모리 (p.1)

- **데이터(Data)**: 사물·현상을 측정·관찰하여 얻은 값. 예: 온도 25℃, 시험 점수 90점.
- **정보(Information)**: 데이터를 모아 의미 있게 정리하거나 가공한 것. 예: 80, 90, 100점의 평균 90점.
- **메모리(Memory)**: 프로그램 실행 중 사용하는 데이터를 저장하는 공간.
- **변수(Variable)**: 데이터 값을 사용하기 위해 붙인 이름. 강의에서는 '데이터를 저장하는 공간에 이름을 부여한 것'으로 설명.

```python
score1 = 80
score2 = 90
score3 = 100
average = (score1 + score2 + score3) / 3
print(average)  # 90.0
```

## 4-2. 변수 정의와 할당 (p.1~2)

Python은 값을 할당하면 변수를 사용할 수 있으며 별도의 자료형 선언이 필요 없다.

```python
name = "Alice"  # str
age = 30        # int
height = 5.5    # float
is_adult = True # bool
new_age = age + 10
print(name)       # Alice
print(new_age)    # 40
print(age)        # 30
```

`=`는 할당 연산자이며 같음을 비교하는 기호가 아니다(같음 비교에는 `==`). 다른 변수에 계산 결과를 할당해도 원래 변수 `age`는 바뀌지 않는다.

### 변수 이름 규칙

| 올바른 변수 | 잘못된 변수 | 원인 |
|---|---|---|
| `score1` | `1score` | 숫자로 시작 불가 |
| `_name` | `user-name` | `-` 사용 불가 |
| `user_name` | `user name` | 공백 사용 불가 |
| `Name`, `name` | `for`, `if` | 예약어는 이름으로 사용 불가 |

대소문자를 구분하므로 `Name`과 `name`은 서로 다른 변수다.

```python
Name = "Kim"
name = "Lee"
print(Name)  # Kim
print(name)  # Lee

import keyword
print(keyword.kwlist)  # 예약어 목록
```

### 동적 타이핑(Dynamic Typing)

변수가 실행 중 서로 다른 자료형의 값을 다시 참조할 수 있다.

```python
x = 4
print(type(x))  # <class 'int'>
x = "four"
print(type(x))  # <class 'str'>
```

### 주석(Comment)

`#` 이후 줄 끝까지는 설명을 위한 주석으로 실행되지 않는다. 강의자료의 주석 토글 단축키는 `Ctrl + /`(편집기·운영체제에 따라 차이).

```python
# 이 줄은 실행되지 않는다.
price = 1000  # 상품 가격
```

## 4-3. 기본 자료형과 `type()` (p.3~5)

| 자료형 | 의미 | 예시 |
|---|---|---|
| `int` | 정수 | `123`, `-5` |
| `float` | 실수 | `3.14`, `10.0` |
| `str` | 문자열 | `'123'`, `'Hello'` |
| `bool` | 논리값 | `True`, `False` |

```python
print(type(123))    # <class 'int'>
print(type("123"))  # <class 'str'>
print(type(3.14))   # <class 'float'>
print(type(True))   # <class 'bool'>
print(type(4 > 2))  # <class 'bool'>
```

정수 `10`과 문자열 `"10"`은 다르다. `10.0`은 소수부가 0이어도 `float`다. 일반 `.py` 스크립트에서는 `type(x)`만 적어 두어도 자동 출력되지 않으므로 `print(type(x))`를 사용한다.

### [강의자료 실습] 8과 5의 합

```python
n1 = 8
n2 = 5
total = n1 + n2
print(total)  # 13
print(n1, "과", n2, "의 합은", total, "입니다.")
```

두 번째 출력은 기본 구분 공백 때문에 `8 과 5 의 합은 13 입니다.`다.

### [강의자료 Quiz] 학생 정보 출력

```python
name = "홍길동"
height = 175
age = 21
hobby = "요리하기"
print(f"{name}의 키는 {height}이고 나이는 {age}세이며 취미는 {hobby} 입니다.")
```

## 4-4. 문자열(String) (p.4)

문자열은 작은따옴표 또는 큰따옴표로 묶는다. 내부 따옴표는 다른 종류로 감싸거나 `\`로 이스케이프한다.

```python
greeting = "Hello, World!"
name = 'Alice'
sentence = "She said, \"Hello!\""
print(sentence)  # She said, "Hello!"
```

문자열에서 `+`는 연결, `*`와 정수는 반복이다.

```python
print("Hong" + "gil" + "dong")  # Honggildong
print("Ha" * 3)                 # HaHaHa
print("=" * 5)                  # =====
```

- 문자열 연결에 공백이 자동으로 추가되지는 않는다.
- `"10" + "20"` → `"1020"`; `"10" + 20` → **TypeError**.
- **[원본 주의]** p.4의 `"Hong" + "gil" + "dong"` 설명에 공백이 포함된 출력이 기재되지만 실제 결과에는 공백이 없다.

## 4-5. 숫자형과 산술 연산 (p.4~5)

`int`는 정수형, `float`는 실수형이다. 부동소수점은 일부 십진 소수를 정확히 저장할 수 없어 정밀도에 한계가 있다.

| 연산자 | 의미 | 예제 | 결과 |
|---|---|---|---|
| `+` | 더하기 | `7 + 4` | `11` |
| `-` | 빼기 | `7 - 4` | `3` |
| `*` | 곱하기 | `7 * 4` | `28` |
| `/` | 나누기 | `7 / 4` | `1.75` |
| `//` | 몫(내림) | `7 // 4` | `1` |
| `%` | 나머지 | `7 % 4` | `3` |
| `**` | 거듭제곱 | `2 ** 3` | `8` |

```python
a = 7 + 4
b = 7 - 4
c = 7 * 4
d = 7 / 4
e = 7 // 4
f = 7 % 4
g = 2 ** 3
print(a, b, c, d, e, f, g)  # 11 3 28 1.75 1 3 8
```

**[보충]** `//`는 내림(floor)이므로 음수일 때 정수 쪽으로 단순 절삭하는 연산과 다르다: `-7 // 2 == -4`.

## 4-6. 불리언(Boolean)과 논리 연산 (p.5~6)

논리값은 `True`와 `False`이고 비교 연산의 결과가 될 수 있다.

```python
is_adult = True
is_teenager = False
print(4 > 2)           # True
print(True and False)  # False
print(True or False)   # True
print(not True)        # False
```

| A | B | `A and B` | `A or B` |
|---|---|---|---|
| True | True | True | True |
| True | False | False | True |
| False | True | False | True |
| False | False | False | False |

- `and`: 양쪽 모두 참일 때 참.
- `or`: 하나 이상 참이면 참.
- `not`: 논리값 반전.
- **[원본 주의]** 자료에서 `Trueand`, `Trueor`처럼 붙어 있는 표기는 실제 코드에서는 `True and`, `True or`처럼 분리해야 한다.

## 4-7. 자료형 변환 (p.6~7)

| 함수 | 기능 | 예 | 결과 |
|---|---|---|---|
| `str()` | 문자열 변환 | `str(10)` | `"10"` |
| `int()` | 정수 변환 | `int("123")` | `123` |
| `float()` | 실수 변환 | `float("123")` | `123.0` |
| `bool()` | 참·거짓 변환 | `bool(0)` | `False` |

```python
x = 10
x = str(x)
print(type(x))  # <class 'str'>

x = "123"
x = int(x)
print(type(x))  # <class 'int'>

x = "123"
x = float(x)
print(type(x))  # <class 'float'>
```

**bool()의 문자열 변환**

```python
print(bool(""))       # False: 빈 문자열
print(bool(" "))      # True: 공백도 문자
print(bool("Hello"))  # True
print(bool("0"))      # True
print(bool("False"))  # True
print(bool(0))        # False
```

문자열의 **뜻**을 읽어 불리언으로 바꾸는 것이 아니다. 비어 있지 않은 문자열은 참이다.

```python
print(int(3.9))        # 3: 반올림이 아닌 소수부 제거
print(float("3.14"))  # 3.14
# int("3.14")         # ValueError
# int("hello")        # ValueError
```

`b = int(a)`는 변환 결과를 **b에** 저장한다. a가 자동으로 바뀌지는 않는다. `a = int(a)`로 다시 할당하면 a가 정수 값을 참조한다.

## 4-8. `input()` (p.7~8)

**`input()`의 반환값은 항상 문자열(`str`)**이다. 숫자 입력 후 계산하려면 `int()` 또는 `float()`로 변환한다.

```python
name = input("이름을 입력하세요: ")
print(name, "님, 안녕하세요?")

num = input("숫자를 입력하세요: ")
print(type(num))  # <class 'str'>
```

[강의자료 실습] 정수와 실수 두 개의 합 구하기:

```python
a = int(input("정수1 입력: "))
b = int(input("정수2 입력: "))
print(a + b)

x = float(input("실수1 입력: "))
y = float(input("실수2 입력: "))
print("두 수의 합은 %.2f" % (x + y))
```

입력이 각각 `7`, `3`일 때 `a = input(...)` 후 `a * 2`는 `77`, `b = int(input(...))` 후 `b + 2`는 `5`가 된다.

## 4-9. `print()`와 줄바꿈 (p.8)

```python
print("hello")
print("hello", "Python")  # hello Python
print("Hello")
print("Python")           # 새 줄
print("Hello", end=" ")
print("Python")           # Hello Python
print("Hello\nPython")  # 문자열 내부 강제 줄바꿈
```

- `print(x, y)`의 인자 사이에는 기본적으로 공백이 들어간다(`sep=" "`).
- `end`의 기본값은 줄바꿈(`"\n"`)이다.
- `end=""`이면 이어 붙이고, `end=":"`이면 콜론만 붙이고 다음 출력과 연결한다.

## 4-10. `%` 형식 지정자 (p.8~9)

| 형식 | 의미 | 예제 출력 |
|---|---|---|
| `%d` | 정수 | `"%d" % 100` → `100` |
| `%f` | 실수, 기본 소수 아래 6자리 | `"%f" % 3.14` → `3.140000` |
| `%s` | 문자열 | `"%s" % "Python"` → `Python` |
| `%c` | 문자 한 개 | `"%c" % "A"` → `A` |

```python
print("%d %d %d" % (100, 200, 300))  # 100 200 300
# print("%d" % (100, 200))            # TypeError: 값 개수 맞지 않음
```

### 정수 출력 너비·정렬

```python
print("|%5d|" % 100)   # |  100|
print("|%05d|" % 100)  # |00100|
print("|%-5d|" % 100)  # |100  |
```

- `%5d`: 최소 너비 5칸, 오른쪽 정렬, 앞에 공백.
- `%05d`: 최소 너비 5칸, 앞자리를 0으로 채움.
- `%-5d`: 최소 너비 5칸, 왼쪽 정렬.

### 실수 및 문자열 출력

```python
print("|%f|" % 123.45)      # |123.450000|
print("|%7.1f|" % 123.45)   # |  123.5|
print("|%7.3f|" % 123.45)   # |123.450|
print("|%10s|" % "Python") # |    Python|
print("|%-10s|" % "Python")# |Python    |
```

`%7.1f`에서 7은 전체 **최소 너비**, 1은 **소수점 아래 자리수**다. `%.2f`는 소수 둘째 자리까지 표시하면서 반올림한다.

## 4-11. `format()` (p.9)

```python
print("{} {}".format(10, 20))
print("{0} {1} {2}".format(100, 200, 300)) # 100 200 300
print("{2} {1} {0}".format(100, 200, 300)) # 300 200 100
print("{0:d} {1:5d} {2:05d}".format(100, 200, 300))
# 100   200 00300
```

`{1:5d}`의 `1`은 **값 1이 아니라 인덱스 1**을 가리킨다. 문자열 내부에 직접 넣은 공백과 자리수 형식에서 만들어지는 공백은 따로 계산한다.

## 4-12. f-string (p.9)

```python
name = "홍길동"
age = 25
print(f"{name}님의 나이는 {age}")  # 홍길동님의 나이는 25

score = 85.678
print(f"점수: {score:.2f}")     # 점수: 85.68
```

```python
name, age = "홍길동", 25
print("%s님의 나이는 %d" % (name, age))
print("{}님의 나이는 {}".format(name, age))
print(f"{name}님의 나이는 {age}")
```

세 줄 모두 같은 결과를 출력한다.

### 4장 시험 핵심

1. `10`(정수), `"10"`(문자열), `10.0`(실수)을 구분한다.
2. `input()`은 문자열을 반환한다.
3. `int("3.14")`는 **ValueError**, `int(3.14)`는 `3`이다.
4. `bool("")`은 `False`, `bool(" ")`은 `True`다.
5. `end=":"`는 공백 없이 콜론을 붙인다.
6. `format()`의 인덱스·출력 너비를 분리해서 해석한다.
7. `%.2f` 및 `:.2f`는 소수 둘째 자리에서 반올림할 수 있다.
8. 눈에 보이지 않는 출력 **공백도 결과에 포함**된다.

---

# 5장. 연산자·조건 표현식·모듈

> 강의자료: `3주차_연산자.pdf` p.1~30 + `4주차_연산자(2).pdf` p.1~5. 아래의 '기본 p.'는 첫 자료, '추가 p.'는 두 번째 자료를 의미한다.

## 5-1. 연산자와 피연산자 (기본 p.1)

- **연산자(Operator)**: 계산·비교·논리 판단을 수행하는 기호 또는 키워드.
- **피연산자(Operand)**: 연산 대상이 되는 데이터.

`10 + 20`에서 `10`과 `20`은 피연산자이고 `+`는 연산자다.

| 분류 | 연산자 | 기능 |
|---|---|---|
| 산술 | `+ - * / // % **` | 사칙·몫·나머지·거듭제곱 |
| 할당 | `= += -= *= /= //= %= **=` | 변수에 결과 저장 |
| 비교 | `== != > < >= <=` | 참/거짓 판단 |
| 논리 | `and or not` | 조건 결합·반전 |

## 5-2. 덧셈 `+` (기본 p.1~4)

| 연산 | 결과 | 결과 자료형 |
|---|---|---|
| `10 + 20` | `30` | int |
| `3.14 + 0.5` | `3.64` | float |
| `10 + 3.14` | `13.14` | float |
| `10 + 2.0` | `12.0` | float |

```python
a = 10
b = 20
c = a + b
print(c)
print(type(c))  # <class 'int'>
```

**[원본 주의]** 기본 자료 p.2에는 `c`에 결과를 저장하고 `print(type(result))`라고 적은 코드가 있다. `result`가 정의되지 않았다면 `NameError`다. `print(type(c))`가 올바른 코드다.

문자열의 덧셈은 연결이다:

```python
print("Hello" + "Python")  # HelloPython
print("Hello" + " " + "Python")  # Hello Python
# print(10 + "abc")         # TypeError
print(str(10) + "abc")      # 10abc
```

### [강의자료 문제 해결 5-1] 1분기 매출액

```python
sales1 = int(input("1월 매출: "))
sales2 = int(input("2월 매출: "))
sales3 = int(input("3월 매출: "))
total = sales1 + sales2 + sales3
print("1분기 전체 매출:", total, "원")
```

## 5-3. 뺄셈 `-` (기본 p.5~6)

```python
print(10 - 5)      # 5
print(3.14 - 0.1)  # 3.04
# print("Hello" - "H")  # TypeError: 문자열 뺄셈 불가
```

### [강의자료 문제 해결 5-2] 1분기 수익

```python
sales = int(input("1분기 매출: "))
purchase = int(input("1분기 매입: "))
profit = sales - purchase
print("수익:", profit, "원")
```

## 5-4. 곱셈 `*` (기본 p.6~8)

```python
print(10 * 20)       # 200
print(3.14 * 3)      # 9.42
print("a" * 3)       # aaa
print("Hello " * 3)  # Hello Hello Hello (마지막 뒤 공백 있음)
print("abc" * 0)     # 빈 문자열 출력
print("abc" * -3)    # 빈 문자열 출력
# print("abc" * 2.5) # TypeError
```

### [강의자료 문제 해결 5-3] 방의 넓이

```python
width = int(input("가로 길이: "))
length = int(input("세로 길이: "))
area = width * length
print("넓이:", area, "㎡")
```

### [강의자료 실습] Good morning 반복 출력

```python
count = int(input("출력 횟수: "))
print("Good morning " * count)
```

## 5-5. 나눗셈 `/` (기본 p.8~11)

```python
print(10 / 2)     # 5.0
print(3.14 / 0.5) # 6.28
print(0 / 123)    # 0.0
# print(10 / 0)   # ZeroDivisionError
# print(10 / "a") # TypeError
# print("a" / "b")# TypeError
```

**중요:** `/`는 정수끼리 나누어 나머지가 없어도 `float`를 반환한다. `int(10 / 3)`은 `3`으로 소수부를 버린다.

### [강의자료 문제 해결 5-4] BMI

BMI = 몸무게(kg) / 키(m)²

```python
weight = float(input("몸무게(kg): "))
height = float(input("키(m): "))
bmi = weight / (height * height)
print("BMI:", bmi)
```

키가 `0`이면 0으로 나누는 문제가 발생한다. 실제 프로그램에서는 입력값 검증이 필요하지만 수업 실습은 기본 계산을 연습하기 위한 예제다.

## 5-6. 나머지 `%`, 몫 `//`, 거듭제곱 `**` (기본 p.12~15)

```python
print(10 % 2)   # 0
print(10 % 3)   # 1
print(10 // 3)  # 3
print(7 // 2)   # 3
print(2 ** 3)   # 8
print(3 ** 2)   # 9
print(5 ** 0)   # 1
```

- `%`: 나머지. `num % 2 == 0`으로 짝수 판별, `num % 3 == 0`으로 3의 배수 판별.
- `//`: 내림 몫. 양의 정수에서는 소수점 아래를 버리는 것과 같다. **[보충]** `-7 // 2 == -4`.
- `**`: 거듭제곱. `2 ** 3`은 `2 × 2 × 2`.

### [강의자료 문제 해결 5-5] 홀짝 게임

```python
count = int(input("구슬 개수: "))
result = count % 2
print(result)  # 짝수면 0, 홀수면 1
```

### [강의자료 문제 해결 5-6] 빵 나누기

```python
bread = 97
count = 3
maxCount = bread // count
rest = bread % count
print("나눠 줄 수 있는 학생 수:", maxCount)  # 32
print("남는 빵 개수:", rest)           # 1
```

### [강의자료 문제 해결 5-7] 감염자 수의 지수 증가

```python
man = 2
date = 30
total = man ** date
print("30일 이후 예상 감염자 수:", total)  # 1073741824
```

강의자료는 초깃값 1명에서 매일 두 배가 되는 **단순한 지수 증가 가정**을 사용한다. 실제 전염병 예측모델과는 다르다.

## 5-7. 할당 연산자 (기본 p.16~18)

| 연산 | 의미 |
|---|---|
| `a += b` | `a = a + b` |
| `a -= b` | `a = a - b` |
| `a *= b` | `a = a * b` |
| `a /= b` | `a = a / b` |
| `a //= b` | `a = a // b` |
| `a %= b` | `a = a % b` |
| `a **= b` | `a = a ** b` |

```python
a = 10
a += 5  # 15
a *= 2  # 30
print(a) # 30
```

### [강의자료 문제 해결 5-8] 복리 계산기

5,000,000원에 매년 5% 복리 적용, 5년 후 금액 계산:

```python
myMoney = 5000000
rate = 0.05
myMoney += myMoney * rate
myMoney += myMoney * rate
myMoney += myMoney * rate
myMoney += myMoney * rate
myMoney += myMoney * rate
print("5년 후 총 수령액:", int(myMoney), "원")
```

수학적 모델은 `P * (1 + r) ** n`이다. `int()`는 소수부를 버리므로 별도의 반올림과 구분해야 한다.

## 5-8. 숫자 비교 연산자 (기본 p.19~21)

| 연산자 | 의미 | 예 | 결과 |
|---|---|---|---|
| `==` | 같다 | `10 == 10` | True |
| `!=` | 다르다 | `10 != 10` | False |
| `>` | 초과 | `10 > 5` | True |
| `<` | 미만 | `10 < 5` | False |
| `>=` | 이상 | `10 >= 10` | True |
| `<=` | 이하 | `10 <= 5` | False |

`=`는 **할당**, `==`는 **같음 비교**. `>=`, `<=`는 기준값을 포함하지만 `>`, `<`는 포함하지 않는다.

### [강의자료 문제 해결 5-9] 범퍼카 탑승

```python
height = int(input("어린이 신장: "))
print(height >= 120)
```

## 5-9. 문자열 비교 (기본 p.21~23)

강의자료는 문자 비교를 ASCII 코드로 설명한다. **[보충]** 실제 Python 문자열 비교는 유니코드 코드 포인트를 기준으로 사전식(왼쪽부터) 비교하며, 영문 ASCII 범위에서는 교재 설명과 일치한다.

```python
print("a" == "a")         # True
print("a" == "b")         # False
print("A" < "B")          # True
print("A" < "a")          # True
print("apple" < "banana") # True
print("python" == "python ") # False: 마지막 공백 다름
print("10" < "2")         # True: 문자열 첫 글자 비교
```

문자열에서 대소문자와 공백도 비교 대상이다. 숫자 크기를 비교하려면 먼저 정수로 형변환해야 한다.

## 5-10. 논리 연산 `and`, `or`, `not` (기본 p.24~28)

| A | B | `A and B` | `A or B` |
|---|---|---|---|
| True | True | True | True |
| True | False | False | True |
| False | True | False | True |
| False | False | False | False |

`and`: **모두** 참이어야 참. `or`: **하나라도** 참이면 참. `not`: 참·거짓 반전.

```python
print(True and False) # False
print(True or False)  # True
print(not True)       # False

num = 15
print(num >= 10 and num <= 20)  # True
print(num < 10 or num > 20)     # False
```

### [강의자료 문제 해결 5-10] 어린이 범퍼카 탑승

키가 **120cm 이상, 170cm 미만**인 경우 허용:

```python
height = int(input("어린이의 신장: "))
print(height >= 120 and height < 170)
```

### 단락 평가(Short-Circuit Evaluation) (p.28~30)

- `and`: 왼쪽이 거짓이면 뒤 표현식은 평가하지 않는다.
- `or`: 왼쪽이 참이면 뒤 표현식은 평가하지 않는다.

```python
num = 10
print((num < 5) and abc)  # False, abc를 평가하지 않음
print((num > 5) or abc)   # True, abc를 평가하지 않음
# print((num > 5) and abc) # NameError
# print((num < 5) or abc)  # NameError
```

`abc`가 선언되지 않아도 실제로 평가하지 않는 경로에서는 오류가 나지 않는다. `and`, `or`는 반드시 `bool` 값을 반환하는 것은 아니다. **[보충]** `0 or 5`는 `5`, `3 and 7`은 `7`을 반환한다.

**[원본 주의]** p.25·27의 `and`↔`&`, `or`↔`|` 설명은 **불리언 두 값으로 계산할 때는 결과가 같을 수 있다**는 뜻으로만 이해하자. `&`, `|`는 비트 연산자이므로 `and`, `or`와 완전히 같지 않으며 단락 평가도 하지 않는다.

## 5-11. 조건 표현식(Conditional Expression) (추가 p.1)

```python
참일_때_값 if 조건식 else 거짓일_때_값
```

```python
height = 130
result = "탑승 가능" if height >= 120 else "탑승 불가능"
print(result)  # 탑승 가능
```

조건식이 참이면 앞의 값을, 거짓이면 뒤의 값을 선택해 변수에 넣는다. 6장의 여러 줄 `if`/`else`와 목적은 같지만 **조건 표현식은 하나의 값을 선택하는 표현식**이다.

### [강의자료 문제 해결 5-11] 적자/흑자

```python
incoming = int(input("수입: "))
outgoing = int(input("지출: "))
result = "흑자" if incoming > outgoing else "적자"
print(result)
```

**[원본 주의]** 수입과 지출이 같아도 이 예제 코드는 조건이 거짓이므로 `적자`라고 출력한다. 이는 예제의 분기 조건 때문이며 일반적인 손익 판단에서는 보합/손익 0을 별도로 처리할 수 있다.

## 5-12. 모듈과 `import` (추가 p.2~3)

**모듈(module)**은 기능을 모아 놓은 파이썬 파일. `import`로 불러와 사용한다.

```python
import random
print(random.randint(1, 10))

import random as rd
print(rd.randint(1, 10))

from random import randint
print(randint(1, 10))

from random import *
print(randint(1, 10))
```

`import random as rd`는 별칭을 사용한다. `from random import *`는 이름 충돌이 생길 수 있어 일반적으로 권장되지 않지만 강의자료에는 사용 예제가 나온다.

## 5-13. `random` 주요 함수 (추가 p.2~5)

| 함수 | 기능 | 핵심 조건 |
|---|---|---|
| `random()` | 난수 실수 | `0 <= x < 1` |
| `uniform(a,b)` | 두 경계 사이 난수 실수 | **[보충]** 부동소수점 반올림에 따라 b 포함 가능 |
| `randint(a,b)` | 난수 정수 | **a, b 둘 다 포함** |
| `randrange(start,stop,step)` | 범위/간격 조건의 난수 정수 | **stop 미포함** |
| `choice(seq)` | 한 요소 선택 | 요소 하나 반환 |
| `sample(seq,k)` | 중복 없이 k개 선택 | 결과 리스트 |
| `choices(seq,k=k)` | 중복 허용 k개 선택 | 결과 리스트 |
| `shuffle(list)` | 리스트 순서 무작위 섞기 | 원본 리스트 변경, 반환값 None |
| `seed(a)` | 난수 생성 상태 초기화 | 동일 시드로 재현 가능 |

```python
import random as rd
print(rd.random())
print(rd.uniform(10, 20))
print(rd.randint(1, 100))      # 1~100 가능
print(rd.randrange(1, 100, 3))# 1, 4, 7, ..., 97 중 하나
print(rd.choice([1, 2, 3]))    # 정수 하나
print(rd.sample(range(10), 3))# 0~9에서 서로 다른 3개 리스트

values = [1, 2, 3, 4, 5]
rd.shuffle(values)
print(values)
```

### `randint()` vs `randrange()`

| 코드 | 선택 가능한 수 |
|---|---|
| `randint(1,5)` | 1, 2, 3, 4, 5 |
| `randrange(1,5)` | 1, 2, 3, 4 |
| `randrange(1,10,2)` | 1, 3, 5, 7, 9 |
| `randrange(0,101,2)` | 0, 2, 4, …, 100 |

### `choice()` vs `sample()` vs `choices()`

```python
import random as rd
items = ["사과", "귤", "포도", "배"]
print(rd.choice(items))           # 문자열 하나
print(rd.sample(items, 2))       # 서로 다른 2개, 리스트
print(rd.choices(items, k=4))    # 중복 가능 4개, 리스트
```

입력이 튜플이어도 `sample()` 결과는 **리스트**다. 중복 없이 필요한 수보다 더 많이 뽑으면 `ValueError`가 발생한다.

### [강의자료 실습] 강의 과목 순서 섞기

```python
import random as rd
lec = ["국어", "영어", "수학", "과학", "사회"]
rd.shuffle(lec)
print(lec)
print(rd.choices(lec))
print(rd.sample(lec, 2))
```

`rd.shuffle(lec)`는 **lec 자체**를 수정한다. `lec = rd.shuffle(lec)`라고 하면 반환값 `None`이 저장된다.

### [강의자료 실습] 로또 번호 6개

```python
import random as rd
lotto = rd.sample(range(1, 46), 6)
print(lotto)  # 1~45 중 중복 없는 6개
lotto.sort()
print(lotto)  # 오름차순
```

`sort()`도 원본 리스트를 직접 바꾼다. 강의자료의 `lotto`처럼 표현식만 적으면 .py 파일에서는 결과가 표시되지 않으니 `print(lotto)`를 사용한다.

### [강의자료 실습] 짝수·홀수 난수, 실수 출력

```python
from random import *
print(randrange(1, 101, 2))   # 홀수 하나: 1~99
print(randrange(0, 101, 2))   # 짝수 하나: 0~100
value = uniform(1.0, 36.5)
print("%.2f" % value)
```

### 난수 시드

```python
import random as rd
rd.seed(42)
first = rd.randint(1, 100)
rd.seed(42)
second = rd.randint(1, 100)
print(first == second)  # True (같은 환경·생성기)
```

시드 하나를 설정했다고 모든 호출에서 **항상 같은 값만 나오는 것은 아니다**. 난수 생성기의 진행 순서를 재현하는 것이다.

## 5-14. 연산자 우선순위 [보충]

다음은 4~7장에 필요한 **주요 연산만 단순화**한 순서다(전체 문법 우선순위 표는 아님).

1. 괄호 `()`
2. 거듭제곱 `**`(단항 부호와의 관계는 별도 규칙 주의)
3. 단항 `+`, `-`
4. `* / // %`
5. `+ -`
6. 숫자/문자열 비교
7. `not`
8. `and`
9. `or`

```python
print(10 + 2 * 3)              # 16
print((10 + 2) * 3)            # 36
print(True or False and False) # True: and 먼저 평가
```

### 5장 오류·주의사항 총정리

- `int + float` → `float`; `int / int` → `float`.
- 문자열끼리 `+` 가능, `-` 불가능. 문자열과 정수 사이 `+`는 오류.
- `10 / 0` → `ZeroDivisionError`, `10 / 'a'` → `TypeError`.
- `//`는 **내림**, `%`는 나머지, `**`는 거듭제곱.
- `=`는 할당, `==`는 비교.
- `and`는 왼쪽이 거짓이면, `or`는 왼쪽이 참이면 **단락 평가**한다.
- 조건 표현식은 `참값 if 조건 else 거짓값` 순서다.
- `randint()`는 끝값 포함; `randrange()`는 끝값 제외.
- `choice()`는 값 한 개, `sample()`·`choices()`는 리스트.
- `sample()`은 중복 없이, `choices()`는 중복 허용.
- `shuffle()`과 `sort()`는 리스트 자체를 변경한다.

---

# 6장. 조건문

> 강의자료: `4주차_조건문.pdf` p.1~14. 자료 안의 실습은 6장 문법 이해용으로 코드의 들여쓰기·출력 문자열을 정상화했다.

## 6-1. 조건문이란? (p.1)

**조건문(Conditional Statement)**은 특정 조건이 참인지 거짓인지에 따라 **프로그램 실행 흐름을 변경**하는 구문이다. 예를 들어 속도가 제한속도 이상이면 경고를 출력하고, 아니면 출력하지 않도록 할 수 있다.

## 6-2. `if`문 (p.1~3)

```python
if 조건식:
    조건식이_참일_때_실행할_문장
```

콜론(`:`) 다음에는 **들여쓰기된 코드 블록**이 온다. 조건식이 거짓이면 블록 내부는 실행하지 않는다.

```python
num = int(input("정수를 입력: "))
if num > 50:
    print("%d는 50보다 크다" % num)
```

조건이 거짓인 경우 별도의 `else`가 없다면 아무것도 출력하지 않고 다음 코드로 넘어간다.

### 들여쓰기의 의미 [강의자료 비교 실습]

```python
score = int(input("점수: "))
if score >= 90:
    print("합격")
    print("축하합니다.")
```

위 코드는 점수가 90 이상일 때 **두 줄 모두** 출력한다. 반면:

```python
score = int(input("점수: "))
if score >= 90:
    print("합격")
print("축하합니다.")
```

여기서는 `축하합니다.`는 조건과 관계없이 **항상** 출력한다.

- 코드 블록의 소속은 **들여쓰기**로 결정된다.
- 필요한 곳에 들여쓰기가 없거나 들여쓰기 규칙이 맞지 않으면 `IndentationError` 등이 발생한다.
- `if`의 조건식 뒤에 콜론(`:`)을 빠뜨리면 문법 오류다.

### [강의자료 문제 해결 6-1] 속도위반 경고하기 (p.3)

```python
carSpeed = int(input("자동차의 현재 속도: "))
if carSpeed >= 50:
    print("속도 위반!")
```

입력 66이면 경고 출력, 45이면 출력하지 않는다. 강의자료 예제의 비교 기준은 `>= 50`이다.

## 6-3. `if~else`문 (p.3~5)

둘 중 하나를 선택할 때 사용한다.

```python
if 조건식:
    참일_때_실행
else:
    거짓일_때_실행
```

```python
score = int(input("점수: "))
if score >= 90:
    print("합격")
else:
    print("불합격")
print("수고하셨습니다.")
```

마지막 `print()`는 어느 분기를 지나더라도 실행된다.

### [강의자료 실습] 짝수·홀수 구분

```python
num = int(input("정수 입력: "))
if num % 2 == 0:
    print("짝수")
else:
    print("홀수")
```

### [강의자료 실습] 비밀번호 로그인

```python
pw = "test"
s = input("패스워드 입력: ")
if pw == s:
    print("로그인")
else:
    print("로그인 에러")
```

문자열 비교에서는 **대소문자·공백까지 일치**해야 한다. `pw = "test"`라면 `"Test"`는 같지 않다.

### [강의자료 실습] 나이와 키로 놀이기구 탑승 판단

```python
name = input("이름 입력: ")
age = int(input("나이 입력: "))
height = int(input("키 입력: "))
if age >= 10 and height >= 110:
    print("놀이기구를 탈 수 있다.")
else:
    print("놀이기구를 탈 수 없다.")
```

두 조건이 모두 참이어야 통과하므로 `and`를 사용한다.

### [강의자료 실습] B학점 구간

```python
score = int(input("성적 입력: "))
if score >= 80 and score < 90:
    print("학점 B")
else:
    print("학점 B가 아닙니다.")
```

같은 조건을 `80 <= score < 90`으로 표현할 수도 있다. **80은 포함, 90은 제외**한다.

### [강의자료 실습] 지역 선택 (`or`, `not`)

```python
area = input("지역 입력: ")
if area == "서울" or area == "경기":
    print("수도권입니다.")
else:
    print("수도권이 아닙니다.")
```

```python
area = input("지역 입력: ")
if not area == "서울":
    print("서울이 아닙니다.")
else:
    print("서울입니다.")
```

**주의:** `if area == "서울" or "경기":`라고 쓰면 의도와 달리 대부분 항상 참이 된다. 각 비교를 완성해 `area == "서울" or area == "경기"`라고 써야 한다.

## 6-4. `pass` 키워드 (p.6~7)

조건문 블록에 실행할 문장을 아직 결정하지 못했을 때 **아무 동작도 하지 않고 통과**하는 구문이다.

```python
score = int(input("점수: "))
if score >= 80:
    pass
else:
    pass
```

`pass`는 블록을 비워 둘 수 없어 임시로 사용하는 자리표시자이며 `break`처럼 반복을 종료하거나 `continue`처럼 다음 반복으로 넘기는 문장은 아니다.

### [강의자료 문제 해결 6-2] 자동 온도 조절 장치 (p.7)

```python
temp = int(input("기계 온도: "))
if temp >= 40:
    print("팬(Fan) 가동")
else:
    print("팬(Fan) 중지")
```

## 6-5. `if~elif~else`문 (p.7~10)

조건이 여러 개일 때 **위에서부터 순서대로 검사**하고, 처음 참이 된 분기 하나만 실행한다.

```python
if 조건1:
    조건1_실행
elif 조건2:
    조건2_실행
else:
    나머지_실행
```

- `elif`는 앞선 조건들이 **거짓일 때만** 검사한다.
- 참이 된 분기 이후의 `elif`와 `else`는 검사하지 않는다.
- `else`는 생략 가능하고, `elif`는 여러 번 사용할 수 있다.

### [강의자료 실습] 점수에 따른 학점 A~F (p.8~9)

```python
score = int(input("점수를 입력하세요: "))
if score >= 90:
    print("A")
elif score >= 80:
    print("B")
elif score >= 70:
    print("C")
elif score >= 60:
    print("D")
else:
    print("F")
```

| 입력 점수 | 결과 |
|---:|---|
| 98 | A |
| 90 | A |
| 82 | B |
| 75 | C |
| 60 | D |
| 59 | F |

`elif score >= 80`에 별도로 `< 90`을 작성하지 않아도 된다. 90 이상이라면 첫 번째 `if`가 참이 되어 거기서 끝나기 때문이다. **큰 경계값부터 검사해야 한다**는 점도 중요하다.

### [강의자료 문제 해결 6-3] 자동 주문 시스템 (p.9~10)

숫자로 주문 옵션을 선택하고, 옵션에 따라 메시지를 출력한다.

```python
print("Good morning. Nice to meet you.")
print("Where are you from?")
print("Please select a number")
choiceNumber = int(input("1.대한민국  2.USA  3.中國: "))

if choiceNumber == 1:
    print("주문하시겠어요?")
elif choiceNumber == 2:
    print("Would you like to order?")
elif choiceNumber == 3:
    print("您需要点菜吗？")
else:
    print("Would you like to order?")
```

**핵심:** `choiceNumber == 1`, `== 2`, `== 3`이 차례로 검사되고, 어느 것도 참이 아니면 `else`가 실행된다. 출력 문자열은 자료의 언어별 선택 예제를 따르되, 일부 중국어 문구 표기는 실행 가능한 문자열로 정리했다.

### [강의자료 문제 해결 6-4] 국가재난지원금 수령액 (p.10~11)

원본 표의 지원 금액은 1인 40만, 2인 60만, 3인 80만, 4인 가구 이상 100만 원이다.

```python
peopleNumber = int(input("인원수를 입력하세요: "))
if peopleNumber == 1:
    print("400,000원 지원")
elif peopleNumber == 2:
    print("600,000원 지원")
elif peopleNumber == 3:
    print("800,000원 지원")
elif peopleNumber >= 4:
    print("1,000,000원 지원")
```

원본에는 0명이나 음수인 경우를 처리하는 `else`가 없다. 표는 교재의 **가상 실습 기준**이며 실제 정책 안내가 아니다.

## 6-6. 중첩 조건문 (p.11~13)

조건문 안에 다른 조건문을 작성하는 것이다. **외부 조건이 참일 때만 내부 조건문을 검사**한다.

```python
num = int(input("양의 정수를 입력: "))
if num > 0:
    print("num:", num)
    if num % 2 == 0:
        print("num은 짝수")
    else:
        print("num은 홀수")
else:
    print("num은 양수가 아니다.")
```

| 입력값 | 출력 요약 |
|---:|---|
| 4 | `num: 4` → `num은 짝수` |
| 1 | `num: 1` → `num은 홀수` |
| 0 | `num은 양수가 아니다.` |
| -2 | `num은 양수가 아니다.` |

**주의:** 안쪽의 `else`와 바깥쪽의 `else`가 서로 다르다. **들여쓰기 수준으로 누구의 else인지** 확인해야 한다.

### [강의자료 문제 해결 6-5] 버스 전용차로 단속 (p.12~13)

강의자료 설정: 월~금에는 단속하며, 단속일에 승용차가 통행하면 위반. 토·일에는 단속하지 않는다.

```python
print("1.월~금, 2.토요일, 3.공휴일")
dayWeek = int(input("요일을 선택하세요: "))

if dayWeek == 1:
    print("버스 전용차로 단속 중입니다.")
    print("1.버스, 2.승용차")
    carType = int(input("차종을 선택하세요: "))
    if carType != 1:
        print("버스 전용차로 위반!!")
    else:
        print("버스입니다.")
else:
    print("토요일 및 공휴일은 단속하지 않습니다.")
```

분기 흐름:

1. 요일을 검사.
2. 단속일(`dayWeek == 1`)일 때만 차종 입력.
3. 차종이 버스가 아니면 위반 메시지.
4. 단속일이 아니면 차종 입력 자체를 실행하지 않는다.

## 6-7. 강의자료의 확인문제 표기 (p.13)

6장 p.13에는 버스 전용차로 단속 예제 다음에 **「확인 문제」 제목만 있고 문항 본문은 실려 있지 않다.** 아래 문제은행에서는 이 부분을 원문 확인문제로 가장하지 않고, 6장 실습에 근거한 **별도 예상문제**로 출제한다.

## 6-8. 조건문 과제: 출석·과제·중간·기말 가중합 (p.14)

강의자료 마지막 과제의 배점은 **출석 20%, 과제 20%, 중간 30%, 기말 30%**다. 총점 60점 미만이면 재수강 메시지를 출력한다.

```python
attendance = float(input("출석 점수: "))
assignment = float(input("과제 점수: "))
midterm = float(input("중간고사 점수: "))
final = float(input("기말고사 점수: "))

total = attendance * 0.2 + assignment * 0.2 + midterm * 0.3 + final * 0.3
print("환산 총점:", total)

if total < 60:
    print("홍길동 학생은 재수강 대상입니다.")
```

각 점수가 100점 만점이라는 **입력 전제** 아래의 코드다. 60점 **미만**이므로 정확히 60점이면 재수강 메시지를 출력하지 않는다.

### 6장 오류·주의사항 총정리

1. `if`, `elif`, `else` 뒤에 **콜론 `:`**을 붙인다.
2. 조건문의 실행 범위는 **들여쓰기**로 결정된다.
3. `if`만 있으면 조건이 거짓일 때 그냥 넘어간다.
4. `if~elif`에서 한 분기가 실행되면 아래 분기를 더 검사하지 않는다.
5. 큰 점수 조건부터 검사하면 학점 구간을 간단하게 구현할 수 있다.
6. `and`는 동시 충족, `or`는 어느 하나 충족, `not`은 반대.
7. `num % 2 == 0`은 짝수 판단의 대표적인 조건이다.
8. `pass`는 아무 동작도 하지 않는다. `break`, `continue`와 다르다.
9. 중첩 조건문에서는 `else`가 어느 `if`에 속하는지 확인한다.
10. `score < 60`과 `score <= 60`은 **경계값 60**에서 다르다.

---

# 7장. 반복문

> 강의자료: `5주차_반복문(최종).pdf` p.1~23. 숫자의 합, 구구단, 홀짝 판단, 공배수·최소공배수, `break`·`continue`, 장바구니·모금 실습 포함.

## 7-1. 반복문이란? (p.1)

**반복문(loop statement)**은 같은 코드를 여러 번 실행하는 제어문이다. 강의자료는 다음 두 가지를 중심으로 설명한다.

| 구문 | 동작 | 대표 상황 |
|---|---|---|
| `for` | 반복 가능한 객체에서 요소를 순서대로 꺼내 반복 | 횟수·범위가 알려졌을 때 |
| `while` | 조건식이 참인 동안 반복 | 종료 조건에 따라 반복할 때 |

반복문을 사용하지 않으면 `print("안녕하세요.")`를 100번 작성해야 하지만, 반복문으로는 간단하게 구현할 수 있다.

```python
for i in range(100):
    print("안녕하세요.")
```

## 7-2. `for~in`문과 구성 요소 (p.2~4)

```python
for 변수 in 반복가능한_객체:
    반복_실행문
```

- `for`, `in`: 반복 구문을 구성하는 키워드.
- **이터러블(iterable)**: 순회 가능한 객체. `range`, 문자열, 리스트, 튜플 등.
- **아이템(item)**: 반복마다 변수로 전달되는 요소.
- **콜론(`:`)**: 반복 블록 시작. 이어지는 문장을 들여쓴다.

```python
for i in range(1, 11):
    print(i)
```

`1`부터 `10`까지 총 10번 반복하며 `i`에 1, 2, …, 10이 순서대로 할당된다.

### [강의자료 실습] 2~8의 짝수 출력

```python
for num in range(2, 10, 2):
    print("num =", num)
```

출력값은 2, 4, 6, 8이다. 범위의 끝값 10은 포함하지 않는다.

### [강의자료 실습] 입력한 횟수만큼 메일 발송 메시지

```python
num = int(input("메일 발송 횟수: "))
for i in range(1, num + 1):
    print("메일 발송!")
```

`num`을 포함하여 횟수만큼 반복하려면 `range(1, num + 1)`을 사용한다. 사용자가 3을 입력하면 3회 출력한다.

## 7-3. `for` + `if` (p.5~6)

### [강의자료 실습] 1~10 출력, 3의 배수에 표시

```python
for num in range(1, 11):
    print("num =", num)
    if num % 3 == 0:
        print("3의 배수!")
```

`num`이 3, 6, 9일 때만 `3의 배수!`가 추가로 출력된다. **조건문이 반복문 안**에 있으므로 반복마다 검사한다.

### [강의자료 실습] 구구단 5단

```python
for num in range(1, 10):
    print(5, "*", num, "=", 5 * num)
```

`num`이 1~9로 변하며 `5 * 1 = 5`부터 `5 * 9 = 45`까지 출력된다.

## 7-4. 누적합(Accumulator) (p.6~7)

반복문을 사용하여 값을 계속 합산할 때 **반복문 밖에서 합계 변수 `total`을 0으로 초기화**해야 한다.

```python
total = 0
for num in range(1, 11):
    total = total + num
print("합계:", total)  # 합계: 55
```

동일한 코드는 `total += num`으로 간단히 작성할 수도 있다.

| 반복 | num | total |
|---:|---:|---:|
| 초기 | - | 0 |
| 1 | 1 | 1 |
| 2 | 2 | 3 |
| 3 | 3 | 6 |
| 4 | 4 | 10 |
| … | … | … |
| 10 | 10 | 55 |

**주의:** `total = 0`을 반복문 내부에 작성하면 매 반복에서 합계가 초기화되어 의도한 누적합을 구하지 못한다. 최종합만 출력할 때는 `print(total)`을 반복문 밖에 둔다.

## 7-5. `range()` (p.7~10)

`range()`는 범위를 나타내는 이터러블 객체를 만든다. 형식은 다음 세 가지다.

```python
range(stop)
range(start, stop)
range(start, stop, step)
```

- `start`: 시작값. 생략 시 기본값 **0**.
- `stop`: 끝 경계값. **포함되지 않음**.
- `step`: 증감 간격. 생략 시 기본값 **1**. 0일 수 없다.

### `range()` 유형 비교

| 표현식 | 실제 반복값 |
|---|---|
| `range(5)` | 0, 1, 2, 3, 4 |
| `range(1, 6)` | 1, 2, 3, 4, 5 |
| `range(1, 11)` | 1~10 |
| `range(2, 10, 2)` | 2, 4, 6, 8 |
| `range(1, 12, 2)` | 1, 3, 5, 7, 9, 11 |
| `range(10, 0, -1)` | 10, 9, …, 1 |
| `range(10, -11, -3)` | 10, 7, 4, 1, -2, -5, -8 |
| `range(5, 1)` | 빈 범위(반복 0회) |

### [강의자료 확인문제] range 값 예상 (p.8)

강의자료의 확인문제 예시에는 `range(1,12,2)`, `range(0,8,2)`, `range(-10,1,1)`처럼 범위의 시작·끝·단계를 해석하는 문제가 들어 있다. 특히 **stop 미포함**과 **step 부호**를 정확히 적용해야 한다.

### 감소하는 반복

```python
for i in range(10, 0, -1):
    print(i)
```

10부터 1까지 출력한다. 감소하는 경우에도 종료 경계는 포함하지 않는다.

### 문자열도 반복 가능 (p.10)

```python
for ch in "Python":
    print(ch)
```

`P`, `y`, `t`, `h`, `o`, `n`이 한 줄씩 출력된다. 문자열은 문자 단위로 순회되는 이터러블이다.

## 7-6. `while`문 (p.11~13)

```python
while 조건식:
    반복_실행문
```

실행 순서:

1. 조건식을 평가한다.
2. 참이면 들여쓰기 블록을 실행한다.
3. 다시 조건식을 평가한다.
4. 조건이 거짓이 될 때 종료한다.

### [강의자료 실습] 1~10 출력

```python
num = 1
while num <= 10:
    print("num:", num)
    num += 1
```

**핵심:** `num += 1`이 있어야 조건이 언젠가 거짓이 된다. 반복변수를 갱신하지 않으면 무한 루프가 발생할 수 있다.

### [강의자료 실습] 1~30 홀수·짝수 출력

```python
num = 1
while num <= 30:
    if num % 2 == 0:
        print("짝수:", num)
    else:
        print("홀수:", num)
    num += 1
```

조건 검사를 `while` 안에 넣고, `num += 1`을 매 반복마다 실행한다.

### [강의자료 실습] 구구단 3단

```python
num = 1
while num <= 9:
    print(3, "*", num, "=", 3 * num)
    num += 1
```

## 7-7. 공배수와 최소공배수 (p.14)

수업자료에는 0~100 범위에서 **3과 8의 공배수**를 찾고, 가장 작은 **양의 공배수**를 출력하는 실습이 나온다.

```python
num = 1
minNum = 0
while num <= 100:
    if num % 3 == 0 and num % 8 == 0:
        print("공배수:", num)
        if minNum == 0:
            minNum = num
    num += 1
print("최소공배수:", minNum)
```

실행 결과:

```text
공배수: 24
공배수: 48
공배수: 72
공배수: 96
최소공배수: 24
```

**포인트:**

- 3과 8로 나눈 나머지가 **동시에 0**이어야 공배수다.
- 처음 찾은 양의 공배수를 `minNum`에 기록하면 최소공배수를 구할 수 있다.
- 0도 수학적으로 공배수이지만, **최소공배수는 최소 양의 공배수**이므로 예제는 1부터 탐색한다.

## 7-8. `for`와 `while` 비교 (p.14~15)

두 코드 모두 1부터 5까지 출력한다.

```python
for num in range(1, 6):
    print(num)
```

```python
num = 1
while num < 6:
    print(num)
    num += 1
```

| 구분 | for | while |
|---|---|---|
| 중심 개념 | 반복 대상·횟수 | 조건식 |
| 초기화 | `range()` 등에서 범위 지정 | 보통 반복 전 직접 초기화 |
| 조건 확인 | 다음 요소 존재 여부 | while 조건식 |
| 값 갱신 | 반복 대상에서 자동 획득 | 필요 시 직접 갱신 |
| 무한 반복 위험 | 일반적인 유한 range에서는 적음 | 종료 조건 갱신 누락 시 큼 |

수업자료에서는 **횟수가 중요하면 for, 특정 조건이 중요하면 while**을 사용하는 것으로 설명한다.

## 7-9. 무한 루프(Infinite Loop) (p.16)

조건식이 계속 참이면 반복문을 끝내지 못하고 같은 코드를 반복하게 된다.

```python
num = 0
# 실행하면 무한 반복:
# while num < 3:
#     print("안녕하세요.")
```

반복문 내부에서 `num`의 값이 바뀌지 않아 조건이 영원히 참이다.

```python
num = 0
while num < 3:
    print("안녕하세요.")
    num += 1
```

수정된 코드는 `안녕하세요.`를 3번 출력하고 종료된다. 조건식이 거짓이 될 수 있도록 값을 갱신하거나 `break`로 종료해야 한다.

## 7-10. `continue` (p.17)

`continue`는 **현재 반복의 나머지 문장만 건너뛰고 다음 반복으로 진행**한다. 반복문 전체를 종료하는 문장은 아니다.

### [강의자료 코드 7-17] 1~10 홀수만 출력

```python
for num in range(1, 11):
    if num % 2 == 0:
        continue
    print(num)
```

출력 결과:

```text
1
3
5
7
9
```

짝수에서는 `continue`를 만나 `print(num)`을 건너뛰고 다음 숫자로 진행한다.

### `continue`와 while의 주의사항 [보충]

```python
num = 0
while num < 5:
    num += 1
    if num == 3:
        continue
    print(num)
```

출력은 `1, 2, 4, 5`다. **증가문 `num += 1`이 `continue`보다 앞에 있기 때문에** 다음 반복으로 정상 진행한다. 증가문이 뒤에만 있고 `continue`가 증가문을 계속 건너뛰면 무한 루프가 발생할 수 있다.

## 7-11. `break` (p.18)

`break`는 반복문을 **그 자리에서 즉시 종료**한다. 나머지 반복 횟수가 남아 있더라도 실행하지 않는다.

### [강의자료 코드 7-18] 누적합이 30 이상이 되는 순간 종료

```python
num = 1
total = 0
while num < 11:
    total += num
    if total >= 30:
        print("num:", num)
        break
    num += 1
```

1부터 더하면 `1+2+3+4+5+6+7 = 28`, 다음으로 8을 더하면 36이므로 `num: 8`을 출력하고 종료한다.

| num | 누적합 | 동작 |
|---:|---:|---|
| 1 | 1 | 계속 |
| 2 | 3 | 계속 |
| 3 | 6 | 계속 |
| 4 | 10 | 계속 |
| 5 | 15 | 계속 |
| 6 | 21 | 계속 |
| 7 | 28 | 계속 |
| 8 | 36 | **break** |

### `break`와 `continue` 비교

| 키워드 | 현재 반복의 남은 문장 | 다음 반복 |
|---|---|---|
| `break` | 실행하지 않음 | **실행하지 않음: 반복 종료** |
| `continue` | 실행하지 않음 | **다음 반복 진행** |

```python
for i in range(1, 8):
    if i == 3:
        continue
    if i == 6:
        break
    print(i)
```

출력은 `1, 2, 4, 5`다. 3은 건너뛰고 6에서 반복이 종료되므로 7은 실행되지 않는다.

## 7-12. `while True`, `break`, `continue` 종합 (p.19)

강의자료 p.19에는 사용자가 `quit`를 입력하면 종료하고, 너무 짧은 단어면 재입력을 요청하는 흐름이 나온다.

```python
while True:
    word = input("무엇이든지 입력하세요: ")
    if word == "quit":
        break
    if len(word) < 5:
        print("5자 이상 입력해주세요")
        continue
    print(f"{word}를 입력했습니다.")
```

- `while True:`는 조건 자체가 언제나 참이므로 `break`가 필요하다.
- `word == "quit"`이면 즉시 반복 종료.
- `len(word) < 5`이면 메시지만 출력하고 다음 입력으로 넘어간다.
- 그 외에는 단어를 확인하는 메시지를 출력한다.

**[보충]** `len()`은 문자열이나 리스트 등의 길이를 구하는 내장 함수다. 강의자료 p.19와 p.21에서 사용한다.

## 7-13. 중첩 반복문(Nested Loop) (p.19)

반복문 안에 또 다른 반복문을 작성하는 것이다. **바깥 반복 1회마다 안쪽 반복이 처음부터 끝까지 실행**된다.

```python
for i in range(1, 4):
    for j in range(1, 3):
        print(i, j)
```

실행 결과:

```text
1 1
1 2
2 1
2 2
3 1
3 2
```

바깥 반복 3회 × 안쪽 반복 2회 = 총 6회 `print()` 실행. 안쪽 반복이 끝난 뒤 바깥 반복의 다음 값으로 이동한다.

### [보충 예제] 2단부터 9단까지 전체 구구단

```python
for dan in range(2, 10):
    for num in range(1, 10):
        print(f"{dan} * {num} = {dan * num}")
```

이 코드는 강의자료 p.19의 **중첩 반복문 원리**를 구구단에 적용한 보충 예제다. 기본 자료 p.6·p.21에는 각각 단일 구구단을 출력하는 실습이 있다.

**주의:** 중첩 반복문 안의 `break`는 기본적으로 **현재 속한 가장 안쪽 반복문만** 종료한다.

## 7-14. 추가 실습 1: 일주일 평균 칼로리 (p.20~21)

수업자료 데이터: `[1300, 1850, 1700, 1500, 2100, 1700, 2300]`.

```python
week = [1300, 1850, 1700, 1500, 2100, 1700, 2300]
total = 0
for kcal in week:
    total = total + kcal
avg = total / len(week)
print(f"일일 평균 섭취량: {avg:.2f}")
```

실행 결과:

```text
일일 평균 섭취량: 1778.57
```

- 리스트는 여러 값을 순서대로 담은 객체이며 `for kcal in week`로 각 값을 꺼낸다.
- `total = 0`은 반복문 이전에 초기화.
- `len(week)`는 리스트 길이(7).
- 평균은 `total / len(week)`이며 `.2f`로 소수 둘째 자리 출력.

**[원본 주의]** 슬라이드 p.21의 출력 문장에는 '성취량'이라는 오타가 있으며 여기서는 '섭취량'으로 통일했다.

## 7-15. 추가 실습 2: 입력받은 단의 구구단 (p.21~22)

**문제 조건:** 입력이 정수 2~9 범위일 때만 해당 구구단을 출력한다. 그 외 입력은 출력하지 않는다.

```python
dan = int(input("단을 입력하시오: "))
if 1 < dan < 10:
    for num in range(1, 10):
        print(f"{dan} * {num} = {dan * num}")
```

7을 입력하면 `7 * 1 = 7`부터 `7 * 9 = 63`까지 출력된다. `if` 안에 `for`가 들어 있으므로 잘못된 단을 입력하면 반복문도 실행되지 않는다.

동일한 조건은 `dan >= 2 and dan <= 9`로 작성할 수도 있다.

## 7-16. 추가 실습 3: 장바구니 합계 (p.22~23)

사용자가 쇼핑을 계속할 때는 `y`를 입력하고, `n`을 입력하면 누적 금액을 출력하고 종료한다.

```python
total = 0
shopping = "y"
while shopping == "y":
    price = int(input("가격: "))
    total = total + price
    shopping = input("계속 하시겠습니까(y or n): ")
print(f"주문금액: {total}")
```

예: `10000` → `y` → `25000` → `y` → `3000` → `n` 입력 시 `주문금액: 38000` 출력.

**실행 흐름:**

1. 반복 시작 전에 `shopping = "y"`이므로 최소 한 번 실행한다.
2. 가격을 입력받아 `total`에 더한다.
3. 재입력 여부를 질문해 `shopping`을 갱신한다.
4. `n`이면 다음 `while` 조건이 거짓이므로 종료한다.

## 7-17. 추가 실습 4: 저금통 모금액 계산 (p.23)

```python
total = 0
while True:
    money = int(input("금액: "))
    total = total + money
    con = input("저금통이 남았나요(y or n): ")
    if con != "y":
        break
print(f"모금액 합계: {total}원")
```

예: `10000` → `y`, `50000` → `y`, `5000` → `n`이면 `모금액 합계: 65000원`을 출력한다.

이 코드는 이전 실습과 비슷하지만 반복 조건이 `while True`라는 차이가 있다. 사용자가 `y`가 아닌 값을 입력할 때 `break`를 이용해 반복을 종료한다.

## 7-18. 누적합·출력 위치·반복 횟수 추적 [보충]

**코드를 눈으로 추적할 때는 변수 값을 표로 기록**하면 좋다.

```python
total = 0
for i in range(1, 6):
    if i % 2 == 0:
        total += i
print(total)
```

| i | 짝수인가? | total |
|---:|---|---:|
| 초기 | - | 0 |
| 1 | 아니오 | 0 |
| 2 | 예 | 2 |
| 3 | 아니오 | 2 |
| 4 | 예 | 6 |
| 5 | 아니오 | 6 |

최종 출력은 `6`이다. **`print(total)`이 반복문 밖에 있으므로 합계 하나만 출력한다.** 만약 반복문 내부에 있으면 반복마다 출력된다.

## 7-19. 7장 오류·주의사항 총정리

1. `range(start, stop, step)`은 **stop을 포함하지 않는다**.
2. `range(5)`는 0~4, `range(1, 6)`은 1~5다.
3. 감소하는 `range()`는 음수 `step`을 사용한다. 예: `range(10, 0, -1)`.
4. `range(1, 6, 0)`은 `ValueError`가 발생한다.
5. `for`는 다음 요소를 순회하고, `while`은 조건이 참인 동안 실행한다.
6. `while`에서는 반복 변수가 언제 갱신되는지 확인한다.
7. 누적합은 **반복문 밖에서 0으로 초기화**한다.
8. `if`가 반복문 안에 있으면 매 반복에서 조건을 검사한다.
9. `continue`는 해당 반복의 뒤쪽 코드를 건너뛰되 다음 반복은 진행한다.
10. `break`는 즉시 반복문을 종료하고, 뒤의 반복도 실행하지 않는다.
11. `while True`는 `break` 같은 종료 수단이 없으면 무한히 반복한다.
12. 중첩 반복문은 **바깥 반복 하나당 안쪽 반복 전체**가 실행된다.
13. 출력이 반복문 안에 있는지 밖에 있는지에 따라 **출력 횟수가 다르다**.
14. `for x in 리스트`에서는 변수 x에 요소가 하나씩 들어간다.
15. `len(리스트)`는 요소의 개수이며, 평균 구하기 실습에서 사용한다.

---


---

# Part II. 확인문제 + 시험형 예상문제 (정답은 Part IV)

**풀이 규칙:** 정답을 보기 전까지 Part IV를 열지 말 것. `>>> 식`은 Python 대화형 셸에서 평가된 표현식이므로 결과를 적는다. 일반 `.py` 파일의 `print()`와 구분한다. 문항 번호 `S`는 강의자료 확인문제, `P`는 추가 예상문제다.

## A. 수업자료의 실제 확인문제 · Quiz (22개 문항군, 내부 세부 문항 포함)

### 4장 데이터와 변수

**S4-1 [수업 PDF Quiz 1, 4장 p.4]** 홍길동은 키 175cm, 나이 21세, 취미가 요리하기다. `name`, `height`, `age`, `hobby` 변수를 만들고 다음 문장과 같은 내용이 출력되도록 코드를 작성하시오.

```text
홍길동의 키는 175이고 나이는 21세이며 취미는 요리하기 입니다.
```

### 5장 연산자 — 기본 자료

**S5-1 [수업 PDF 확인문제, p.5]** 다음을 순서대로 평가한 결과 세 개를 적으시오.

```python
num1 = 3.14
num2 = 0.25
result = num1 + num2
# ① result  ② float(result)  ③ int(result)
```

**S5-2 [수업 PDF 확인문제, p.8]** 다음 빈칸을 채우시오.

```python
s = 'Hello '
result = s * ____    # 'Hello '가 5회 반복

s = __________
result = s * 3       # 'python python python '이 되도록
```

**S5-3 [수업 PDF 확인문제, p.8]** 다음 중 실행 시 오류가 발생하는 것은? (모두 선택)

```text
① 2 * 'Hello python' * 3
② 'Hello python' * 0.1
③ 'Hello python' * 5
④ 5 * 'Hello python'
⑤ 'Hello python' * -2
```

**S5-4 [수업 PDF 확인문제, p.12]** 다음 중 계산 오류가 발생하는 것은? (모두 선택)

```text
① 10 / 2
② 10 / 3.14
③ 1.0 / 0.2
④ 'Hello python' / 2.0
⑤ 'Hello python' / 2
```

**S5-5 [수업 PDF 확인문제, p.12]** `0 / 100000`의 결과와 자료형을 쓰시오.

**S5-6 [수업 PDF 확인문제, p.12]** `100000 / 0`은 무슨 결과를 만드는가? 오류라면 오류 종류를 쓰시오.

**S5-7 [수업 PDF 확인문제, p.16]** 다음 두 프로그램에 대한 설명 중 **틀린** 것은?

```python
# 프로그램 1
num1 = 10
num2 = 3
num1 // num2

# 프로그램 2 (별도 실행)
num1 = 20
num2 = 6
num1 // num2
```

```text
① 두 결과는 같다.
② 두 결과 모두 3이다.
③ 프로그램 1은 1, 프로그램 2는 2이다.
④ 결과의 자료형은 둘 다 int이다.
```

**S5-8 [수업 PDF 확인문제, p.16]** 거듭제곱 `**`에 관한 설명 중 **틀린 것**을 모두 고르시오.

```text
① 2 ** 2의 값은 2 * 2와 같다.
② 2 ** 2의 값은 (2 * 2) + (2 * 2)와 같다.
③ 3 ** 5는 3의 5제곱이다.
④ 1 ** 1000000의 값은 1000000이다.
⑤ 1000000 ** 0의 값은 1이다.
```

**S5-9 [수업 PDF 확인문제, p.18]** 대화형 실행 결과를 고르시오.

```python
num = 3
num = 30
num
```

```text
① 3   ② 30   ③ num is 3   ④ num is 30
```

**S5-10 [수업 PDF 확인문제, p.21]** 다음 비교식 여섯 개의 결과를 순서대로 쓰시오.

```python
5 != 8
10 < 5
-5 >= 5
5 <= -1
9 > 0
-1 == -5
```

**S5-11 [수업 PDF 확인문제, p.24]** 문자열 비교식 세 개의 결과를 순서대로 쓰시오.

```python
'A' > 'a'
'z' >= 'X'
'^' < '{'
```

**S5-12 [수업 PDF 확인문제, p.24]** 아래 실행 결과가 `False`가 되게 하는 연산자를 모두 고르시오.

```python
'p' ____ 'y'
# 후보 ① ==  ② !=  ③ >  ④ <=
```

**S5-13 [수업 PDF 확인문제, p.24]** 다음 비교의 결과는? 

```python
'Hello' != 'python'
```

**S5-14 [수업 PDF 확인문제, p.24의 4번 · 의미 정리]** 슬라이드에는 **서로 다른 개수의 공백으로 이루어진 두 문자열을 `==`로 비교했는데 `True`로 표시된 코드**를 바르게 고치는 문제가 있다. 다음 코드는 실제로 무엇을 출력하는가? `True`가 되도록 코드를 한 줄 고치시오.

```python
print(' ' == '  ')
```

**S5-15 [수업 PDF 확인문제, p.28]** 다음 논리식의 실행 결과는?

```python
(10 > -10) and (3.14 > 0) or (-1 == 0)
```

**S5-16 [수업 PDF 확인문제, p.28]** 실내 온도가 16℃ 이하이거나 28℃ 초과일 때 냉·난방기가 작동하도록 빈칸을 채우시오.

```python
temperature <= ____ ____ temperature > ____
```

**S5-17 [수업 PDF 확인문제, p.30]** `str1`이 정의되지 않았어도 아래 식이 오류 없이 `True`를 반환하도록 연산자를 고르시오.

```python
num1 = 8
num2 = 3
(num1 >= num2) ____ str1
# ① and  ② or  ③ not  ④ !=
```

### 7장 반복문

**S7-1 [수업 PDF 확인문제, 7장 p.8]** `range(1, 12, 2)`가 만드는 정수를 모두 적으시오.

**S7-2 [수업 PDF 확인문제, 7장 p.8]** `range(0, 8, 2)`가 만드는 정수를 모두 적으시오.

**S7-3 [수업 PDF 확인문제, 7장 p.8]** `-10`에서 `0`까지 1씩 증가하는 숫자를 얻도록 `range(시작, 끝, 단계)`의 세 인자를 쓰시오.

**S7-4 [수업 PDF 확인문제, 7장 p.8]** `range(1, 11, 2)`가 만드는 정수를 모두 적으시오.

> **6장에 대한 출처 주의:** 6장 p.13에는 '확인 문제' 제목만 있고 실제 문제가 없다. 대신 p.3~12 실습 및 p.14 출석·과제·중간·기말 성적 과제를 **Part III 코딩 연습**과 아래 예상문제에 반영했다.

## B. 수업자료 기반 + 교재 외 대비 예상문제 (정답은 Part IV)

**P1 [4장 · 예상]** 다음의 결과를 순서대로 쓰시오.

```python
x = '7'
y = int(x)
print(x * 2)
print(y + 2)
print(type(x))
```

**P2 [4장 · 예상]** 다음 실행 결과를 공백까지 적으시오.

```python
print('|%5d|%05d|%-5d|' % (42, 42, 42))
```

**P3 [4장 · 예상]** 다음의 실행 결과는? 

```python
print(bool(''))
print(bool(' '))
print(bool('False'))
```

**P4 [5장 · 예상]** 다음 결과를 순서대로 쓰시오.

```python
print(11 / 2)
print(11 // 2)
print(11 % 2)
print(2 ** 4)
```

**P5 [5장 · 예상]** 다음 코드의 결과 또는 오류를 쓰시오.

```python
x = 5
x += 3
x *= 2
print(x)
```

**P6 [5장 · 예상]** `randint(1, 5)`와 `randrange(1, 5)`는 각각 어느 값까지 반환할 수 있는가?

**P7 [5장 · 예상]** `random.choice(seq)`, `random.choices(seq, k=3)`, `random.sample(seq, 3)`의 중복 허용 여부와 반환 형태를 설명하시오.

**P8 [6장 · 예상]** 다음 코드에서 점수를 `85`로 입력하면 무엇이 출력되는가?

```python
score = 85
if score >= 90:
    print('A')
elif score >= 80:
    print('B')
elif score >= 70:
    print('C')
else:
    print('F')
```

**P9 [6장 · 예상]** 다음 코드에 `50`을 입력하면 무엇이 출력되는가?

```python
num = 50
if num > 50:
    print('큼')
print('완료')
```

**P10 [6장 · 예상]** 다음 표현식이 `True`가 되는 `age`, `height` 조건을 설명하시오.

```python
age >= 10 and height >= 110
```

**P11 [7장 · 예상]** 다음 코드의 결과는?

```python
total = 0
for i in range(1, 6):
    if i % 2 == 0:
        total += i
print(total)
```

**P12 [7장 · 예상]** 다음 코드의 결과는?

```python
num = 0
total = 0
while num < 6:
    num += 1
    if num == 4:
        continue
    total += num
print(total)
```

**P13 [7장 · 예상]** 다음 코드의 결과는?

```python
total = 0
for i in range(1, 8):
    if i == 3:
        continue
    if i == 6:
        break
    total += i
print(total)
```

**P14 [7장 · 예상]** 다음 코드의 출력 횟수는 몇 회인가?

```python
for i in range(2, 5):
    for j in range(1, 4):
        print(i, j)
```

---


# Part III. 필기형 서술형 — 직접 프로그램 작성하기

> **실전 규칙:** 문제를 읽고 **정답 코드 없이** 직접 적는다. `import`가 필요한 문제에는 `import`까지 적는다. 들여쓰기, 콜론, 변수 초기화, 반복 경계값, 자료형 변환을 스스로 확인한다. 별도 언급이 없다면 숫자 입력은 정상적인 범위로 들어온다고 가정한다. 원문 실습을 문제화한 것은 `[수업자료 실습 기반]`, 새로 만든 것은 `[추가 서술형]`으로 표시했다.

## 4장 — 변수·입출력

**W01 [수업자료 실습 기반 · p.3~4 · 쉬움]** `n1=8`, `n2=5`로 변수에 저장하고 두 수의 합을 계산하여 `8과 5의 합은 13입니다.`처럼 출력하는 프로그램을 작성하시오.

**W02 [수업자료 Quiz 1 · p.4 · 쉬움]** 이름 `홍길동`, 키 `175`, 나이 `21`, 취미 `요리하기`를 각각 변수에 저장하여 `홍길동의 키는 175이고 나이는 21세이며 취미는 요리하기 입니다.`라고 출력하시오.

**W03 [수업자료 실습 기반 · p.8 · 쉬움]** 정수 두 개를 `input()`으로 입력받아 합계를 출력하시오. 이어서 실수 두 개를 입력받아 합계를 소수점 둘째 자리까지 출력하시오(두 계산을 독립적으로 작성해도 됨).

## 5장 — 연산자·조건식·난수

**W04 [수업자료 문제 해결 5-1 · 기본 p.3 · 쉬움]** 1월·2월·3월 매출액을 정수로 입력받고, 1분기 전체 매출 합계를 출력하시오.

**W05 [수업자료 문제 해결 5-4 · 기본 p.9~10 · 쉬움]** 몸무게(kg)와 키(m)를 실수로 입력받아 `BMI = 몸무게 / (키 * 키)`를 계산하고 소수점 둘째 자리까지 출력하시오.

**W06 [수업자료 문제 해결 5-6 · 기본 p.13~14 · 쉬움]** 빵 97개를 학생 한 명당 3개씩 나누어준다고 가정한다. 빵을 받을 수 있는 학생 수(`//`)와 남는 빵 개수(`%`)를 구하시오. (강의자료처럼 `bread=97`, `count=3`을 사용.)

**W07 [수업자료 문제 해결 5-11 · 추가 p.1 · 쉬움]** 수입과 지출을 정수로 입력받아 수입이 더 크면 `흑자`, 그렇지 않으면 `적자`를 출력하는 **조건 표현식**을 사용하시오.

**W08 [수업자료 실습 기반 · 추가 p.5 · 중간]** `random` 모듈로 1~45 사이에서 **중복 없는** 로또 번호 6개를 뽑아 오름차순으로 출력하시오.

## 6장 — if·elif·else·중첩 조건문

**W09 [수업자료 실습 기반 · p.4~5 · 쉬움]** 정수 하나를 입력받아 짝수이면 `짝수`, 홀수이면 `홀수`를 출력하시오.

**W10 [수업자료 실습 기반 · p.8 · 중간]** 점수를 입력받아 90 이상 A, 80 이상 B, 70 이상 C, 60 이상 D, 나머지 F를 출력하시오. `if~elif~else`를 사용하시오.

**W11 [수업자료 실습 기반 · p.5 · 중간]** 나이와 키를 입력받아 나이 10세 이상 **그리고** 키 110cm 이상이면 `탑승 가능`, 아니면 `탑승 불가능`을 출력하시오.

**W12 [수업자료 조건문 과제 · p.14 · 중간]** 출석·과제·중간·기말 점수를 각각 입력받고 가중치 20%, 20%, 30%, 30%로 총점을 계산하시오. 점수가 60 미만이면 `홍길동 학생은 재수강 대상입니다`를 출력하시오.

**W13 [수업자료 문제 해결 6-5 기반 · p.12~13 · 중간]** `day=1`이면 평일 단속일, 그 밖에는 단속하지 않는다고 가정한다. 평일일 때만 차종을 입력받아 `1=버스`이면 `정상`, 다른 값이면 `위반`을 출력하고, 평일이 아니면 `단속 없음`을 출력하는 중첩 조건문을 작성하시오.

## 7장 — for·while·break·continue·중첩 반복문

**W14 [수업자료 실습 기반 · p.6~7 · 쉬움]** `for`문으로 1부터 10까지의 정수 합을 구해 출력하시오.

**W15 [수업자료 실습 기반 · p.6 · 쉬움]** `for`문으로 구구단 5단을 1부터 9까지 출력하시오.

**W16 [수업자료 추가 실습 1 · p.20~21 · 중간]** `week=[1300,1850,1700,1500,2100,1700,2300]` 리스트의 평균 칼로리를 `for`문과 누적합으로 계산하여 소수점 둘째 자리까지 출력하시오.

**W17 [수업자료 추가 실습 2 · p.21~22 · 중간]** 정수 `dan`을 입력받고, 2~9일 때만 해당 구구단을 출력하시오. 그 외 입력에서는 구구단을 출력하지 않으시오.

**W18 [수업자료 추가 실습 3 · p.22 · 중간]** 가격을 입력받아 합계에 더하고, 쇼핑을 계속할지 `y/n`을 입력받으시오. `y`이면 계속하고 그 밖에는 합계 출력 후 종료하는 `while` 프로그램을 작성하시오.

**W19 [수업자료 추가 실습 4 · p.23 · 중간]** `while True`를 사용하여 저금통 금액을 계속 입력받아 합산하시오. `저금통이 남았나요(y or n)`에 `y`가 아닌 답을 입력하면 `break`로 종료하고 모금 합계를 출력하시오.

**W20 [수업자료 실습 기반 · p.14 · 중간]** 1부터 100까지에서 3과 8의 공배수를 `for`문으로 출력하고, 그중 처음 등장하는 수를 최소공배수로 기록하여 출력하시오. 0은 제외하시오.

**W21 [수업자료 중첩 반복문 기반 · p.19 · 중간]** 중첩 `for`문으로 2단부터 9단까지 각 단의 1~9 배수를 출력하시오.

**W22 [추가 서술형 · 중간]** 1~10까지 반복하면서 3은 `continue`로 건너뛰고, 8을 만나면 `break`로 종료하시오. 나머지 숫자를 출력하시오.

**W23 [추가 서술형 · 중간]** `while`문을 사용하여 1부터 입력값 `n`까지의 **짝수 합**을 출력하시오.

### 종이에 작성할 때 6가지 체크

1. `int(input(...))` 또는 `float(input(...))`로 필요한 형변환을 했는가?
2. `if`, `elif`, `else`, `for`, `while`의 마지막에 콜론 `:`이 있는가?
3. 같은 블록의 들여쓰기를 동일하게 맞췄는가?
4. `total = 0` 같은 초기화가 반복문 **밖에** 있는가?
5. `range(시작, 끝+1)`처럼 마지막 값 포함 여부를 맞췄는가?
6. `continue`·`break` 및 `print()`의 위치가 의도와 맞는가?

---


# Part IV. 정답 · 핵심 해설 · 서술형 예시 답안

> **이 아래는 풀기 전에 보지 말 것.** 코드 작성 문제의 답안은 가능한 구현 중 하나다. 변수명이나 출력 문구는 문제 요구사항을 만족한다면 달라도 된다.

## A. 수업 PDF 확인문제 정답

| 번호 | 정답 | 핵심 근거 |
|---|---|---|
| S4-1 | W02 코드 참조 | 4개 변수와 `print()` 사용 |
| S5-1 | `3.39`, `3.39`, `3` | 실수 덧셈, `int()` 소수부 제거 |
| S5-2 | `5`, `'python '` | 문자열 반복에서 공백도 반복 |
| S5-3 | ② | `str * float`는 불가, `str * 음의 정수`는 빈 문자열 |
| S5-4 | ④, ⑤ | 문자열을 `/`로 나눌 수 없음 |
| S5-5 | `0.0`, `float` | `/`로 나누면 실수형 |
| S5-6 | `ZeroDivisionError` | 0으로 나눌 수 없음 |
| S5-7 | ③ | 두 프로그램의 몫 모두 3 |
| S5-8 | ②, ④ | `2**2=4`, `1**1000000=1` |
| S5-9 | ② (`30`) | 두 번째 할당으로 `num` 값 갱신 |
| S5-10 | `True, False, False, False, True, False` | 비교 연산의 True/False |
| S5-11 | `False, True, True` | 영문 ASCII 범위/유니코드 순서 |
| S5-12 | ①, ③ | `'p' == 'y'`, `'p' > 'y'`는 거짓 |
| S5-13 | `True` | 서로 다른 문자열 |
| S5-14 | `False`; 예: `print(' ' == ' ')` | 공백 개수도 문자열 비교에서 중요 |
| S5-15 | `True` | `(True and True) or False` |
| S5-16 | `16`, `or`, `28` | 16 이하 또는 28 초과 |
| S5-17 | ② `or` | 왼쪽이 참이므로 `str1` 미평가(단락 평가) |
| S7-1 | `1, 3, 5, 7, 9, 11` | 종료값 12 제외 |
| S7-2 | `0, 2, 4, 6` | 종료값 8 제외 |
| S7-3 | `-10, 1, 1` | `range(-10, 1, 1)` |
| S7-4 | `1, 3, 5, 7, 9` | 종료값 11 제외 |

> **원문 정답표 주의:** 수업자료의 이미지·주석 중 잘못 표시된 파이썬 코드, 공백이나 표현 오류가 있는 경우 실제 Python 실행 규칙을 기준으로 수정·설명했다. 특히 `and`와 `&`를 항상 동일하다고 생각하지 말 것.

## B. 예상문제 정답

| 번호 | 정답 | 설명 |
|---|---|---|
| P1 | `77` / `9` / `<class 'str'>` | `x`는 변환 후에도 문자열 |
| P2 | `\|   42\|00042\|42   \|` | 외부 구분 기호 외의 공백을 임의로 넣지 않음 |
| P3 | `False`, `True`, `True` | 빈 문자열만 False |
| P4 | `5.5`, `5`, `1`, `16` | `/`, `//`, `%`, `**` 구별 |
| P5 | `16` | 5+3=8 → 8×2=16 |
| P6 | `randint`: 5 포함, `randrange`: 5 제외 | 범위의 끝 포함 차이 |
| P7 | `choice`: 요소 1개 / `choices`: 중복 허용 리스트 / `sample`: 중복 없는 리스트 | 랜덤 함수 비교 |
| P8 | `B` | 첫 번째 참인 `elif`만 실행 |
| P9 | `완료` | `50 > 50`은 False, `print`는 if 밖 |
| P10 | 나이 10 이상 **그리고** 키 110 이상 | and의 두 조건 모두 충족 |
| P11 | `6` | 2 + 4 |
| P12 | `17` | 4를 건너뛰고 1+2+3+5+6 |
| P13 | `12` | 3 건너뛰고 6에서 종료, 1+2+4+5 |
| P14 | `9회` | 바깥 3회 × 안쪽 3회 |

**P2 정확한 출력:** 아래 코드 블록에는 `42` 앞뒤 공백을 포함했다.

```text
|   42|00042|42   |
```

## C. 필기형 코딩 서술형 예시 답안

### W01. 변수에 8과 5 저장 후 합 출력

```python
n1 = 8
n2 = 5
total = n1 + n2
print(f'{n1}과 {n2}의 합은 {total}입니다.')
```

### W02. 학생 정보 출력

```python
name = '홍길동'
height = 175
age = 21
hobby = '요리하기'
print(f'{name}의 키는 {height}이고 나이는 {age}세이며 취미는 {hobby} 입니다.')
```

### W03. 정수 합 / 실수 합

```python
a = int(input('정수1: '))
b = int(input('정수2: '))
print(a + b)

c = float(input('실수1: '))
d = float(input('실수2: '))
print('%.2f' % (c + d))
```

### W04. 1분기 매출액 합계

```python
sales1 = int(input('1월 매출: '))
sales2 = int(input('2월 매출: '))
sales3 = int(input('3월 매출: '))
total = sales1 + sales2 + sales3
print('1분기 매출액:', total)
```

### W05. BMI 계산

```python
weight = float(input('몸무게(kg): '))
height = float(input('키(m): '))
bmi = weight / (height * height)
print(f'BMI: {bmi:.2f}')
```

### W06. 빵 나누기

```python
bread = 97
count = 3
print('빵을 받을 학생 수:', bread // count)
print('남은 빵:', bread % count)
```

### W07. 흑자/적자 조건 표현식

```python
incoming = int(input('수입: '))
outgoing = int(input('지출: '))
result = '흑자' if incoming > outgoing else '적자'
print(result)
```

### W08. 로또 번호 생성

```python
import random as rd
lotto = rd.sample(range(1, 46), 6)
lotto.sort()
print(lotto)
```

### W09. 짝수·홀수 판별

```python
num = int(input('정수: '))
if num % 2 == 0:
    print('짝수')
else:
    print('홀수')
```

### W10. 학점 A~F

```python
score = int(input('점수: '))
if score >= 90:
    print('A')
elif score >= 80:
    print('B')
elif score >= 70:
    print('C')
elif score >= 60:
    print('D')
else:
    print('F')
```

### W11. 놀이기구 탑승

```python
age = int(input('나이: '))
height = int(input('키: '))
if age >= 10 and height >= 110:
    print('탑승 가능')
else:
    print('탑승 불가능')
```

### W12. 가중치 총점과 재수강

```python
attendance = float(input('출석 점수: '))
assignment = float(input('과제 점수: '))
midterm = float(input('중간 점수: '))
final_exam = float(input('기말 점수: '))
total = attendance * 0.2 + assignment * 0.2 + midterm * 0.3 + final_exam * 0.3
print('환산 총점:', total)
if total < 60:
    print('홍길동 학생은 재수강 대상입니다')
```

### W13. 단속일과 차종 (중첩 if)

```python
day = int(input('요일 구분(평일=1): '))
if day == 1:
    car = int(input('차종(버스=1): '))
    if car == 1:
        print('정상')
    else:
        print('위반')
else:
    print('단속 없음')
```

### W14. 1부터 10까지 합

```python
total = 0
for i in range(1, 11):
    total += i
print(total)
```

### W15. 구구단 5단

```python
for i in range(1, 10):
    print(f'5 * {i} = {5 * i}')
```

### W16. 일주일 평균 칼로리

```python
week = [1300, 1850, 1700, 1500, 2100, 1700, 2300]
total = 0
for kcal in week:
    total += kcal
avg = total / len(week)
print(f'평균: {avg:.2f}')
```

### W17. 2~9단 입력 검증

```python
dan = int(input('단: '))
if 2 <= dan <= 9:
    for i in range(1, 10):
        print(f'{dan} * {i} = {dan * i}')
```

### W18. 장바구니 합계

```python
total = 0
shopping = 'y'
while shopping == 'y':
    price = int(input('가격: '))
    total += price
    shopping = input('계속 쇼핑(y/n): ')
print('주문금액:', total)
```

### W19. 저금통 모금 합계

```python
total = 0
while True:
    money = int(input('금액: '))
    total += money
    con = input('저금통이 남았나요(y or n): ')
    if con != 'y':
        break
print(f'모금액 합계: {total}원')
```

### W20. 3과 8의 공배수와 최소공배수

```python
first = 0
for num in range(1, 101):
    if num % 3 == 0 and num % 8 == 0:
        print(num)
        if first == 0:
            first = num
print('최소공배수:', first)
```

### W21. 2단부터 9단 중첩 반복문

```python
for dan in range(2, 10):
    for i in range(1, 10):
        print(f'{dan} * {i} = {dan * i}')
```

### W22. continue와 break

```python
for i in range(1, 11):
    if i == 3:
        continue
    if i == 8:
        break
    print(i)
```

출력값은 한 줄씩 `1, 2, 4, 5, 6, 7`이다.

### W23. while문으로 짝수의 합

```python
n = int(input('n: '))
num = 1
total = 0
while num <= n:
    if num % 2 == 0:
        total += num
    num += 1
print(total)
```

---

# Part V. 최종 시험 직전 핵심 확인

| 장 | 반드시 알고 있어야 할 핵심 | 필기 코딩에 자주 쓰는 형태 |
|---|---|---|
| 4장 | 자료형·변수·`input()` 형변환·`print()`·포매팅 | `int(input())`, `f'{x:.2f}'` |
| 5장 | 산술·할당·비교·논리·조건표현식·난수 | `%`, `//`, `**`, `and`, `or` |
| 6장 | 조건 범위·조건 순서·들여쓰기·중첩 `if` | `if/elif/else`, `pass` |
| 7장 | `range()`·누적합·`while`·`break/continue`·중첩 반복 | `for`, `while`, `total +=` |

## 시험 전에 마지막으로 확인할 오류들

| 코드/상황 | 결과/주의 |
|---|---|
| `int('3.14')` | `ValueError` |
| `'10' + 10` | `TypeError` |
| `10 / 0` | `ZeroDivisionError` |
| 미정의 이름 사용 | `NameError` (단락 평가로 건너뛰면 미발생) |
| `if x > 5` (콜론 없음) | `SyntaxError` |
| 들여쓰기 누락 | `IndentationError` |
| `range(1, 10, 0)` | `ValueError` |
| `while` 조건 갱신 없음 | 무한 반복 가능 |
| `print()`와 `end` | 공백·줄바꿈 정확히 판단 |
| `float` 포매팅 `:.2f` | 소수 둘째 자리 출력, 반올림 |

## 서술형을 쓰는 최소 절차

1. 입력할 값과 자료형을 정하고 `int(input())`, `float(input())`를 작성한다.
2. 판단이 필요하면 `if/elif/else`, 반복이 필요하면 `for`나 `while`을 선택한다.
3. 합계라면 `total=0`을 반복문 위에 둔다.
4. `for`는 끝값 제외, `while`은 조건 갱신을 검사한다.
5. 모든 `:`와 들여쓰기, 출력문 위치를 확인한다.
6. 손으로 예시 입력 1개를 넣어 실행 흐름을 검산한다.

**범위 주의:** 터틀그래픽은 교수 공지에 따라 제외했다. 이 문서의 **실제 확인문제 부분은 업로드한 PDF에 포함된 것만** 담았다. 별도 교재의 확인문제·연습문제 전체를 검토한 것은 아니다.

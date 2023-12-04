---
layout: single
title:  "Jump to Python 02-1"
typora-root-url: ../
---
# 02 파이썬 프로그래밍의 기초, 자료형1

## 02-1 숫자형

숫자형태로 이루어진 자료형 ( 정수, 실수, 8진수, 16진수등 )

### 숫자형은 어떻게 만들고 사용할까?

정수형( integer ) 정수를 뜻하는 자료형

```python
>>> a = 123
>>> a = -178
>>> a = 0
```

실수형( floating- point ) 소수점이 포함된 숫자

```python
>>> a = 1.2
>>> a = -3.45
```

8진수와 16진수 

```python
#8진수
>>> a = 0o177
>>> print(a)
127

#16진수
>>> a = 0x8ff
>>> b = 0xABC
>>> print(b)
2748
```

### 숫자형을 활용하기 위한 연산자

사칙연산

```python
>>> a = 3
>>> b = 4

>>> a + b
7

>>> a - b
-1

>>> a * b
12

>>> a / b
0.75
```

x의 y제곱을 나타내는 **연산자

```python
>>> a = 3
>>> b = 4
>>> a ** b
81
```

나눗셈 후 나머지를 리턴하는 %연산자

```python
>>> 7 % 3
1

>>> 3 % 7
3
```

나눗셈의 몫을 리턴하는 //연산자

```python
>>> 7 // 4
1
```

## 02-2 문자열 자료형

문자열이란 문자, 단어들으로 구성된 문자들의 집합을 말한다.

ex) “Life is too short, You need Python”

“a”

“123”

따옴표로 둘러싸어 있으면 모두 문자열이라고 보면 된다.

### 문자열은 어떻게 만들고 사용할까?

```python
#1. 큰따옴표로 양쪽 둘러싸기
"Hello World"

#2. 작은따옴표로 양쪽 둘러싸기
'Python is fun'

#3. 큰 따옴표 3개를 연속으로 사용하여 양쪽 둘러싸기
"""Life is too short, You need Python"""
#4. 작은 따옴표 3개를 연속으로 사용하여 양쪽 둘러싸기
'''Life is too short, You need Python'''
```

### 문자열 안에 작은 따옴표나 큰 따옴표를 포함시키고 싶을 때

문자열을 만드는 방법이 4가지인 이유: 문자열 안에 작은 따옴표와 큰 따옴표가 들어갈 수 도 있어서.

문자열 안에 작은 따옴표 포함하기

```python
>>> food = "Python's favorite food is perl"
```

문자열 안에 큰 따옴표 포함하기

```python
>>> say = '"Python is very easy." he says.'
```

역슬래시를 사용해서 작은 따옴표와 큰 따옴표를 문자열에 포함하기 

```python
>>> food = 'Python\'s favorite food is perl'
>>> say = "\"Python is very easy.\" he says."
```

### 여러 줄인 문자열을 변수에 대입하고 싶을 때

문자열이 항상 한 줄은 아니다. 여러 줄의 문자열을 변수에 대입하고 싶다면

```python
#1. 줄을 바꾸기 위한 이스케이프 코드 \n 삽입하기
>>> multiline = "Life is too short\nYou need python"
#읽기가 불편하고 줄이 길어지는 단점이 있다.

#2. 연속된 작은 따옴표 3개 또는 큰따옴표 3개 사용하기
>>> multiline = """Life is too short
				...You need python
				..."""
```

### 이스케이프 코드

| 코드 | 설명 |
| \n | 문자열 안에 서 줄바꿈 |
| --- | --- |
| \t | 문자열 사이에 탭 간격 |
| \\ | \를 그대로 표현 |
| \’ | ' 를 그대로 표현 |
| \” | " 를 그대로 표현 |
| \r | 캐리지 리턴 |
| \f | 폼 피드 |
| \a | 벨 소리 |
| \b | 백 스페이스 |
| \000 | 널 문자 |

### 문자열 연산하기

파이썬에서는 문자열을 더하거나 곱할 수 있다.

문자열 더해서 연결하기

```python
>>> head = "Python"
>>> tail = " is fun!"
>>> head + tail
'Python is fun!'
```

문자열 곱하기

```python
>>> a = "python"
>>> a * 2
'pythonpython'
```

문자열 곱하기 응용

```python
>>> print("=" * 50)
>>> print(My Program)
>>> print("=" * 50)
```

문자열 길이 구하기

문자열의 길이는 len 함수를 사용하면 쉽게 구할 수 있다.

```python
>>> a = "Life is too short"
>>> len(a)
17
```

### 문자열 인덱싱과 슬라이싱

인덱싱(indexing) 무언가를 가리킨다.

슬라이싱(slicing) 무언가를 잘라낸다.

문자열 인덱싱

```python
>>> a = "Life is too short, You need python"
>>> a[3]
'e'
```

문자열 인덱싱 활용하기

```python
>>> a = "Life is too short, You need python"
>>> a[0]
'L'
>>> a[12]
's'
>>> a[-1]
'n'
```

문자열 슬라이싱

문자열에서 단어를 뽑아 내는 방법

```python
>>> a = "Life is too short, You need python"

#1
>>> b = a[0] + a[1] + a[2] + a[3]
>>> b
'Life'

#2
>>> a[0:4]
'Life'
```

문자열을 슬라이싱 하는 방법

```python
>>> a = "Life is too short, You need python"

#공백도 문자로 취급한다.
>>> a[0:5]
'Life '

#항상 시작번호가 0일 필요는 없다.
>>> a[0:2]
'Li'
>>> a[5:7]
'is'
>>> a[12:17]
'short'

#끝번호를 생략하면 시작번호부터 끝까지 슬라이싱 한다.
>>> a[19:]
'You need Python'

#시작번호를 생략하면 처음부터 끝번호까지 슬라이싱 한다.
>>> a[:17]
'Life is too short'

#시작번호와 끝번호 둘다 생략하면 문자열의 전체를 출력한다.
>>> a[:]
'Life is too short, You need python'

#슬라이싱에서도 -기호를 사용할 수 있다.
>>> a[19:-7]
'You need'
#이때에도 -7은 포함하지 않고 -8까지만 출력한다.
```

슬라이싱으로 문자열 나누기

자주 사용하는 슬라이싱 기법.

```python
>>> a = "20230331Rainy"
>>> year = a[4:]
>>> day = a[4:8]
>>> weather = a[8:]

>>> year
2023
>>> day
0331
>>> weather
'Rainy'
```

### 문자열 포매팅이란?

```python
#문자열 안의 특정 값만이 다를때, 이것을 바꾸는 것을 가능하게 하는 것이 '문자열 포매팅'
"현재 온도는 18도 입니다."
"현재 온도는 20도 입니다."
```

### 문자열 포매팅 따라 하기

```python
#1. 숫자 바로 대입
>>> "I eat %d apples." %3
'I eat 3 apples.'

#2. 문자열 바로 대입
>>> "I eat %s apples." %"five"
'I eat five apples.'

#3. 숫자 값을 나타내는 변수로 대입
>>> number = 3
>>> "I eat %d apples." %number
'I eat 3 apples.'

#4. 2개 이상의 값 넣기
# 괄호안에 쉼표로 구분하여 각각의 값을 넣어준다.
>>> number = 10
>>> day = "three"
>>> "I ate %d apples. so I was sick for %s days" % (number, day)
'I ate 10 apples. so I was sick for day days'
```

### 문자열 포맷 코드

| 코드 | 설명 |
| %s | 문자열 string |
| --- | --- |
| %c | 문자 1개 character |
| %d | 정수 integer |
| %f | 부동소수 floating-point |
| %o | 8진수 |
| %x | 16진수 |
| %% | 문자% 자체 |

%s 포맷 코드는 어떤 형태의 값이든 변환하여 넣을 수 있다.

```python
>>> "I have %s apples" %3
'I have 3 apples'
>>> "reate is %s" %3.234
'reate is 3.234'
```

포매팅 연산자 %d와 %가 같은 문자열 안에 있다면 %를 나타내기 위하여 %%를 사용해야한다.

```python
#exemple
>>> "Error is %d%%." %98
'Error is 98%'
```

### 포맷 코드와 숫자 함께 사용하기

```python
#1. 정렬과 공백
>>> "%10.s" %"hi"
'        hi' 
#hi가 오른쪽 정렬됨. %10s는 전체길이가 10인 문자열 공간에서 대입되는 값을 오른쪽으로 정렬하고
#나머지는 공백으로 남겨두라는 의미임.
#반대쪽인 왼쪽 정렬은 %-10s가 됨.
>>> "%-10shane." %'hi'
'hi        hane'

#2. 소수점 표현하기
>>> "%0.4f %3.42134234
'3.4213'
#소수점을 4자리까지만 표현하고 싶은 경우 위와 같이 작성.
#%0.4f 에서 0은 길이에 상관하지 않는다, .은 소수점, 4는 소수점 뒤에 나올 숫자의 개수
#0을 생략하여 %.4f와 같이 사용하기도 함.
```

### format함수를 사용한 포매팅

format함수를 사용하면 발전된 스타일로 문자열 포맷을 지정할 수 있다.

```python
#1. 숫자 바로 대입하기
>>> "I eat {0} apples".format(3)
'I eat 3 apples'
#{0} 부분이 3으로 바뀌었다.

#2. 문자열 바로 대입하기
>>> "I eat {0} apples".format("five")
'I eat five apples'
#{0} 부분이 five로 바뀌었다.

#3. 2개 이상의 값 넣기
>>> number = 10
>>> day = "three"
>>> "I ate {0} apples. so I was sick for {1} days.".format(number, day)
'I ate 10 apples. so I was sick for three days.'
#2개 이상의 값을 넣을 경우 인덱스 항목이 format함수의 입력값으로 순서에 맞게 바뀐다.

#4. 이름으로 넣기
>>> "I ate {number} apples. so I was sick for {day} days.".format(number = 10, day = 3)
'I ate 10 apples. so I was sick for 3 days.'
#name 형태를 사용하는 방법도 있다. 반드시 name = value 같은 형태의 입력값이 있어야 한다.

#5. 인덱스와 이름을 혼용해서 넣기
>>> "I ate {0} apples. so I was sick for {day} days.".format(10, day = 3)
'I ate 10 apples. so I was sick for 3 days.'

#6. 왼쪽 정렬
>>> "{0:<10}".format("hi")
'hi        '
# :<10 표현식을 사용하면 치환되는 문자열을 왼쪽으로 정렬하고 문자열의 총 자릿수를
# 10으로 맞출 수 있다.
# 같은 방식으로 오른쪽 정렬은 :>10 을 사용하여 할 수 있다.
# :^10 을 사용하면 가운데 정렬도 가능하다.

#7. 공백 채우기
>>> "{0:=^10}".format("hi")
'====hi===='
>>> "{0:!<10}".format("hi")
'hi!!!!!!!!'
#공백 대신 지정한 문자 값으로 채워 넣을 수 있다.
# : 와 <, >, ^ 사이에 채워 넣을 문자값을 넣는다.

#8. 소수점 표현하기
>>> y = 3.42134234
>>> "{0:0.4f}".foramt(y)
'3.4213'

>>> "{0:10.4f}".foramt(y)
'    3.4213'

#9. { 또는 } 문자 표현하기
>>> "{{ and }}". format()
'{ and }'
# format함수를 사용해 문자열을 포매팅할 경우 { or }를 문자 그대로 사용하고 싶은 경우 2개를
# 연속하여 사용하면 된다.
```

### f 문자열 포매팅

파이썬 3.6이상부터 f 문자열 포매팅을 사용할 수 있다.

문자열 앞에 f 접두사를 붙이면 f 문자열 포매팅 기능을 사용할 수 있다.

```python
>>> name = '홍길동'
>>> age = 30
>>> f'나의 이름은 {name}입니다. 나이는 {age}입니다.'
'나의 이름은 홍길동입니다. 나이는 30입니다.'
#f 문자열 포매팅은 변수값을 참조할 수 있다. 또한 표현식도 지원한다.
#표현식은 중괄호 안의 변수를 계산식과 함께 사용하는 것.

>>> age = 30
>>> f'나는 내년이면 {age + 1}살이 된다.'
'나는 내년이면 31살이 된다.'

#딕셔너리
#딕셔너리는 key 와 value를 한 쌍으로 가지는 자료형.
>>> d = {'name' : '홍길동', 'age' : 30}
>>> f'나의 이름은 {d["name"]}입니다. 나이는 {d[age"]}입니다.'
'나의 이름은 홍길동입니다. 나이는 30입니다.'

#정렬
>>> f'{"hi":>10}' #오른쪽 정렬
'hi        '

>>> f'{"hi":<10}' #왼쪽 정렬
'        hi'

>>> f'{"hi":^10}' #가운데 정렬
'    hi    '

#공백 채우기
>>> f'{"hi":=^10}'
'====hi===='

>>> f'{"hi":!<10}'
'hi!!!!!!!!'

#소수점 표현
>>> y = 3.42134234
>>> f'{y:0.4f}'
'3.4213'

# { or } 표현
>>> f'{{ and }}'
'{ and }'
```

### 문자열 관련 함수들

문자열 내장 함수

문자열 변수 이름뒤에 . 을 붙인 후 함수 이름을 써주면 사용할 수 있다.

문자 개수 세기 - count

```python
>>> a = "hobby"
>>> a.count('b')
2
```

위치 알려주기 - find, index

```python
#1. find
>>> a = "Python is the best choice"
>>> a.find('b')
14

>>> a.find('k')
-1
#문자열 중 b가 처음으로 나온 위치 반환, 문자나 문자열이 존재하지 않는다면 -1 반환

#2. index
>>> a = "Life is too short"
>>> a. index('t')
8

>>>a.index('k') #Error!
#t가 맨처음 나온 위치 반환, 문자나 문자열이 없다면 오류발생.
```

문자열 삽입 - join

```python
>>> ",".join('abcd')
'a,b,c,d'

>>> ",".join(['a', 'b', 'c', 'd'])
'a,b,c,d'
```

소문자를 대문자로 바꾸기 - upper

```python
>>> a = "hi"
>>> a.upper()
'HI'
```

대문자를 소문자로 바꾸기 - lower

```python
>>> a = "HI"
>>> a.lower()
'hi'
```

공백 지우기 - lstrip, rstrip, strip

```python
>>> a = " hi "

#왼쪽 공백 지우기
>>> a.lstrip()
'hi '

#오른쪽 공백 지우기
>>> a.rstrip()
' hi'

#양쪽 공백 지우기
>>> a. strip()
'hi'
```

문자열 바꾸기 - replace

```python
>>> a = "Life is too short"
>>> a.replace("Life", "Your leg")
'Your leg is too short'
#replec(바뀔 문자열, 바꿀 문자열)
```

문자열 나누기 - split

```python
#1
>>> a = "Life is too short"
>>> a.split()
['Life', 'is', 'too', 'short']

#2
>>> b = "a:b:c:d"
>>>b.split(':')
['a', 'b', 'c', 'd']
```

split 함수는 괄호안에 아무것도 넣어주지 않으면 공백 등을 기준으로 문자열을 나누어 준다.

만약, 괄호안에 특정 값이 있을 경우 ex) b.split(”;”) 괄호 안의 값을 구분자로 문자열을 나누어 준다.

이렇게 나누어진 값은 리스트에 하나씩 들어간다.

**문자열 함수는 문자열을 바꾸는게 아니라 문자열을 바꾼 값을 리턴하는 것을 주의하자.**

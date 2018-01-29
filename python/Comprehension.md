# Python | Comprehension

List Comprehension 개념을 이번 기회에 확실히 정리하고 넘어가고자 한다. 리스트 안에 for문을 포함하는 리스트 내포(List Comprehension)을 이용하면 좀 더 편리하고 직관적인 프로그램을 만들 수 있다.

<br>
Python 2에서 지원하는 Comprehension

* List Comprehension

Python 3에서 지원하는 Comprehension

* List Comprehension
* Dictonary Comprehension
* Set Comprehension
* (+ Generator Comprehension; Generator Expression)

<br>

## 1.List Comprehension


정의 : 반복가능객체로 부터 항목을 가져와 지정된 표현식에 따라 새로운 리스트 컬렉션을 생성하는 것

```python
표현식 for 항목 in 반복가능객체 [if 조건]]
```
반복가능객체 : 입력으로 사용되는 Iteration이 가능한 데이터Sequence 또는 컬렉션

반복가능객체는 for 루프를 돌며 각각의 항목을 하나씩 가져오게 되고, if 조건식이 있으면 해당 항목이 조건에 맞는지 체크하게 된다. 

만약 조건에 맞으면 표현식(Output Expression)에 각 항목을 대입하여 출력 결과를 얻게 된다.

간단한 예시를 들어보자. 

```python
>>> a = [1,2,3,4]
>>> result = []
>>> for num in a:
...     result.append(num*3)
...
>>> print(result)
[3, 6, 9, 12]
```

위 예제를 List Comprehension을 아래처럼 간단히 나타낼 수 있다. 

```python
>>> result = [num * 3 for num in a]
>>> print(result)
[3, 6, 9, 12]
```

만약 짝수에만 3을 곱하여 담고 싶다면 다음과 같이 "if 조건"을 사용할 수 있다.

```python
>>> result = [num * 3 for num in a if num % 2 == 0]
>>> print(result)
[6, 12]
```

<br>
### **추가로,**

보통 list에 불필요한 값은 밑줄로 표기한다.
```python
zeroes = [0 for _ in numbers]  # zeroes는 numbers와 동일한 길이
```

List comprehension에는 여러 for를 포함시킬 수 있다.

```python
pairs = [(x,y)
		for x in range(10)
		for y in range(10)]

# (0,0) (0,1) ... (9,8) (9,9) 총 100개

```

뒤에 나오는 for는 앞에 나온 결과에 대해 반복한다.

```python
increasing_pairs = [(x,y)  # x < y인 경우만 해당
						for x in range(10)	# range(low, high)는 [low, low + 1, ..., hi - 1]을 의미함
						for y in range(x + 1, 10)]
```

## 2.Set Comprehension

List Comprehension과 거의 같지만, 결과가 Set으로 반환된다는 점이 다르다.

```python
{표현식 for 항목 in 반복가능객체 [if 조건]}
```

## 3.Dictionary Comprehension

마찬가지로 List Comprehension이나 Set Comprehension과 거의 같지만 표현식이 Key:Value이며, 결과로 Dict가 반환된다는 점이 다르다.

```python
{Key:Value for 항목 in 반복가능객체 [if 조건]}
```

<br>
-----
# REFERENCES
* [초보몽키의 개발공부로그](https://wayhome25.github.io/python/2017/02/26/py-17-comprehension/)
* [점프 투 파이썬](https://wikidocs.net/22)
* [PythonStudy.com](http://pythonstudy.xyz/python/article/22-Python-Comprehension)

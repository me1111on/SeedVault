## 파이썬 dictionary
```python
#선언방법
dict = {}
dict["키이름"] = value


dict.keys()
#key들의 목록이 List로

dict.values()
#value들의 목록이 List로

dict.items()
#key, value 한쌍을 튜플로 묶은 List로

```



## 파이썬 collections
```python 
from collections import Counter

zz = "abc dde fffffffff ab~"
Counter(zz)
# Counter({'f': 9, ' ': 3, 'a': 2, 'b': 2, 'd': 2, 'c': 1, 'e': 1, '~': 1})
# Dictionary 형태


# Dictionary의 함수들을 이용할 수 있음.

Counter(zz).gets('#')
# None
Counter(zz).items()
# dict_items([('a', 2), ('b', 2), ('c', 1), (' ', 3), ('d', 2), ('e', 1), ('f', 9), ('~', 1)]) -> 얘는 튜플
# 이외에서 keys(), values()등도 사용가능


Counter(zz).most_common()
# [('f', 9), (' ', 3), ('a', 2), ('b', 2), ('d', 2), ('c', 1), ('e', 1), ('~', 1)] 가장 높은 빈도수 순서대로 
```

## 파이썬 Priority Queue
https://medium.com/@yhmin84/%ED%8C%8C%EC%9D%B4%EC%8D%AC-%EC%9A%B0%EC%84%A0%EC%88%9C%EC%9C%84-%ED%81%90-priority-queue-%EB%A5%BC-%EC%9C%84%ED%95%9C-heapq-%EB%AA%A8%EB%93%88-%EC%82%AC%EC%9A%A9%EB%B2%95-b33c4e0ef2b1
```python


```

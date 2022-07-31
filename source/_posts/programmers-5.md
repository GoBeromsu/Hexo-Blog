---
title: 신규 아이디 추천
categories: algorithm
date: 2022-07-25 15:54:34
tags: Programmers
---

## 풀이

```python
def solution(new_id):
    answer = ''
    answer = new_id.lower()
    temp =''
    for s in answer:
        if s.isalnum() or s=='-' or s=='_'or s=='.':
            temp+=s
    answer=temp
    temp=answer[0]
    for i in range(1,len(answer)):
        if answer[i-1]=='.' and answer[i]=='.':
            continue
        temp+=answer[i]
    answer=temp.strip('.')
    if answer=='':
        answer+='a'
    if len(answer)>=16:
        answer=answer[0:15]
    if answer[-1]=='.':
        answer=answer[:len(answer)-1]
    while len(answer)<=2:
        answer+=answer[-1]
    return answer
```
- 파이썬의 문자열을 다룰 수 있는가를 물어보는 문제이다
  - lower()은 문자열을 바꾸는게 아니라 바뀐 문자열을 리턴함수이다

## 회고

```python
import re

def solution(new_id):
    st = new_id
    st = st.lower()
    st = re.sub('[^a-z0-9\-_.]', '', st)
    st = re.sub('\.+', '.', st)
    st = re.sub('^[.]|[.]$', '', st)
    st = 'a' if len(st) == 0 else st[:15]
    st = re.sub('^[.]|[.]$', '', st)
    st = st if len(st) > 2 else st + "".join([st[-1] for i in range(3-len(st))])
    return st

```

- 위의 문제를 정규식으로 깔끔하게 풀어낸 사람도 존재한다
- 난 솔직히 더럽게 푼건데 사실 정규식으로 풀기를 원한 문제였을가 싶다
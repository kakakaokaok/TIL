# 제목
해시태그(#)를 사용하여 1~6 레벨의 제목을 사용할 수 있다.

```markdown
# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6
```

# 굵게, 기울이기, 취소선
```markdown
**굵게**
*기울이기*
~~취소선~~
```

# 표
```markdown
| 개  | 똥  | 아  |
| --- | --- | --- |
| 똥  | 쌌  | 니  |
| 아  | 니  | 오    |
```

# 목록
## Unordered list
```markdown
- 목록 1
- 목록 2

* 목록 1
* 목록 2
등등
```

## Ordered list
```markdown
1. 목록 1
2. 목록 2
3. 목록 3
등등
```
## 섞어서 사용 가능
```markdown
1. 한 번 더
	- 나에게
	- 질풍같은
2. 용기를
	- 거친 파도에도
	- 굴하지 않게
```
# 코드블록 삽입
백틱을 앞 뒤로 3개씩 사용하고, 위쪽 백틱 뒤에 어떤 언어를 사용하는지 표시한다
```python
print("Hello, world!")
```
### 인라인 코드 삽입
백틱을 앞뒤로 1개씩 사용해 삽입한다

# 인용
```markdown
> 앞에 꺾쇠 표시를 사용한다
> > 함 더
> > > 함 더
```
# 구분선
```
---
- - -
-----------
***
* * *
***********
```

# URL
```markdown
[실라벌스로 이동합니다](https://syllaverse.com)
```

# 파일 링크
![alt 텍스트](파일경로)

# 순서
순서가 있는 듯 하다.
예를들어
- ## 리스트와 제목 사용
## - 제목은 적용되지만 리스트는 적용 안됨
# > 제목은 적용되지만 인용은 안됨
> # 제목과 인용 둘 다 적용됨
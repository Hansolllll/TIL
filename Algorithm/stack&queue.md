# stack(스택)
- 선입후출의 자료구조 
- 입구와 출구가 동일한 형태로 시각화(예시:박스 쌓기)
![스택](./../assets/stack.jpeg)

- 삽입과 삭제의 동작으로 구성됨
    - python
    ```python
    stack.append() 
    => stack에 원소 추가

    stack.pop()
    => stack에서 원소 빼기

    print(stack[::-1])
    => 집어넣은 역순으로 출력
    print(stack)
    => 집어넣은 순서대로 출력
    ```

    - C++
    ```c++
    stack.push() 
    => stack에 원소 추가

    stack.pop()
    => stack에서 원소 빼기

    cout << s.top << ' ';
    => 가장 마지막에 집어넣은 원소 출력

    s.pop();
    => 가장 마지막 원소 꺼내기
    ```
    *cout* => `<<(변수)<< or <<'문자열'<<`의 형태로 작성해 출력하는데 이용


    - Java 
    ```java
    stack.push() 
    => stack에 원소 추가

    stack.pop()
    => stack에서 원소 빼기

    while (!s.empty()){
        System.out.print(s.peek()+' ');
    => peek으로 최상단 원소 확인
        s.pop();
    => pop으로 꺼내기
    }
    ```

# queue(큐)
- 선입선출의 자료구조
- 입구와 출구가 모두 뚫린 터널같은 형태
![queue](./../assets/queue.jpeg)

- python
```python
from collections import deque
=> 리스트로 구현가능하지만 효율을 위해 deque 사용할 것

queue.append() 
=> queue에 원소 추가

queue.popleft()
=> queue에서 원소 빼기

print(squeue)
=> 집어넣은 순서대로 출력

queue.reverse()
=> 뒤집기

print(queue)
=> 집어넣은 역순으로 출력
```

- C++
```c++
using namespace std;
=> std 라이브러리 사용
q.push() 
=> queue에 원소 추가

q.pop()
=> queue에서 원소 빼기

cout << q.front << ' ';
=> 앞에서부터 원소 출력

q.pop();
=> 원소 꺼내기
```
*cout* => `<<(변수)<< or <<'문자열'<<`의 형태로 작성해 출력하는데 이용


- Java 
```java
q.offer() 
=> queue에 원소 추가

q.poll()
=> queue에서 원소 빼기

while (!s.empty()){
System.out.print(q.poll()+' ');
=> 가장 먼저 들어온 원소부터 추출
}
```
# priority queue(우선순위 큐)
- 우선순위가 높은 데이터 순으로 삭제하는 자료구조
- 가치데이터와 함께 넣음 

## 구현방법
- 배열, 연결리스트, 힙으로 구현 가능하며, 힙 사용이 가장 효율적

## `heap`
- 참고1:  https://gmlwjd9405.github.io/2018/05/10/data-structure-heap.html
- 참고2: https://gmlwjd9405.github.io/2018/05/10/algorithm-heap-sort.html
- 우선순위 큐를 위해 만들어진 자료구조로 최댓값, 최솟값을 쉽게 추출 가능
- 힙정렬(`heap sort`): 힙트리를 이용해 자료를 정렬
- 최대 힙(`max heap`): 부모노드 키값 > 자식노드 키값
- 최소힙(`min heap`): 부모노드 키값 < 자식노드 키값
- 이때 부모-자식 간에만 대소관계가 성립하며, 형제노드 사이에선 성립하지 않음

### `heap` 구현
```python
import sys
import heapq

def heapsort(iterable):
    h = []
    result = []

    # 힙에 원소삽입(파이썬은 기본적으로 min heap형태로 동작)
    # heappush(heap, item): item을 heap에 추가
    for _ in iterable:
        heapq.heappush(h, value)

    # 힙에 삽입된 원소 차례대로 꺼내 result에 담기
    # heappop(heap): heap에서 가장 작은 원소 pop, heap이 빈 경우 IndexError
    for i in range(len(h)):
        result.append(heapq.heappop(h))
    return result

    # max heap 형태로 동작하게 하고 싶다면 -value와 -h를 사용할 것
```


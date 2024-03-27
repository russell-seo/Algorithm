## DFS 깊이 우선 탐색(Depth-First Search)

- 깊이 우선 탐색(DFS)는 하나의 순환 알고리즘으로 백트래킹에 사용하는 대표적인 탐색 알고리즘 이다.
- 루트 노드 에서 시작해서 다음 분기로 넘어가기 전에 해당 분기를 완벽하게 탐색하는 방식을 말한다. 주로 재귀함수, Stack으로 구현할 수 있다.

아래 그림은 DFS를 Stack의 그림으로 표현 한 내용이다.


![image](https://github.com/russell-seo/Algorithm/assets/79154652/d8b08b86-de9b-4192-b2a4-eedc31abbbad)


![image](https://github.com/russell-seo/Algorithm/assets/79154652/52fd6ed2-71c0-41c1-800b-60afa6010db1)


![image](https://github.com/russell-seo/Algorithm/assets/79154652/351a1eb5-2be0-4a56-a3f1-80ed9f24e4c5)


![image](https://github.com/russell-seo/Algorithm/assets/79154652/5cb1c56d-1030-41c8-972e-8a6ecd73519a)


### 시간복잡도

- 인접 행렬에서의 시간 복잡도: O(V2)
- 인접 리스트에서의 시간 복잡도:O(V+E)
- V:정점(노드)개수, E:간선개수

### 장단점

장점

- DFS는 현재 순회중인 정점만 저장하는 스택 데이터 구조를 사용하기 때문에 BFS에 비해 메모리 공간을 덜 차지한다.
- DFS는 목표가 특정 정점에 최대한 빨리 도달하는 것일 때 유용하다.
- DFS를 사용하여 그래프에서 순환을 감지할 수 있다.

단점

- 순환 그래프의 경우 DFS가 무한루프에 빠질 수 있다
- DFS는 두 정점 사이의 최단 경로를 찾으려는 경우 사용하기에 가장 좋은 알고리즘은 아닐 수 있다.

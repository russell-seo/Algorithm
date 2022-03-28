 
 
 # 자바 런타임 메모리 구조 및 과정
 
 
   ## JVM (Java Virtual Machine)
   
   - 자바 가상 머신으로 자바 바이트코드를 실행할 수 있는 주체다.
     
     - CPU나 운영체제의 종류와 무관하게 실행이 가능하다. 즉 운영체제 위에서 동작하는 프로세스로 `자바 코드를 컴파일해서 얻은 바이트 코드를 해당 운영체제가 이해할 수 있는 기계어로 바꿔 실행시켜주는 역할`
     - JVM 구성을 살펴보면 크게 4가지(Class Loader, Execution Engine, Garbage Collector, Runtime Data Area)로 나뉜다.

   ![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=http%3A%2F%2Fcfile22.uf.tistory.com%2Fimage%2F9973563D5ACE0315215FF6)
   
   
   ## Class Loader
   
   - 자바에서 소스를 작성하면 Person.java 처럼 .java 파일이 생성된다.
   - .java 소스를 자바 컴파일러가 컴파일 하면 Person.class 같은 .class파일(바이트코드)이 생서된다.
   - 이렇게 생서된 클래스 파일들을 엮어서 JVM이 운영체제로 부터 할당받은 메모리영역인 `Runtime Data Area`로 적재하는 역할을 Class Loader가 한다.(자바 어플리케이션이 실행주 일때 이런 작업이 수행)
  
  
  ## Execution Engine
  
  - Class Loader에 의해 `메모리에 적재된 클래스(바이트 코드)들을 기계어로 변경해 명령어 단위로 실행하는 역할` 을 한다.
  - 명령어를 하나하나 실행하는 Interpreter(인터프리터) 방식이 있고, JIT(Just-In-Time) 컴파일러를 이용하는 방식이 있다.
  - JIT 컴파일러는 적절한 시간에 전체 바이트 코드를 네이티브 코드로 변경해 Execution Engine이 네이티브로 컴파일된 코드를 실행하는 것으로 성능을 높이는 방식이다.
  
  
  ## Garbage Collector
  
  - Garbage Collector(GC)는 Heap 메모리 영역에 생성(적재) 된 객체들 중에 `참조되지 않는 객체들을 탐색 후 제거하는 역할`을 한다.
  - GC가 역할을 하는 시간은 정확히 언제인지를 알 수 없다.(참조가 없어지자마자 해제되는 것을 보장하지 않음)
  - 또 다른 특징은 GC가 수행되는 동안 GC를 수행하는 쓰레드가 아닌 다른 모든 쓰레드가 일시정지된다.
  - 특히 Full GC가 일어나서 수 초간 모든 쓰레드가 정지한다면 장애로 이어지는 치명적인 문제가 생길 수 있는 것이다.

  ## Heap Area & Garbage Collector
  
  - Heap(힙) 영역은 좀 더 살펴봐야 하는 이유는 GC의 주요대상이기 때문(Stack, Method 영역)
  - Heap 영역은 5개의 영역(eden, survivor1, survivor2, old, permanent)로 나뉜다.
  - Heap 영역을 굳이 5개로 나눈 이유는 효율적으로 GC가 일어나게 하기 위함이다.
  - GC는 Minor GC와 Major GC로 나뉜다.
  
        - Minor GC : New 영역에서 일어나는 GC
              - 최초에 객체가 생성되면 Eden 영역에 생성된다.
              - Eden 영역에 객체가 가득차게 되면 첫 번째 GC가 일어난다.
              - survivor1 영역에 Eden 영역의 메모리를 그대로 복사된다. 그리고 survivor1 영역을 제외한 다른 영역의 객체를 제거한다.
              - Eden 영역도 가득차고 survivor1 영역도 가득차게 된다면, Eden 영역에 생성된 객체와 survivor1영역에 생성된 객체 중에 참조되고 있는 객체가 있는지 검사한다.
              - 참조 되고 있지 않은 객체는 내버려두고 참조되고 있는 객체만 survivor2영역에 복사한다.
              - survivor2영역을 제외한 다른 영역의 객체들을 제거한다.
              - 위의 과정중에 일정 횟수 이상 참조되고 있는 객체들을 survivor2에서 old 영역으로 이동시킨다.
              - 위 과정을 계속 반복, survivor2 영역까지 꽉 차기 전에 계속해서 old로 비움
              
  - Major GC(Full GC) : Old 영역에서 일어나는 GC
      - `old 영역에 있는 모든 객체들을 검사하며 참조되고 있는지 확인한다.`
      - 참조되지 않은 객체들을 모아 한 번에 제거한다.
          - Minor GC보다 시간이 훨씬 많이 걸리고 실행중에 GC를 제외한 모든 쓰레드가 중지된다.
      - Major GC 가 일어나면 Old 영역에 있는 참조가 없는 객체들을 표시하고 그 객체들을 모두 제거한다.
          - 그러면서 Heap 메모리 영역에 중간중간 구멍이 생기는데 이 부분을 없애기 위해 재구성을 하게 된다. 따라서 메모리를 옮기고 있는데 다른 쓰레드가 메모리를 사용해버리면 안되기 떄문에 모든 쓰레드가 정지하게 된다.


## JAVA 의 메모리 구조 

  - 개발자로서 컴공 지식은 하루하루 써 내려가야 할 지식 이라고 생각하여 이 글을 기록하기 시작했다.




  ### Class Path
  
  - 자바 가상머신(JVM)이 프로그램을 실행 할 떄, 클래스 파일을 찾는 데 기준이 되는 파일 경로, 즉 JVM이 클래스 파일을 찾는 경로.
  
  - bin 은 자바소스(.java 파일)가 컴파일 되어 새롭게 생성되는 .class 파일이 모여 있는 곳 이다.
    그것들이 모여 있는 위치가 'bin' 폴더
    
    
  
  ### 메모리 구조
  
  - JVM(자바 가상머신)이 실행되면 OS 가 JVM에게 필요한 메모리를 할당 해준다.

  - 컴퓨터 프로그램이 실행 되기 위해 필요한 메모리를 '메인 메모리' 라고 한다. 우리말로는 주기억장치, 물리족으로는 램(RAM)이라고 부르는 놈이다.
  
    이 RAM인 메인메모리를 관리하는게 OS 이고, JVM은 OS로 부터 필요한 만큼 할당을 받는다.
    
    OS로 부터 받은 메모리 공간을 `RUntime Data Area` 라고 하는데 이 ARea를 5개 영역으로 쪼개어 관리 한다.
    
    
 ### Runtime Data Area
 
 아래 5개의 목록으로 나누어 진다.
 
  - Class Area(=Method Area)
  - Stack Area
  - Heap Area
  - Native Method Stack Area
  - PC Register

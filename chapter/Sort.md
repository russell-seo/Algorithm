# 선택정렬

- 선택 정렬은 이름에 맞게 현재 위치에 들어갈 값을 찾아 정렬하는 배열이다.
- 최소 선택 정렬은 오름차순 으로 정렬, 최대 선텩 정렬은 내림차순으로 정렬

- 정렬 되지 않은 인덱스의 맨 앞에서 부터, 이를 포함한 그 이후의 배열 값 중 가장 작은 값을 찾아간다.
- 가장 작은 값을 찾으면, 그 값을 현재 인덱스의 값과 바꿔준다.
- 시간 복잡도는 O(n^2) 이다, 공간복잡도는 O(n)

~~~java

public void sort(){
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] a = new int[n];

        for (int i=0; i<a.length; i++){
            int x = sc.nextInt();
            a[i] = x;
        }

        //13 5 11 7 23 15
        // 0 1 2 3 4 5
        for(int i=0; i<n; i++){
            int m = i;
            for(int j=i+1; j<n; j++){
                if(a[i] > a[j]){
                    m = j;
                }
            }
            int l = a[i];
            a[i] = a[m];
            a[m] = l;
        }

~~~



# 버블정렬

- 버블 정렬은 매번 연속된 두개 인덱스를 비교하여, 정한 기준의 값을 뒤로 넘겨 정렬하는 방법
- 오름 차순이면 매 인덱스 비교 시 가장 큰 값이 맨 뒤로 이동한다. 즉 n 크기의 배열에서 0 인덱스 일때 가장 큰 값이 n 인덱스에 위치하게 된다.
- 전체 배열의 크기 - 현재 순환한 바퀴 수 만큼 반복
- 시간복잡도는 O(n^2), 공간복잡도 O(n)

~~~java

int [] arr = new int[n];

for(int i=0; i<n-1; i++){
    for(int j=0; j<n-i-1; j++){
      if(arr[j] > arr[j+1]){
         int tmp = a[j];
         a[j] = a[j+1];
         a[j+1] = tmp; 
      }    
   }
}



~~~ 

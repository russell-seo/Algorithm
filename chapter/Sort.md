# 선택정렬

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

- 버블 정렬은 

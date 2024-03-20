
# 피보나치 수열

`피보나치 수열` 이란?

- 이 전 두항의 합이 다음 항의 합이 되는 수열을 의미한다. 즉 첫째 항과 둘째 항이 1이고 이후 모든 항은 바로 앞 두항의 합으로 이루어지는 수열

![image](https://github.com/russell-seo/Algorithm/assets/79154652/c63f6855-5430-413c-96ef-f42111a88b8b)


## 피보나치 수열 계산식
> 피보나치 수열 계산식은
> 
> F(0) = 0, F(1) = 1 일때
> 
> F[n] = F(n-1) + F(n-2) 이다.
> 
> 즉 n번째 항은 n-1 번째 항과 n-2번째 항을 더한 값이 된다.


즉 피보나치 수열은 재귀함수로 나타낼 수 있으며 아래 코드와 같이 표현된다.

~~~java

public int pibonaci(int n){
  if(n==1) return 1;
  else if(n==2) return 1;
  else return pibonaci(n-2) + pibonaci(n-1); 
}

~~~

하지만 피보나치 수열은 n의 수가 커질수록 엄청 느리며 시간복잡도는 O(2^n) 이다.

그렇기에 DP(Dynamic Programming)을 사용하여 TOP-DOWN, BOTTOM-UP 두가지 방식을 사용한다.


## DP

DP(Dynamic Programming)은 복잡한 문제를 간단한 여러 개의 문제로 나누어 푸는 방법을 말한다.

DP는 큰문제를 작은 문제로 분할 가능해야 하며, 작은 문제에서 구한 정답이 그것을 포함하는 큰 문제에서도 동일해야 한다.

위의 피보나치 수열을 DP로 풀어볼려고 한다.

TOP-DOWN

~~~java

int[] dps = new int[100];

int DP(int n){
        if(n == 1) return 1;

        if(n == 2) return 2;

        if(dps[n] != 0){
            return dps[n];
        }
        
        return dps[n] = DP(n-2) + DP(n-1);
    }

~~~

BOTTOM-UP

~~~java
int [] dps = new int[100];

int DP(int n){
  dps[0] = 1;
  dps[1] = 2;

  for(int i=2; i<n; i++){
    dp[i] = dp[n-1] + dp[n-2];
  }

  return dps[n-1];

}

~~~

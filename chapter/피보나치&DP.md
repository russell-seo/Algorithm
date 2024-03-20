
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





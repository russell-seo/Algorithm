# 가중치 랜덤 알고리즘

알고리즘 자체는 매우 단순하다.

  1. 주어진 데이터를 가중치의 오름차순으로 정렬

  2. 랜덤 기준값을 정하고, 정렬된 데이터를 순회하며 각 가중치를 누적하다가 기준값 이상이 되면 종료





## 설명


아래의 예시를 바탕으로 그림과 코드를 통해 살펴보자


![image](https://github.com/russell-seo/CodingTest/assets/79154652/87d7d4ff-4b2b-4499-8e7b-aa9546ba36a1)



​

2-1. 주어진 데이터를 가중치의 오름차순으로 정렬

​![image](https://github.com/russell-seo/CodingTest/assets/79154652/3d9c2a6d-2899-474b-9a59-667d4aaee275)


우선 데이터의 가중치를 백분율로 평준화를 시켜준 뒤, 가중치의 오름차순으로 정렬한다.


가중치 평준화 -> 가중치의 오름차순 정렬


~~~java
class WeightedRandom {
    private final List<Pair<String, Double>> candidates;

    public WeightedRandom(List<Pair<String, Integer>> target) {
        // 1. 총 가중치 합 계산
        double totalWeight = 0;
        for (Pair<String, Integer> pair : target) {
            totalWeight += pair.weight;
        }

        // 2. 주어진 가중치를 백분율로 치환 (가중치 / 총 가중치)
        List<Pair<String, Double>> candidates = new ArrayList<>();
        for (Pair<String, Integer> pair : target) {
            candidates.add(new Pair<>(pair.word, pair.weight / totalWeight));
        }

        // 3. 가중치의 오름차순으로 정렬
        candidates.sort(Comparator.comparingDouble(p -> p.weight));
        this.candidates = candidates;
    }
}

~~~


2-2. 랜덤 기준값 이상이 될 때 까지 정렬된 데이터를 순회하며 가중치 누적


![image](https://github.com/russell-seo/CodingTest/assets/79154652/adaa79c7-6c86-4b78-8080-fd263fd0ea91)



이제 랜덤 기준값을 정한다. 본 예시에선 0.4로 선정하였다.

![image](https://github.com/russell-seo/CodingTest/assets/79154652/aa80ee6a-0779-4e87-a4e8-7efc4a105f55)

그 다음으론 정렬된 데이터를 순회하며 가중치를 누적하다가 기준치 이상이 되는 값을 선택하면 된다.


![image](https://github.com/russell-seo/CodingTest/assets/79154652/51bc0425-3413-4874-b02a-20ef6d2d196c)


~~~java
class WeightedRandom {
    private final List<Pair<String, Double>> candidates;

    public String getRandom() {
        // 1. 랜덤 기준점 설정
        final double pivot = Math.random();

        // 2. 가중치의 오름차순으로 원소들을 순회하며 가중치를 누적
        double acc = 0;
        for (Pair<String, Double> pair : candidates) {
            acc += pair.weight;

            // 3. 누적 가중치 값이 기준점 이상이면 종료
            if (pivot <= acc) {
                return pair.word;
            }
        }

        return null;
    }
}
~~~


### 검증

~~~java
public class WeightedRandomTest {
    public static void main(String[] args) {
        List<Pair<String, Integer>> target = Arrays.asList(
                new Pair<>("Microsoft", 4),
                new Pair<>("Apple", 2),
                new Pair<>("Google", 9),
                new Pair<>("Amazon", 5)
        );

        WeightedRandom random = new WeightedRandom(target);

        // 1만번 랜덤 추출 테스트
        int count = 10000;
        Map<String, Integer> wordCount = new HashMap<>();
        for (int i = 0; i < count; i++) {
            String word = random.getRandom();
            wordCount.put(word, 1 + wordCount.getOrDefault(word, 0));
        }

        for (Entry<String, Integer> e : wordCount.entrySet()) {
            System.out.printf("%s 등장 확률 : %.2f\n", e.getKey(), (double) e.getValue() / (double) count);
        }
    }
}
~~~

# Best Time to Buy and Sell Stock II


You are given an integer array `prices` where `prices[i]` is the price of a given stock on the `ith` day.

On each day, you may decide to buy and/or sell the stock. You can only hold **at most one** share of the stock at any time. However, you can buy it then immediately sell it on the **same day**.

Find and return _the **maximum** profit you can achieve_.

**Example 1:**

**Input:** prices = [7,1,5,3,6,4]<br>
**Output:** 7<br>
**Explanation:** Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.<br>
Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.<br>
Total profit is 4 + 3 = 7.

**Example 2:**

**Input:** prices = [1,2,3,4,5]<br>
**Output:** 4<br>
**Explanation:** Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.<br>
Total profit is 4.<br>

**Example 3:**

**Input:** prices = [7,6,4,3,1]<br>
**Output:** 0<br>
**Explanation:** There is no way to make a positive profit, so we never buy the stock to achieve the maximum profit of 0.

**Constraints:**

- `1 <= prices.length <= 3 * 104`
- `0 <= prices[i] <= 104`



## 풀이

```php
class Solution {

  /**
   * @param Integer[] $prices
   * @return Integer
   */
  function maxProfit($prices) {
    $wallet = 0;
    
    for($i = 0; $i < count($prices)-1; $i++){
      if($prices[$i] < $prices[$i+1]){
        $wallet += ($prices[$i+1] - $prices[$i]);
      }
    }
    return $wallet;
  }
}
```

시간복잡도 : O(n)
공간복잡도 : O(1)

시간복잡도는, for 루프 안에서 비교연산이 n-1만큼 작동한다 이를통해 n이 추론됨  
공간복잡도는 처음에 wallet에 할당되는거가 n-1만큼 반복되니까 n인가 생각했다가 하나의 변수에 반복적으로 할당되는거면 1인가 해서 chatgpt에 물어봤는데 O(1)이란다.

가장 효율적으로 많은 이익을 내려면 각각의 경우의수를 다 따져가면서 가장 많은 이익을 내는 루트를 찾는 형태가 되야할거 같은데, 잠깐만 생각해도 너무 복잡하다. 결국은 인접한 가격만 확인해서 흑자면 플러스 해주고 아니면 그 인접한 녀석을 다시 기준으로 다시 인접한 녀석과 비교하는식으로 진행했다. 어제 버블소트 했던거랑 비슷하게 인접한 녀석끼리 비교하는식이 되었다.

빡세다....... 두시간 이상 잡아먹은거 같은데 문제도 첨에 감이 안잡히고 풀면서도 이게 맞나, 문제가 그게 맞나,, 이렇게 해도되나 이런식이었던 것 같다.

지금은 문제를 풀고서 불필요한 부분을 좀 줄여놓은 상태여서 짧은데, 그 전에는 더 길었고 불필요한 연산이나 변수들이 있었다.
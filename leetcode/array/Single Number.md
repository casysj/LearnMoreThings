# Single Number

Given a **non-empty** array of integers `nums`, every element appears _twice_ except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.

**Example 1:**

**Input:** nums = [2,2,1]<br>
**Output:** 1

**Example 2:**

**Input:** nums = [4,1,2,1,2]<br>
**Output:** 4

**Example 3:**

**Input:** nums = [1]<br>
**Output:** 1

**Constraints:**

- `1 <= nums.length <= 3 * 104`
- `-3 * 104 <= nums[i] <= 3 * 104`
- Each element in the array appears twice except for one element which appears only once.

## 풀이

```php
class Solution {
    /**
     * @param Integer[] $nums
     * @return Integer
     */
    function singleNumber($nums) {
      $result = 0;
      foreach($nums as $val){
        $result ^= $val;
      }
      return $result;
    }
}
```
### 복잡도

시간복잡도 O(n)  
공간복잡도 O(1)  

### 해설

비트연산에 대해 전혀 생각지도 못해서 고생했다.  
해결책은 XOR을 사용하는 방법이다.

**XOR 성질**  
a ^ b ^ c = a ^ c ^ b  
xor연산은 순서를 바꿔도 같은 결과가 나옵니다.  
  
a ^ a = 0  
자기자신과 xor연산을 하면 0이 됩니다.  
  
a ^ 0 = a  
0과 xor하면 자기자신이 나옵니다.

교환법칙에 아무래도 핵심으로 보인다.  
같은 값을 XOR연산을 해주면 0이 되고 이어서 그 다음숫자와 XOR을 해주면 그 다음숫자가 나온다.  
결국 수많은 수의 조합이지만 교환법칙에 의해서 짝을 이루는 수를 모두 0으로 만들어줄 수 있고  
결국에는 하나만 남은 숫자가 결과로 나오게 되는것이다.  
어메이징..
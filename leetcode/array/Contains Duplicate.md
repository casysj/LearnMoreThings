# Contains Duplicate

Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.

**Example 1:**

**Input:** nums = [1,2,3,1]<br>
**Output:** true

**Example 2:**

**Input:** nums = [1,2,3,4]<br>
**Output:** false

**Example 3:**

**Input:** nums = [1,1,1,3,3,4,3,2,4,2]<br>
**Output:** true

**Constraints:**

- `1 <= nums.length <= 105`
- `-109 <= nums[i] <= 109`

## 풀이

```php
class Solution {

    /**
     * @param Integer[] $nums
     * @return Boolean
     */
    function containsDuplicate($nums) {
      $isTrue = [];
      foreach($nums as $val){
        if($isTrue[$val] === true){
          return true;
        } else {
          $isTrue[$val] = true;
        }
      }
      return false;
    }
}
```

시간 복잡도 O(n)  
공간 복잡도 O(1)

해시테이블을 이용하면 간단하게 해결!
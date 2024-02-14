# Rotate Array

Given an integer array `nums`, rotate the array to the right by `k` steps, where `k` is non-negative.

**Example 1:**

**Input:** nums = [1,2,3,4,5,6,7], k = 3<br>
**Output:** [5,6,7,1,2,3,4]<br>
**Explanation:**<br>
rotate 1 steps to the right: [7,1,2,3,4,5,6]<br>
rotate 2 steps to the right: [6,7,1,2,3,4,5]<br>
rotate 3 steps to the right: [5,6,7,1,2,3,4]

**Example 2:**

**Input:** nums = [-1,-100,3,99], k = 2<br>
**Output:** [3,99,-1,-100]<br>
**Explanation:** <br>
rotate 1 steps to the right: [99,-1,-100,3]<br>
rotate 2 steps to the right: [3,99,-1,-100]

**Constraints:**

- `1 <= nums.length <= 105`<br>
- `-231 <= nums[i] <= 231 - 1`<br>
- `0 <= k <= 105`

**Follow up:**

- Try to come up with as many solutions as you can. There are at least **three** different ways to solve this problem.
- Could you do it in-place with `O(1)` extra space?

## 풀이

```php
class Solution {

    /**
     * @param Integer[] $nums
     * @param Integer $k
     * @return NULL
     */
    function rotate(&$nums, $k) {
      $k %= count($nums);
      if ($k === 0){
        return NULL;
      }
      $rotateArr = [];
      for($i = count($nums)-1; $i > count($nums)-1-$k ; $i--){
        $rotateArr[] = $nums[$i];
      }
      
      for($i = count($nums)-1-$k; $i >= 0 ; $i--){
        $nums[$i+$k] = $nums[$i];
      }
      
      for($i = 0; $i < $k; $i++){
        $nums[$k-1-$i] = $rotateArr[$i];
      }
        
    }
}
```

시간복잡도 : O(n)으로 추정한다. $nums의 배열의 크기에 비례해서 for loop가 반복될 수 있기 때문이다.  
공간복잡도 : O(1)이라고 chatgpt가 그런다. rotateArr 부분이 어떻게 될지 궁금했는데 $nums에 비례해서 rotateArr의 크기가 증가하는게 아니다. $k 값에따라 변동이 있을뿐이다.


최대한 내장함수 없이 구현해보고 싶었다. 근데 내장함수를 쓰고 싶었어도 머릿속에 갖고 있는게 없어서 난감했다. 담번에 내장함수를 활용한 부분도 생각해보겠다.

일단 $k에 의해 이동하는 만큼을 배열 뒤부터 잘라내서 새 배열에 저장해두고서  
나머지 부분을 배열의 끝부분으로 하나씩 이동시켰다.  
그리고 잘라낸 부분을 원래 배열 앞쪽에 하나씩 넣어주는식으로 풀었다.
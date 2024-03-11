# Intersection of Two Arrays II

Given two integer arrays `nums1` and `nums2`, return _an array of their intersection_. Each element in the result must appear as many times as it shows in both arrays and you may return the result in **any order**.

**Example 1:**

**Input:** nums1 = [1,2,2,1], nums2 = [2,2]  
**Output:** [2,2]

**Example 2:**

**Input:** nums1 = [4,9,5], nums2 = [9,4,9,8,4]  
**Output:** [4,9]  
**Explanation:** [9,4] is also accepted.

**Constraints:**

- `1 <= nums1.length, nums2.length <= 1000`
- `0 <= nums1[i], nums2[i] <= 1000`

**Follow up:**

- What if the given array is already sorted? How would you optimize your algorithm?
- What if `nums1`'s size is small compared to `nums2`'s size? Which algorithm is better?
- What if elements of `nums2` are stored on disk, and the memory is limited such that you cannot load all elements into the memory at once?


## 풀이

```php
class Solution {

  /**
   * @param Integer[] $nums1
   * @param Integer[] $nums2
   * @return Integer[]
   */
  function intersect($nums1, $nums2) {
    $hashTable2 = [];

    foreach($nums2 as $num){
      $hashTable2[$num]++;
    }

    $result = [];

    foreach($nums1 as $num1) {
      if(isset($hashTable2[$num1]) && $hashTable2[$num1] >0){
        $result[] = $num1;
        $hashTable2[$num1]--;
      }
    }
    return $result;
  }
```

시간 복잡도: O(m+n)
공간 복잡도: O(m+n)

한쪽 배열을 해시테이블로 만든다. 배열의 값을 해시테이블의 키로 사용하고 값이 몇번 나왔는지 세서 해시테이블의 값으로 넣어준다.<br>
이후에 다른 하나의 배열을 반복문으로 돌아가면서 해당 값을 해시테이블에서 조회해보고 값이 남아있는 경우에 이를 결과배열에 푸시해준다.

## 추가

```php
class Solution {

  /**
   * @param Integer[] $nums1
   * @param Integer[] $nums2
   * @return Integer[]
   */
  function intersect($nums1, $nums2) {
	if(count($nums1) < count($nums2)){
	  $this->intersect($nums2,$nums1);
	}
    $hashTable2 = [];

    foreach($nums2 as $num){
      $hashTable2[$num]++;
    }

    $result = [];

    foreach($nums1 as $num1) {
      if(isset($hashTable2[$num1]) && $hashTable2[$num1] >0){
        $result[] = $num1;
        $hashTable2[$num1]--;
      }
    }
    return $result;
  }
```

리트코드 디스커션에서 살펴본것인데 위와같은 접근법으로 두 매개변수의 길이를 비교해서 길이가 더 작은 변수를 두번째 매개변수로 넣어주면 공간복잡도를 O(n)으로 만들 수 있다. 좀 더 보편적으로 표현하면 O(min(m,n))이 되겠다.
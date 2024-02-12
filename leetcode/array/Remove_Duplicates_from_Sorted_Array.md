# Remove Duplicates from Sorted Array

Given an integer array `nums` sorted in **non-decreasing order**, remove the duplicates [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) such that each unique element appears only **once**. The **relative order** of the elements should be kept the **same**. Then return _the number of unique elements in_ `nums`.

Consider the number of unique elements of `nums` to be `k`, to get accepted, you need to do the following things:

- Change the array `nums` such that the first `k` elements of `nums` contain the unique elements in the order they were present in `nums` initially. The remaining elements of `nums` are not important as well as the size of `nums`.
- Return `k`.

**Custom Judge:**

The judge will test your solution with the following code:

int[] nums = [...]; // Input array
int[] expectedNums = [...]; // The expected answer with correct length

int k = removeDuplicates(nums); // Calls your implementation

assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}

If all assertions pass, then your solution will be **accepted**.

**Example 1:**

**Input:** nums = [1,1,2]
**Output:** 2, nums = [1,2,_]
**Explanation:** Your function should return k = 2, with the first two elements of nums being 1 and 2 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).

**Example 2:**

**Input:** nums = [0,0,1,1,1,2,2,3,3,4]
**Output:** 5, nums = [0,1,2,3,4,_,_,_,_,_]
**Explanation:** Your function should return k = 5, with the first five elements of nums being 0, 1, 2, 3, and 4 respectively.
It does not matter what you leave beyond the returned k (hence they are underscores).

**Constraints:**

- `1 <= nums.length <= 3 * 104`
- `-100 <= nums[i] <= 100`
- `nums` is sorted in **non-decreasing** order.



## code
```php
class Solution {
	/**
	 * @param Integer[] $nums
	 * @return Integer
	 */
	function removeDuplicates(&$nums) {
		$idx = 0;
		while($idx < (count($nums)-1)) {
			$uniqueVal = $nums[$idx];
			while($nums[$idx+1] === $uniqueVal){
				array_splice($nums,$idx+1,1);
			}
			
			$idx++;
		}
	}
}
```

생각보다 시간이 오래걸렸다.
```php
while($nums[$idx+1] === $uniqueVal){
	array_splice($nums,$idx+1,1);
}
```
`===`를 쓰느냐 `==` 를 쓰느냐에 따라 결과가 달라졌다.  
예를들어 `0 == null` 이 true를 반환하는데 인덱스가 배열의 범위를 벗어나서 `while`이 계속 true를 반환하게되면 문제가 생긴다

`unset`과 `array_splice`의 차이도 어느정도 알게 되었다.
unset은 배열을 재정렬하지 않고 array_splice는 배열을 재정렬한다.
재정렬된다는게 인덱스가 다시 정렬된다는 의미이다.

# Plus One
You are given a **large integer** represented as an integer array `digits`, where each `digits[i]` is the `ith` digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading `0`'s.

Increment the large integer by one and return _the resulting array of digits_.

**Example 1:**

**Input:** digits = [1,2,3]<br>
**Output:** [1,2,4]<br>
**Explanation:** The array represents the integer 123.<br>
Incrementing by one gives 123 + 1 = 124.<br>
Thus, the result should be [1,2,4].

**Example 2:**

**Input:** digits = [4,3,2,1]<br>
**Output:** [4,3,2,2]<br>
**Explanation:** The array represents the integer 4321.<br>
Incrementing by one gives 4321 + 1 = 4322.<br>
Thus, the result should be [4,3,2,2].

**Example 3:**

**Input:** digits = [9]<br>
**Output:** [1,0]<br>
**Explanation:** The array represents the integer 9.<br>
Incrementing by one gives 9 + 1 = 10.<br>
Thus, the result should be [1,0].

**Constraints:**

- `1 <= digits.length <= 100`
- `0 <= digits[i] <= 9`
- `digits` does not contain any leading `0`'s.



# 풀이
```php
function plusOne($digits) {
	$digits = array_reverse($digits);
	foreach($digits as $idx => &$digit){
	  if($idx === 0){
		$digit++;
	  }
	  
	  if(isset($digits[$idx-1]) && $digits[$idx-1] === 10){
		$digits[$idx-1] = 0;
		$digit++;
	  }
	  
	  if($idx === array_key_last($digits) && $digit === 10){
		$digit = 0;
		array_push($digits,1);
	  }
	}
	
	return array_reverse($digits);
}
```

시간 복잡도 : O(n)
공간 복잡도 : O(1)

처음에는 매개변수로 들어오는 배열의 맨 끝자리부터 시작해서 처음 인덱스까지 진행하며 첫 1을 더하고 이후에 올림이 발생하면 수를 더하는 형태로 진행했다.

그리고 맨 마지막에는 array_unshift를 사용해 올림이 있을경우 1를 추가해주는 형태로 했다.

이후에 위와같이 바꿔서 했는데 정확하진 않지만 이전 방법이 조금 더 속도가 빠른편인가 싶다.
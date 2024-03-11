# Datastructure : Array

lookup O(1)
push O(1)
insertion O(n)
delete O(n)

unshift O(n)
이거는 배열의 처음에 새로운 데이터를 추가하는건데 새로 추가하면서 뒤에 있는 배열의 요소들을 하나씩 민다. 이럴경우 모든 요소를 방문해 밀어주는 모양이 되어서 빅오 n이다

## static array and dynamic array
메모리 할당이 동적이냐 고정이냐의 얘기.
배열의 크기가 고정되어있거나 동적으로 조정이 되느냐.
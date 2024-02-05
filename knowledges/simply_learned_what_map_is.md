
오늘은 Map이라는 자료구조 내지 js의 Map에 대해 조금 살펴보자. (30분 컷 작성을 위해 최소한의 정보만 씀..)
이 주제는 어제 다뤘던 문제에서 사용된 map에서 비롯되었다.

```
const mapA = new Map(arrA.map(obj => [obj.key, obj]));
```

js코드이다
여기서 살펴볼 것은 Map 생성자와
Array.map() 함수다.

##### Map 자료구조
map은 기본적으로 Key-Value 가 한 쌍을 이뤄서 저장되는 구조다
여기서 key는 중복되지 않고 고유한 값을 가진다.
배열은 순차적으로 데이터를 불러올 수 있으나 map은 key값을 사용해 value를 불러올 수 있다.

위 js의 Map() 생성자의 인자는 iterable이 들어간다.
그리고 key-value가 짝을이루어진 값을 받아서 구조를 만들어낸다

```
const myMap = new Map([
  [1, "one"],
  [2, "two"],
  [3, "three"],
]);
```

위 사용법을 보면 2차 배열구조로서 2차 배열들이 두개의 값을 갖고 있다. 그리고 이 값이 각각 key와 value로 할당이 된다.

```
arrA.map(obj => [obj.key, obj])
```

이를통해 위 map() 함수가 무엇을 만들어내는지 얼추 감을 잡을 수 있는데

```
[
  [obj.key, obj],
  [obj.key, obj],
  [obj.key, obj],
]
```

이런 모양으로 배열이 생성이된다.

##### Array.prototype.map()
>The **`map()`** method of [`Array`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array) instances creates a new array populated with the results of calling a provided function on every element in the calling array.

mdn에서 찾아보면 map함수의 설명이 이렇다.
해당 배열의 모든 값들을 사용해 만들어진 반환값들을 모아서 **새로운 배열을 만든다**

정리를 해보자면.
map함수를 사용해서 2차 배열을 만든다.
그리고 이 2차배열이 Map 생성자를 통해서 새로운 map 구조를 만들어내는데
그 key와 value들은 2차배열을 만들때 규격에 맞게 작성해준것이다.

내가 작성해야하는 실전에서의 데이터 모습은 대략

```
Map {
  1 => { key: 1, value: obj1 },
  2 => { key: 2, value: obj2 },
  3 => { key: 3, value: obj3 }
}
```

이런 모양새가 된다.

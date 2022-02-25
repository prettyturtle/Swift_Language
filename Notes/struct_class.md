# struct VS class

### 구조체와 클래스의 비슷한점

- 프로퍼티, 메서드를 정의할 수 있다.
- 구조체와 클래스가 갖는 값에 접근하기 위해 서브스크립트 문법으로 정의할 수 있다.
- 초기화 될 때의 상태를 지정하기 위해 이니셜라이저를 정의할 수 있다.
- extension으로 확장하여 기능을 추가할 수 있다.
- 특정 기능을 실행하기 위해 특정 프로토콜을 준수할 수 있다.

### 구조체와 클래스의 차이점

- 구조체는 상속할 수 없다.
- 타입캐스팅은 클래스의 인스턴스에만 허용된다.
- 디이니셜라이저는 클래스의 인스턴스에만 활용할 수 있다.
- 참조 횟수 계산(Reference Counting)은 클래스의 인스턴스에만 적용된다.

---

### 구조체는 값 타입, 클래스는 참조 타입이다

```swift
// 구조체, 클래스 정의
struct StructPerson {
    var name: String
    var age: Int
}
class ClassPerson {
    var name: String
    var age: Int
    
    // 이니셜라이저
    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }
}

// A는 StructPerson이라는 구조체를 할당받았다.
// B는 A를 할당받았다.
var A = StructPerson(name: "A", age: 1)
var B = A

// B의 나이를 바꿔본다
B.age = 100

// A, B의 나이를 출력해보면 
print(A.age) // 1
print(B.age) // 100
// 라고 나오는데 B는 A를 할당받았지만
// 구조체는 값 타입이므로 값이 복사되어 A와는 다른 값을 같는다

// C는 ClassPerson이라는 클래스를 할당받았다.
// D는 C를 할당받았다.
var C = ClassPerson(name: "C", age: 3)
var D = C

// D의 나이를 바꿔본다
D.age = 200
    
// C, D의 나이를 출력해보면
print(C.age) // 200
print(D.age) // 200

// 아까와는 다르게 동일한 값이 출력되었다.
// 왜냐하면 클래스는 참조 타입이기 때문에
// C와 D가 참조하는 주소는 같은 것을 알 수 있다.
```

---

### 식별 연산자

- 참조하는 주소가 같은지 아닌지를 확인하는 비교하는 연산자

```swift
class Person {}

let A = Person()
let B = A
let C = Person()

print(A === B) // true
print(B === C) // false
print(C !== A) // true
```

---

### 스위프트의 기본 데이터 타입(String, Int, Bool, Array, Dictionary, Set 등)은 모두 구조체이다

---

### 구조체와 클래스 중 무엇을 사용해야할까?

- 다음 조건 중 하나 이상에 해당된다면 구조체를 사용하는 것을 권장한다
    1. 연관된 간단한 값의 집합을 캡슐화하는 것만이 목적일 때
    2. 캡슐화한 값을 참조하는 것보다 복사하는 것이 합당할 때
    3. 구조체에 저장된 프로퍼티가 값 타입이며 참조하는 것보다 복사하는 것이 합당할 때
    4. 다른 타입으로부터 상속받거나 자신을 상속할 필요가 없을 때
- 위 조건들을 제외한 경우는 클래스를 사용하면 된다

---

### 참고

- 공식문서(한국어): [https://jusung.gitbook.io/the-swift-language-guide/language-guide/09-classes-and-structures](https://jusung.gitbook.io/the-swift-language-guide/language-guide/09-classes-and-structures)
- 야곰 - 스위프트 프로그래밍 3판

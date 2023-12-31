
# C++ 표준 라이브러리

- C 언어의 상위 집합으로 알려짐.
- C 언어의 객체지향 개념을 추가하려는 목적으로 설계했기 때문에 '클래스가 추가된 C 라고 부른다.'
- C++ 은 C 언어 기반을 두르고 있기 때문에 숙련된 C 프로그래머 라면 익숙할 것이다.
- 두 언어에는 차이점 이 있다.
	- C++ 은 1368페이지 정도 달하는 반해
	- C는 274 페이지에 불가하다.

```c++
// C++20 이전 버전에서는 이렇게 사용
#include <iostram>;

// C++20 이후 버전
import <iostream>

int main() {
	std::cout << "Hello, World!" << std::endl;
	return 0;
}

```

---
## 기초

### 주석

- 프로그래머에게 전달하는 메세지이며, 컴파일은 이 부분을 무시합니다.
- C++ 에서 주석은 2가지 방식으로 사용한다. 
	- `//` 슬래시 2개를 연달아 적으면 그 줄은 주석이 되는 방식
	- `/**/` 여러 줄 주석 방식

### 모듈 임포트

- c++ 20 부터 새롭게 추가된 대표적인 기능 중 하나인 **모듈** (module) 이다.
- 모듈은 이전에 **헤더 파일** (header file) 이라 부르던 메커니즘을 완전히 대체한다. 
- 어떤 모듈에 담긴 기능을 사용하고 싶다면 그 모듈을 `import` 문으로 불러오면 된다.
- `import <iostream>;`  iostream 모듈을 불러온다.

### 전처리 지시자

- 현재 사용하는 컴파일러가 아직 C++20 모듈 기능을 지원하지 않는다면 include 전처리 지시자로 변경해야한다.
- C++ 로 작성된 소스 코드를 프로그램으로 만드는 빌드 작업은 3 단계를 거친다.
	- **전처리 단계**에서는 소스 코드에 담긴 메타 정보를 처리한다.
	- **컴파일 단계**에서는 소스 코드를 기계가 읽을 수 있는 객체 파일로 변환한다.
	- **링크 단계**에서는 변환한 여러 객체 파일을 애플리케이션으로 엮는다.

#### 지시자 (디렉티브 directive)

- 전처리기에 전달할 사항을 표현하며, 앞으로 나온 # 문자로 시작한다.
- 헤더 파일의 주 용도는 소스 파일에서 정의할 함수를 선언하는 것이다.
- 이러한 함수 선언은 그 함수의 호출 방식, 매개변수 개수와 타입, 리턴 타입 등을 컴파일러에 알려준다.
- 함수 정의는 실제로 수행할 동작을 작성한다.
- C++ 모듈이 등장하기 전에는 선언문을 주로 확장자가 .h 인 헤더파일에 작성하고, 정의는 확장자가 .cpp 인 소스 파일에 작성했다.
	- 하지만 모듈이 추가되어서 더 이상 선언과 정의를 분리할 필요가 없게 되었다. 


| 전처리 지시자     | 기능                                                                                                                                                                                       | 사용 예시                                                                                                                                                                        |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| #include 파일     | 지정된 파일의 내용을 지시자 위치에 넣는다.                                                                                                                                                 | 다른 곳에 정의된 함수를 사용할 목적으로 해당 함수의 선언문이 담긴 헤더 파일을 가져온다.                                                                                          |
| #define 키 값     | 코드에서 '키' 에 해당하는 부분을 모두 '값' 으로 지정한 내용으로 바꾼다.                                                                                                                    | C 언어에서는 주로 상수값이나 매크로를 정의하는 데 사용되었다. C++ 상수 및 매크로 정의에 대해 좀 더 개선된 메커니즘을 제공한다.메크로는 자칫 위험할 수 있어서 사용할 때 주의한다. |
| #ifdef 키 #endif  | 지정한 '키'가 #define 문으로 정의되어 있으면 #ifdef 로 묶인 코드 블록을 포함시키고 정의가 안되어있으면 포함시키지 않는다.                                                                  | 주로 중복해서 추가되는 것을 막는 용도로 사용한다.                                                                                                                                |
| #ifndef 키 #endif | 지정한 '키'가 #define 문으로 정의되어 있지 않다면 #ifndef 로 묶인 코드 블록을 포함시키고 정의가 되어 있으면 포함시키지 않는다.                                                             |                                                                                                                                                                                  |
| #pragma xyz       | xyz 에 대한 구체적인 동작은 컴파일러 마다 다르다. 대부분의 컴파일러가 #pragma 를 지원하며, 주로 전처리 과정에서 이 지시자에 도달할 때 경고나 에러메세지를 화면에 표시하는 용도로 사용한다. | -                                                                                                                                                                                |

### 네임스페이스

- 코드에서 이름이 서로 충돌하는 문제를 해결하기 위해 나온 개념이다.
```c++
namespace myCode {
	void foo() {
		std::cout << "Foo() Called in the mycode namespace!!" << std::endl;
	}
}
//=================================================//
// 호출 방법 1
int main(int argc, char* argv[]) {
	mycode::foo(); 
}
//=================================================//
using namespace myCode;
// 호출 방법 2
int main(int argc, char* argv[]) {
	foo(); 
}
//=================================================//

```

#### 중첩 네임스페이스

```c++
// C++17 이후
namespace MyLIB::NetWorking::FTP {

}

// C++17 이전
namespace MyLIB {
	namespace NetWorking {
		namespace FTP {
		}
	}
}

```


#### 네임스페이스 앨리어스

- 네임스페이스의 이름을 다르게 만들거나 또는 더 짧게 만들 수 있다.
```c++
namespace MyFTP = MyLIB::NetWorking::FTP;
```



### 리터널

- 코드에 표시한 숫자나 스트링과 같은 값을 의미한다.
- C++는 다양한 표준 리터럴을 제공한다.
	- 십진수 리터럴 : 123
	- 8진수 리터럴 : 0173
	- 16진수 리터럴 0x78
	- 이진수 리터럴 : 0b1111011
- 또한 C++ 에서는 다음과 같은 리터럴을 지원한다.
	- 부동소수점 : 3.14f
	- 배정도 (double) : 3.14
	- 16진수 부동 소수점 : ABCp-10, 0xb.cp121
	- 단일 문자 : 'a'
	- 0으로 끝나는 문자 배열 "character array"

### 변수

- 블록 안에서 변수를 선언한 줄 다음부터 어디에서나 그 변수에 접근할 수 있다.
```c++
int uninitializedInt; // 초기화 안된 변수 
int initalizedInt = 7; // 초기화 선언한 변수
```

| 타입                     | 설명                                                             | 예시                                                       |
| ------------------------ | ---------------------------------------------------------------- | ---------------------------------------------------------- |
| (signed) int             | 4 Byte 정수로 표현                                               | int i {-7};                                                |
| (signed) short (int)     | 작은 범위의 정수 (2Byte)                                         | short s {13}; signed short s {15}; signed short int s {16} |
| (signed) long (int)      | 큰 정수 (4Byte)                                                  | long l {-7L};                                              |
| (signed) long long (int) | 아주 큰 범위의 정수 (8Byte)                                      | long long ll {14LL};                                       |
| unsigned type            | 앞에 나온 정수 타입의 범위를 >= 0 으로 제한                      | unsigned int i {2U};                                       |
| float                    | 부동 소수점 (단정도)                                             | float f {7.2f};                                            |
| double                   | 부동 소수점. 정밀도가 크다. (배정도)                             | double d {7.2};                                            |
| long double              | 부동 소수점. 정밀도가 double 보다 크다                           | long double d {16.98L}                                     |
| char                     | 단일 문자                                                        | char ch {'m'};                                             |
| unsigned char            | 단일 문자                                                        |                                                            |
| char8_t (c++20)          | 단일 n 비트 UTF n 인코딩을 적용한 유니코드 문자(8,16,32 중 하나) | char8_t c8 {u8'm'};                                        |
| char16_t                 | 단일 n 비트 UTF n 인코딩을 적용한 유니코드 문자(8,16,32 중 하나) | char16_t c16 {u'm'};                                       |
| char32_t                 | 단일 n 비트 UTF n 인코딩을 적용한 유니코드 문자(8,16,32 중 하나) | char32_t c32 {U'm'};                                       |
| wchar_t                  | 단일 확장 문자. 구체적인 크기는 컴파일 마다 다르다               | wchar_t w {L'm'};                                          |
| bool                     | 부울 타입으로 true, false 중 하나의 값을 가진다.                 | bool b {true};                                                           |


### 연산자

| 연산자               | 설명                                                            |
| -------------------- | --------------------------------------------------------------- |
| =                    | 오른쪽의 값을 왼쪽 표현식에 대입하는 이항 연산자                |
| !                    | 표현식의 참/거짓 을 반전시키는 단항 연산자                      |
| +                    | 덧셈을 나타내는 이항 연산자                                     |
| - * /                | 뺄셈, 곱셈, 나눗셈                                              |
| %                    | 나눗셈의 나머지 값을 계산하는 이항 연산자                       |
| ++                   | 표현식의 값을 1증가 시키는 단항 연산자                          |
| --                   | 표현식의 값을 1감소 시키는 단항 연산자                          |
| +=, -=, `*=`, /=, %= | 각 항에 대한 축약 표현                                          |
| & &=                 | 양쪽에 나온 표현끼리 비트 단위 AND 수행                         |
| `| |=`               | 양쪽에 나온 표현끼리 비트 단위 OR 수행                          |
| >> << <<= >>=        | 왼쪽에 나온 표현식의 비트값을 오른쪽에 나온 수만큼 시프트 한다. |
| ^ ^=                 | 양쪽에 나온 표현식에 대해 비트 단위 XOR 연산 수행                                                                |


### 열거 타임

- 열거 타입을 사용하면 숫자를 나열하는 방식과 범위를 마음대로 정의해서 변수를 선언하는 데 활용할 수 있다.
```c++
const int PieceTypeKing { 0 };
const int PieceTypeQueen { 1 };

int MyPiece {PieceTypeKing};
```

- 이렇게 표현해도 되지만 자칫 위험한 상황이 발생할 수 있다. 말로 표현하는 myPiece 를 일반값 int 로 표현했기 때문에 다른 프로그래머가 myPiece 값을 증가시키는 코드를 추가하면 어떻게 될까?
	- 킹을 나타내는 값에 1을 더하면 퀸이 되어버려서 체스 게임이 망가진다.
	- 마이너스 값으로 지정하면 심각한 문제가 발생할 수 있다.

#### Strongy typed enumeration type
- 강타입 열거 타입
- 특정 몇가지의 말에 해당하는 값만 가지도록 제한하려면 enum 타입을 정의한다.
```c++
enum class PieceType {King, Queen, Rook, Pawn};

PieceType piece {PieceType::King};

enum class PieceType {
	King = 1,
	Queen,
	Rook = 10,
	Pawn
};
```

- 에러 나올 상황
```c++
if(PieceType::Quene == 2) {...}
```
- 값이 내부적으로 정수로 표현된다고 해서 자동으로 정수로 변환되지 않는다.


79페이지부터 다시 시작
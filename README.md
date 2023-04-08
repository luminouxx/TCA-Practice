# Swift The Composable Architecture

+ [SCA - 공식 깃허브](https://github.com/pointfreeco/swift-composable-architecture)

## The Composable Architecture?

많은 화면 간의 상태를 공유하는 방법을 제공. 

이는 특정 화면의 변화를 다른 화면에서 즉시 관찰할 수 있도록 한다.

### TCA 아키텍처

- Redux 같은 상태관리 방식
- 기타 여러 라이브러리가 있다.

### TCA의 구성

- State:
    
    말 그대로
    
- Action : 도메인 액션
    - 에) 검색이라면 검색어 입력, 검색어 삭제 등
    - 할 일이라면 할 일 삭제, 할일 추가
- Environment:
- Reducer
    
    들어온 액션에 따라 상태를 변화시켜주는 역할
    
- Store
    
    상태, 액션을 가지고 있음 - 커멘드 센터
    

### MVVM과 차이

- MVVM은 따로 관리
- 리덕스 관련 패턴은
    - 스토어에서 종합적으로 관리
    - 액션을 주면 상태를 받는 식

## 사용 예시

---

```swift
// 도메인 상태
struct CounterState: Equatable {
	var count = 0
}
// 도메인 액션
enum CounterAction: Equatable {
	case addCount
	case SubtractCount 
}

struct CounterEnvironment {}

let counterReducer = Reducer<CounterState, CiunterAction, CounterEnvironment> 
{ state, action, environment in
	//들어온 액션에 따라 상태를 변경
	switch action {
	case .addCount:
		state.count += 1
		return Effect.none
	case .subtractCount: 
		state.count -= 1
		return Effect.none
	} 
}

struct CounterView: View {
	let store: Store<CounterState, CounterAction>
	
	var body: some View {
  
	}
}

let exmaple: App {
	let counterStore = Store(initialS  
}
```

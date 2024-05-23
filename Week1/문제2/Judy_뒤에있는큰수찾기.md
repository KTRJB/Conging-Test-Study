```swift
// 시도 1
func solution(_ numbers:[Int]) -> [Int] {
    var numberArray = numbers
    var result: [Int] = []
     
    while !(numberArray.isEmpty) {
        let num = numberArray.removeFirst() // 하나씩 빼기
        let graterNumbers = numberArray.filter { num < $0 } // 큰 값만 남기기
        result.append(graterNumbers.isEmpty ? -1 : graterNumbers.first!) // 가장 가까운 값 or -1
    }
    
    return result
}
// 결과: 7번부터 시간초과

// 시도 2
func solution(_ numbers:[Int]) -> [Int] {
    var numberArray = numbers
    var result: [Int] = []
     
    mainLoop: while !(numberArray.isEmpty) {
        let num = numberArray.removeFirst()
       
        for i in numberArray { // 하나씩 비교하기
            if num < i {
                result.append(i) // 큰값이면 넣고 바로 다음 숫자로 넘어가기
                continue mainLoop
            }
        }
        result.append(-1) // 없으면 -1
    }
    
    return result
}
    
// 14부터 시간초과

// 최종
func solution(_ numbers:[Int]) -> [Int] {
    var numberStack: [(number: Int, index: Int)] = []
    var result: [Int] = Array(repeating: -1, count: numbers.count)
    
    for (index, num) in numbers.enumerated() {
        while let last = numberStack.last, last.number < num { // 현재 스택 최상위보다 큰 수이면
            let popedNumber = numberStack.removeLast() // 스택에서 하나 빼고
            result[popedNumber.index] = num // 숫자 인덱스 위치에 넣기
        }
        
        numberStack.append((number: num, index: index)) // 스택에 인덱스 정보와 함께 넣기
    }
    
    return result
}
// +5
```

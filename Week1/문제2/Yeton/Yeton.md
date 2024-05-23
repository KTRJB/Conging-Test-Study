3. 베스트앨범

```swift

// 2. Lv.2 - 뒤에 있는 큰 수 찾기


### 마지막 4문제 시간초과 ㅠㅠ

func solution(_ numbers:[Int]) -> [Int] {
    var result = [Int]()
    
    for i in 0...numbers.count - 1 {
        var num = 0
        
        while num == 0 {
            if i == numbers.count - 1 {
                num = -1
                break
            }
            
            for j in i+1...numbers.count - 1 {
                if numbers[j] > numbers[i] {
                    num = numbers[j]
                    break
                }
            }
            
            if num == 0 {
                num = -1
            }
        }
        
        result.append(num)
    }
    
    return result
}

print(solution([2, 3, 3, 5]))

### 개선 - stack사용해서 시간복잡도 줄이기

func solution(_ numbers:[Int]) -> [Int] {
    var stack = [0]
    var index = 1
    var result = Array(repeating: -1, count: numbers.count)
    
    while index < numbers.count {
        while !stack.isEmpty && numbers[stack.last!] < numbers[index] {
            ans[stack.popLast()!] = numbers[index]
        }
        
        stack.append(index)
        index += 1
    }
    
    return result
}
```

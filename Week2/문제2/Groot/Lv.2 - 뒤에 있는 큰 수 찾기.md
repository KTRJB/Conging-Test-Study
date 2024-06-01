// 이전에 풀었던 문제라 점수 모름
```swift
import Foundation

func solution(_ s:String) -> Int {
    var array = s.map { String($0) }
    var stack = [String]()
    var count = 0

    // 1부터 총 s.count + 1 만큼 돌면서 확인
    for i in 1..<array.count + 1 {
        var index = i
        stack.removeAll()

        // s.count + 1 같은 인덱스 대응을 위해 % 사용
        while index < array.count + i {
            if stack.isEmpty {
                stack.append(array[index % array.count])
            } else {
                // stack에 차례대로 넣고 성립되면 제거
                let ans = stack.last! + array[index % array.count]
                if ans == "{}" || ans == "()" || ans == "[]" {
                    stack.removeLast()
                } else {
                    stack.append(array[index % array.count])
                }
            }

            index += 1
        }

        // while문이 끝나고 스택이 비어있으면 성립으로 판단

        if stack.isEmpty {
            count += 1
        }
    }

    return count
}
```

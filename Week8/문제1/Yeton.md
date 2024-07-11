// 5점
```swift
func solution(_ cards1:[String], _ cards2:[String], _ goal:[String]) -> String {
    var index1 = 0
    var index2 = 0
    
    for g in goal {
        if g == cards1[index1] {
            if index1 < cards1.count - 1 {
                index1 += 1
            }
        } else if g == cards2[index2] {
            if index2 < cards2.count - 1 {
                index2 += 1
            }
        } else {
            return "No"
        }
    }
    
    return "Yes"
}

print(solution(["a", "b", "c"],  ["d"], ["d", "b"]))

```

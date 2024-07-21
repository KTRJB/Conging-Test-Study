```swift
 1. 대충 만든 자판

import Foundation

func solution(_ keymap:[String], _ targets:[String]) -> [Int] {
  var dic: [Character: Int] = [:]
  var result = Array(repeating: 0, count: targets.count)

  for string in keymap {
    for (i, char) in string.enumerated() {
      dic[char] = min(dic[char] ?? 101, i + 1)
    }
  }

  for (i, str) in targets.enumerated() {
    for char in str {
      guard let count = dic[char] else {
        result[i] = -1
        break
      }
      result[i] += count
    }
  }


  return result
}

print(solution(["ABACD", "BCEFD"], ["ABCD","AABB"]))
print(solution(["AA"], ["B"]))
print(solution(["AGZ", "BSSS"], ["ASA","BGZ"]))
```

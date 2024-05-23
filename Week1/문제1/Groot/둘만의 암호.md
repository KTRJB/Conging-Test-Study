```swift
import Foundation

func solution(_ s:String, _ skip:String, _ index:Int) -> String {
    let str = "abcdefghijklmnopqrstuvwxyz".filter { !skip.contains($0) }.map { String($0) }

    var result = ""

    for string in s {
        let sindex = str.firstIndex(of: String(string))!

        result += str[(sindex + index) % str.count]
    }


    return result
}
```

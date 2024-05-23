1. Lv.1 - 둘만의 암호

```swift
import Foundation

func solution(_ s:String, _ skip:String, _ index:Int) -> String {
  var asciA = Int(UnicodeScalar("a").value)
  var asciZ = Int(UnicodeScalar("z").value)

  // skip할 아스키코드
  let skipArray = skip.map {
    Int(UnicodeScalar(String($0))!.value)
  }

  var result = [String]()
  for i in s { // i = a
    var asci = Int(UnicodeScalar(String(i))!.value) // 65
    var count = 0

    while count < index {
      asci += 1

      if asci > asciZ {
        asci = asciA
      }

      if !skipArray.contains(asci) {
        count += 1
      }
    }

    result.append(String(UnicodeScalar(asci)!))
  }

  return result.reduce("") { $0 + $1 }
}
```

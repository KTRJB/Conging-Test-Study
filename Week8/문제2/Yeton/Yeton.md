```swift
// 2. 의상
// 못 품... 해설 참고 ㅠ
// A의 종류가 N개, B의 종류가 M개 일 때 가능한 모든 경우의 수는 (N+1)(M+1)로 구할 수 있다.

func solution(_ clothes:[[String]]) -> Int {
    var result = 1
    var dict = [String:Int]()
    
    
    for cloth in clothes {
        dict[cloth[1], default: 1] += 1
    }
    
    for x in dict.values {
        result *= x
    }
    
    return result - 1
}

print(solution([["yellow_hat", "headgear"], ["blue_sunglasses", "eyewear"], ["green_turban", "headgear"]]))

// 챗지피티한테 한줄로 고차함수로 바꿔달라 한 코드 ㅋㅋㅋ
//func solution2(_ clothes: [[String]]) -> Int {
//    return clothes.reduce(into: [:]) { $0[$1[1], default: 1] += 1 }
//        .values
//        .reduce(1, *) - 1
//}
```

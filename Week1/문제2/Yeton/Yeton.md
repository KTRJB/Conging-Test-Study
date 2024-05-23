3. 베스트앨범

```swift

func solution(_ genres:[String], _ plays:[Int]) -> [Int] {
    var dics: [String: Int] = [:]
    var playNumByGenres: [String: [Int]] = [:]
    
    for i in 0...genres.count - 1 {
        
        if dics.filter({ $0.key == genres[i] }).count > 0 {
            dics[genres[i]]! += plays[i]
        } else {
            dics.updateValue(plays[i], forKey: genres[i])
        }
        
        
        if playNumByGenres.filter({ $0.key == genres[i] }).count > 0 {
            playNumByGenres[genres[i]]?.append(plays[i])
        } else {
            playNumByGenres.updateValue([plays[i]], forKey: genres[i])
        }
        
    }
    
    var dicsSorted = dics.sorted { $0.value > $1.value }
    
    for (genre, values) in playNumByGenres {
        playNumByGenres[genre] = values.sorted(by: >)
    }
    
    var result: [Int] = []
    for (genre, value) in dicsSorted {
        if playNumByGenres[genre]!.count >= 2 {
            if playNumByGenres[genre]![0] == playNumByGenres[genre]![1] {
                var indexs: [Int] = []
                
                for (index, play) in plays.enumerated() {
                    if play == playNumByGenres[genre]![0] {
                        indexs.append(index)
                    }
                }
                
                indexs.sorted { $0 < $1 }
                result.append(indexs[0])
                result.append(indexs[1])
            } else {
                result.append(plays.firstIndex(of: playNumByGenres[genre]![0])!)
                result.append(plays.firstIndex(of: playNumByGenres[genre]![1])!)
            }
        } else if  playNumByGenres[genre]!.count == 1 {
            result.append(plays.firstIndex(of: playNumByGenres[genre]![0])!)
        }
        
    }
    print(dicsSorted)
    print(playNumByGenres)
    return result
}

print(solution(["classic", "pop", "classic", "classic", "pop"], [500, 600, 500, 400, 2500]))


//      필요한 데이터
//      1.  ["classic": 1450, "pop": 3100]
//      2.  ["classic": [800, 500, 150], "pop": [2500, 600]]
```

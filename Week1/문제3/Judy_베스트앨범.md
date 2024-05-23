```swift
func solution(_ genres:[String], _ plays:[Int]) -> [Int] {
    var playCountList: [String: Int] = [:] // [장르 : 청취수]
    var songList: [Int: (genre: String, count: Int)] = [:] //[고유번호 : (장르, 청취수)]
    var result: [Int] = []
    
    for (genre, playCount) in zip(genres, plays) {
		    // 장르별 총 청취수
        playCountList[genre] = (playCountList[genre] ?? 0) + playCount
    }
    
    for i in 0..<genres.count { // songList 할당
        songList[i] = (genre: genres[i], count: plays[i])
    }
    
    let genresList = playCountList.sorted(by: { $0.value > $1.value }) // 청취수 높은 순으로 장르 정렬
    
    for hotGenre in genresList { // 청취수 높은 순으로
        let songFilteredList = songList.filter { $0.value.genre == hotGenre.key } // 현채 장르인 노래들 찾기
        let hotList = songFilteredList.sorted(by: { ($0.value.count, $1.key) > ($1.value.count, $0.key)}) // 청취수 높은순, 고유 번호 낮은 순으로 정렬
        hotList.prefix(2).forEach { result.append($0.key) } // 상위 2개의 key(고유번호)만 넣기
    }
    
    return result
}
```

# leetcode_Longest_Substring_Without_Repeating_Characters
+ 중복되지않는 한에서 최장 길이 구하기
+ 在一個字串求出最長的距離，但中間不能重複包刮同樣的字元
-----
+ Example1
```
Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3.
```
----
+ Example2
```
Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
```
----
+ Example3
```
Input: s = "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3.
Notice that the answer must be a substring, "pwke" is a subsequence and not a substring.
```
----
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        
        start = 0 # 시작점 출력
        maxlen = 0 # 길이 측정
        check = {} # 저장 함수 <중복 방지>
        
        for i,c in enumerate(s): #enumerate 함수로 0 a\n 1 b\n 2 c\n이렇게 만들기
            if c in check and start <= check[c]: # 만약 c가 저장 함수에 이미 저장 되어있고 시작점이 저장 되어있는 숫자 위치보다 작거나 같을경우 실행
                start = check[c] + 1 # 만약 있다면 그 중복된 값의 다음것부터 계산하기 위해 start위치를 중복된 값의 다음것으로 이동 
            else:
                maxlen = max(maxlen, i - start + 1) # 현재 길이가 더 긴지 아니면 i-start+1 위치의 거리가 더 긴지 체크
            check[c] = i # 매 항목 check함수에 저장  {'a': 3, 'b': 7, 'c': 5} 
        return maxlen
```
---
```
결론 : 
만약abcabcbb라는 input이 있으면 결과값을 쭉 스켄함 , 중복이 없으면 len이 계속 늘어나고 check에 이미 판단했던 문자들 저장 , 
만약 그 후 중복된 값들이 있을경우 그 값들의 다음값 즉 abcabcbb일땐 abca a가 중복이므로 첫번째 a 다음칸으로 start를 옮기고 
현재위치 i 에서 start를 뺀 값을 +1후 어느것이 더 긴 길이인지 판단.
```
---
```
結論:
假設我們有abcabcbb這個input時 如果沒有重複到的字元，那這著函式累加長度，直到遇到重複的字元時，
把start這個位置換成重複到的字元的下一個來計算現在的位置到start的位置，並求出誰比較長。
```
---
### Result
Runtime: 54 ms, faster than 97.90% of Python3 online submissions for Longest Substring Without Repeating Characters.\
Memory Usage: 14 MB, less than 49.20% of Python3 online submissions for Longest Substring Without Repeating Characters.

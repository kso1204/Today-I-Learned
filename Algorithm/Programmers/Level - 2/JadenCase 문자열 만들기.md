# JadenCase 문자열 만들기

# 문제 설명

1. JadenCase란 모든 단어의 첫 문자가 대문자이고, 그 외의 알파벳은 소문자인 문자열입니다.

2. 문자열 s가 주어졌을 때, s를 JadenCase로 바꾼 문자열을 리턴하는 함수, solution을 완성해주세요.


# 제한 사항


```
제한 조건
s는 길이 1 이상인 문자열입니다.
s는 알파벳과 공백문자(" ")로 이루어져 있습니다.
첫 문자가 영문이 아닐때에는 이어지는 영문은 소문자로 씁니다. ( 첫번째 입출력 예 참고 )

s	return
"3people unFollowed me"	"3people Unfollowed Me"
"for the last week"	"For The Last Week"

```

# 해결 방안

1. 전체 소문자 나눠서 앞에만 대문자

# 풀이

- 좋은 풀이

```

public String solution(String s) {
        String answer = "";
        String[] sp = s.toLowerCase().split("");
        boolean flag = true;

        for(String ss : sp) {
            answer += flag ? ss.toUpperCase() : ss;
            flag = ss.equals(" ") ? true : false;
        }

        return answer;
  }

```

- 나의 풀이

```

class Solution {
    public String solution(String s) {
        String answer = "";
        
        s = s.toLowerCase();
        
        String[] str = s.split(" ");
        
        for(int i=0;i<str.length;i++) {
            
            char[] ch = str[i].toCharArray();
            
            for(int j=0;j<ch.length;j++) {
                
                if(j==0) {
                    answer += String.valueOf(ch[j]).toUpperCase();
                    continue;
                }
                
                answer += String.valueOf(ch[j]);
                
            }
            
            if(i<str.length-1) {
                answer += " ";   
            }
        }
        
        
        return answer;
    }
}

```
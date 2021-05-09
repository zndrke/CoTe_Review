# KT ★

### 1. A,B 박스에 있는 공 옮기기★

##### 문제설명

- formBox[i] 에는 "A" 혹은 "B" 가 있고, "A"는 A->B를 의미함
- ball[i 에는 이동하는 공의 개수가 있음
- numA,numB는 현재 공의 개수가 있음
- 만약 numA 혹은 numB의 개수가 1000개가 넘으면 1000개까지만 옮김



~~~java
class Solution {
    public int[] solution(String[] fromBox, int[] ball, int numA, int numB){
        int answer[] ={0,0};
        for (int i = 0; i < fromBox.length; i++){
            if (fromBox[i].equals("A")) {
                numA -= ball[i];
                numB += ball[i];
                if (numB >= 1000) {
                    int over = numB - 1000;
                    numB -= over;
                    numA += over;
                }    
            }
            else {
                numA += ball[i];
                numB -= ball[i];
                if (numA >= 1000) {
                    int over = numA - 1000;
                    numB += over;
                    numA -= over;
                }
            }
        }
        answer[0] = numA;
        answer[1] = numB;
        return answer;
    }
}
~~~



### 2. 상담을 진행하고 있던 시간★

##### 문제설명

- 각 고객별 상담시작시작과 종료시각이 담긴 2차원배열 customer가 매개변수로 주어질 때, 적어도 한명 이상의 고객이 상담을 진행하고 있던 시간은 총 몇분인지 return

~~~java
import java.util.*;
class solution{
    class Time implements Comparable<Time>{
        int start;
        int end;
        
        Time(int start, int end) {
            this.start = start;
            this.end = end;
        }
        
        @Override
        public int CompareTo(Time t) {
            return this.start - t.start;
        }
    }
    public int solution(int[][] customer) {
        int answer = 0;
        PriorityQueue<Time> pq = new PriorityQueue<>();
        
        for(int k = 0; k < customer.length; k++) {
            Time time = new Time(customer[k][0], customer[k][1]);
            pq.offer(time);
        }
        
        int last = 0;
        for (int j = 0; j < customer.length ;j++) {
            if (last < customer[j][1]) {
                last = customer[j][1];
            }
        }
        
        for (int i = 0; i < last; i++) {
            Time time = pq.poll();
            if (time.start <= i) {
                i = time.end - 1;
            }
            else {
                answer++;
                pq.offer(time);
            }
        }
        return last - answer;
    }
}
~~~



### 3. 거리가 가장 작은 값과 큰값 구하기★

##### 문제설명

- X = 0, Y = 0 지점으로 부터 가장 가까운 집까지의 거리의 제곱과 가장 먼 집까지의 거리의 제곱을 한줄에 표현하라



- 테이블 HOUSE_LOCATIONS

| NAME  | TYPE       |
| ----- | ---------- |
| OWNER | VARCHAR(N) |
| X     | INT        |
| Y     | INT        |



~~~sql
SELECT MIN(H.X*H.X + H.Y*H.Y) AS CLOSE, MAX(H.X*H.X + H.Y*H.Y)
FROM HOUSE_LOCATIONS
~~~


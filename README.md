# short-distance
#python
maps안에 1과 0이 있는데 0은 장애물로 막혀있고 1은 지나갈수 있다 출발지점(왼쪽맨위)에서 도착지점까지 갈수있는 가장 적은 수의 블록칸의 개수를 구해라 도착지는 오른쪽 맨아래다
dfs알고리즘
popleft()
-python 리스트 자료구조를 보면 pop(i) 이라는 연산이 있습니다.
-바로 i번째 인덱스를 삭제하는 연산입니다.
-원래 보통의 자료구조에서 pop()연산이라고 하면 제일 끝에 요소가 삭제가 됩니다.
-이를 반대로 한 것이 바로 popleft() 입니다.
-popleft()는 제일 끝 요소가 아니라 제일 앞의 요소가 삭제가 됩니다.
더빠른 속도를 위해 List() 아닌 deque()를 사용!


from collections import deque
def solution(maps):
    xx=[-1,1,0,0]
    yy=[0,0,-1,1]
    a=len(maps)
    b=len(maps[0])
    datas=[[-1 for _ in range(b)] for _ in range(a)]  
    data=deque()
    data.append([0,0])
    datas[0][0]=1
    while data:
       x,y=data.popleft() #data안의 첫번째 요소가 삭제
       for i in range(4):
            Xx=x+xx[i]
            Yy=y+yy[i]
            if 0 <= Xx < a and 0 <= Yy < b and maps[Xx][Yy] == 1:
                if datas[Xx][Yy]==-1:
                    datas[Xx][Yy]=datas[x][y]+1
                    data.append([Xx,Yy])
    answer=datas[-1][-1]
    return answer
maps=[[1,0,1,1,1],[1,0,1,0,1],[1,0,1,1,1],[1,1,1,0,1],[0,0,0,0,1]]
a=solution(maps)
print(a)

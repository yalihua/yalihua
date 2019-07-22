n,m=map(int, input("请输入n和m：").split())
value=list(map(float, input("输入物品价值：").split()))
print('请输入约束条件:')
s=[]
for k in range(m):
    p=list(map(int, input().split()))
    s.append(p)
t=list(map(int, input("输入约束条件的约束值："%m).split()))
value_max=0
v=0
def bacltrack(i):
    global value_max,v,n,m
    j=1
    if i>=n:
        if v>value_max:
            value_max=v
    else:
        for r in range(m):
            c=t[r]-s[r][i]
            if c<0:
                j=0
        if j==1:
            for g in range(m):
                t[g]=t[g]-s[g][i]
            v=v+value[i]
            bacltrack(i+1)
            for h in range(m):
                t[h]=t[h]+s[h][i]
            v=v-value[i]
        bacltrack(i+1)
bacltrack(0)
print("最大价值为：",value_max)

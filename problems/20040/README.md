# 문제 20040

## 📌 문제 설명
예시로 제공되는 문제입니다.

## ✅ 풀이 현황
- [x] C
- [x] C++
- [ ] C#
- [x] Python

## 🧠 풀이 요약

간선을 추가하기 전에, 두 점을 잇는 간선이 존재했었는지 확인하는 과정이 필요
현재의 간선을 제외한, 다른 방법으로 두 점을 잇는 간선이 존재했을 경우, 현재의 간선을 그음으로써 싸이클이 완성되기 때문

분리집합을 활용, 간선으로 연결된 점들을 집합 형태로 표현한다.


```
    분리 집합 생성(구조체) 및 집합의 갯수를 N개로 초기화

    for(M개의 간선만큼 반복)
    {
        간선으로 연결된 두 점을 입력을 받음

        두 점을 하나의 집합으로 merge함
        if(이때, 기존에 두 점을 포함하는 집합이 존재했을 경우)
            현재의 반복 횟수를 반환하고 종료
    }

    for문을 탈출했을 경우 0을 반환하고 종료
```

```
    struct disjoint_set
    {
        int *par;
        int *sz;
        
        void init(int n);
        int root(int a);
        bool merge(int a, int b);
        bool test(int a, int b);
        int size(int a);
    };

    void disjoint_set::init(int n)
    {
        par = new int[n];
        sz = new int[n];
        
        for (int i = 0; i < n; i++)
        {
            par[i] = i;
            sz[i] = 1;
        }
    }

    int disjoint_set::root(int a)
    {
        if (a == par[a])
            return a;
        
        return par[a] = root(par[a]);
    }

    bool disjoint_set::merge(int a, int b)
    {
        int ra = root(a);
        int rb = root(b);
        
        if (ra == rb)
            return false;
        
        if (sz[ra] > sz[rb])
        {
            par[rb] = ra;
            sz[ra] += sz[rb];
        }
        else
        {
            par[ra] = rb;
            sz[rb] += sz[ra];
        }
        
        return true;
    }

    bool disjoint_set::test(int a, int b)
    {
        return root(a) == root(b);
    }

    int disjoint_set::size(int a)
    {
        return sz[root(a)];
    }
```
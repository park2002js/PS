# 문제 2128

## 📌 문제 설명
예시로 제공되는 문제입니다.

## ✅ 풀이 현황
- [ ] C
- [ ] C++
- [ ] C#
- [ ] Python

## 🧠 풀이 요약

```
    cin >> N >> D >> K;

    vector<int> stat(N+1);

    //학생 입력 받기
    for(K번)
    {
        int cnt;
        cin >> cnt;

        while(cnt--)
        {
            cin >> p
            stat[현재 반복 횟수] |= (1 << (p-1));
            /*
                비트 문자열 형태로 저장하기 위한 코드
                OR 연산을 통해 이전의 비트열(풀이 가능한 문제 종류)를 살리고
                p-1을 통해 풀 수 있는 비트열을 0번째에서 부터 시작할 수 있도록 함
            */

        }
    }
    int ans=0;
    int field_limit = 1 << D; // 2^D-1 인 비트열을 생성
    for(field = 비트열을 limit까지 1씩 더하며 반복, limit는 D가 결정)
    {
        // unhappy case로 원하지 않는 case의 경우 건너 뛰기
        if(bcnt(현재 비트열열) > K)
            continue;
        /*
            bcnt는 현재의 비트열의 1의 갯수를 카운트
            '비트열' >> 1 결과에 '& 1'을 하여 마지막 비트열만 추출해서 count 변수에 더하기
            이 반복은 비트열이 0이 될때까지(모든 비트가 0)반복

            이 bcnt의 목적은 문제의 조건인 "K"개의 문제 풀이 가능을 따르기 위해 존재 (K개 초과의 문제를 풀 수 있는 조합의 생성 경우 자체를 제거)
        */

        /*
            더 나아가 "동적 계획법"의 "최적화 여부"를 체크하여 개선 가능
            
            a,b,c 문제를 풀 수 있는 학생들은 a,b,c,d 문제를 풀 수 있는 학생에 포함이 된다.
            즉, K 종류의 문제에 대해, K 종류 중 1개라도 풀 수 있는 학생은 K 종류의 문제를 풀 수 있는 학생에 포함되기 때문에

            'bcnt <= k 인 경우에만 문제를 푼다' 를 'bcnt == k인 경우에만 문제를 푼다'로 경우의 수를 줄일 수 있다.
            따라서 unhappy case의 조건을 bcnt() > K 에서서 bcnt != K 로 확장 할 수 있다.
        */

        int cnt = 0;
        for(N명의 학생에 대해해)
        {
            if[((현재 학생이 풀 수 있는 문제의 비트 표현) OR (현재 반복번째의 문제 종류 비트 표현)) == (현재 반복번째의 문제 종류 비트 표현)]
                cnt++;
        }
        max(cnt, ans);  // 최대 수만 남기기
    }
unhappy case

```



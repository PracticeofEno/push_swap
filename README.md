# push_swap
## 개요
- push_swap은 두개의 스택을 이용하여 int로 구성된 숫자Set를 정렬하는 알고리즘 게임입니다
- 이 소스를 컴파일하면 문제를 해결하는 push_swap과 그것을 체크하는 checker를 생성합니다
- 이를 스택 A, B 라고 하겠습니다
- 스택 A는 정렬되지 않은 양의 난수, 음의 난수로 구성되어있습니다
- 스택 B는 비어있습니다
- 목표는 오름차순으로 스택 A를 정렬하는것 입니다
- 이를 위한 사용할수 있는 도구는 다음과 같습니다
- 100개를 정렬하는데 1100개 미만의 명령Set를 사용해야 합니다
- 500개를 정렬시 7000개 미만의 명령Set를 사용해야 합니다

| 명령어 | 기능 | 
| --- | --- | 
| sa | 스택A의 top과 top 바로 아래 원소 2개를 교환합니다 
| sb | 스택B의 top과 top 바로 아래 원소 2개를 교환합니다
| ss | 스택A와 스택B 모두 sawp을 실시합니다 ( sa + sb )
| pa | 스택B의 top을 스택A로 push합니다 
| pb | 스택A의 top을 스택B로 push합니다 
| ra | 스택A의 모든 요소를 한칸씩 위로 이동합니다. top은 제일 아래로 갑니다
| rb | 스택B의 모든 요소를 한칸씩 위로 이동합니다. top은 제일 아래로 갑니다 
| rr | 스택A와 스택B 모두 rotate를 실행합니다 ( ra + rb )
| rra | 스택A의 모든 요소를 한칸씩 밑으로 이동합니다. 스택의 가장아래에 있는 요소는 top이 됩니다 
| rrb | 스택B의 모든 요소를 한칸씩 밑으로 이동합니다. 스택의 가장아래에 있는 요소는 top이 됩니다 
| rrr | 스택A와 스택B 모두 reverse rotate를 실행합니다 (rra + rrb) 

## 구현 언어
- C

## push_swap
- push_swap을 해당 숫자Set를 정렬한 명령어의 조합을 순서대로 구합니다

## checker
- checker는 해당 명령어들을 수행한 후 스택A가 정렬되어있는지 확인합니다
- 정렬되어있으면 OK, 그렇지 않다면 Error를 출력합니다  

## 결과
- 효율성 (명령어 카운트)  
![2022-11-15 오후 5-04-50](https://user-images.githubusercontent.com/57505385/201863637-e66dc4f8-788b-4787-933b-562a027a998a.png)
- 체커결과  
![123](https://user-images.githubusercontent.com/57505385/201863933-8d16bee3-9c6c-45b0-8d89-5002f6321035.png)
## 간단한 실행 예제) 3 2 1 -> SA , RRA
![설명1](https://user-images.githubusercontent.com/57505385/201691667-4a1d52cc-1e50-4c99-adae-f58471aececc.png)
-----
![설명2](https://user-images.githubusercontent.com/57505385/201691677-7c4e05b4-ce57-4ddc-b833-5106ae0f0727.png)
------
![설명3](https://user-images.githubusercontent.com/57505385/201691673-bacc0f46-2e6e-4a0b-a985-57ce8995fc6e.png)
------

## 구현방법
1. 숫자Set들의 크기가 3보다 크다면 해당 스택을 한바퀴 rotate 시키면서 다른 스택으로 중앙값(숫자Set에서 딱 중앙에 위치하는 수)보다 큰 수를 넘긴다  
-> 숫자 0~100을 기준으로 정렬된 모습  
![디바이드모습](https://user-images.githubusercontent.com/57505385/201852997-1673a606-69db-4fc0-8417-96de6ba718e8.png)
2. 넘겨진 숫자Set의 크기가 3 이하라면 명령어들을 이용해서 A스택 뒷부분에 숫자를 이동시킨다  
-> 0~2가 정렬이 끝난 모습  
![02소팅](https://user-images.githubusercontent.com/57505385/201853004-44cc2fb1-1b4c-4215-b174-dbb8ad28976f.png)
3. 모든 숫자가 정렬이 끝날때까지 divide과 1번과 2번의 작업을 반복한다.

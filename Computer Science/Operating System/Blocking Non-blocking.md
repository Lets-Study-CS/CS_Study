# Blocking, Non-blocking

`Blocking`과 `Non-blocking`은 현재 웹을 공부하는 입장에서 가장 자주 등장하는 개념 중 하나이자, `Synchronous` 와 `Asynchronous` 사이에서 가장 햇깔리는 개념 중 하나이다.

우선 `Blocking` 과 `Non-blocking` 의 정의부터 확인해보고자 한다.

## 블로킹 Blocking

> A 함수가 B 함수를 호출 할 때, B 함수가 **자신의 작업이 종료되기 전**까지 A함수에게 제어권을 돌려주지 않는 것
> 

## 논블로킹 Non-blocking

> A함수가 B함수를 호출 할 때, B 함수가 제어권을 바로 A함수에게 넘겨주면서, A **함수가 다른 일을 할 수 있도록 하는 것**
> 

결국 호출된 함수가 제어권을 갖고있냐, 아니냐를 두고 블로킹, 논블로킹이라는 정의를 두는 것이다.

그렇다면 `Synchronous` 와 `Asynchronous` 는 어떨까?

## 동기 Synchronous

> A 함수가 B 함수를 호출 할 때, A 함수가 B 함수의 **작업 완료 후 리턴을 기다리거나**, 혹은 B함수로부터 바로 리턴 받더라도 작업 완료 여부를 호출하는 것이다.
> 

## 비동기 Asynchronous

> A 함수가 B 함수를 호출 할 때, B 함수에게 callback을 전달해서 **B함수의 작업이 완료되면 B함수가 전달받은 callback을 실행하고**, A함수의 작업 완료 여부를 신경쓰지 않는 것 이다.
> 

즉, 호출되는 함수의 작업 완료 여부를 누가 신경쓰냐의 관점이 중요하다.

---

이를 바탕으로 만들어진 IBM developerWorks의 2x2 매트릭스를 확인해보자

![Untitled](https://images.velog.io/images/tess/post/7f1e8bff-032f-4709-a965-f1271d02d733/2021-03-07T20_37_39.png)

이 그림에서, `Sync-Blocking`과 `Async-NonBlocking`은 대표적인 예시가 많다. 

![Untitled](https://i.imgur.com/06P0Q6m.png)

그렇다면 나머지 둘은 어떻게 설명해야할까?

![Untitled](https://i.imgur.com/a8xZ9No.png)

언어적 그대로 해석하는 것이 가장 쉽게 느껴진다.

우선 `Sync-Nonblocking`은 호출 된 함수의 완료 여부를 기다리는 것 없이, 호출 하는 함수는 계속 진행을 하며, 호출 함수의 작업 여부만 확인하면 된다.

![Untitled](https://i.imgur.com/zKF0CgK.png)

`Async-Blocking` 은 어떨까? 똑같이 B 함수의 callback이 실행이 되야한다. 다만 `Blocking` 이기 때문에, callback이 호출 될 때 까지 기다릴 것 이다.
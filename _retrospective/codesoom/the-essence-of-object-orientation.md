---
title: 코드숨 객체지향의 사실과 오해 스터디 회고
subTitle:
category:
tags:
createdat: 2021-01-25 02:54:00
updatedat: 2021-01-25 02:54:00
---

코드숨에서 객체지향 스터디를 시작했는데, 그 처음으로 객체지향의 사실과 오해를 읽고 스터디를 진행했다. 책이 너무 재밌고 이해가 쉽게 설명되어 있어서 읽는 것은 어렵지 않았지만, 새롭게 배우는 개념들이 너무 많아서 정리가 잘되지 않았다. 이 책을 읽고 나면 나는 무엇을 할 수 될까?

## 정리

처음에는 정리를 하려고 했다. 객체지향이란 무엇이고, 책임, 역할, 협력, 메시지, 타입 등등 정리할 것들이 너무 많았다. 그런데 이미 이런 것들은 책에서 잘 설명되어 있고, 이런 것들을 달달 외운다고 하더라도 우리가 객체지향 설계를 할 수 없다면 아무짝에도 쓸모없을 것이다.

## 기존의 문제

객체지향에 대해서만 얘기를 하다가 기존에는 어떤 문제가 있었길래 이러한 객체지향 프로그래밍이 만들어졌는가?에 대해서는 너무 고민을 안한 것 같았다. 기존의 절차지향적인 프로그래밍에는 어떤 문제가 있을까? 그래서 한 가지 문제에 대해서 두 가지 방법을 모두 적용해서 문제를 풀어보기로 했다. 간단하게 현재 스터디를 하는 상황을 프로그래밍 해봤다.

### 절차지향적인 방법

절차지향적인 방법은 프로그램이 흐르는 과정을 모두 따라가야 무슨 일이 일어나는지 알 수 있다. 그리고 데이터와 함수가 분리되어 있어서 계속해서 데이터를 외부에서 주입해 주어야 한다. 그리고 만약 그 주어지는 대상이 비슷한 부분이 있지만 조금이라도 다르다면 새로운 함수를 계속해서 만들어줘야 한다.

```js
question(message, person) {
    talk(message, person);
}

answer(message, yunseok) {
    talk(message, yunseok)
}


main() {
    introduce();
    
    listen(() => {
        stop();
        answer();
    });
    const person = pick();
    const question = getQuestion();
    const answer = doQuestion(person, question);
    findInBran(brain);
    summary(answer);
}

pick() {
    return randomPerson;
}

getQuestion() {
    return getFromNote();
}

doQuestion(person, question) {
    say(person, question);
}
```

### 객체지향적인 방법

절차지향적인 방법은 우리의 프로그램을 아주 큰 시스템에게 우리가 필요한 것을 질문을 던진다. 그러면 그 시스템은 다시 그 질문에 답하는데 필요한 것들을 다시 작은 시스템에게 질문을 하고 응답을 하여 우리에게 필요한 것을 만든다. 기존에는 프로그램의 흐름을 모두 우리가 정의했다면, 객체지향에서는 각 책임에 대해 책임을 지는 객체에게 메시지를 통해서 시키고 응답하여 객체들끼리 어떻게 협력할 것으로 프로그램의 흐름을 만들고 세부적으로 어떻게 동작할지는 객체에게 맡긴다. 즉 객체 단위에서 메시지에 어떻게 응답할지 프로그램을 작성하기 때문에 더 단순하게 만들 수 있다.

```js
interface participant {
    question(person)
    answer(person)
}

main() {
    mc.intro();

    const mc: Participant = Mc(brain);
    mc.question(participant);

    const nan = Person(brain);
    const hyejin = Person(brain);
    nan.question(mc);

    nan.question(hyejin);
}

class mc() implement participant {
    brain;
    questions = ['객체지향이란 무엇인가?'];
    answers = ['객체로 짜는거다', '협력을 한다'];

    intro() {
        console.log('책에 대한 내용 소개');
    }

    question(person: Participant) {
        const answer = person.answer(questions[0]);
        return answer
    }

    answer() {
        return summary();
    }

    summary(content) {
        const answer = brain.findAnswer(content);
        console.log(compose(answer, answers););
    }
}

class person() implements participant {
    brain;
    questions = ['객체지향이란 무엇인가?'];
    
    question(person) {
        const answer = person.answer(questions[0])
    }
    
    answer(question) {
        const answer = brain.findAnswer(question)
        return answer
    }
}
```

## 좋았던 점

* 작은 프로그램이라도 객체지향적인 방법으로 문제를 해결해보려는 시도를 했다. 너무 작은 프로그램을 만들어서 전부 파악할 순 없었지만 어떻게 문제를 해결할지 아주 작은 사이클을 연습했다. 계속 연습해서 나중에는 자동으로 객체지향적인 사고로 설계를 할 수 있도록 연습해야겠다.

## 아쉬운 점

* 시간이 부족해서 더 큰 시스템을 만들어보지 못했다.

## Sources

* 객체지향의 사실과 오해 - 교보문고 - <http://www.kyobobook.co.kr/product/detailViewKor.laf?barcode=9788998139766>
* 객체지향의 사실과 오해 서평 - <https://hannut91.github.io/blogs/books/the-essence-of-object-orientation>
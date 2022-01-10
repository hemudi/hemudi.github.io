---
title: "Data Structure - Linked List"
categories: "DataStructure"
date: 2022-01-10
last_modified_at: 2022-01-10
# published: false
related: false
toc: true
toc_sticky: true
toc_label: "Linked List"
tags:
    - Linked List
---

__💡 Linked List 에 대해 개인적으로 학습하고 정리한 글입니다. 틀린 부분이나 오류가 있을 경우 댓글로 알려주시면 감사하겠습니다!__
{: .notice--warning}

# __🖇 Linked List__
* 물리적으로 흩어져 있는 자료들을 서로 연결하여 하나로 묶어 관리하는 데이터 구조
* 노드 간의 연결을 이용해 리스트를 구현한 것

## __특징__
- 데이터(노드)와 링크로 구성되어 있으며 링크가 노드들을 연결하는 역할을 한다.
- 데이터들은 메인 메모리상의 어디에나 흩어져 존재할 수 있다.
- 순서를 유지하기 위해 각각의 데이터는 다음 데이터를 가리키는 줄을 가진다.
- 첫 데이터에서부터 순서대로 줄을 따라가면 모든 데이터를 방문할 수 있다.
- 배열처럼 미리 공간을 확보할 필요도 없으며 필요할 때마다 동적으로 노드를 생성해 연결하면 된다.
- 링크 필드를 위한 추가 공간이 필요하다.
- 연산의 구현이나 사용 방법이 배열에 비해 복잡하여 오류가 발생할 가능성이 높다.
- 오류가 없더라도 동적 할당과 해제가 너무 빈번하게 일어나면 메모리 관리를 위한 처리시간이 길어져 프로그램이 느려질 수도 있다.

## __Array Vs. Linked List__
||Array|Linked List|
|:-:|-|-|
|__크기__|최초 선언 시 크기로 고정되며 사용되지 않는 공간도 함께 할당해야해서 비효율적임|고정 되지 않으며 필요할때마다 추가하여 공간 활용이 효율적임|
|__삽입__|중간에 데이터를 삽입하기 어려움 추가하려는 위치 이후의 모든 자료들을 전부 하나씩 뒤로 미는 연산이 필요함|중간에 삽입하기 쉬움 링크만 수정하면 됨|
|__삭제__|중간에 데이터를 삭제하기 어려움 삭제 후 남은 데이터들의 위치를 다시 옮겨줘야함|링크만 수정하면 되서 쉬움|
|__탐색__|인덱스를 사용하면 빠르게 가능|무조건 처음부터 순차적으로 노드를 찾아가는 과정을 거쳐야해서 효율이 좋지 못함|
|__구현__|쉬움|어려움|

## __구조__

![](https://user-images.githubusercontent.com/34249911/148717000-f487dd11-30d5-4c87-b074-070a6c26009b.png)

### __Node__
- 연결 리스트는 노드들의 집합으로 이들은 데이터를 저장하고 있고 서로 연결되어 있다.
- 일반적인 노드는 ``데이터 필드(data field)``와 ``링크(link field)``로 구성되어 있다.
- 데이터 필드에는 저장하고자 하는 데이터가 들어가며 다양한 자료형이 올 수가 있다.
- 링크 필드에는 다음 노드의 주소를 저장한다.
- 연결 리스트를 탐색하기 위해선 첫번째 노드의 주소를 알아야 하는데 이 노드의 주소를 저장하는 노드를 ``Head`` 한다. 반드시 지정해줘야 함.
- 연결 리스트의 마지막은 마지막 노드의 링크 필드를 ``NULL`` 값으로 하여 표현한다. ``Tail`` 이라고도 함.

## __종류__
### __1. Singly Linked List 단순 연결 리스트__
- 하나의 방향으로만 연결되어 있으며 맨 마지막 노드의 링크 필드는 NULL 값을 가진다.

### __2. Circular Linked List 원형 연결 리스트__
- 단순 연결 리스트와 같지만 맨 마지막 노드의 링크 값이 다시 첫번째 노드를 가리킨다.

### __3. Doubly Linked List 이중 연결 리스트__
- 각 노드마다 링크 필드가 2개씩 존재하며 각각 선행 노드(previous node)와 후행 노드(next node)를 가리킨다.
  

## __구현__
### __기본 구조__

```js
class Node {
    constructor(value){
        this.value = value;
        this.next = null;
    }
}

class LinkedList {
    constructor(){
        this.head = null;
        this.tail = null;
        this.length = 0;
    }
    ...
}
```
    
### __추가__
#### __1. 맨 앞에 추가(unshift)__
```js
addFirst(value) {
    const newNode = new Node(value);

    newNode.next = this.head;
    this.head = newNode;

    if(this.head.next == null){
        this.tail = this.head;
    }

    this.length++;
}

unshift(value){
    const newNode = new Node(value);

    if(!this.head){
        this.head = newNode;
        this.tail = this.head;
    } else {
        newNode.next = this.head;
        this.head = newNode;
    }

    this.length++;
    return this;
}
```
- 생성한 새로운 노드의 next 로 head 를 지정한다. head 는 연결리스트의 맨 첫번째 노드이기 때문에!
- 그 후 head 를 새로운 노드로 변경한다.
- 만약 head 의 next 가 null 이라면, 즉 리스트에 노드가 하나 뿐이라면 그 노드는 head 이자 tail 이니 tail 로 설정
- 리스트의 길이 + 1
  
#### __2. 끝에 추가(push)__
```js
addLast(value){
    let newNode = new Node(input);

    if(this.length == 0){
        this.addFirst(input);
    } else {
        this.tail.next = newNode;
        this.tail = newNode;
        this.length++;
    }
}

push(){}
```
- 리스트의 길이가 0 이라면 addFirst 를 호출해 맨 앞에 추가
- 현재 노드의 맨 마지막 노드인 tail 의 next로 새로운 노드를 설정하고 tail 을 새 노드로 설정
- 리스트의 길이 + 1

#### __3. 중간에 추가__
- index 위치의 Node 탐색

```js
getNode(index){
    let node = this.head;
    
    for(let i = 0; i < index; i++){
        node = node.next;
    }

    return node;
}

// getNode 다른 방식
get(index){
    if(index < 0 || index >= this.length) return null;

    let counter = 0;
    let curNode = this.head;

    while(counter !== index){
        current = current.next;
        counter++;
    }

    return current;
}
```

- 노드 추가

```js
add(index, value){
    if(index === 0){
        addFirst(value);
    } else {
        let preNode = getNode(index - 1);
        let idxNode = preNode.next;
        let newNode = new Node(value);

        preNode.next = newNode;
        newNode.next = idxNode;

        this.length++;

        if(newNode.next === null){
            this.tail = newNode;
        }
    }
}

insert(index, value){
    if(index < 0 || index > this.length) return false;
    if(index === this.length - 1) return this.push(value);
    if(index === 0) return this.unshift(value);

    const newNode = new Node(value);
    let pre = this.get(index - 1);
    let temp = pre.next;

    pre.next = newNode;
    newNode.next = temp;
    this.length++;
    return true;
}
```
- 만약 index 가 0이라면 맨 앞에 추가하는거니까 addFirst 를 호출
- index 위치의 노드의 이전 노드도 알아야 하니까 ``getNode(index - 1)`` 로 이전 노드를 구한 뒤 그 노드의 next 속성으로 index 이전 노드와 index 노드를 구한다.
- 새로운 노드를 생성해 이전 노드의 next 로 설정하고 현재 노드의 next 로 index 노드를 설정한다.
- 만약 현재 노드의 next 가 null 이라면 마지막 노드이므로 tail 을 newNode 로 설정

### __삭제__
#### __1. 처음 노드 삭제(shift)__
```js
removeFirst(){
    let first = this.head;
    this.head = first.next;
    first = null;
    this.length--;
}

shift(){
    if(!this.head) return undefined;

    let first = this.head;
    this.head = first.next;
    this.length--;

    if(this.length === 0){
        this.tail = null;
    }

    return first;
}
```
- head 노드를 first 노드로 지정하고 first 노드의 next 노드인 두번째 노드를 head 로 지정한다.
- first 를 null 로, 길이는 -1 해준다.

#### __2. 중간 노드 삭제__
```js
remove(index){
    if(index === 0){
        return removeFirst();
    } else {
        let preNode = getNode(index - 1);
        let deletedNode = preNode.next;

        preNode.next = deletedNode.next;

        if(deletedNode === this.tail){
            this.tail = preNode;
        }

        deletedNode = null
        length--;
    }
}

remove(index){
    if(index < 0 || index >= this.length) return false;
    if(index === this.length - 1) return this.pop();
    if(index === 0) return this.shift();

    let pre = this.get(index - 1);
    let remove = pre.next;
    pre.next = remove.next;
    this.length--;

    return removed;
}
```
- 삭제할 노드의 이전 노드를 getNode 로 구하고 그 노드의 next 로 삭제할 노드를 구함
- 이전 노드의 next 를 삭제 대상 노드의 next 로 설정
- 만약 삭제 노드가 tail 노드라면 tail 을 이전 노드로 설정해줌

#### __3. pop__
```js
pop() {
    if(!this.head) return undefined;

    let curNode = this.head;
    let newTail = curNode;

    while(curNode.next){
        newTail = curNode;
        curNode = curNode.next;
    }

    this.tail = newTail;
    this.tail.next = null;
    this.length--;

    if(this.length === 0){
        this.head = null;
        this.tail = null;
    }

    return curNode;
}
```
- head 가 null / undefined 이면 리스트에 아무 데이터도 없는 것
- 끝 노드까지 찾아 끝까지 탐색하면 curNode 는 맨 끝의 노드를 newTail 은 그 이전의 노드를 가리키게 된다.

### __데이터 변경__
```js
set(index, value){
    const foundNode = this.get(index);
    if(foundNode){
        foundNode.value = value;
        return true;
    }
    return false;
}
```

### __리스트 뒤집기__
```js
reverse(){
    let node = this.head;
    this.head = this.tail;
    this.tail = node;

    let next;
    let pre = null;

    for(let i = 0; i < this.length; i++){
        next = node.next;
        node.next = pre;
        pre = node;
        node = next;
    }
    
    return this;
}
```

## __시간 복잡도__
### 1. 맨 앞 맨 뒤 삽입 : O(1)
- 리스트의 맨 앞이나 맨 뒤에 새로운 요소를 추가할 때 늘 같은 시간이 걸린다.

### 2. 제거 : O(1) / O(N)
- 맨 앞에서 제거할땐 맨 앞의 노드 하나만 제거하면 되기 때문에 O(1)
- 맨 뒤의 값을 제거할땐 전체 리스트를 탐색해야 하므로 O(N)

### 3. 탐색 : O(N)
- 특정 값을 찾기 위해서는 전체 리스트를 처음부터 순차대로 순회해야한다.

---
## 참고
- [JavaScript 알고리즘 & 자료구조 마스터클래스](https://www.udemy.com/course/best-javascript-data-structures/)
- [생활코딩 : Linked List](https://opentutorials.org/module/1335/8821)
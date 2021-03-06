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

__π‘ Linked List μ λν΄ κ°μΈμ μΌλ‘ νμ΅νκ³  μ λ¦¬ν κΈμλλ€. νλ¦° λΆλΆμ΄λ μ€λ₯κ° μμ κ²½μ° λκΈλ‘ μλ €μ£Όμλ©΄ κ°μ¬νκ² μ΅λλ€!__
{: .notice--warning}

# __π Linked List__
* λ¬Όλ¦¬μ μΌλ‘ ν©μ΄μ Έ μλ μλ£λ€μ μλ‘ μ°κ²°νμ¬ νλλ‘ λ¬Άμ΄ κ΄λ¦¬νλ λ°μ΄ν° κ΅¬μ‘°
* λΈλ κ°μ μ°κ²°μ μ΄μ©ν΄ λ¦¬μ€νΈλ₯Ό κ΅¬νν κ²

## __νΉμ§__
- λ°μ΄ν°(λΈλ)μ λ§ν¬λ‘ κ΅¬μ±λμ΄ μμΌλ©° λ§ν¬κ° λΈλλ€μ μ°κ²°νλ μ­ν μ νλ€.
- λ°μ΄ν°λ€μ λ©μΈ λ©λͺ¨λ¦¬μμ μ΄λμλ ν©μ΄μ Έ μ‘΄μ¬ν  μ μλ€.
- μμλ₯Ό μ μ§νκΈ° μν΄ κ°κ°μ λ°μ΄ν°λ λ€μ λ°μ΄ν°λ₯Ό κ°λ¦¬ν€λ μ€μ κ°μ§λ€.
- μ²« λ°μ΄ν°μμλΆν° μμλλ‘ μ€μ λ°λΌκ°λ©΄ λͺ¨λ  λ°μ΄ν°λ₯Ό λ°©λ¬Έν  μ μλ€.
- λ°°μ΄μ²λΌ λ―Έλ¦¬ κ³΅κ°μ νλ³΄ν  νμλ μμΌλ©° νμν  λλ§λ€ λμ μΌλ‘ λΈλλ₯Ό μμ±ν΄ μ°κ²°νλ©΄ λλ€.
- λ§ν¬ νλλ₯Ό μν μΆκ° κ³΅κ°μ΄ νμνλ€.
- μ°μ°μ κ΅¬νμ΄λ μ¬μ© λ°©λ²μ΄ λ°°μ΄μ λΉν΄ λ³΅μ‘νμ¬ μ€λ₯κ° λ°μν  κ°λ₯μ±μ΄ λλ€.
- μ€λ₯κ° μλλΌλ λμ  ν λΉκ³Ό ν΄μ κ° λλ¬΄ λΉλ²νκ² μΌμ΄λλ©΄ λ©λͺ¨λ¦¬ κ΄λ¦¬λ₯Ό μν μ²λ¦¬μκ°μ΄ κΈΈμ΄μ Έ νλ‘κ·Έλ¨μ΄ λλ €μ§ μλ μλ€.

## __Array Vs. Linked List__
||Array|Linked List|
|:-:|-|-|
|__ν¬κΈ°__|μ΅μ΄ μ μΈ μ ν¬κΈ°λ‘ κ³ μ λλ©° μ¬μ©λμ§ μλ κ³΅κ°λ ν¨κ» ν λΉν΄μΌν΄μ λΉν¨μ¨μ μ|κ³ μ  λμ§ μμΌλ©° νμν λλ§λ€ μΆκ°νμ¬ κ³΅κ° νμ©μ΄ ν¨μ¨μ μ|
|__μ½μ__|μ€κ°μ λ°μ΄ν°λ₯Ό μ½μνκΈ° μ΄λ €μ μΆκ°νλ €λ μμΉ μ΄νμ λͺ¨λ  μλ£λ€μ μ λΆ νλμ© λ€λ‘ λ―Έλ μ°μ°μ΄ νμν¨|μ€κ°μ μ½μνκΈ° μ¬μ λ§ν¬λ§ μμ νλ©΄ λ¨|
|__μ­μ __|μ€κ°μ λ°μ΄ν°λ₯Ό μ­μ νκΈ° μ΄λ €μ μ­μ  ν λ¨μ λ°μ΄ν°λ€μ μμΉλ₯Ό λ€μ μ?κ²¨μ€μΌν¨|λ§ν¬λ§ μμ νλ©΄ λμ μ¬μ|
|__νμ__|μΈλ±μ€λ₯Ό μ¬μ©νλ©΄ λΉ λ₯΄κ² κ°λ₯|λ¬΄μ‘°κ±΄ μ²μλΆν° μμ°¨μ μΌλ‘ λΈλλ₯Ό μ°Ύμκ°λ κ³Όμ μ κ±°μ³μΌν΄μ ν¨μ¨μ΄ μ’μ§ λͺ»ν¨|
|__κ΅¬ν__|μ¬μ|μ΄λ €μ|

## __κ΅¬μ‘°__

![](https://user-images.githubusercontent.com/34249911/148717000-f487dd11-30d5-4c87-b074-070a6c26009b.png)

### __Node__
- μ°κ²° λ¦¬μ€νΈλ λΈλλ€μ μ§ν©μΌλ‘ μ΄λ€μ λ°μ΄ν°λ₯Ό μ μ₯νκ³  μκ³  μλ‘ μ°κ²°λμ΄ μλ€.
- μΌλ°μ μΈ λΈλλ ``λ°μ΄ν° νλ(data field)``μ ``λ§ν¬(link field)``λ‘ κ΅¬μ±λμ΄ μλ€.
- λ°μ΄ν° νλμλ μ μ₯νκ³ μ νλ λ°μ΄ν°κ° λ€μ΄κ°λ©° λ€μν μλ£νμ΄ μ¬ μκ° μλ€.
- λ§ν¬ νλμλ λ€μ λΈλμ μ£Όμλ₯Ό μ μ₯νλ€.
- μ°κ²° λ¦¬μ€νΈλ₯Ό νμνκΈ° μν΄μ  μ²«λ²μ§Έ λΈλμ μ£Όμλ₯Ό μμμΌ νλλ° μ΄ λΈλμ μ£Όμλ₯Ό μ μ₯νλ λΈλλ₯Ό ``Head`` νλ€. λ°λμ μ§μ ν΄μ€μΌ ν¨.
- μ°κ²° λ¦¬μ€νΈμ λ§μ§λ§μ λ§μ§λ§ λΈλμ λ§ν¬ νλλ₯Ό ``NULL`` κ°μΌλ‘ νμ¬ νννλ€. ``Tail`` μ΄λΌκ³ λ ν¨.

## __μ’λ₯__
### __1. Singly Linked List λ¨μ μ°κ²° λ¦¬μ€νΈ__
- νλμ λ°©ν₯μΌλ‘λ§ μ°κ²°λμ΄ μμΌλ©° λ§¨ λ§μ§λ§ λΈλμ λ§ν¬ νλλ NULL κ°μ κ°μ§λ€.

### __2. Circular Linked List μν μ°κ²° λ¦¬μ€νΈ__
- λ¨μ μ°κ²° λ¦¬μ€νΈμ κ°μ§λ§ λ§¨ λ§μ§λ§ λΈλμ λ§ν¬ κ°μ΄ λ€μ μ²«λ²μ§Έ λΈλλ₯Ό κ°λ¦¬ν¨λ€.

### __3. Doubly Linked List μ΄μ€ μ°κ²° λ¦¬μ€νΈ__
- κ° λΈλλ§λ€ λ§ν¬ νλκ° 2κ°μ© μ‘΄μ¬νλ©° κ°κ° μ ν λΈλ(previous node)μ νν λΈλ(next node)λ₯Ό κ°λ¦¬ν¨λ€.
  

## __κ΅¬ν__
### __κΈ°λ³Έ κ΅¬μ‘°__

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
    
### __μΆκ°__
#### __1. λ§¨ μμ μΆκ°(unshift)__
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
- μμ±ν μλ‘μ΄ λΈλμ next λ‘ head λ₯Ό μ§μ νλ€. head λ μ°κ²°λ¦¬μ€νΈμ λ§¨ μ²«λ²μ§Έ λΈλμ΄κΈ° λλ¬Έμ!
- κ·Έ ν head λ₯Ό μλ‘μ΄ λΈλλ‘ λ³κ²½νλ€.
- λ§μ½ head μ next κ° null μ΄λΌλ©΄, μ¦ λ¦¬μ€νΈμ λΈλκ° νλ λΏμ΄λΌλ©΄ κ·Έ λΈλλ head μ΄μ tail μ΄λ tail λ‘ μ€μ 
- λ¦¬μ€νΈμ κΈΈμ΄ + 1
  
#### __2. λμ μΆκ°(push)__
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
- λ¦¬μ€νΈμ κΈΈμ΄κ° 0 μ΄λΌλ©΄ addFirst λ₯Ό νΈμΆν΄ λ§¨ μμ μΆκ°
- νμ¬ λΈλμ λ§¨ λ§μ§λ§ λΈλμΈ tail μ nextλ‘ μλ‘μ΄ λΈλλ₯Ό μ€μ νκ³  tail μ μ λΈλλ‘ μ€μ 
- λ¦¬μ€νΈμ κΈΈμ΄ + 1

#### __3. μ€κ°μ μΆκ°__
- index μμΉμ Node νμ

```js
getNode(index){
    let node = this.head;
    
    for(let i = 0; i < index; i++){
        node = node.next;
    }

    return node;
}

// getNode λ€λ₯Έ λ°©μ
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

- λΈλ μΆκ°

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
- λ§μ½ index κ° 0μ΄λΌλ©΄ λ§¨ μμ μΆκ°νλκ±°λκΉ addFirst λ₯Ό νΈμΆ
- index μμΉμ λΈλμ μ΄μ  λΈλλ μμμΌ νλκΉ ``getNode(index - 1)`` λ‘ μ΄μ  λΈλλ₯Ό κ΅¬ν λ€ κ·Έ λΈλμ next μμ±μΌλ‘ index μ΄μ  λΈλμ index λΈλλ₯Ό κ΅¬νλ€.
- μλ‘μ΄ λΈλλ₯Ό μμ±ν΄ μ΄μ  λΈλμ next λ‘ μ€μ νκ³  νμ¬ λΈλμ next λ‘ index λΈλλ₯Ό μ€μ νλ€.
- λ§μ½ νμ¬ λΈλμ next κ° null μ΄λΌλ©΄ λ§μ§λ§ λΈλμ΄λ―λ‘ tail μ newNode λ‘ μ€μ 

### __μ­μ __
#### __1. μ²μ λΈλ μ­μ (shift)__
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
- head λΈλλ₯Ό first λΈλλ‘ μ§μ νκ³  first λΈλμ next λΈλμΈ λλ²μ§Έ λΈλλ₯Ό head λ‘ μ§μ νλ€.
- first λ₯Ό null λ‘, κΈΈμ΄λ -1 ν΄μ€λ€.

#### __2. μ€κ° λΈλ μ­μ __
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
- μ­μ ν  λΈλμ μ΄μ  λΈλλ₯Ό getNode λ‘ κ΅¬νκ³  κ·Έ λΈλμ next λ‘ μ­μ ν  λΈλλ₯Ό κ΅¬ν¨
- μ΄μ  λΈλμ next λ₯Ό μ­μ  λμ λΈλμ next λ‘ μ€μ 
- λ§μ½ μ­μ  λΈλκ° tail λΈλλΌλ©΄ tail μ μ΄μ  λΈλλ‘ μ€μ ν΄μ€

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
- head κ° null / undefined μ΄λ©΄ λ¦¬μ€νΈμ μλ¬΄ λ°μ΄ν°λ μλ κ²
- λ λΈλκΉμ§ μ°Ύμ λκΉμ§ νμνλ©΄ curNode λ λ§¨ λμ λΈλλ₯Ό newTail μ κ·Έ μ΄μ μ λΈλλ₯Ό κ°λ¦¬ν€κ² λλ€.

### __λ°μ΄ν° λ³κ²½__
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

### __λ¦¬μ€νΈ λ€μ§κΈ°__
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

## __μκ° λ³΅μ‘λ__
### 1. λ§¨ μ λ§¨ λ€ μ½μ : O(1)
- λ¦¬μ€νΈμ λ§¨ μμ΄λ λ§¨ λ€μ μλ‘μ΄ μμλ₯Ό μΆκ°ν  λ λ κ°μ μκ°μ΄ κ±Έλ¦°λ€.

### 2. μ κ±° : O(1) / O(N)
- λ§¨ μμμ μ κ±°ν λ λ§¨ μμ λΈλ νλλ§ μ κ±°νλ©΄ λκΈ° λλ¬Έμ O(1)
- λ§¨ λ€μ κ°μ μ κ±°ν λ μ μ²΄ λ¦¬μ€νΈλ₯Ό νμν΄μΌ νλ―λ‘ O(N)

### 3. νμ : O(N)
- νΉμ  κ°μ μ°ΎκΈ° μν΄μλ μ μ²΄ λ¦¬μ€νΈλ₯Ό μ²μλΆν° μμ°¨λλ‘ μνν΄μΌνλ€.

---
## μ°Έκ³ 
- [JavaScript μκ³ λ¦¬μ¦ & μλ£κ΅¬μ‘° λ§μ€ν°ν΄λμ€](https://www.udemy.com/course/best-javascript-data-structures/)
- [μνμ½λ© : Linked List](https://opentutorials.org/module/1335/8821)
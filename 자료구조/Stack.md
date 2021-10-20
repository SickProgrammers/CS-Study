# Stack이란 무엇인가?

## 목차
  - [스택의 개념](#스택의-개념)
  - [스택의 연산](#스택의-연산)
  - [스택의 구현](#스택의-구현)



## 스택의 개념

- 사전적 의미
```
스택의 사전적 의미는 '쌓다', '더미'와 같다.
```

- 스택은 리스트의 한쪽 끝으로 자료의 삽입, 삭제가 이루어지는 자료구조이다.
- 가장 최근에 들어온 자료가 가장 먼저 나가게 되는 '후입선출'의 형태를 가진다.
- 스택의 입출력은 맨 위에서만 일어나기 때문에 스택의 중간에는 데이터를 삭제하는 것이 불가능 하다.
- 스택이 입출력이 이루어지는 부분을 스택 상단 `Stack top`, 바닥 부분을 스택 하단 `Stack bottom`, 스택에 저장되는 것을 요소 `Element`라 부르며 스택에 요소가 하나도 없을 때 그러한 스택을 공백 스택 `Empty stack` 이라고 한다.
- 스택에 요소를 삽입하는 연산을 `PUSH`, 삭제 연산을 `POP` 라고 한다.


## 스택의 연산 메서드
- pop
  - 스택의 가장 최상위(마지막)에 위치한 데이터를 추출한 후에 스택에서 삭제합니다.
- push
  -  스택의 가장 최상위(마지막)에 데이터를 삽입합니다.
- isEmpty
  - 스택이 empty 상태인지 확인합니다.
- clear
  - 스택에 저장된 모든 데이터를 삭제하고 스택을 초기화합니다.
- peek
  - 스택의 가장 최상위(마지막)에 위치한 데이터를 추출합니다.
  - pop 메서드와는 달리 스택에서 데이터를 삭제하지 않습니다.


## 스택의 구현
```java
interface Stack{
    boolean isEmpty();
    boolean isFull();
    void push(char item);
    char pop();
    char peek();
    void clear();
}
 
public class ArrayStack implements Stack {
    
    private int top;
    private int stackSize;
    private char stackArr[];
 
    // 스택을 생성하는 생성자
    public ArrayStack(int stackSize) {
        top = -1;    // 스택 포인터 초기화
        this.stackSize = stackSize;    // 스택 사이즈 설정
        stackArr = new char[this.stackSize];    // 스택 배열 생성
    }
    
    // 스택이 비어있는 상태인지 확인
    public boolean isEmpty() {
        // 스택 포인터가 -1인 경우 데이터가 없는 상태이므로 true 아닌 경우 false를 return
        return (top == -1);
    }
    
    // 스택이 가득찬 상태인지 확인
    public boolean isFull() {
        // 스택 포인터가 스택의 마지막 인덱스와 동일한 경우 true 아닌 경우 false를 return
        return (top == this.stackSize-1);
    }
    
    // 스택에 데이터를 추가
    public void push(char item) {
        if(isFull()) {
            System.out.println("Stack is full!");
        } else {             
            stackArr[++top] = item;    // 다음 스택 포인터가 가리키는 인덱스에 데이터 추가
            System.out.println("Inserted Item : " + item);
        }
    }
    
    // 스택의 최상위(마지막) 데이터 추출 후 삭제
    public char pop() {
        if(isEmpty()) {
            System.out.println("Deleting fail! Stack is empty!");
            return 0;
        } else { 
            System.out.println("Deleted Item : " + stackArr[top]);
            return stackArr[top--];
        }                
    }
    
    // 스택의 최상위(마지막) 데이터 추출
    public char peek() {
        if(isEmpty()) {
            System.out.println("Peeking fail! Stack is empty!");
            return 0;
        } else { 
            System.out.println("Peeked Item : " + stackArr[top]);
            return stackArr[top];
        }
    }
    
    // 스택 초기화
    public void clear() {
        if(isEmpty()) {
            System.out.println("Stack is already empty!");
        } else {
            top = -1;    // 스택 포인터 초기화
            stackArr = new char[this.stackSize];    // 새로운 스택 배열 생성
            System.out.println("Stack is clear!");
        }
    }
    
    // 스택에 저장된 모든 데이터를 출력
    public void printStack() {
        if(isEmpty()) {
            System.out.println("Stack is empty!");
        } else {
            System.out.print("Stack elements : ");
            for(int i=0; i<=top; i++) {
                System.out.print(stackArr[i] + " ");
            }
            System.out.println();
        }
    }
}
```
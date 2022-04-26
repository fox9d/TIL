# Dispatch
- 어떤 메소드를 호출할 지 결정하고 실행시키는 과정을 디스패치라고 한다.
- 디스패치는 정적 디스패치(Static Dispatch)와 동적 디스패치(Dynamic Dispatch)가 있다.

### SuperInterface
```java
package com.example;  
  
public interface SuperInterface {  
    public void a();  
}
```

### Sub
```java
package com.example;  
  
public class Sub implements SuperInterface {  
    @Override  
    public void a() {  
        System.out.println("Override method");  
    }  
}
```

### Main
```java
package com.example;  
  
public class Main {  
  
    public static void main(String[] args) {  
  
        Sub sub = new Sub();  
        sub.a(); // 정적 디스패치  
  
        SuperInterface superInterface = new Sub();  
        superInterface.a(); // 동적 디스패치  
    }  
}
```

## Static Dispatch
- 컴파일 시점에 어떤 메소드가 실행될 지 인지하고 있는 경우
- 런타임이 아니더라도 어떤 메소드가 실행될 지 이미 결정되어 있다.

## Dynamic Dispatch
- 런타임 시점에 어떤 메소드를 실행될지 정해지는 경우
- 컴파일러가 컴파일시 어떤 메소드를 실행해야할 지 알 수 없기 때문에 런타임 시점에 결정한다.
	- 런타임 전에 인스턴스 생성이 불가능하기 때문에, 자료형에 대입되는 객체의 재정의된 메소드를 실행할 지 상위타입의 메소드를 실행할 지 알 수 없기 때문이다.

## bytecode
```java
// class version 52.0 (52)
// access flags 0x21
public class com/example/Main {

  // compiled from: Main.java

  // access flags 0x1
  public <init>()V
   L0
    LINENUMBER 3 L0
    ALOAD 0
    INVOKESPECIAL java/lang/Object.<init> ()V
    RETURN
   L1
    LOCALVARIABLE this Lcom/example/Main; L0 L1 0
    MAXSTACK = 1
    MAXLOCALS = 1

  // access flags 0x9
  public static main([Ljava/lang/String;)V
   L0
    LINENUMBER 7 L0
    NEW com/example/Sub
    DUP
    INVOKESPECIAL com/example/Sub.<init> ()V
    ASTORE 1
   L1
    LINENUMBER 8 L1
    ALOAD 1
    INVOKEVIRTUAL com/example/Sub.a ()V
   L2
    LINENUMBER 10 L2
    NEW com/example/Sub
    DUP
    INVOKESPECIAL com/example/Sub.<init> ()V
    ASTORE 2
   L3
    LINENUMBER 11 L3
    ALOAD 2
    INVOKEINTERFACE com/example/SuperInterface.a ()V (itf)
   L4
    LINENUMBER 12 L4
    RETURN
   L5
    LOCALVARIABLE args [Ljava/lang/String; L0 L5 0
    LOCALVARIABLE sub Lcom/example/Sub; L1 L5 1
    LOCALVARIABLE superInterface Lcom/example/SuperInterface; L3 L5 2
    MAXSTACK = 2
    MAXLOCALS = 3
}

```
- 위의 예시 Main 클래스에 대한 bytecode이다.
- `INVOKEVIRTUAL com/example/Sub.a ()V` 부분을 보면 정적 디스패치가 이루어진 것을 알 수 있다.
- `INVOKEINTERFACE com/example/SuperInterface.a ()V (itf)` 이 부분은 동적 메서드 부분인데, 인터페이스의 메서드를 명시하고 있는 것을 볼 수 있다.
	- 컴파일 시점에 인스턴스가 생성되지 않기 때문에 해당 타입의 메소드를 명시하고 있지만, 런타임 시점에선 Sub클래스의 재정의된 a() 메소드가 실행될 것이다.

### 실행결과
> Override method
Override method

## Double Dispatch
- 디스패치가 연속으로 두번 실행되는 것을 의미한다.


#### **참고**
https://doompok.tistory.com/21
https://defacto-standard.tistory.com/413
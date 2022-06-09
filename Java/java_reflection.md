# Reflection
- 런타임 시점에 class의 메타정보에 접근을 가능하게 해주는 JavaAPI

- 부모 타입으로 인스턴스를 생성했지만 자식이 가진 메서드를 사용하고 싶을때, reflectionAPI를 사용하여 실행할 수 있다.
	- 사용자가 작성하는 클래스의 정보는 static환경에 저장된다.
	- 컴파일된 bytecode(static area)에 접근하여 해당 클래스의 정보를 가져와 사용한다.


- 컴파일타임이 아닌 런타임에 작업이 시행되기 때문에 오버헤드가 발생할 수 있다.
	- 프레임워크나 라이브러리에 사용하는 것이 적절하다.


# 사용
```java
ClassName className = new ClassName();  
  
Class c = ClassName.class; // 클래스 정보 대입  
  
System.out.println(c.getClass());  
System.out.println(c.getName());  
  
Class c2 = Class.forName("com.example.ClassName"); // 클래스 이름으로 찾기  
  
System.out.println(c2.getName());  
  
String constructor = String.valueOf(c2.getConstructor());  
System.out.println(constructor);
```


---
참고
- 신용권. 이것이 자바다. 출판지: 한빛미디어(주)
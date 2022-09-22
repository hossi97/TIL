# Call by Value

자바를 처음 공부하다보면,

Call by Value 혹은 Call by Reference 라는 단어를 심심찮게 볼 수 있다.

`Call by Value` 를 직역하면 `값에 의한 호출` 을 의미하고,

`Call by Reference` 를 직역하면 `참조에 의한 호출` 을 의미한다.

용어의 의미에 대해 알아보기 전에,

먼저 아래 코드에 대해 생각해보자.

```java
public class Reference {

    public static void main(String[] args) {
        Reference ref = new Reference();
        ref.callByValue();
    }

    public void callByValue() {
        int num = 10;
        String str = "abc";

        System.out.println("=== before passValue ===");
        System.out.println("num = " + num);
        System.out.println("str = " + str);

        passValues(num, str);

        System.out.println("=== After passValue ===");
        System.out.println("num = " + num);
        System.out.println("str = " + str);
    }

    public void passValues(int num, String str) {
        num = 20;
        str = "ABC";

        System.out.println("=== In passValue ===");
        System.out.println("num = " + num);
        System.out.println("str = " + str);
    }

}
```

위 코드의 출력 결과는 어떻게 나올까?

결과는 아래와 같다.

```
=== before passValue ===
num = 10
str = abc
=== In passValue ===
num = 20
str = ABC
=== After passValue ===
num = 10
str = abc
```

## Java 의 자료형

기본적으로 Java 의 자료형은 2가지로 나뉜다.

-   원시형, Primitive Type
-   참조형, Reference Type

여기서 중요한 사실은

모든 Reference Type 의 클래스(혹은 객체)들은 `java.lang.Object` 클래스를 상속한다.

즉, 모든 Reference Type 의 최상위 조상은 `java.lang.Object` 클래스이다.

## Primitive Type 과 Reference Type 의 차이점

Primitive Type 과 Reference Type 사이에는 아주 큰 차이점이 있다.

그것은 바로 `값의 저장방식에 대한 차이` 이다.

Moshi
===

Moshi 是一个现代化的面向 Android 和 Java 的 JSON 库，它简化了 JSON 到 java 对象的转化过程。

```java
String json = ...;

Moshi moshi = new Moshi.Builder().build();
JsonAdapter<BlackjackHand> jsonAdapter = moshi.adapter(BlackjackHand.class);

BlackjackHand blackjackHand = jsonAdapter.fromJson(json);
System.out.println(blackjackHand);
```


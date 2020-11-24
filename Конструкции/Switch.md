java 8
```java
switch (value) {
    case 1:
    case 2:
    case 3:
        System.out.println("Hello");
        break;
}
```


java 12
```java
switch (value) {
    case 1, 2, 3:
        System.out.println("Hello");
        break;
}
```

_________________________________________________________
java 8
```java
switch (str) {
        case "1":
            value = 1;
            break;
        case "2":
            value = 2;
            break;
}
```



java 12
```java
int value = switch (str) {
    case "1" -> 1;
    case "2" -> 2;
    default -> 0;
};
```


вместо переменной и = можно использовать return

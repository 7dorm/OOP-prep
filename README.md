# СОВЕТЫ
    Если не по теме сказать скипнуть
    Не зависать долго
    Продавать себя
    Говорить по делу
    Быть уверенным в своем ответе
    Определения точно - обьяснение формально
    Наезжать если знаешь (задавить мозгами)
    ГОВОРИТЬ ОБОБЩЕННО

---

# ЗАУЧИТЬ
`Обьект - единица сущности обладающая своими свойствами и полями`


(при разном наборе аргументов спецификация одинаковая но поведение разное)
(Члены класса поэтому не перегрузка)

спецификация (параметры, метод, тд)

интерфейс поведение - абстрактный состояние

---

# ЗАПОМНИТЬ
## Типы

`(Stack) быстрый доступ, на завершении функции или метода удаляет все примитивные типы обьявленные в методе (хранят значение напрямую)`
```
Примитивные типы:
	Числовые типы:
		Целые:
			byte
			short
			int
			long
			char
		Вещественные:
			double
			float
```
`(Heap) объекты существуют дольше и очищаются GC (Хранят адрес объекта)`
```
Ссылочные типы:
	Массивы
	Классы
	Интерфейсы
```

## Коллекции 
```
Iterable<E> (интерфейс)
│  → Базовый интерфейс, поддерживает for-each. Есть Iterator.
│
└── Collection<E> (интерфейс)
    │  → Основной интерфейс коллекций (кроме Map).
    │
    ├── List<E> (интерфейс)
    │   → Упорядоченный список, доступ по индексу, допускает дубликаты.
    │
    │   ├── AbstractList<E> (абстрактный класс)
    │   │   → Частичная реализация List, оставляет только ключевые методы для дописывания.
    │   │
    │   ├── ArrayList<E> (класс)
    │   │   → Реализован на динамическом массиве. Быстрый доступ по индексу, медленные вставки в середину.
    │   │
    │   ├── Vector<E> (класс, устаревающий)
    │   │   → Как ArrayList, но синхронизированный. Медленнее.
    │   │
    │   │   └── Stack<E> (класс)
    │   │       → Реализация LIFO-стека на базе Vector.
    │   │
    │   ├── AbstractSequentialList<E> (абстрактный класс)
    │   │   → Основа для списков с последовательным доступом (не по индексу).
    │   │
    │   └── LinkedList<E> (класс)
    │       → Двусвязный список. Быстрые вставки/удаления, но доступ по индексу медленный (O(n)).
    │
    │   └── CopyOnWriteArrayList<E> (класс, потокобезопасный)
    │       → Копирует весь массив при изменении. Хорош для многопоточного чтения.
    │
    ├── Set<E> (интерфейс)
    │   → Множество: уникальные элементы, без индексов.
    │
    │   ├── HashSet<E> (класс)
    │   │   → Основан на HashMap. Элементы хранятся в хэш-таблице. Быстрый поиск/вставка O(1).
    │   │
    │   │   └── LinkedHashSet<E> (класс)
    │   │       → Как HashSet, но хранит порядок вставки.
    │   │
    │   ├── SortedSet<E> (интерфейс)
    │   │   → Множество с сортировкой (по natural order или Comparator).
    │   │
    │   │   └── NavigableSet<E> (интерфейс)
    │   │       → Добавляет методы навигации (floor, ceiling, lower, higher).
    │   │
    │   │       └── TreeSet<E> (класс)
    │   │           → Основан на красно-чёрном дереве (Balanced BST). Элементы всегда отсортированы.
    │   │
    │   └── CopyOnWriteArraySet<E> (класс)
    │       → Потокобезопасный Set на основе CopyOnWriteArrayList.
    │
    ├── Queue<E> (интерфейс)
    │   → Очередь FIFO или с приоритетом.
    │
    │   ├── Deque<E> (интерфейс)
    │   │   → Двусторонняя очередь (FIFO + LIFO).
    │   │
    │   │   ├── ArrayDeque<E> (класс)
    │   │   │   → Реализован на массиве, работает как стек и очередь. Быстрее, чем Stack/LinkedList.
    │   │   │
    │   │   └── LinkedList<E> (класс)
    │   │       → Может работать и как список, и как очередь/стек.
    │   │
    │   ├── PriorityQueue<E> (класс)
    │   │   → Основан на бинарной куче (heap). Элементы всегда извлекаются по приоритету (минимум или максимум).
    │   │
    │   └── ConcurrentLinkedQueue<E> (класс)
    │       → Неблокирующая очередь на атомарных CAS-операциях. Хороша для многопоточности.
    │
    └── BlockingQueue<E> (интерфейс, из java.util.concurrent)
        → Очередь с блокировкой при вставке/извлечении, используется для producer/consumer.
        │
        ├── ArrayBlockingQueue<E> (класс)
        │   → Ограниченная очередь на массиве. Блокируется при переполнении.
        │
        ├── LinkedBlockingQueue<E> (класс)
        │   → Очередь на связном списке. Может быть ограниченной или без ограничений.
        │
        ├── PriorityBlockingQueue<E> (класс)
        │   → Как PriorityQueue, но потокобезопасная.
        │
        ├── DelayQueue<E> (класс)
        │   → Элементы доступны только после истечения времени задержки (используется для задач с тайм-аутом).
        │
        └── SynchronousQueue<E> (класс)
            → Очередь ёмкостью 0: вставка блокируется, пока другой поток не извлечёт элемент.
```
```
Map<K,V> (интерфейс)
│  → Отображение ключ → значение. Ключи уникальны.
│
├── AbstractMap<K,V> (абстрактный класс)
│   → Базовая реализация Map.
│   │
│   ├── HashMap<K,V> (класс)
│   │   → Хэш-таблица. Быстрые операции O(1). Не гарантирует порядок.
│   │
│   │   └── LinkedHashMap<K,V> (класс)
│   │       → Хэш-таблица + двусвязный список. Сохраняет порядок вставки.
│   │
│   ├── TreeMap<K,V> (класс)
│   │   → Красно-чёрное дерево. Ключи всегда отсортированы.
│   │
│   └── WeakHashMap<K,V> (класс)
│       → Ключи на weak-ссылках. Автоматически удаляются GC.
│
├── Hashtable<K,V> (класс, устаревающий)
│   → Потокобезопасная версия HashMap. Синхронизированная, но медленная.
│   │
│   └── Properties (класс)
│       → Специализированный Hashtable<String,String>. Используется для конфигураций *.properties.
│
├── ConcurrentMap<K,V> (интерфейс)
│   → Потокобезопасные Map.
│   │
│   └── ConcurrentHashMap<K,V> (класс)
│       → Разделяет таблицу на сегменты. Высокая производительность в многопоточности.
│
└── IdentityHashMap<K,V> (класс)
    → Сравнивает ключи по == (сравнение ссылок), а не equals().
```

Пример:
```java
import java.util.*;
import java.util.concurrent.*;

public class CollectionsDemo {
    public static void main(String[] args) {
        // ===== List =====
        List<String> list = new ArrayList<>();
        list.add("A");
        list.add("B");
        list.add("B"); // допускает дубликаты
        System.out.println("List (ArrayList): " + list);
        System.out.println("Элемент по индексу 1: " + list.get(1));

        // ===== Set =====
        Set<String> set = new HashSet<>();
        set.add("A");
        set.add("B");
        set.add("B"); // дубликат проигнорируется
        System.out.println("Set (HashSet): " + set);

        // ===== SortedSet / TreeSet =====
        SortedSet<Integer> treeSet = new TreeSet<>();
        treeSet.add(5);
        treeSet.add(2);
        treeSet.add(10);
        System.out.println("TreeSet (отсортирован): " + treeSet);

        // ===== Queue =====
        Queue<String> queue = new LinkedList<>();
        queue.add("Первый");
        queue.add("Второй");
        queue.add("Третий");
        System.out.println("Queue (LinkedList): " + queue);
        System.out.println("poll(): " + queue.poll()); // забирает и удаляет первый
        System.out.println("После poll: " + queue);

        // ===== PriorityQueue =====
        PriorityQueue<Integer> pq = new PriorityQueue<>();
        pq.add(42);
        pq.add(5);
        pq.add(17);
        System.out.println("PriorityQueue (минимум первым): " + pq);
        System.out.println("poll(): " + pq.poll()); // вернёт 5

        // ===== Deque =====
        Deque<String> deque = new ArrayDeque<>();
        deque.addFirst("Начало");
        deque.addLast("Конец");
        System.out.println("Deque: " + deque);
        System.out.println("removeLast(): " + deque.removeLast());

        // ===== Map =====
        Map<String, Integer> map = new HashMap<>();
        map.put("Яблоко", 3);
        map.put("Апельсин", 5);
        map.put("Банан", 2);
        System.out.println("Map (HashMap): " + map);
        System.out.println("Значение по ключу 'Яблоко': " + map.get("Яблоко"));

        // ===== LinkedHashMap (сохраняет порядок) =====
        Map<String, Integer> linkedMap = new LinkedHashMap<>();
        linkedMap.put("A", 1);
        linkedMap.put("B", 2);
        linkedMap.put("C", 3);
        System.out.println("LinkedHashMap: " + linkedMap);

        // ===== TreeMap (сортировка по ключам) =====
        Map<String, Integer> treeMap = new TreeMap<>();
        treeMap.put("C", 3);
        treeMap.put("A", 1);
        treeMap.put("B", 2);
        System.out.println("TreeMap (сортировка по ключу): " + treeMap);

        // ===== ConcurrentHashMap =====
        ConcurrentMap<String, String> concurrentMap = new ConcurrentHashMap<>();
        concurrentMap.put("one", "один");
        concurrentMap.put("two", "два");
        System.out.println("ConcurrentHashMap: " + concurrentMap);
    }
}
/*
List (ArrayList): [A, B, B]
Элемент по индексу 1: B
Set (HashSet): [A, B]
TreeSet (отсортирован): [2, 5, 10]
Queue (LinkedList): [Первый, Второй, Третий]
poll(): Первый
После poll: [Второй, Третий]
PriorityQueue (минимум первым): [5, 42, 17]
poll(): 5
Deque: [Начало, Конец]
removeLast(): Конец
Map (HashMap): {Апельсин=5, Банан=2, Яблоко=3}
Значение по ключу 'Яблоко': 3
LinkedHashMap: {A=1, B=2, C=3}
TreeMap (сортировка по ключу): {A=1, B=2, C=3}
ConcurrentHashMap: {one=один, two=два}
*/
```

`Collections: класс со статическими методами (сортировка, поиск, создание неизменяемых коллекций)`

`Arrays: методы для массивов, конвертация в списки`

### Неизменяемые коллекции
```java
List.of(1, 2, 3)
Map.of("k1", 1, "k2", 2)
```

## Исключения
```
Throwable
├─ Error
│   ├─ VirtualMachineError - ошибка виртуальной машины
│   │   ├─ OutOfMemoryError - недостаточно памяти в heap
│   │   ├─ StackOverflowError - переполнение стека
│   │   └─ InternalError - внутренная ошибка JVM
│   ├─ LinkageError - проблемы с загрузкой/связкой классов
│   │   ├─ NoClassDefFoundError - класс не найден
│   │   ├─ ClassFormatError - некорректный формат .class
│   │   └─ UnsatisfiedLinkError - не удалось подключить натвиную библиотеку
│   ├─ AssertionError - неудачная проверка assert
│   └─ ThreadDeath - Поток завершён с помощью stop()
│
└─ Exception
    ├─ IOException - ошибки I/O
    │   ├─ FileNotFoundException - файл не найден
    │   ├─ EOFException - конец потока достигнут неожиданно
    │   └─ SocketException - ошибка сокета
    ├─ SQLException - ошибка работы с БД
    ├─ ClassNotFoundException - класс не найден при динамической загрузке
    ├─ InterruptedException - поток был прерван во премя ожидания
    ├─ ReflectiveOperationException - ошибки при рефлексии
    │   ├─ IllegalAccessException - доступ к классу/методу/полю запрещён
    │   ├─ InvocationTargetException - вызов метода через reflection вызвал исключение
    │   └─ InstantiationException - нельзя создать экземпляр класса 
    ├─ RuntimeException - unchecked исключения, часто ошибки логики
    │   ├─ NullPointerException - обращение к null
    │   ├─ IndexOutOfBoundsException - индекс вне допустимого диапазона
    │   │   ├─ ArrayIndexOutOfBoundsException - индекс массива
    │   │   └─ StringIndexOutOfBoundsException - индекс строки
    │   ├─ IllegalArgumentException - неправильный аргумент метода
    │   │   └─ NumberFormatException - ошибка преобразования строки в число Integer.valueOf();
    │   ├─ IllegalStateException - метод вызван в некорректном состоянии объекта
    │   ├─ ArithmeticException - арифметическая ошибка
    │   ├─ ClassCastException - неправильное приведение типов
    │   ├─ UnsupportedOperationException - операция не поддерживается (неизменяемая коллекция)
    │   └─ ConcurrentModificationException -  коллекция изменялась во время итерации
    └─ (другие checked)
```

## Аннотация

`Аннотация - метаданные, которые можно прикреплять к методам, классам, полям, параметрам и т.д.`

### Как создать свой

```java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface Loggable {
    String level() default "INFO";
}

@Loggable(level = "DEBUG")
public class MyService {

    @Loggable
    public void doWork() {
        System.out.println("Working...");
    }
}
```
### Популярные применения:
- Логирование (@Loggable, @Audit).
- Валидация (@NotNull, @Length).
- Конфигурация фреймворков (DI, JPA, Spring).
- Генерация кода (Lombok — @Getter, @Builder).

## Декоратор

`Декоратор - структурный паттерн, позволяющий динамически добавлсять объекту новое поведение, оборачивая его в другой объект с тем же интерфейсом`

Пример
```java
interface Printer {
    void print(String msg);
}

class ConsolePrinter implements Printer {
    public void print(String msg) { System.out.println(msg); }
}

class TimestampDecorator implements Printer {
    private final Printer delegate;
    TimestampDecorator(Printer delegate) { this.delegate = delegate; }
    public void print(String msg) {
        delegate.print("[" + System.currentTimeMillis() + "] " + msg);
    }
}
```

## Полиморфизм
`Полиморфизм - Возможность обьектов с одинаковой спецификацией иметь различную реализацию`

### Статичный
```java
class MathUtils {
    // Перегрузка метода (overloading)
    public int add(int a, int b) {
        return a + b;
    }

    public double add(double a, double b) {
        return a + b;
    }

    public String add(String a, String b) {
        return a + b;
    }
}
```

### Динамический

```java
class Animal {
    public void makeSound() {
        System.out.println("Some generic sound...");
    }
}

class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Woof!");
    }
}

class Cat extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Meow!");
    }
}
```

### Параметрический

```java 
class Box<T> { 
    private T value;

    public Box(T value) {
        this.value = value;
    }

    public T getValue() {
        return value;
    }

    public void setValue(T value) {
        this.value = value;
    }
}

public class ParametricPolymorphismDemo {
    public static void main(String[] args) {
        Box<Integer> intBox = new Box<>(123);
        Box<String> strBox = new Box<>("Hello!");

        System.out.println(intBox.getValue()); 
        System.out.println(strBox.getValue());
    }
}
```



примитивные типы не могут generic параметрами


## Инкапсуляция
`Инкапсуляция - сокрытие внутреннего состояния объекта и управление доступом к нему через методы`

```java 
class BankAccount {
    // поля закрыты (private) -> напрямую к ним доступ запрещён
    private String owner;
    private double balance;

    // конструктор
    public BankAccount(String owner, double balance) {
        this.owner = owner;
        this.balance = balance;
    }

    // геттер (чтение)
    public double getBalance() {
        return balance;
    }

    // сеттер (контролируемое изменение)
    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
        } else {
            System.out.println("Недостаточно средств!");
        }
    }
}
```

## Абстракция
`Абстракция - выделение только значимых характеристик объекта и сокрытие ненужных деталей реализации.`

```java 
abstract class Shape {
    // абстрактный метод (нет реализации)
    public abstract double area();

    // общий метод (есть реализация)
    public void printArea() {
        System.out.println("Площадь = " + area());
    }
}

class Circle extends Shape {
    private double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double area() {
        return Math.PI * radius * radius;
    }
}

class Rectangle extends Shape {
    private double width, height;

    public Rectangle(double width, double height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public double area() {
        return width * height;
    }
}

public class AbstractionDemo {
    public static void main(String[] args) {
        Shape s1 = new Circle(5);
        Shape s2 = new Rectangle(4, 6);

        s1.printArea(); // Площадь = 78.54
        s2.printArea(); // Площадь = 24
    }
}
```

## Наследование
`Наследование — это механизм ООП, при котором один класс (дочерний, подкласс) может использовать поля и методы другого класса (родительский, суперкласс)`

```java 
// Родительский класс
class Animal {
    String name;

    public Animal(String name) {
        this.name = name;
    }

    public void eat() {
        System.out.println(name + " ест.");
    }

    public void sleep() {
        System.out.println(name + " спит.");
    }
}

// Дочерний класс
class Dog extends Animal {
    public Dog(String name) {
        super(name); // вызов конструктора родителя
    }

    // свой метод
    public void bark() {
        System.out.println(name + " лает: Гав!");
    }

    // переопределение метода
    @Override
    public void eat() {
        System.out.println(name + " ест косточку.");
    }
}

// Ещё один подкласс
class Cat extends Animal {
    public Cat(String name) {
        super(name);
    }

    @Override
    public void eat() {
        System.out.println(name + " ест рыбу.");
    }
}
```



## StreamAPI
`Stream API — это новый способ работать со структурами данных в функциональном стиле.`

### Способы создания
Схема работы:
```
Источник --- Промежуточные операторы --- Терминальный оператор
```

#### Из коллекции
```java
List<String> names = Arrays.asList("Anna", "Bob", "Alex");

// последовательный поток
Stream<String> stream1 = names.stream();

// параллельный поток
Stream<String> stream2 = names.parallelStream();
```

#### Из массива
```java
String[] arr = {"Anna", "Bob", "Alex"};

// через Arrays.stream
Stream<String> stream1 = Arrays.stream(arr);
```

#### Из значений
```java
Stream<String> stream2 = Stream.of("Anna", "Bob", "Alex");
```

#### С изпользованием генератором
```java
Stream<Double> randomNumbers = Stream.generate(Math::random).limit(5);
```

#### С использованием итератора

```java 
Stream<Integer> evenNumbers = Stream.iterate(0, n -> n + 2).limit(5);
```

#### Из BufferedReader.lines()
```java 
Path path = Paths.get("example.txt");

try (Stream<String> lines = Files.lines(path)) {
    lines.forEach(System.out::println);
}
```

#### Из Spliterator или StreamSupport
```java
List<String> list = Arrays.asList("A", "B", "C");
Spliterator<String> spliterator = list.spliterator();

Stream<String> stream = StreamSupport.stream(spliterator, false);
stream.forEach(System.out::println);
```


### Промежуточные операторы
Каждый промежуточный оператор возвращает Stream и не выполняется пока не будет вызван терминальный оператор

- `filter(Predicate<T>)` - фильтрует элементы
- `map(Function<T,R>)`- преобразует каждый элемент
- `flatMap(Function<T,Stream<R>>)` - «разворачивает» вложенные стримы
- `distinct()` - убирает дубликаты
- `sorted() / sorted(Comparator)` - сортирует элементы
- `limit(n)` - берёт только первые n элементов
- `skip(n)` - пропускает первые n элементов
- `peek(Consumer<T>)` - позволяет заглянуть внутрь (обычно для отладки)

### Терминальные операторы
Каждый терминальный оператор завершает работу потока, после чего этот поток нельзя больше использовать. Запускает выполнение всех промежуточных операций

- `forEach(Consumer<T>)` - применяет действие ко всем элементам
- `collect(Collector)` - собирает результат в коллекцию, строку, Map
- `reduce()` - свёртка (агрегация) в одно значение
- `count()` - количество элементов
- `min(Comparator) / max(Comparator)` - минимум / максимум
- `findFirst() / findAny()` - первый элемент / любой элемент
- `anyMatch(Predicate)` - есть ли хотя бы один элемент, удовлетворяющий условию
- `allMatch(Predicate)` - все ли удовлетворяют условию
- `noneMatch(Predicate)` - ни один не удовлетворяет условию
- `toArray()` - собрать в массив

### Функциональные интерфейсы

#### `Predicate<T>` - проверка условия для элемента

`Тип`: _@FunctionalInterface_ с методом __boolean test(T t)__

Пример:
```java
Predicate<String> startsWithA = s -> s.startsWith("A");
```

#### `Function<T, R>` - преобразование объекта типа T в объект типа R
`Тип`: _@FunctionalInterface_ с методом __R apply(T t)__

Пример:
```java 
Function<String, Integer> lengthFunc = String::length;
```

#### `Comparator<T>` - сравнение двух объектов (-1, 0, 1);
`Тип`: _@FunctionalInterface_ с лямбда-совместимым методом __int compare(T o1, T o2)__

Пример:
```java
Comparator<String> byLength = (a, b) -> Integer.compare(a.length(), b.length());
```

#### `Comsumer<T>` - принимает объект и выполняет действие ничего не возвращая
`Тип`: _@FunctionalInterface_ с методом __void accept(T t)__

Пример:
```java
Consumer<String> printUpper = s -> System.out.println(s.toUpperCase());
```

#### `Collector<T, A, R>` - определяет стратегию, как собрать поток в результат

`Тип`: интерфейс из java.util.stream

Пример:
```java
List<String> result = names.stream()
    .filter(n -> n.startsWith("A"))
    .collect(Collectors.toList());

String joined = names.stream()
    .collect(Collectors.joining(", "));
```

### Структура наследования
```
BaseStream<T, S extends BaseStream<T, S>>  (базовый интерфейс)
   │
   ├── Stream<T>         (объектные потоки)
   │
   ├── IntStream         (потоки int)
   │
   ├── LongStream        (потоки long)
   │
   └── DoubleStream      (потоки double)
```

### Примитивные специализированные потоки

Чтобы избежать автоупаковки/распаковки, для примитивов есть отдельные интерфейсы:
-   IntStream
-	LongStream
-	DoubleStream

👉 Они тоже наследуются от BaseStream, но добавляют методы для работы с конкретными типами:
-	sum(), average(), min(), max()
-	range(), rangeClosed() (только у IntStream/LongStream)

### Дополнительные элементы

-  Collectors - используется, чтобы собрать поток обратно в коллекцию или агрегировать данные.
- Spliterator - разбивает элементы на части для параллельной обработки.
  - Основные методы
    - `tryAdvance(Consumer<? super T> action)` — аналог `Iterator.next()`.
    -	`trySplit()` — делит источник на две части (важно для `parallelStream()`).
    -	`estimateSize()` — примерная оценка количества элементов.
    -	`characteristics()` — характеристики (например, ORDERED, SORTED, SIZED).
  - Характеристики
    - `ORDERED` — элементы имеют порядок
	- `DISTINCT` — уникальные элементы
	- `SORTED` — элементы отсортированы
	- `SIZED` — известен размер
	- `IMMUTABLE` — структура не изменяется
	- `CONCURRENT` — потокобезопасный

Пример использование Spliterator
```java
import java.util.*;
import java.util.Spliterator;

public class SpliteratorDemo {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Anna", "Bob", "Alex", "Alice");

        Spliterator<String> spliterator = names.spliterator();

        // обработка одного элемента
        while(spliterator.tryAdvance(System.out::println));

        System.out.println("--- Разделение ---");

        Spliterator<String> split1 = names.spliterator();
        Spliterator<String> split2 = split1.trySplit(); // делим на две части

        System.out.println("Первая часть:");
        split1.forEachRemaining(System.out::println);

        System.out.println("Вторая часть:");
        if(split2 != null)
            split2.forEachRemaining(System.out::println);
    }
}
```

1. Любой _Collection_ (List, Set) может создавать __Spliterator__
2. _Stream_ создается через `spliterator()`


Пример ручного создания потока:
```java
Spliterator<String> spliterator = names.spliterator();
Stream<String> customStream = StreamSupport.stream(spliterator, true); // true → parallel
```


## Generics

`Generics позволяют создавать классы, интерфейсы и методы, которые работают с разными типами данных, не теряя типобезопасности.`

Пример:
```java
class Box<T> {
    private T value;

    public void set(T value) { this.value = value; }
    public T get() { return value; }
}

Box<Integer> intBox = new Box<>();
intBox.set(10);
int x = intBox.get(); // нет необходимости в cast
```

### Наследование

#### Базовое наследование

```java
class Parent<T> {
    T value;
    void set(T value) { this.value = value; }
    T get() { return value; }
}

class Child<T> extends Parent<T> {
    void print() { System.out.println(get()); }
}
```

#### Наследование с фиксированным типом
```java
class IntegerParent<T> {
    T value;
    T get() { return value; }
}

class IntegerChild extends IntegerParent<Integer> {
    void print() { System.out.println(get()); }
}
```

#### Ограничения
```java
class NumberBox<T extends Number> {
    private T value;
    T get() { return value; }
    void set(T value) { this.value = value; }
}

NumberBox<Integer> intBox = new NumberBox<>();
NumberBox<Double> doubleBox = new NumberBox<>();
// NumberBox<String> strBox = new NumberBox<>(); // ❌ Ошибка компиляции
```

#### Wildcards (неопределённый тип)
```java
List<? extends Number> list1; // может хранить List<Integer> или List<Double>
List<? super Integer> list2;   // может хранить List<Integer>, List<Number>, List<Object>
```

- `? extends T` → ограничение сверху (covariant)
- `? super T` → ограничение снизу (contravariant)
  
### Cхема наследования
```
Object
  │
  ├─ Number
  │    ├─ Integer
  │    ├─ Double
  │    ├─ Long
  │    └─ ...
  │
  └─ Other classes

Generic<T>
  │
  ├─ Box<T>
  │    ├─ Child<T>           // наследник с тем же параметром
  │    └─ IntegerChild        // наследник с фиксированным типом Integer
  │
  ├─ Bounded<T extends Number>
  │
  └─ Collections (List<T>, Set<T>, Map<K,V>)
       └─ ArrayList<T>, HashSet<T>, HashMap<K,V>
```

## Модификаторы доступа
`Модификаторы доступа — это чаще всего ключевые слова, которые регулируют уровень доступа к разным частям твоего кода.`

4 модификатора доступа:
- `private` - ограничивает видимость данных и методов пределами одного класса
- `default` (package visible) - установлен в Java по умолчанию для всех полей и методов
- `protected` - Поля и методы, обозначенные модификатором доступа protected, будут видны: в пределах всех классов, находящихся в том же пакете, что и наш; в пределах всех классов-наследников нашего класса.
- `public` - поля и методы, объявленные с модификатором public, видны другим классам из текущего пакета и из внешних пакетов, вообще в любом месте программы

- `final` - после инициализации конструктора все потоки обязательно получают инициализированную переменную (happend-before)
- `static` - 

## Отношения между классами

- `Generalization` → наследование (extends).
- `Realization` → реализация интерфейса (implements).
- `Dependency` → использование в методах.
- `Association` - ссылка на другой объект.
- `Aggregation` - слабое “часть-целое” (объекты независимы).
- `Composition` - сильное “часть-целое” (жизнь частей зависит от целого).

## Параллелелилзм
`Параллелизм — это выполнение нескольких задач одновременно`
- `Многопоточность` (multithreading) — несколько потоков в одном процессе.
- `Многопроцессность` (multiprocessing) — несколько процессов (обычно тяжелее, чем потоки).
- `Асинхронность` (async) — переключение задач без ожидания блокировок (чаще в event loop).

### Отличие потока от процесса
```
Процесс:
+---------------------------+
|   Процесс (адресное пр-во)|
|   +-------------------+   |
|   | Код               |   |
|   | Данные (heap)     |   |
|   | Стек              |   |
+---------------------------+

Потоки внутри процесса:
+---------------------------+
|   Процесс (общая память)  |
|   +-------------------+   |
|   | Thread 1 (стек 1) |   |
|   | Thread 2 (стек 2) |   |
|   | Thread 3 (стек 3) |   |
+---------------------------+
```

### Общая архитектура параллелелизма

```
Параллелизм
│
├── Процессы (Processes)
│   ├── Изолированные адресные пространства
│   ├── IPC (взаимодействие через каналы/сокеты/общую память)
│   └── Тяжёлые в создании и переключении
│
├── Потоки (Threads)
│   ├── Общая память внутри процесса
│   ├── Лёгкие в создании
│   └── Нужно синхронизировать доступ к данным
│
├── Асинхронность (Async / Event Loop)
│   ├── Не обязательно новые потоки
│   ├── Использует неблокирующий ввод-вывод
│   └── Планировщик переключает задачи
│
└── Гибридные модели
    ├── Пулы потоков (Thread Pools) 
    ├── Акторы (Akka, Erlang) 
    └── Зеленые потоки / корутины
```

Сравнение:

Модель | Как работает | Плюсы | Минусы | Примеры
--- | --- | --- | --- | ---
Thread Pool | ОС-потоки, задачи ставятся в очередь | Просто, эффективно | Ограничено числом потоков | Java Executors, C++ thread pool
Акторы | Объекты с очередью сообщений, без общей памяти | Упрощает многопоточность, подходит для распределённых систем | Иногда накладные расходы на передачу сообщений | Akka, Erlang, Orleans
Зелёные потоки / Корутины | Лёгкие потоки на уровне VM/рантайма | Очень дешёвые, масштабируются до миллионов |Сложнее отладка, нужна поддержка VM | Go, Kotlin, Loom


### Параллелелизм в Java

#### Threads  
```java
class MyTask extends Thread {
    public void run() {
        System.out.println("Running in thread: " + Thread.currentThread().getName());
    }
}

public class Main {
    public static void main(String[] args) {
        new MyTask().start();
    }
}
```
    - Прямое управление потоками.
    - Нужно вручную следить за синхронизацией.

#### Runnable/Callable
```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Runnable executed!");
    }
}

class MyCallable implements java.util.concurrent.Callable<String> {
    public String call() {
        return "Result from Callable";
    }
}
```
	- Runnable — задача без возврата.
	- Callable<T> — задача с возвратом результата (Future<T>).

#### Executor Framework
```java
import java.util.concurrent.*;

public class Main {
    public static void main(String[] args) throws Exception {
        ExecutorService pool = Executors.newFixedThreadPool(2);

        Future<String> result = pool.submit(() -> "Hello from thread pool");

        System.out.println(result.get());
        pool.shutdown();
    }
}
```
    - Управление пулом потоков.
	- Не нужно создавать потоки вручную.
	- Поддержка Future, Callable.

#### Fork/Join Framework
```java
import java.util.concurrent.*;

class MyTask extends RecursiveTask<Integer> {
    int[] arr; int start, end;

    MyTask(int[] arr, int start, int end) {
        this.arr = arr; this.start = start; this.end = end;
    }

    @Override
    protected Integer compute() {
        if (end - start <= 2) {
            int sum = 0;
            for (int i = start; i < end; i++) sum += arr[i];
            return sum;
        }
        int mid = (start + end) / 2;
        MyTask left = new MyTask(arr, start, mid);
        MyTask right = new MyTask(arr, mid, end);
        left.fork();
        return right.compute() + left.join();
    }
}
```
    Подходит для больших задач, которые делятся на подзадачи.

#### Parallel Streams
```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        List<Integer> nums = Arrays.asList(1,2,3,4,5,6);

        nums.parallelStream()
            .map(n -> n * n)
            .forEach(System.out::println);
    }
}
```
	Простая параллельная обработка коллекций.
	Основано на Fork/Join.

#### CompletableFuture
```java
import java.util.concurrent.*;

public class Main {
    public static void main(String[] args) {
        CompletableFuture.supplyAsync(() -> "Async result")
                .thenAccept(System.out::println);
    }
}
```
	Поддерживает цепочки асинхронных задач.
	Удобнее, чем Future.
    Асинхронность (CompletableFuture) построена поверх пула потоков.

### Дерево зависимостей

```
Java Concurrency
│
├── Потоки (Thread API)
│   ├── Thread (extends Thread)
│   ├── Runnable
│   └── Callable + Future
│
├── Executor Framework
│   ├── ThreadPoolExecutor
│   ├── ScheduledExecutorService
│   └── Future, CompletionService
│
├── Fork/Join Framework
│   ├── RecursiveTask<T>
│   └── RecursiveAction
│
├── Parallel Streams
│   └── parallelStream()
│
└── Асинхронность
    └── CompletableFuture
```

### Ключевые слова синхронизации
#### `synchronized`
- Делает код потокобезопасным.
- Вход в блок → очищение кешей потока.
- Выход из блока → запись всех изменений в общую память.
- Только один может зайти в 

```java
class Counter {
    private int count = 0;

    // Синхронизированный метод
    public synchronized void increment() {
        count++;
    }

    // Синхронизированный блок
    public void decrement() {
        synchronized (this) {
            count--;
        }
    }

    public int getCount() {
        return count;
    }
}
```

#### `volatile`
- Используется, когда нужно, чтобы переменная была видна всем потокам сразу.
- Не делает операции атомарными (например, count++ не защищено).
```java
class Flag {
    private volatile boolean running = true;

    public void stop() {
        running = false; // изменения увидят все потоки
    }

    public void run() {
        while (running) {
            // работа
        }
    }
}
```

#### `final` 
- Гарантирует, что после инициализации объекта final-поля становятся видимыми для других потоков
- Но не защищает от изменения содержимого объекта, на который ссылается поле.
- Это часть Java Memory Model (JMM).
```java
class Config {
    final int size;
    Config(int size) {
        this.size = size; // гарантированная публикация
    }
}
```

#### `static`
- модификатор, применяемый к полю, блоку, методу или внутреннему классу. 
- Данный модификатор указывает на  привязку субъекта  к текущему классу.
- Если переменная статична, то глобальное её значение одно для всех
- Если блок статичен, то он инициализирует внутренние статические переменные
- Статические методы так же привязанны к классу

#### `wait/notify/notifyAll`
- Не явлюятся ключевыми словами. Это методы класса Object
- Работают только вместе с synchronized.
- Реализуют “кооперацию потоков” (одни ждут, другие подают сигнал).
- `wait()` — поток ждёт, пока его не разбудят.
- `notify()` — будит один поток, который ждал на этом мониторе.
- `notifyAll()` — будит все потоки.
```java
class Shared {
    private boolean ready = false;

    public synchronized void waitForSignal() throws InterruptedException {
        while (!ready) {
            wait(); // ждем сигнала
        }
        System.out.println("Got signal!");
    }

    public synchronized void sendSignal() {
        ready = true;
        notifyAll(); // разбудим все потоки
    }
}
```

### Активные/Пассивные объекты
Характеристика | Пассивный объект | Активный объект
---|---|---
Поток | Не создаёт поток |Имеет собственный поток
Синхронизация | Внешняя | Внутренняя (сам управляет)
Инициатор действий | Вызов извне | Сам выполняет работу
Примеры | Буфер, счётчик, очередь | Thread, Executor Worker, Actor
- Пассивные объекты → данные, ресурсы, модели, к которым обращаются потоки.
- Активные объекты → фоновые воркеры, серверные обработчики, таймеры, Actor-модели.

## JMM (Java Memory Model)
`JMM (Java Memory Model) — это модель памяти Java, которая определяет, как многопоточные программы взаимодействуют с памятью.`

- В многопоточной среде каждый поток может кешировать переменные в регистрах или в CPU-кэше.
- Без правил один поток мог бы “не увидеть” изменения другого.
- JMM вводит строгие правила: когда изменения из одного потока становятся видимыми для других.

### Основные принципы
#### Main memory vs Working memory
- `Main memory` → общая память (heap).
- `Working memory` → локальные кеши потоков (регистры, CPU-кэш).

Каждый поток копирует переменные из основной памяти к себе, и работает с ними.
Поэтому без синхронизации данные могут быть устаревшими.

#### Happens-before
`Eсли одно действие “happens-before” другого, то результат первого гарантированно виден второму.`

Примеры правил:
- Вход в synchronized блок - видим все изменения, сделанные предыдущим потоком в этом мониторе.
- Выход из synchronized блока - все изменения сбрасываются в main memory.
- Запись в volatile переменную - видна всем, кто потом её читает.
- Завершение конструктора - все final-поля гарантированно видимы.
- Вызов start() потока - все изменения до start() будут видны в новом потоке.
- Вызов join() - все изменения в потоке будут видны после завершения.

#### Перемешивание инструкций (Reordering)

`Компилятор и процессор могут менять порядок исполнения команд для оптимизации. Но JMM гарантирует, что относительно happens-before это безопасно.`

### Важные гарантии JMM
1.	`Atomicity` (атомарность) — какие операции выполняются “неделимо” (например, чтение/запись volatile long 64-бит).
2.	`Visibility` (видимость) — изменения одного потока становятся видимыми другим.
3.	`Ordering` (упорядоченность) — операции происходят в определённом порядке с точки зрения других потоков.

`Атомарная операция — это операция, которая выполняется полностью или не выполняется вовсе, и невозможно её прервать или увидеть промежуточное состояние другим потоком.`

## ClassLoader
Принципы работы ClassLoader (загрузчика классов)
Загрузчики классов отвечают за загрузку, связывание и инициализацию Java-классов. 
![img](https://habrastorage.org/r/w1560/getpro/habr/upload_files/eb5/76d/0f0/eb576d0f0ea8c56c71ad302afa08a37f.png)
- Иерархия: Загрузчики классов образуют иерархию, где каждый загрузчик может делегировать загрузку класса своему родительскому загрузчику.
- Принцип делегирования: При получении запроса на загрузку класса, загрузчик сначала передает его родительскому загрузчику. Только если родительский загрузчик не может найти класс, его загружает дочерний загрузчик.
- Загрузка классов: Процесс включает в себя поиск и загрузку .class файлов, их проверку и подготовку к выполнению.

## JSM (Java Security Model)
1. Policy
Это основной файл политики безопасности (java.policy), который определяет, какие права имеет код в зависимости от:
- источника (CodeSource: URL, протокол, подпись);
- загруженного класса (ClassLoader).
- Хранится обычно в:
  - $JAVA_HOME/lib/security/java.policy (глобальная политика);
  - ~/.java.policy (пользовательская политика);
  - можно задать свой через -Djava.security.policy=....
Пример политики:
```java
grant codeBase "file:/home/user/app/-" {
    permission java.io.FilePermission "/tmp/*", "read,write";
    permission java.net.SocketPermission "localhost:1024-", "connect,resolve";
};
```
Это значит:
- всему коду из /home/user/app/ разрешается читать/писать файлы в /tmp/,
- и соединяться по сокетам к localhost.

2. Permissions
Это конкретные права, которыми управляет Policy. Каждое разрешение — это объект-наследник java.security.Permission.
Основные типы:
- FilePermission – доступ к файловой системе;
- SocketPermission – работа с сетью;
- RuntimePermission – доступ к системным операциям (exitVM, setSecurityManager, getClassLoader и т. д.);
- PropertyPermission – чтение/запись системных свойств;
- AllPermission – полный доступ (обычно не рекомендуется).

Пример кода:
```java
Permission p = new FilePermission("/tmp/*", "read");
System.out.println(p.getActions()); // read
```

3. AccessController
- Это механизм проверки прав во время выполнения.
- Работает через стек вызовов: если метод пытается выполнить действие (например, открыть файл), JVM вызывает AccessController.checkPermission(...).
- Проверяется, есть ли у всех классов в стеке вызова нужное разрешение.
- Если нет — выбрасывается AccessControlException.

Пример:
```java
import java.security.AccessController;
import java.security.PrivilegedAction;

public class Main {
    public static void main(String[] args) {
        // Запуск привилегированного кода
        String userHome = AccessController.doPrivileged(
            (PrivilegedAction<String>) () -> System.getProperty("user.home")
        );
        System.out.println(userHome);
    }
}
```
Здесь doPrivileged отрезает стек вызовов выше этого места: проверка прав идёт только для текущего кода, а не для всех вызывающих.

4. Как это работает вместе
	1.	Программа выполняется → вызывает чувствительную операцию (чтение файла, открытие сокета, системное свойство).
	2.	JVM вызывает AccessController.checkPermission().
	3.	checkPermission идёт по стеку вызовов, сверяет каждую функцию с Policy.
	4.	Если у каждого класса в стеке есть это право → операция разрешается.
	5.	Если хотя бы у одного нет → AccessControlException.

doPrivileged нужен, чтобы не “тащить” проверки наверх. Например:
- библиотека должна прочитать файл настроек;
- она знает, что имеет на это право;
- но вызывающий код может не иметь → тогда doPrivileged позволяет библиотеке выполнить действие.

	1.	JVM загружает класс → создаёт ProtectionDomain.
	2.	Смотрит в Policy: какие Permissions полагаются этому коду.
	3.	Записывает их в ProtectionDomain.
	4.	При вызове чувствительных операций → AccessController.checkPermission(...).
	5.	Если право есть → операция разрешена.

```
java.security.Permission   (абстрактный)
 ├── java.io.FilePermission
 ├── java.net.SocketPermission
 ├── java.util.PropertyPermission
 ├── java.lang.RuntimePermission
 ├── java.lang.reflect.ReflectPermission
 ├── java.security.AllPermission
 └── java.security.BasicPermission (абстрактный)
       ├── java.security.SecurityPermission
       ├── java.security.UnresolvedPermission
       └── др.
```

## Сохраняемость

Сериализация — это процесс преобразования объекта в поток байтов для:
- сохранения в файл / базу;
- передачи по сети;
- кэширования;
- создания глубоких копий.

Десериализация — обратный процесс: из байтов → объект.

### Serializable
- Это маркерный интерфейс (java.io.Serializable).
- Не содержит методов.
- Если класс его реализует, JVM разрешает сериализацию объекта по умолчанию.

```java
import java.io.*;

class Person implements Serializable {
    private String name;
    private int age;

    public Person(String n, int a) {
        this.name = n;
        this.age = a;
    }
}

public class Main {
    public static void main(String[] args) throws Exception {
        Person p = new Person("Alice", 25);

        // Сериализация
        try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("person.ser"))) {
            oos.writeObject(p);
        }

        // Десериализация
        try (ObjectInputStream ois = new ObjectInputStream(new FileInputStream("person.ser"))) {
            Person p2 = (Person) ois.readObject();
            System.out.println("Объект восстановлен!");
        }
    }
}
```

Когда класс помечен implements Serializable, JVM использует ObjectOutputStream и ObjectInputStream.

Механизм:
1. При вызове oos.writeObject(obj):
   - JVM проверяет, реализует ли объект Serializable.
   - Если нет → NotSerializableException.
	- Если да → начинает процесс сериализации.
2.	Для сериализации используется ObjectStreamClass — это дескриптор класса:
	- Имя класса;
	- UID (serialVersionUID);
	- Список сериализуемых полей (не static и не transient).
3.	JVM берёт список полей через Reflection API (Class.getDeclaredFields()), сортирует их по имени и сериализует.
	- Доступ к приватным полям обеспечивается через AccessibleObject.setAccessible(true) внутри ObjectStreamClass.
	- Поэтому сериализуются даже приватные поля.
4.	Значения полей пишутся в поток через DataOutput (writeInt, writeUTF и т.д.).
5.	При десериализации (ois.readObject()):
	- JVM ищет класс в classpath.
	- Сверяет serialVersionUID.
	- Создаёт объект без вызова конструктора (!).
    	- Это делается через ReflectionFactory.newConstructorForSerialization, который использует sun.misc.Unsafe для аллокации объекта без конструктора.
	- Читает поля из потока и через Reflection заполняет объект.

### Externalizable
- Это подинтерфейс Serializable (java.io.Externalizable extends Serializable).
- Содержит 2 метода:
    `void writeExternal(ObjectOutput out) throws IOException;`

    `void readExternal(ObjectInput in) throws IOException, ClassNotFoundException;`

- Нужно вручную описать, как сохранять и восстанавливать объект.
- Требует публичного конструктора без аргументов (JVM вызывает его при десериализации).

```java
import java.io.*;

class Person implements Externalizable {
    private String name;
    private int age;

    public Person() {} // обязателен

    public Person(String n, int a) {
        this.name = n;
        this.age = a;
    }

    @Override
    public void writeExternal(ObjectOutput out) throws IOException {
        out.writeUTF(name);
        out.writeInt(age);
    }

    @Override
    public void readExternal(ObjectInput in) throws IOException, ClassNotFoundException {
        this.name = in.readUTF();
        this.age = in.readInt();
    }

    @Override
    public String toString() {
        return name + " (" + age + ")";
    }
}

public class Main {
    public static void main(String[] args) throws Exception {
        Person p = new Person("Bob", 30);

        try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("person.ser"))) {
            oos.writeObject(p);
        }

        try (ObjectInputStream ois = new ObjectInputStream(new FileInputStream("person.ser"))) {
            Person p2 = (Person) ois.readObject();
            System.out.println("Восстановлено: " + p2);
        }
    }
}
```

Когда класс реализует Externalizable:
1.	JVM видит, что у класса есть writeExternal и readExternal.
2.	При сериализации вызывает не Reflection, а твои методы напрямую — то есть программист полностью отвечает за то, что попадёт в поток.
3.	При десериализации:
	- JVM вызывает публичный конструктор без аргументов;
	- потом вызывает readExternal(in), где ты сам читаешь и восстанавливаешь состояние.

## ReflectionAPI
Reflection (рефлексия) — это API в Java, которое позволяет программе анализировать и изменять структуру и поведение классов во время выполнения (runtime).

```java
import java.lang.reflect.*;

class Example<T> {
    private String secret;
    public void test(T param) {}
}

public class Main {
    public static void main(String[] args) throws Exception {
        Class<?> clazz = Example.class;

        // Получаем Field
        Field field = clazz.getDeclaredField("secret");
        System.out.println("Field: " + field.getName());

        // Получаем Method
        Method method = clazz.getDeclaredMethod("test", Object.class);
        System.out.println("Method: " + method.getName());

        // Generic информация о методе
        Type[] types = method.getGenericParameterTypes();
        for (Type t : types) {
            System.out.println("Generic param: " + t);
        }
    }
}
```
1.	загрузили класс по имени,
2.	нашли метод add,
3.	создали объект,
4.	вызвали метод — не зная о ArrayList на этапе компиляции.

### Как реализован Reflection в JVM
1.	Каждый загруженный класс хранится в метаданных JVM (метаданные описывают поля, методы, конструкторы, аннотации и т.д.).
2.	Когда вызывается Class.forName("..."), JVM через ClassLoader загружает класс и создаёт объект java.lang.Class, который представляет этот тип.
3.	Методы вроде getFields(), getMethods() и т.п. возвращают объекты отражения (Field, Method, Constructor), которые являются прокси для метаданных JVM.
4.	Для доступа к приватным полям/методам используется AccessibleObject.setAccessible(true) → это отключает проверки модификаторов доступа через sun.reflect или jdk.internal.reflect.
5.	Для вызова методов используется Method.invoke(), внутри которого идёт JNI-вызов в JVM, которая напрямую дергает метод в байткоде.

### Иерархия
```
java.lang.Object
   └── java.lang.Class<T>                   // представление типа (класса, интерфейса, массива, enum)
        ├── реализует java.lang.reflect.GenericDeclaration
        ├── реализует java.lang.reflect.AnnotatedElement
        └── реализует java.io.Serializable

java.lang.reflect.AccessibleObject          // базовый для управления доступом
   ├── java.lang.reflect.Field              // отражение поля
   ├── java.lang.reflect.Method             // отражение метода
   └── java.lang.reflect.Constructor<T>     // отражение конструктора

java.lang.reflect.Member (интерфейс)        // общий для членов класса
   ├── Field
   ├── Method
   └── Constructor

java.lang.reflect.Type (интерфейс)          // абстракция generic-типа
   ├── Class<?>                             // обычный класс как тип
   ├── ParameterizedType                    // параметризованный тип (List<String>)
   ├── TypeVariable<D extends GenericDeclaration>
   │        └── T, E, K ...                 // переменные generic-типа
   ├── WildcardType                         // подстановки (? extends Number, ? super T)
   └── GenericArrayType                     // массив generic-типа (T[])

java.lang.reflect.AnnotatedElement (интерфейс)
   ├── Class
   ├── Method
   ├── Field
   ├── Constructor
   ├── Package
   └── (начиная с Java 8) Parameter, Module

java.lang.reflect.GenericDeclaration (интерфейс)
   ├── Class
   ├── Method
   └── Constructor
```

### Что решает

Reflection API в Java решает несколько ключевых проблем, связанных с динамическим управлением и анализом кода во время выполнения, которые невозможно эффективно решить статически (на этапе компиляции). Давай разберём по пунктам.

#### Динамическое исследование классов и объектов

Проблема: в статически типизированной Java на этапе компиляции мы не можем знать все классы, которые будут использоваться.
Решение через Reflection: можно узнать, какие поля, методы, конструкторы и аннотации есть у объекта в runtime.

Пример:
```java
Class<?> clazz = Class.forName("com.example.MyClass");
Method[] methods = clazz.getDeclaredMethods();
for (Method m : methods) {
    System.out.println(m.getName());
}
```
- Это важно для фреймворков, которые работают с кодом, который ещё не написан или загружается динамически.


#### Доступ к приватным и защищённым членам

Проблема: иногда нужно читать или изменять поля и методы, к которым обычный код не имеет доступа.
Решение через Reflection: Field.setAccessible(true) позволяет обращаться даже к приватным полям.

Пример:
```java
Field f = obj.getClass().getDeclaredField("secret");
f.setAccessible(true);
f.set(obj, 42);
```
- Это полезно для тестов, сериализации, библиотек внедрения зависимостей.


#### Динамический вызов методов

Проблема: на этапе компиляции мы не знаем, какой метод нужно вызвать, или имя метода приходит из конфигурации.
Решение через Reflection: можно вызвать метод по имени.

```java
Method method = obj.getClass().getMethod("doWork", String.class);
method.invoke(obj, "Hello");
```

#### Работа с аннотациями

Проблема: как понять, какие аннотации есть на классе/методе/поле, чтобы применять конфигурации или правила?
Решение: через Reflection можно считывать аннотации в runtime.

```java
if (clazz.isAnnotationPresent(MyAnnotation.class)) {
    MyAnnotation ann = clazz.getAnnotation(MyAnnotation.class);
    System.out.println(ann.value());
}
```

#### Создание объектов динамически

Проблема: нужно создать объект класса, имя которого известно только во время выполнения.
Решение: можно создать объект через Constructor.newInstance() или Class.newInstance().
```java
Class<?> clazz = Class.forName("com.example.Plugin");
Object plugin = clazz.getDeclaredConstructor().newInstance();
```
- Это основа для плагинных систем, DI-контейнеров и модульной архитектуры.

#### Работа с generic-типа и метаданными

Проблема: иногда нужно узнать тип параметров generic (например, List<String>).
Решение: Reflection через Type, ParameterizedType, TypeVariable.
```java
Field listField = MyClass.class.getDeclaredField("list");
ParameterizedType type = (ParameterizedType) listField.getGenericType();
System.out.println(type.getActualTypeArguments()[0]); // String
```


## JNI (Java Native Interface)
`JNI (Java Native Interface) — это механизм в Java, позволяющий вызывать нативный код (C/C++/Assembler) из программы на Java и наоборот — вызывать Java-код из нативных библиотек.`

Это своего рода «мост» между JVM и «внешним миром» (native OS-библиотеки, драйверы, системные API).

1.	Доступ к возможностям ОС Например, работа с низкоуровневыми API Windows/Linux/macOS, которые недоступны напрямую в Java.
2.	Высокая производительность Критичные по скорости части программы можно писать на C/C++ и вызывать из Java.
3.	Интеграция со сторонними библиотеками Иногда библиотека существует только для C/C++ (например, графическая, криптографическая, ML-библиотека). Через JNI можно «подключить» её к Java.
4.	Низкоуровневый доступ Драйверы устройств, работа с памятью, доступ к железу.


В Java объявляется метод как `native`
```java
public class NativeExample {
    // объявление "чужого" метода
    public native void sayHello();

    static {
        // подгружаем динамическую библиотеку (libexample.so / example.dll)
        System.loadLibrary("example");
    }
}
```

Компилятор javac создаёт .class.

Утилита javac -h (раньше javah) генерирует C-заголовок (.h) для реализации метода.
```java
#include <jni.h>
JNIEXPORT void JNICALL Java_NativeExample_sayHello(JNIEnv *, jobject);
```
В C/C++ пишется реализация:
```java
#include <jni.h>
#include <stdio.h>
#include "NativeExample.h"

JNIEXPORT void JNICALL Java_NativeExample_sayHello(JNIEnv *env, jobject obj) {
    printf("Hello from C!\n");
}
```

Код компилируется в динамическую библиотеку (.so, .dll, .dylib).

Java-программа вызывает sayHello(), и JVM через JNI обращается к нативной библиотеке.

### Архитектура JNI
```
Java Code (NativeExample.java)
        ↓
JVM (через JNI)
        ↓
JNI Wrapper (сгенерированный .h и реализованный .c/.cpp)
        ↓
Native Library (example.dll / libexample.so)
        ↓
ОС / железо
```

### Важные моменты
- JNIEnv * — это указатель на структуру, через которую C/C++ может вызывать методы JVM (например, создавать объекты, вызывать методы Java).
- Методы JNI всегда начинаются с Java_<ИмяКласса>_<ИмяМетода>.
- Нужно аккуратно работать с памятью, чтобы не допустить утечек или падений JVM.
- Обычно используют только когда Java API недостаточно.

## instanceof
`instanceof проверяет, является ли объект экземпляром определённого класса или интерфейса.`

1. Не через Reflection API
   - instanceof обрабатывается JVM на уровне байткода.
   - В байткоде это инструкция checkcast или instanceof.
   - Проверка идёт по внутренним метаданным класса (Class pointers), которые JVM хранит для каждого объекта.
2.	Механизм JVM
   - Каждый объект в JVM содержит ссылку на его Class объект (Class pointer).
   - Когда выполняется obj instanceof SomeClass, JVM проверяет:
     - Есть ли в цепочке наследования класс SomeClass?
     -	Если SomeClass — интерфейс, проверяет, реализует ли объект его.
	- Это быстрая операция на уровне машинного кода, не использующая Reflection API.
3.	Сравнение с Reflection
	- Reflection может делать аналогичную проверку, но медленнее:
        ```java
        if (SomeClass.class.isInstance(obj)) { ... }
        ```
    - Здесь isInstance() использует тот же механизм, что instanceof, но через API Class.

## GC 
Garbage Collector (GC) — это механизм JVM, который автоматически освобождает память, удаляя объекты, к которым больше нет ссылок.
- Цель: не освобождать память вручную (как в C/C++), а автоматизировать управление памятью.
- GC работает в куче (heap) — это область памяти, где создаются все объекты.

### Устройство памяти
Память в JVM делится на несколько частей, но для GC важны:
```
Heap
 ├─ Young Generation
 │    ├─ Eden
 │    └─ Survivor (S0, S1)
 └─ Old Generation (Tenured)
```
1.	Young Generation (молодое поколение)
	- Здесь создаются новые объекты.
	- Часто объекты быстро становятся ненужными → оптимизация через быстрый GC.
	- Состоит из:
    	- Eden — новые объекты.
    	- Survivor — копии живых объектов после minor GC.
2.	Old Generation (старое поколение / tenured)
	- Объекты, которые прожили долго, перемещаются сюда.
	- Очистка происходит реже (major GC / full GC).
3.	Permanent / Metaspace (Java 8+)
	- Для классов, методов и метаданных JVM.
	- Отдельная область, управляется GC отдельно.

### Работа GC
GC запускается, когда:
1.	Недостаток памяти в поколении
	- Например, Eden заполнен → Minor GC.
	- Old Generation почти полна → Full GC.
2.	Явный вызов (редко)
```java
System.gc(); // просьба JVM, не гарантирует немедленный запуск
```
3.	Некоторые JVM делают background GC (concurrent), чтобы поддерживать свободное место и минимизировать паузы.

### Алгоритмы GC
#### Mark-and-Sweep (Пометка и Очистка)

Идея:
1.	Mark (пометка) — отмечаем все объекты, до которых можно добраться от корневых ссылок (root references: стэк, статические поля, JNI).
2.	Sweep (очистка) — все непомеченные объекты удаляются, память освобождается.

Особенности:
- Простой, но может фрагментировать память.
- Используется в Old Generation GC как базовый механизм.

#### Generational GC (Поколенческая сборка)
Идея:
- Большинство объектов живёт недолго - делим кучу на поколения.
- Young Generation → частые и быстрые сборки (Minor GC).
- Old Generation → редкие и дорогие сборки (Major/Full GC).

Пояснение:
- После Minor GC живые объекты из Eden копируются в Survivor.
- После нескольких переселений объект “стареет” → переходит в Old Generation.

#### Copying / Copy Collector (Копирование)

Используется в Young Generation:
- Копируем живые объекты из Eden + Survivor в другую Survivor область.
- Остальное → автоматически освобождается.

Плюсы:
- Очень быстрый, потому что не нужно искать «пустые места» — просто копируем живые объекты.

#### Compacting GC (Компактирование)
- После Mark-and-Sweep память может фрагментироваться.
- Compacting GC сдвигает живые объекты, чтобы освободить непрерывный блок памяти.
- Используется в Old Generation при Full GC.

#### Concurrent / Parallel GC

Concurrent GC:
- GC работает параллельно с приложением, минимизируя паузы.

Parallel GC (Throughput GC):
- Использует несколько потоков, чтобы ускорить сборку.

Примеры в JVM:
- Serial GC — однопоточный, простой, для небольших приложений.
- Parallel GC — многопоточный, высокая производительность.
- CMS (Concurrent Mark-Sweep) — минимизация пауз, параллельная очистка Old Generation.
- G1 GC (Garbage First) — делит Old Generation на регионы, параллельная и инкрементальная очистка, оптимизирован под большие кучи.
- ZGC / Shenandoah (Java 11+) — Low-Latency GC, почти без пауз, для огромной кучи (ТБ памяти).

#### Жизненный цикл объекта с точки зрения GC
```
1. new Object() → создаётся в Eden
2. Minor GC → живые объекты переходят в Survivor
3. Несколько Minor GC → объект «стареет» → переходит в Old Generation
4. Major / Full GC → очищаются ненужные объекты в Old Generation
```
- Прямые ссылки (root) защищают объект от удаления.
- Объекты без ссылок → candidates for GC.

### Определение лимита
Параметр | Что задаёт
---|---
-Xms<size> | Начальный размер кучи (initial heap size)
-Xmx<size> | Максимальный размер кучи (maximum heap size)
-Xmn<size> | Размер молодого поколения (Young Generation)
-XX:SurvivorRatio=N | Соотношение Eden : Survivor (по умолчанию 8:1)
-XX:NewRatio=N | Соотношение Old : Young Generation

### Как JVM понимает, что Eden или Old переполнено
1.	Eden
	- Новый объект помещается в currentTop
	- Если currentTop + size > edenEnd → Minor GC
2.	Survivor
	- Служит для копирования живых объектов после Minor GC
	- Если Survivor переполнен → часть объектов сразу идёт в Old Generation
3.	Old Generation
	- При заполнении → Full GC
	- Если после Full GC нет свободной памяти → OutOfMemoryError: Java heap space

## Память JVM
```
JVM Memory
 ├── Heap (куча)                → для объектов
 │    ├─ Young Generation        → молодые объекты
 │    │     ├─ Eden              → новые объекты
 │    │     └─ Survivor (S0/S1)  → живые объекты после minor GC
 │    └─ Old Generation (Tenured) → долгоживущие объекты
 ├── Stack (стек потоков)        → локальные переменные, вызовы методов
 ├── Metaspace (Java 8+)         → классы, методы, метаданные
 └── Native Memory               → нативные библиотеки, JNI, внутренние структуры JVM
```

1. Heap (куча)
   - Хранит все объекты, создаваемые через new.
   - Делится на поколения:
   - Young Generation (Eden + Survivor) — краткоживущие объекты;
   - Old Generation — долгоживущие объекты, которые пережили несколько minor GC.

2. Stack (стек)
- Каждый поток JVM имеет свой стек.
- Хранит локальные переменные, параметры методов и адрес возврата.
- Объекты из стека — root references для GC.

3. Metaspace (ранее Permanent Generation, до Java 8)
	- Permanent Generation (PermGen) до Java 8 — фиксированный размер памяти для: классов, методов, констант, аннотаций.
	- Metaspace (Java 8+) — динамический, выделяется в native memory.
    	- Неограниченный рост при необходимости.
    	- Цель: хранение метаданных классов (Class, Method, Field, annotations).

Зачем нужен:
	•	JVM должна хранить метаинформацию классов отдельно от heap, чтобы GC heap не трогал структуру классов.
	•	Позволяет загружать и выгружать классы (dynamic class loading), что важно для контейнеров, OSGi, Spring.


## VMT (Virtual Method Table)
- В Java почти все методы являются виртуальными (кроме static, private, final).
- Виртуальный метод — это метод, вызов которого разрешается в runtime в зависимости от реального типа объекта.
```java
class Animal {
    void sound() { System.out.println("Animal sound"); }
}

class Dog extends Animal {
    void sound() { System.out.println("Woof!"); }
}

Animal a = new Dog();
a.sound();  // "Woof!" — вызов зависит от реального типа Dog
```
- Здесь компилятор не знает на этапе компиляции, какой метод будет вызван — Animal.sound() или Dog.sound().
- Решение: виртуальная таблица методов (VMT).

Идея:
- Каждый класс в JVM хранит таблицу методов (VMT), где указаны адреса методов для вызова.
- При создании объекта JVM хранит ссылку на VMT его класса.
- Когда вызывается виртуальный метод, JVM:
	1.	Берёт VMT объекта
	2.	Находит нужный метод по смещению (offset)
	3.	Вызывает его

Пример:
```java
class Animal {
    void sound() {}
    void sleep() {}
}

class Dog extends Animal {
    void sound() {}   // переопределение
}
```

VMT for Animal:
Offset | Method
--- | ---
0 | sound()
1 | sleep()

VMT for Dog
Offset | Method
---|---
0 | Dog.sound()
1 | sleep()

Важно: offset для метода одинаков для всех подклассов → JVM может быстро вызывать метод по смещению.

### Исключения
`static`, `private` и `final` методы
- Эти методы не виртуальные → вызов разрешается на этапе компиляции.
- JVM не использует VMT для таких методов — они напрямую связываются через адрес метода (static linking).

### Преимущества VMT
1.	Динамическое связывание → поддержка полиморфизма.
2.	Быстрый вызов → смещение по таблице O(1).
3.	Простая организация наследования → переопределение метода просто заменяет указатель в VMT.

### Важные моменты реализации в JVM
- Каждому классу соответствует одна таблица методов.
- Объект хранит только ссылку на VMT, а не саму таблицу.
- JVM может оптимизировать вызовы через inline caching или JIT, если типы известны во время выполнения.

### Inline Caching

Inline Caching — это оптимизация JVM для ускорения виртуальных вызовов.

Как работает:
1.	JVM помнит какой метод был вызван по конкретному call site (место вызова).
2.	Если следующий раз вызов идёт с объектом того же типа, JVM не смотрит VMT, а использует закешированный метод.
3.	Это снижает стоимость динамического поиска метода, особенно в горячих циклах.

Пример:
```java
Animal a = new Dog();
for (int i = 0; i < 1000; i++) {
    a.sound();  // JVM кеширует Dog.sound() для этой call site
}
```
- На 1000 итераций JVM может вызывать метод напрямую, минуя VMT lookup → очень быстро.

```
Call site:
   a.sound()  ──┐
                │ JVM сначала смотрит inline cache
                ▼
           Cached method? ──► Yes → вызывает напрямую
                │
                No
                ▼
           Lookup in VMT (offset 0)
                │
                ▼
           Вызывает метод конкретного класса (Dog/Cat)
                │
                ▼
         JIT может закешировать для future calls
```

### Cхема работы
```
Compile-time                     Runtime
─────────────                    ─────────────
Animal a = new Dog();            ┌─────────────┐
                                 │ Object: Dog │
Call: a.sound() ---------------->│ VMT pointer │──► VMT Dog
                                 │             │    ┌─────────────────┐
Compile-time resolves signature   │             │    │ Offset 0: sound()│ → Dog.sound()
by parameter: no arguments       └─────────────┘    │ Offset 1: sound(String) │ → Animal.sound(String)
                                                       │ Offset 2: move()         │ → Animal.move()
                                                       └─────────────────────────┘

Call: a.sound("loud")            ┌─────────────┐
                                 │ Object: Dog │
Compile-time resolves signature   │ VMT pointer │
by parameter: String -----------►│             │──► VMT lookup not needed for overloaded method
                                 └─────────────┘
Overloaded method resolved
statically in Animal class: Animal.sound(String)

Call: a.move()                   ┌─────────────┐
                                 │ Object: Dog │
Compile-time resolves signature   │ VMT pointer │──► VMT Dog
by parameter: no arguments        │             │    │ Offset 2: move() │ → Animal.move()
Virtual method call → runtime selects actual implementation from VMT
```
1. Overriding (переопределение) → виртуальный вызов через VMT (sound() → Dog.sound()).
2.	Overloading (перегрузка) → выбор метода статически на этапе компиляции (sound("loud") → Animal.sound(String)).
3.	VMT (Virtual Method Table) хранит адреса методов для каждого класса.
4.	JVM сначала выбирает сигнатуру по параметрам, затем, если метод переопределён, делает runtime lookup через VMT.



## Static linking 
Static linking — это связывание методов на этапе компиляции.

Используется для:
- static методов
- private методов
- final методов (которые нельзя переопределить)

## JIT (Just In Time)
`JIT - это часть JVM, которая во время выполнения (runtime) компилирует часто используемый байткод в машинный код и кеширует его`

- JVM сначала интерпретирует байткод (slow).
- JIT компилятор компилирует часто используемый (hot) код в машинный код во время выполнения.
- Применяет оптимизации:
	1. Inline caching
	2. Методы inline — вставляет тело метода прямо в вызывающий код
	3. Escape analysis — оптимизация локальных объектов
	4. Loop unrolling, dead code elimination

JIT + Inline caching + VMT → почти такие же быстрые вызовы виртуальных методов, как статические вызовы.

### Механизм работы
1.	Загрузка байткода → JVM получает .class и интерпретирует его.
2.	Профилирование → JVM считает, какие методы выполняются часто.
3.	Компиляция в нативный код → JIT берёт горячие методы и компилирует их.
4.	Оптимизация:
	- Убираются лишние проверки.
	- Делается inlining (вставка тела метода вместо вызова).
	- Используется loop unrolling (разворачивание циклов).
	- Применяется escape analysis (убирает ненужные объекты из кучи, размещает их на стеке).
5.	Кеширование → при следующем вызове метод уже выполняется напрямую в машинном коде.

### Когда работает JIT?

JIT-компиляция включается во время выполнения программы (runtime), когда JVM видит, что:
- Метод вызывается много раз (так называемый hot method).
- Условие ветвления или цикл выполняются сотни/тысячи раз (hot loops).

Тогда JIT принимает решение:
- компилировать этот метод в машинный код (native code),
- кешировать его,
- и в будущем вызывать напрямую, без интерпретации байткода.

То есть JIT работает не сразу при старте, а после “разогрева” (warm-up), когда JVM собрала статистику.
JIT встроен в JVM и использует механизм профилирования (profiling):
- JVM считает количество вызовов методов и циклов.
- Запоминает, какие пути в коде чаще всего исполняются (например, if почти всегда true → можно оптимизировать).
- Отслеживает типы объектов, которые реально попадают в виртуальные вызовы.

## I/O 
В Java есть три больших семейства API для I/O:
1.	Stream API (java.io)
	- Классическая модель потоков байтов/символов.
	- Синхронная, блокирующая модель.
	- Работает с последовательным чтением/записью.
2.	New I/O (NIO, java.nio, Java 1.4+)
	- Введён для работы с буферами и каналами.
	- Поддерживает memory-mapped файлы, неблокирующие сокеты, селекторы.
	- Более эффективен для высоконагруженных приложений (например, серверов).
3.	NIO.2 (java.nio.file, Java 7+)
	- Расширение NIO.
	- Упрощённая работа с файловой системой (Path, Files, FileVisitor).
	- Аысинхронный I/O через AsynchronousChannel.

### Классическая модель (java.io)
Основные интерфейсы:
- InputStream / OutputStream → работа с байтами.
- Reader / Writer → работа с символами (Unicode-aware).

Байтовые потоки
- InputStream — базовый класс для чтения байтов.
- OutputStream — базовый класс для записи байтов.
Примеры: FileInputStream, BufferedInputStream, DataOutputStream.

Символьные потоки
- Reader и Writer — для текста (UTF-16 → системная кодировка).
Примеры: FileReader, BufferedWriter, PrintWriter.

Декораторы (паттерн Decorator)
- BufferedInputStream, BufferedReader — буферизация.
- DataInputStream — чтение примитивов (readInt(), readDouble()).
- ObjectInputStream — десериализация объектов.

```java
import java.io.*;

public class StreamIOExample {
    public static void main(String[] args) throws IOException {
        try (FileInputStream fis = new FileInputStream("input.txt");
             FileOutputStream fos = new FileOutputStream("output.txt")) {

            int data;
            while ((data = fis.read()) != -1) {
                fos.write(data);
            }
        }
    }
}
```

```java
import java.io.*;

public class ReaderWriterExample {
    public static void main(String[] args) throws IOException {
        try (BufferedReader reader = new BufferedReader(new FileReader("input.txt"));
             BufferedWriter writer = new BufferedWriter(new FileWriter("output.txt"))) {

            String line;
            while ((line = reader.readLine()) != null) {
                writer.write(line.toUpperCase());
                writer.newLine();
            }
        }
    }
}
```

### NIO (java.nio)
- Введено для эффективной работы с файлами и сетевыми соединениями.
- Основные компоненты:

1. Buffer
- ByteBuffer, CharBuffer, IntBuffer и др.
- Хранение данных в виде массивов с указателями position, limit, capacity.
- Можно маппить файл в память (FileChannel.map() → MappedByteBuffer).

2. Channel
- Двусторонние каналы ввода-вывода.
- Более гибкая альтернатива Stream.
Примеры: FileChannel, SocketChannel, DatagramChannel.

3. Selector
-	Для работы с множеством неблокирующих каналов в одном потоке.
-	Применяется в асинхронных серверах (реализация reactor pattern).

```java
import java.io.*;
import java.nio.*;
import java.nio.channels.*;

public class NIOExample {
    public static void main(String[] args) throws IOException {
        try (FileInputStream fis = new FileInputStream("input.txt");
             FileChannel channel = fis.getChannel()) {

            ByteBuffer buffer = ByteBuffer.allocate(1024);
            while (channel.read(buffer) > 0) {
                buffer.flip();
                while (buffer.hasRemaining()) {
                    System.out.print((char) buffer.get());
                }
                buffer.clear();
            }
        }
    }
}
```

### NIO.2 (Java 7+)

Добавлены:
- Path API (java.nio.file.Path)
    -	Современная альтернатива File.
    -	Методы: Files.exists(path), Files.copy(src, dst) и т.д.
- FileVisitor API
    -	Обход файловых деревьев (Files.walkFileTree).
- WatchService
    -	Подписка на события файловой системы (создание, удаление, изменение).
- Асинхронные каналы (AsynchronousFileChannel, AsynchronousSocketChannel)
    -	Позволяют работать в неблокирующем режиме с Future или CompletionHandler.

```java
import java.nio.file.*;
import java.io.IOException;
import java.util.List;

public class NIO2Example {
    public static void main(String[] args) throws IOException {
        Path path = Paths.get("input.txt");

        // Читаем все строки
        List<String> lines = Files.readAllLines(path);
        lines.forEach(System.out::println);

        // Записываем в новый файл
        Files.write(Paths.get("output.txt"), lines);
    }
}
```

```java
import java.io.IOException;
import java.nio.ByteBuffer;
import java.nio.channels.AsynchronousFileChannel;
import java.nio.file.*;
import java.util.concurrent.Future;

public class AsyncIOExample {
    public static void main(String[] args) throws IOException {
        Path path = Paths.get("input.txt");

        try (AsynchronousFileChannel asyncChannel = AsynchronousFileChannel.open(path, StandardOpenOption.READ)) {
            ByteBuffer buffer = ByteBuffer.allocate(1024);
            Future<Integer> result = asyncChannel.read(buffer, 0);

            while (!result.isDone()) {
                System.out.println("Файл читается асинхронно...");
            }

            buffer.flip();
            while (buffer.hasRemaining()) {
                System.out.print((char) buffer.get());
            }
        }
    }
}
```

### I/O и Сериализация
- ObjectInputStream и ObjectOutputStream → стандартная сериализация объектов.
- Поддерживается через интерфейсы Serializable и Externalizable.
- Можно сохранять объектное состояние в файл или пересылать по сети.

### Схема уровней
```
Application Code
     │
     ▼
java.io (Stream API)
  - InputStream / OutputStream (байты)
  - Reader / Writer (символы)
     │
     ▼
java.nio (Buffers, Channels, Selectors)
  - ByteBuffer, CharBuffer
  - FileChannel, SocketChannel
  - Selector (non-blocking I/O)
     │
     ▼
java.nio.file (NIO.2)
  - Path, Files, FileVisitor, WatchService
  - AsynchronousFileChannel
     │
     ▼
Operating System (syscalls: read, write, mmap, epoll/kqueue)
```

Модель | Пакеты / Классы | Особенности | Скорость | Когда использовать ✅
---|---|---|---|---
Базовый Streams API | java.io.InputStream, OutputStream | Работает с байтами, низкоуровневый доступ | Низкая (много системных вызовов) | Работа с бинарными файлами (изображения, аудио, PDF)
Reader/Writer (символьные потоки) | java.io.Reader, Writer, BufferedReader | Работает с текстом (Unicode), удобен для строк | Средняя (можно буферизовать) | Текстовые файлы, CSV, логи
NIO (New I/O) | java.nio.channels.FileChannel, ByteBuffer | Использует буферы и каналы, поддерживает memory-mapped files | Высокая (прямой доступ к OS API) |  Большие файлы, серверы, работа с сокетами
NIO.2 (Java 7+) |  java.nio.file.Files, Paths |  Высокоуровневый API, простые методы readAllLines, write |  Средне-высокая (зависит от задачи) | Утилиты, быстрая работа с файлами, конфиги
Async I/O (AIO) | java.nio.channels.AsynchronousFileChannel | Асинхронный, неблокирующий ввод/вывод | Очень высокая (для I/O-bound задач) | Серверы с высокой нагрузкой, неблокирующие сетевые операции

# ПОЧИТАТЬ


DSL code


1.  Концепция реализации графического пользовательского интерфейса. Java FX.
2.  Реализация языка Groovy на основе JVM
3.  Реализация DSL с помощью языка Groovy

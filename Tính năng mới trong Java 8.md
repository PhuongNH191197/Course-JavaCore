## Java 8

| No | Tên phiên bản            | Ngày release |
| -- | ------------------------ | ------------ |
| 1  | Java SE 8                |  2014-03-18  |
| 2  | Java SE 8 Update 5       |  2014-04-15  |
| 3  | Java SE 8 Update 11      |  2014-07-15  |
| 4  | Java SE 8 Update 20      |  2014-08-19  |
| 5  | Java SE 8 Update 25      |  2014-10-14  |

## 1. Lamda Expressions
Tính năng đầu tiên, đồng thời là tính năng nổi bật nhất của Java8: hỗ trợ cú pháp Lambda,  đây dường như là cải tiến lớn nhất trong cú pháp lập trình Java kể từ thời điểm phát hành Generics  và Annotations trong Java 5.

Lambda expressions là một tính năng mới quan trọng trong Java 8. Lambda expressions giống class vô danh biểu diễn dưới dạng biểu thức. Chỉ bằng một biểu thức nó có thể biểu diễn thực thi cho method của functional interfaces. 

Functional interfaces là interface chỉ có 1 method. Lambda expressions cung cấp cách thức mới làm việc với Collection một cách đơn giản và hiệu quả, tăng hiệu năng (performance) của hệ thống chạy trong môi trường đa lõi (multicore).

### 1.1. Cấu trúc của lambda expressions

| Params        | Arrow tocken | Body |
| --------------| ------------ | ---- |
| `(argument)`  | `->` | `{body};` |

```Java
(arg1, arg2...) -> { body }

(type1 arg1, type2 arg2...) -> { body }
```

- LamExp có thể không có, có một, hoặc nhiều tham số. 
```Java
// không tham số
() -> System.out.println("Hello World");

// một tham số
(a) -> return a+a;

// một tham số với kiểu dữ liệu
(String s) -> { System.out.println(s); }

// hai tham số
(int a, int b) -> return a+b;
```
- Tham số của có thể được định nghĩa kiểu một cách tường minh hoặc không cần định nghĩa kiểu. Kiểu sẽ được suy ra từ ngữ cảnh cụ thể.
- Các tham số được đặc trong hai dấu đóng mở đơn `(params)`, khi chỉ có một tham số thì có thể không cần đặt trong dấu đóng mở. 
```Java
a -> return a+a;
```
- Body code của LamExp được đặt trong dấu đóng mở nhọn `{body}`, khi body code chỉ có một sử lý (thể hiện) thì không cần có dấu đóng mở nhọn.

Cú pháp Lambda trong Java cho phép tự suy luận kiểu dữ liệu. Hãy xem xét các ví dụ có sẵn sau đây:

```Java
//sort by age
Collections.sort(listDevs, new Comparator<Developer>() {
    @Override
    public int compare(Developer o1, Developer o2) {
	return o1.getAge() - o2.getAge();
    }
});

//lambda
listDevs.sort((Developer o1, Developer o2) -> o1.getAge() - o2.getAge());

//lambda, valid, parameter type is optional
listDevs.sort((o1, o2) -> o1.getAge() - o2.getAge());
```

### 1.2. Duyệt collection

Cách thông thường khởi tạo và in ra danh sách:
```Java
//Khai báo và khởi tạo list các phần tử Integer.
List<Integer> list = Arrays.asList(1, 2, 3, 4, 5, 6, 7);
//Duyệt và in ra console từng phần tử của danh sách.
for(Integer n: list) {
    System.out.println(n);
}
```

Sử dụng LamExp
```Java
List<Integer> list = Arrays.asList(1, 2, 3, 4, 5, 6, 7);
list.forEach(n -> System.out.println(n));
```

Sử dụng tham chiếu
```Java
List<Integer> list = Arrays.asList(1, 2, 3, 4, 5, 6, 7);
list.forEach(System.out::println);
```

### 1.3. forEach examples

#### 1.3.1. forEach and Map

Normal way to loop a Map.
```Java
Map<String, Integer> items = new HashMap<>();
    items.put("A", 10);
    items.put("B", 20);
    items.put("C", 30);
    items.put("D", 40);
    items.put("E", 50);
    items.put("F", 60);

    for (Map.Entry<String, Integer> entry : items.entrySet()) {
	System.out.println("Item : " + entry.getKey() + " Count : " + entry.getValue());
    }
```

In Java 8, you can loop a `Map` with `forEach` + lambda expression.
```Java
Map<String, Integer> items = new HashMap<>();
    items.put("A", 10);
    items.put("B", 20);
    items.put("C", 30);
    items.put("D", 40);
    items.put("E", 50);
    items.put("F", 60);

    items.forEach((k, v) -> System.out.println("Item : " + k + " Count : " + v));
```

#### 1.3.2. forEach and List

Normal for-loop to loop a List.
```Java
List<String> items = new ArrayList<>();
    items.add("A");
    items.add("B");
    items.add("C");
    items.add("D");
    items.add("E");

    for(String item : items){
	System.out.println(item);
    }
```

In Java 8, you can loop a `List` with `forEach` + lambda expression or method reference.
```Java
List<String> items = new ArrayList<>();
    items.add("A");
    items.add("B");
    items.add("C");
    items.add("D");
    items.add("E");

    //lambda
    //Output : A, B, C, D, E
    items.forEach(item -> System.out.println(item));
    
    //Output : C
    items.forEach(item->{
	if("C".equals(item)){
	     System.out.println(item);
	}
    });
		
    //method reference
    //Output : A,B,C,D,E
    items.forEach(System.out::println);

    //Stream and filter
    //Output : B
    items.stream()
	.filter(s -> s.contains("B"))
	.forEach(System.out::println);
```

## 2. Stream

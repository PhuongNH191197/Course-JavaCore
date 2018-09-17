## Java 8

| Tên phiên bản       ||
| ------------------- | ---------- |
| Java SE 8           | 2014-03-18 |
| Java SE 8 Update 5  | 2014-04-15 |
| Java SE 8 Update 11 | 2014-07-15 |
| Java SE 8 Update 20 | 2014-08-19 |
| Java SE 8 Update 25 | 2014-10-14 |

## 1. Lamda Expressions
Tính năng đầu tiên, đồng thời là tính năng nổi bật nhất của Java8: hỗ trợ cú pháp Lambda,  đây dường như là cải tiến lớn nhất trong cú pháp lập trình Java kể từ thời điểm phát hành Generics  và Annotations trong Java 5.

Lambda expressions là một tính năng mới quan trọng trong Java 8. Lambda expressions giống class vô danh biểu diễn dưới dạng biểu thức. Chỉ bằng một biểu thức nó có thể biểu diễn thực thi cho method của functional interfaces. 

Functional interfaces là interface chỉ có 1 method. Lambda expressions cung cấp cách thức mới làm việc với Collection một cách đơn giản và hiệu quả, tăng hiệu năng (performance) của hệ thống chạy trong môi trường đa lõi (multicore).

| Tên phiên bản       | Arrow tocken | Body |
| ------------------- | ---------- | ---------- |
| `([Data type] [param1], [param2], [param_n])` | `->` | `{body};` |

- LamExp có thể không có, có một, hoặc nhiều tham số. () -> "Framgia"; (a) -> return a\*a; (int a, int b) -> return a\*b
- Tham số của có thể được định nghĩa kiểu một cách tường minh hoặc không cần định nghĩa kiểu. Kiểu sẽ được suy ra từ ngữ cảnh cụ thể.
- Các tham số được đặc trong hai dấu đóng mở đơn (params), khi chỉ có một tham số thì có thể không cần đặt trong dấu đóng mở. a -> return a\*a
- Body code của LamExp được đặt trong dấu đóng mở nhọn {body}, khi body code chỉ có một sử lý (thể hiện) thì không cần có dấu đóng mở nhọn.

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

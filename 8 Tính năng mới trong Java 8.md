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
	listDevs.sort((Developer o1, Developer o2)->o1.getAge()-o2.getAge());
	
	//lambda, valid, parameter type is optional
	listDevs.sort((o1, o2)->o1.getAge()-o2.getAge());
```

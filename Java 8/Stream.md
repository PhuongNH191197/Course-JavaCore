# Stream

Stream là một đối tượng mới của Java được giới thiệu từ phiên bản Java 8, giúp cho việc thao tác trên collection và array trở nên dễ dàng và tối ưu hơn. Vậy nó là gì? Trong bài viết này, chúng ta hãy cùng tìm hiểu về Stream trong Java 

Định nghĩa đơn giản thì Stream là một wrapper của collection và array. Nó wrap một collection sẵn có và các data source khác để hỗ trợ việc thao tác trên các collection, datasource đó sử dụng Lambda Expression. Vì thế, bạn chỉ cần chỉ định cái bạn muốn làm, còn việc làm như thế nào, Stream sẽ lo cái đó.

## 1. Các đặc điểm của Stream:

- `Không lưu trữ`: Stream không phải là 1 kiểu câu trúc dữ liệu để chứa các đối tượng, thành phần. Stream truyền tải các thành phần từ các nguồn (source) như 1 cấu trúc dữ liệu, một mảng nào đó
- `Không chỉnh sửa`: Một toán tử thực hiện trên một stream tạo ra 1 kết quả nào đó nhưng nó không sửa nguồn của nó.
- `Lazy seek`: Nhiều toán tử thao tác trên stream như filter, map thực hiện theo cơ chế lazy. Các toán tử của stream chia làm 2 loại intermediate và terminal Intermediate operation luôn luôn là lazy. Chi tiết về các loại toán tử sẽ được đề cập ở phần bên dưới.
- `Có thể không bị chặn`: Collection có kích thước giới hạn, stream thì không. Các toán tử limit() và findFirst() có thể cho phép tính toán trên các stream vô hạn trong thời gian giới hạn
- `Tiêu hao (Consumable)`: Các thành phần của một stream chỉ được duyệt 1 lần trong vòng đời của 1 stream. Để duyệt lại các đối tượng thì stream cần được sinh lại.
- Stream hỗ trợ hoàn hảo cho Lambda Expression.
- Stream không chứa các element của collection hay array.
- Stream là immutable object.
- Chúng ta không thể dùng index để access các element trong Stream.
- Stream hỗ trợ thao tác song song các element trong collection hay array.

#### *Các loại toán tử của Stream*
> Intermediate operation: toán tử trung gian trả về stream mới, chúng luôn là lazy. Ví dụ khi thực hiện filter(), nó không thực hiện việc lọc ngay lập tức mà nó tạo ra 1 stream mới. Cái mà khi được duyệt(thực thi) sẽ chứa các phần tử hợp lệ của stream ban đầu. Lưu ý Stream được tạo từ toán tử intermediate sẽ không bắt đầu duyệt cho đến khi có 1 toán tử terminal thực hiện.

> Terminal operation: toán tử đầu cuối, sẽ duyệt(thực thi) 1 stream để trả về 1 kết quả. Sau khi toán tử terminal được thực hiện, stream sẽ được xét như là đã được tiêu thụ, dùng (consumed), không còn được sử dụng nữa. Trong trường hợp bạn vẫn muốn duyệt cùng kiểu tập hợp dữ liệu đó, bạn cần phải quay lại data source và tạo ra stream mới.


## 2. Tạo Stream như thế nào?

- Từ các class con của Collection thông qua phương thức `stream()` và `parallelStream()`.
- Từ 1 mảng bằng cách sử dụng `Arrays.stream(Object[])`;
- Từ các dòng của 1 file thông qua `BufferedReader.lines()`;
- Hoặc từ các method của class Files

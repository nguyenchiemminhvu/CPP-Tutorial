Chào các bạn! Chúng ta lại đồng hành trong khóa học lập trình trực tuyến ngôn ngữ C++ hướng thực hành.

Các bạn đã làm việc với một số kiểu dữ liệu cơ bản trong ngôn ngữ C++ như kiểu số nguyên (**int**, **int32_t**, ...), kiểu số nguyên không dấu (**uint32_t**, **uint64_t**, ...), kiểu số thực (**float**, **double**, ...), hay kiểu kí tự (char). 

Những kiểu dữ liệu này khi khai báo biến sẽ tạo ra những vùng nhớ trong máy tính để lưu trữ những giá trị có ý nghĩa. Những kiểu dữ liệu khác nhau có thể lưu trữ giá trị giống nhau, ví dụ giá trị **3** trong số nguyên cũng tương đương với giá trị **3.0** trong tập hợp số thực. 

Trong một số trường hợp tính toán cụ thể hoặc cần biểu diễn giá trị dưới những định dạng khác nhau, chúng ta cần thực hiện **ép kiểu (casting)** để chuyển đổi qua lại những kiểu dữ liệu có khả năng lưu trữ giá trị giống nhau.

Trong ngôn ngữ C++, ép kiểu (**casting**) được chia làm 2 loại:

###Ép kiểu ngầm định (implicit type conversion)

Ép kiểu ngầm định (**implicit type conversion**) được thực hiện bất cứ khi nào một kiểu dữ liệu cơ bản được sử dụng, nhưng giá trị được cung cấp thuộc kiểu dữ liệu cơ bản khác, và người dùng không nói cho **compiler** biết cách để thực hiện việc chuyển đổi này.

Chúng ta cùng xem qua ví dụ này:

	float f_value = 3; //initialize float point value with integer 3

Trong trường hợp này, **compiler** không chỉ thực hiện copy giá trị 3 gán vào vùng nhớ mà biến **f_value** đang nắm giữ, mà còn thực hiện chuyển giá trị số nguyên 3 sang số thực 3.0f, sau đó, giá trị 3.0f mới được gán cho biến **f_value**.

Việc khởi tạo giá trị cho biến bằng giá trị của một biến có kiểu dữ liệu khác cũng đi kèm với việc thực hiện ép kiểu ngầm định.

	float f_value = 10.0f;
	double d_value(f_value);

Mặc dù **f_value** và **d_value** đều dùng để lưu trữ giá trị số thực, nhưng khi găp 2 kiểu dữ liệu khác nhau, **compiler** vẫn thực hiện ép kiểu cho lệnh khởi tạo này.

Trong một số trường hợp cụ thể, **compiler** sẽ đưa ra cảnh báo về việc ép kiểu ngầm định có thể gây mất hoặc sai dữ liệu.

	double d_value = DBL_MAX; // DBL_MAX is maximum value of double type
	float f_value(d_value);
	cout << f_value << endl;

Như các bạn đã biết, kiểu **double** có kích thước 8 bytes trong khi kiểu **float** chỉ có kích thước 4 bytes. Vì thế, giá trị mà biến kiểu **double** có thể vượt ngoài khả năng lưu trữ của biến kiểu **float**.

Điều này dẫn đến việc in giá trị biến **f_value** lên màn hình là không chính xác. Với việc gán giá trị thuộc kiểu dữ liệu có kích thước lớn hơn cho một biến có kích thước nhỏ hơn hoàn toàn có khả năng xảy ra mất dữ liệu nếu không kiểm soát được giá trị của nó.

###Ép kiểu rõ ràng (explicit type conversion)

Ép kiểu rõ ràng (**explicit type conversion**) là việc chuyển đổi kiểu dữ liệu một cách rõ ràng bởi yêu cầu của lập trình viên. 

Có 5 cách khác nhau trong việc ép kiểu rõ ràng: 

- C-Style casts.
- Static casts.
- Const casts.
- Dynamic casts.
- Reinterpret casts.

Chúng ta cùng xét ví dụ sau:

	int i_value1 = 10;
	int i_value2 = 4;
	float f_value = i_value1 / i_value2;

Biến **f_value** sẽ được gán giá trị là 2.0 vì phép chia hai số nguyên sẽ trả về kết quả là một giá trị số nguyên. Làm thế nào chúng ta có thể nói với **compiler** rằng chúng ta muốn có kết quả trả về là số thực?

####C-style casts

Trong chuẩn ngôn ngữ C, **casting** được thực hiện thông qua toán tử **()** với tên của kiểu dữ liệu bạn muốn chuyển đổi về được đặt bên trong.

	int i_value1 = 10;
	int i_value2 = 4;
	float f_value = (float)i_value1 / i_value2;

Trong đoạn chương trình trên, mình sử dụng **float cast** để nói với **compiler** đưa **i_value1** về kiểu **float**. Sau khi **i_value1** được ép về kiểu **float**, **i_value2** cũng được ép về kiểu **float** để thực hiện phép chia 2 số thực.

Ngôn ngữ C++ cho phép thực hiện **C-style cast** giống với cách gọi hàm:

	f_value = float(i_value1) / i_value2;

Việc thực hiện **C-style cast** không được **compiler** kiểm tra tại thời điểm biên dịch chương trình, nên **compiler** sẽ không đưa ra những cảnh báo, điều này khiến các lập trình viên có thể làm những việc không có ý nghĩa.

***Các bạn nên tránh sử dụng C-style cast.***

####Static casts

Ngôn ngữ C++ giới thiệu cho chúng ta 1 toán tử ép kiểu gọi là **static_cast**. Các bạn có thể đã gặp toán tử này (trong bài kiểu kí tự khi mình cần lấy mã **ASCII** của 1 kí tự). 

	char ch = 'A';
	cout << static_cast<int16_t>(ch) << endl; //print 65, not 'A'

Ưu điểm của toán tử **static_cast** là nó yêu cầu **compiler** kiểm tra kiểu dữ liệu tại thời điểm biên dịch chương trình, hạn chế được những lỗi ngoài ý muốn. 

	int i_value1 = 10;
	int i_value2 = 4;
	float f_value = static_cast<float>(i_value1) / i_value2;

##
###Tổng kết

Việc ép kiểu nên được hạn chế sử dụng, vì bất cứ khi nào thực hiện hành vi ép kiểu cũng tiềm ẩn khả năng xảy ra vấn đề với chương trình. Trong một số trường hợp cụ thể chúng ta bắt buộc phải sử dụng ép kiểu, nên sử dụng **static_cast** thay vì ép kiểu theo **C-Style**.

Trong phần hướng dẫn lập trình C++ cơ bản, mình chỉ hướng dẫn các bạn sử dụng toán tử **static_cast** để thực hiện chuyển đổi các kiểu dữ liệu cơ bản. Những cách ép kiểu rõ ràng khác (reinterpret_cast và dynamic_cast) mình sẽ giới thiệu đến các bạn trong những phần có liên quan về sau. 

**Hẹn gặp lại các bạn trong bài học tiếp theo trong khóa học lập trình C++ hướng thực hành.**


Mọi ý kiến đóng góp hoặc thắc mắc có thể đặt câu hỏi trực tiếp tại diễn đàn 

[www.daynhauhoc.com](www.daynhauhoc.com "DayNhauHoc")

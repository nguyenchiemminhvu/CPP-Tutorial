Chào các bạn! Trong chương này, mình muốn giới thiệu đến các bạn một số kiểu dữ liệu khác với những gì các bạn đã được học và sử dụng trong các bài học trước, ngoài ra còn có thêm một số từ khóa về kiểu dữ liệu thường dùng trong chuẩn **C++11**.

Trong bài học này, chúng ta sẽ tìm hiểu cách sử dụng thư viện **cstdint**, một thư viện được chuẩn **C++99** định nghĩa và chúng có thể được sử dụng trên nhiều nền tảng. Nhưng trước hết, chúng ta cùng nhìn lại những kiểu dữ liệu số nguyên mà chúng ta từng biết.

	signed short		_short; 		//2 bytes: -32768 to 32767
	unsigned short		_u_short; 		//2 bytes: 0 to 65535
	signed int			_int; 			//4 bytes: -2147483648 to 2147483647
	unsigned int		_u_int; 		//4 bytes: 0 to 4294967295
	signed long long	_long_long; 	//8 bytes: -9223372036854775808 to 9223372036854775807
	unsigned long long	_u_long_long; 	//8 bytes: 0 to 18446744073709551615

*Lưu ý: Khi khai báo biến không có từ khóa **unsigned** đứng trước, compiler sẽ mặc định đặt từ khóa **signed** trước kiểu dữ liệu. (kiểu **signed** có nhận giá trị âm, kiểu **unsigned** chỉ nhận giá trị từ 0 trở lên)* 

Khi làm việc với một số hệ thống cũ, kiểu dữ liệu **int** và **unsigned int** chỉ có kích thước 2 bytes chứ không phải 4 bytes như Visual studio 2015 đã định nghĩa.

***Các bạn đã nhận ra những rắc rối mà chúng ta sẽ gặp phải khi làm việc với kiểu số nguyên rồi phải không?*** Trong khi chúng ta cần phải nhớ rất nhiều thứ trong ngôn ngữ lập trình C++, chúng ta bây giờ còn phải nhớ cả kích thước của từng kiểu dữ liệu số nguyên khi chúng được định nghĩa với những cái tên hoàn toàn khác nhau (**short**, **int**, **long**, ...).

Đó chính là lý do thư viện **cstdint** xuất hiện, nó đảm bảo rằng biến (variable) kiểu số nguyên mà bạn chọn chiếm cùng kích thước vùng nhớ trên mọi kiến trúc hệ thống.

###Fixed-width integers

Trong thư viện này, chúng ta hiện tại chỉ quan tâm đến một số kiểu dữ liệu số nguyên thông dụng sau:

	//Name		//Type				//Range
	int8_t 		1 byte signed		-128 to 127
	uint8_t		1 byte unsigned		0 to 255
	int16_t		2 bytes signed		-32768 to 32767
	uint16_t	2 bytes unsigned	0 to 65535
	int32_t		4 bytes signed		-2147483648 to 2147483647
	uint32_t	4 bytes unsigned	0 to 4294967295
	int64_t		8 bytes signed		-9223372036854775808 to 9223372036854775807
	uint64_t	8 bytes unsigned	0 to 18446744073709551615

**int8_t** là kiểu dữ liệu số nguyên có dấu với độ lớn 8 bits (bit là đơn vị lưu trữ nhỏ nhất trong máy tính), và 1 byte độ lớn vùng nhớ máy tính tương đương với 8 bits. Tương tự cho các kiểu dữ liệu khác như **int64_t** là kiểu số nguyên 8 bytes (64 bits bằng 8 bytes).

Khi sử dụng cách khai báo kiểu dữ liệu này, chúng ta biết chính xác kích thước vùng nhớ mà chúng ta sử dụng là bao nhiêu, từ đó dễ dàng suy luận ra phạm vi giá trị mà biến có thể chứa hơn.

Để sử dụng những cách khai báo kiểu dữ liệu này, các bạn chỉ cần đơn giản include thư viện **cstdint** tại phần khai báo thư viện sử dụng. Ví dụ:

	#include <iostream>
	#include <cstdint>
	using namespace std;

	int main()	{
		
		int32_t var(5);
		int another_integer(var);

		if(var == another_integer)	{
			cout << "(var == another_variable) is true" << endl;
		}

		system("pause");
		return 0;
	}
	
Như các bạn thấy ở ví dụ trên, hai biến **var** và **another_integer** tuy khác cách khai báo nhưng chúng có cùng kích thước bộ nhớ và cùng lưu trữ giá trị số nguyên, nên mình hoàn toàn có thể sử dụng hai biến này với mục đích giống nhau. Điều khác biệt duy nhất là khi nhìn vào biến **var**, ta dễ dàng nhận biết kích thước vùng nhớ mà biến đó đang chiếm giữ hơn.

###Macros

Thư viện **cstdint** định nghĩa cho chúng ta một số **macro** để chúng ta dễ dàng lấy giá trị cực đại (max value) hoặc cực tiểu (min value) của mỗi kiểu dữ liệu số nguyên chúng ta vừa học ở trên.

**Macro** là gì? Nó là một cái tên mà lập trình viên đề ra. Bất cứ khi nào cái tên đó được sử dụng trong chương trình, nó thay thế bằng nội dung mà **macro** đó định nghĩa. Để định nghĩa một macro, các bạn sử dụng chỉ thị ```#define``` như sau:

	#define MY_VALUE 100

Sau đó, khi compiler bắt gặp các bạn sử dụng cái tên MY_VALUE, nó sẽ được thay thế bằng giá trị 100.

	uint16_t value = MY_VALUE; // value = 100
	cout << MY_VALUE + pow(MY_VALUE, 2) << endl; // 100 + pow(100, 2)

Chúng ta còn nhiều điều để nói về **Macro** trong C++, nhưng trong bài này mình chỉ nói cách định nghĩa **Macro** tương tự việc khai báo một hằng số (**const**) như trên để phục vụ cho bài học này.

Trong thư viện **cstdint** chúng ta có thể sử dụng các **Macro** sau:

####Signed integers: minimum value

	INT8_MIN - Giá trị cực tiểu (minimum value) của kiểu int8_t
	INT16_MIN - Giá trị cực tiểu (minimum value) của kiểu int16_t
	INT32_MIN - Giá trị cực tiểu (minimum value) của kiểu int32_t
	INT64_MIN - Giá trị cực tiểu (minimum value) của kiểu int64_t

Các bạn hãy thử chạy những dòng lệnh này trên Visual studio 2015 và xem lại những giá trị **MIN** trong bảng ở phần trên. 

	cout << "Minimum value of uint8_t = "  INT8_MIN << endl;
	cout << "Minimum value of uint16_t = "  INT16_MIN << endl;
	cout << "Minimum value of uint32_t = "  INT32_MIN << endl;
	cout << "Minimum value of uint64_t = "  INT64_MIN << endl;


####Signed integers: maximum value

	INT8_MAX - Giá trị cực đại (maximum value) của kiểu int8_t
	INT16_MAX - Giá trị cực đại (maximum value) của kiểu int16_t
	INT32_MAX - Giá trị cực đại (maximum value) của kiểu int32_t
	INT64_MAX - Giá trị cực đại (maximum value) của kiểu int64_t

Cùng thử in ra giá trị của những Macro này xem thế nào.

	cout << "Maximum value of uint8_t = "  INT8_MAX << endl;
	cout << "Maximum value of uint16_t = "  INT16_MAX << endl;
	cout << "Maximum value of uint32_t = "  INT32_MAX << endl;
	cout << "Maximum value of uint64_t = "  INT64_MAX << endl;

####Unsigned integers: maximum value

Vì kiểu **unsigned integer** có giá trị nhỏ nhất là 0 nên người ta không cần phải định nghĩa những **Macro** cho minimum value mà chỉ cần quan tâm đến maximum value.

	UINT8_MAX - Giá trị cực đại (maximum value) của kiểu uint8_t
	UINT16_MAX - Giá trị cực đại (maximum value) của kiểu uint16_t
	UINT32_MAX - Giá trị cực đại (maximum value) của kiểu uint32_t
	UINT64_MAX - Giá trị cực đại (maximum value) của kiểu uint64_t

Tương tự như trên, các bạn thử in ra giá trị của những **Macro** này.

####Sử dụng thư viện cstdint

Bây giờ mình sẽ sử dụng thư viện **cstdint** để giải một bài toán đơn giản.

***Yêu cầu: Nhập 5 giá trị số nguyên từ bàn phím, in ra màn hình kết quả lớn nhất và nhỏ nhất của 5 giá trị đó.***

Sau khi đọc yêu cầu bài toán, chúng ta cần đưa ra giải pháp trước khi bắt tay vào viết mã.

Trước hết, chúng ta cần 2 biến kiểu số nguyên, một biến để lưu giá trị lớn nhất trong 5 số vừa nhập, một biến để lưu giá trị nhỏ nhất của 5 số đó.

	int32_t min_value;
	int32_t max_value;

Bây giờ, chúng ta tạm thời bỏ qua việc tìm giá trị lớn nhất và nhỏ nhất của 5 số khác nhau, mà cùng giải quyết một bài toán đơn giản hơn, đó là tìm giá trị lớn nhất và nhỏ nhất của 2 số nguyên **a** và **b**. 

- Tìm giá trị lớn nhất trong hai số **a** và **b**:

Chúng ta chỉ cần thực hiện 1 phép so sánh kiểm tra xem giá trị của a có lớn hơn b hay không? Nếu **(a lớn hơn b)** là **đúng**, giá trị lớn nhất là **a**, ngược lại, giá trị lớn nhất là **b**.

	if(a > b)
		cout << a << endl;
	else
		cout << b << endl;

- Tìm giá trị nhỏ nhất trong hai số **a** và **b**:

Chúng ta làm tương tự như trên, nhưng cần thay đổi một chút ở phần biểu thức so sánh. Nếu **(a bé hơn b)** là **đúng**, giá trị nhỏ nhất là **a**, ngược lại, giá trị nhỏ nhất là **b**.

Khá đơn giản phải không các bạn! Áp dụng lại cho bài toán tìm giá trị lớn nhất và nhỏ nhất từ 5 giá trị số nguyên mà người dùng nhập vào từ bàn phím:

- Tìm giá trị lớn nhất của 5 số khác nhau:

Như mình đã khai báo biến ```max_value``` ở trên, biến này sẽ lưu giá trị lớn nhất tại thời điểm ban đầu. Cứ mỗi lần so sánh với một giá trị trong 5 giá trị người dùng vừa nhập, nếu phát hiện giá trị nào lớn hơn giá trị max hiện tại, chúng ta gán lại giá trị ```max_value``` bằng giá trị của người dùng vừa nhập.

	for(int8_t i = 1; i <= 5; i++)	{
		int32_t value;
		//nhập giá trị vào biến value tại đây
		
		//thực hiện so sánh giá trị max hiện tại với giá trị vừa nhập
		if(value > max_value) //nếu đúng thì thực hiện gán lại giá trị max mới
			max_value = value;
	}

	//in ra kết quả là giá trị lớn nhất của 5 số vừa nhập

- Tìm giá trị nhỏ nhất của 5 số khác nhau:

Đối với trường hợp này, chúng ta sử dụng biến ```min_value``` tương tự trường hợp tìm ```max_value``` nhưng đối lại điều kiện so sánh một chút. Cứ mỗi lần so sánh với một giá trị trong 5 giá trị người dùng vừa nhập, nếu phát hiện giá trị nào nhỏ hơn giá trị ```min_value``` hiện tại, chúng ta gán lại giá trị ```min_value``` bằng giá trị người dùng vừa nhập

	for(int8_t i = 1; i <= 5; i++)	{
		int32_t value;
		//nhập giá trị vào biến value tại đây
		
		//thực hiện so sánh giá trị max hiện tại với giá trị vừa nhập
		if(value < min_value) //nếu đúng thì thực hiện gán lại giá trị min mới
			min_value = value;
	}
	
	//in ra kết quả là giá trị nhỏ nhất của 5 số vừa nhập

Chúng ta còn bỏ sót một chi tiết vô cùng quan trọng! Giá trị ban đầu của ```max_value``` và ```min_value``` nên là bao nhiêu?

Đối với biến ```max_value```, chúng ta cần một giá trị đảm bảo rằng người dùng sẽ không nhập vào số nguyên nào nhỏ hơn giá trị max ban đầu, và không thể vượt quá phạm vi lưu trữ giá trị của kiểu dữ liệu bạn chọn. Chúng ta không còn giá trị nào phù hợp hơn ngoài **INT32_MIN**.

Tương tự, giá trị ban đầu phù hợp nhất cho biến ```min_value``` là **INT32_MAX**.

**(Vì mình chọn sử dụng biến kiểu *int32_t* để lưu trữ)**

Cuối cùng, chúng ta có thể viết ra một chương trình tương đối hoàn thiện cho bài toán trên:

	#include <iostream>
	#include <cstdint>
	using namespace std;
	
	int main()	
	{
		int32_t min_value = INT32_MAX;
		int32_t max_value = INT32_MIN;
		const int8_t number_of_value = 5;
	
		for (int8_t i = 1; i <= 5; i++)	{
			int32_t current_value;
			cout << "Please enter an integer value: ";
			cin >> current_value;
	
			if (current_value < min_value)
				min_value = current_value;
	
			if (current_value > max_value)
				max_value = current_value;
		}
	
		cout << "Minimum value: " << min_value << endl;
		cout << "Maximum value: " << max_value << endl;
	
		system("pause");
		return 0;
	}

##
###Tổng kết

- Sử dụng thư viện **cstdint** giúp các bạn kiểm soát tốt hơn kích thước vùng nhớ của kiểu dữ liệu số nguyên mà bạn khai báo cho biến, đồng thời cũng dễ dàng ước lượng phạm vi giá trị của biến cho phù hợp.

- Thư viện **cstdint** cũng được định nghĩa bên trong **namespace std**, vì thế khi sử dụng thư viện này, các bạn nên có thêm dòng khai báo ```using namespace std;``` để đảm bảo mọi thứ hoạt động bình thường.


**Hẹn gặp lại các bạn trong bài học tiếp theo trong khóa học lập trình C++ hướng thực hành.**


Mọi ý kiến đóng góp hoặc thắc mắc có thể đặt câu hỏi trực tiếp tại diễn đàn 

[www.daynhauhoc.com](www.daynhauhoc.com "DayNhauHoc")


Chào các bạn học viên đang theo dõi khóa học lập trình trực tuyến ngôn ngữ C++.

Trong bài học hôm nay, chúng ta sẽ cùng tìm hiểu một chủ đề rất quan trọng đối với phần C++ cơ bản, đó chính là **Function** (có thể gọi là Hàm).

##
###Function (Hàm)

Có nhiều cách để nói về khái niệm **function** khác nhau.

>Function là một đoạn các câu lệnh có thể tái sử dụng. Function cho phép lập trình viên cấu trúc chương trình thành những phân đoạn khác nhau để thực hiện những công việc khác nhau.

Các bạn đã từng sử dụng **function** (hàm) trong những bài học trước. Những hàm tính toán toán học trong thư viện **cmath**, những hàm xử lý **C-style string** thuộc thư viện **cstring**, hay thậm chí là hàm **main** mà các bạn đã nghe nói đến ở phần đầu của khóa học này.

**Function** (hàm) được người ta ví như một cái hộp đen, các bạn không biết bên trong nó là gì, nhưng nó có một đầu vào (input) và một đầu ra (output). Việc của các bạn khi sử dụng cái hộp đen này (thực hiện lời gọi hàm) là đưa những dữ liệu đầu vào tương thích vào đầu vào của nó, và nó sẽ cho bạn kết quả tại đầu ra.

Ví dụ:

	#include <cstring>
	//......
	char str[] = "This is a sample string";
	int length = strlen(str); //use strlen function

Mình hoàn toàn không biết bên trong hàm strlen gồm có những dòng lệnh gì, được thực hiện như thế nào, mà chỉ biết rằng hàm **strlen** có đầu vào là một chuỗi kí tự, đầu ra của nó là một giá trị đặc tả độ dài của chuỗi kí tự mình truyền vào.

Cứ mỗi lần các bạn sử dụng hàm trong một câu lệnh, chúng ta gọi đó là 1 lời gọi hàm (**function call**). Chúng ta có thể thực hiện gọi hàm nhiều lần trong một chương trình, ví dụ:

	char str1[] = "string 1";
	char str2[] = "string 2";

	if(strlen(str1) == strlen(str2))	{
		//do something
	}

Đây chính là khả năng tái sử dụng của hàm. Với một lần định nghĩa hàm, chúng ta có thể dùng nó nhiều lần (có thể với nhiều input khác nhau) tùy vào mục đích sử dụng.

###Khai báo (declare) và định nghĩa (define) function

Một **function** (hàm) được tạo ra từ những yếu tố sau:

- Kiểu trả về của hàm (data type of output).
- Tên hàm (function name).
- Danh sách tham số (function parameters).
- Khối lệnh (block of statements).

![](0.png)

***Một hàm được định nghĩa thường nhằm để giải quyết một công việc nào đó (có thể thực hiện nhiều lần lặp đi lặp lại). Vì thế, tên hàm nên diễn đạt được tên công việc mà các bạn muốn máy tính thực hiện.***

Thông thường, chúng ta sử dụng động từ để biểu diễn hành động, công việc cần thực hiện. Chúng ta cũng thường sử dụng động từ để đặt tên cho hàm. Ví dụ: moveUp, moveDown, turnLightOn, readFile, ...

- Hàm có thể có giá trị trả về hoặc không có giá trị trả về.
- Hàm bắt buộc phải có tên, quy tắc đặt tên giống với quy tắc đặt tên biến.
- Hàm có thể có 1 tham số, nhiều tham số hoặc không có tham số nào.
- Khối lệnh phía sau hàm chứa những dòng lệnh mà nó sẽ được thực hiện trong mỗi lần gọi hàm.

Ví dụ:

![](1.png)

Mình vừa định nghĩa 2 hàm mẫu có tên là **addition** và **introduce**, trong đó:

- Hàm addition có kiểu trả về là **int**. Hàm introduce không có kiểu trả về (**void**).
- Hàm addition nhận 2 giá trị đầu vào là 2 số nguyên. Hàm introduce không cần giá trị đầu vào nào cả.
- Hàm addition có biến cục bộ tên là summary được khai báo bên trong khối lệnh. Hàm introduce không có biến nào được khai báo.
- Hàm addition tính tổng giá trị của 2 biến ở đầu vào, và return giá trị tổng bằng từ khóa **return**. Hàm introduce không có giá trị trả về nên chưa cần sử dụng từ khóa **return**.

***Các bạn cần đặt phần code định nghĩa các hàm nằm trên hàm main thì chúng ta mới có thể sử dụng chúng bên trong hàm main được. Cũng tương tự, nếu chúng ta gọi hàm A từ khối lệnh bên trong hàm B thì hàm A phải được định nghĩa bên trên hàm B.***

###Sử dụng hàm (do function call)

Cũng tương tự như cách các bạn sử dụng hàm của các thư viện có sẵn, nhưng chúng ta đã định nghĩa hàm **addition** và **introduce** bên trong file main.cpp nên chúng ta có thể gọi trực tiếp đến chúng mà không cần include thư viện nào khác.

	int addition(int value1, int value2)
	{
		int sumary = value1 + value2;
		return sumary;
	}

	void introduce()
	{
		cout << "Hello!" << endl;
		cout << "I'm a program" << endl;
	}

	int main()
	{
		introduce();

		int32_t i_value1 = 5;
		int32_t i_value2 = 7;
		int32_t sum = addition(i_value1, i_value2);

		cout << i_value1 << " + " << i_value2 << " = " << sum << endl;
		
		return 0;
	}

- Vì hàm **introduce** không có giá trị trả về nên chúng ta chỉ cần gọi tên của nó ra, và hàm **introduce** cũng không nhận giá trị đầu vào nào cả, nên chúng ta để trống bên trong cặp dấu ngoặc đứng sau lời gọi hàm.

- Đối với hàm **addition** nó sẽ có giá trị trả về là kiểu số nguyên, nên mình khai báo thêm biến **sum** bên trong hàm **main** để lưu trữ giá trị sau khi tính toán của hàm **addition**. Ngoài ra, hàm addition yêu cầu 2 giá trị số nguyên làm đầu vào, nên mình đưa biến ```i_value1``` và ```i_value2``` vào cặp dấu ngoặc phía sau tên hàm.

###Hoạt động bên trong lời gọi hàm

Mỗi hàm sẽ thực hiện một công việc mà lập trình viên định nghĩa cho chúng. Thông thường, một chương trình sẽ tạm thời gián đoạn một công việc đang được thực hiện để thực hiện công việc khác mà nó bắt buộc phải làm. Bạn có thể thấy điều này trong thực tế. Ví dụ, bạn đang đọc sách nhưng nhận được một cuộc gọi điện thoại từ người thân, bạn sẽ đánh dấu trang sách mà bạn đang đọc, thực hiện cuộc gọi, và trở lại đọc sách tại trang mà bạn đã đánh dấu.

Chương trình C++ làm việc tương tự như vậy. Chương trình đang thực hiện một chuỗi các câu lệnh bên trong khối lệnh hiện tại, đến khi 1 lời gọi hàm xuất hiện, nó nói với CPU tạm hoãn công việc trong khối lệnh hiện tại và chuyển đến thực thi hàm khác.

Sau khi thực hiện xong công việc bên trong hàm được gọi, CPU quay lại thực hiện các câu lệnh phía sau vị trí mà nó đã đánh dấu tại lời gọi hàm.

![](2.png)

###Địa chỉ của hàm (function address)

Khi chạy chương trình, những hàm được định nghĩa khác nhau cũng được cấp phát cho những vùng nhớ khác nhau nằm đâu đó trong thiết bị lưu trữ của máy tính. Có chút gì đó tương tự với biến (**variable**) phải không các bạn?

Đối với biến (**variable**), hệ điều hành cung cấp vùng nhớ cho nó để lưu trữ giá trị. Đối với hàm (**function**), hệ điều hành cung cấp vùng nhớ cho nó để lưu trữ các đoạn mã lệnh.

- Khi thực hiện lời gọi biến thông qua tên biến, chương trình tìm đến vùng nhớ mà tên biến đó đang nắm giữ để truy xuất giá trị của biến.

- Khi thực hiện lời gọi hàm (function call) thông qua tên hàm, chương trình tạm gián đoạn công việc đang thực hiện, chuyển đến vùng nhớ mà hàm đó đang nắm giữ và thực hiện những mã lệnh trong vùng nhớ đó.

Mình sẽ cho các bạn xem địa chỉ của hàm addition và introduce trên máy tính của mình (kĩ thuật này mình sẽ nói đến trong các bài học tiếp theo):

![](3.png)

Như các bạn thấy, hàm addition và introduce có 2 địa chỉ khác nhau trong bộ nhớ máy tính.

###Sử dụng từ khóa return

Từ khóa **return** được sử dụng trong 2 ngữ cảnh khác nhau:

- Đối với hàm không có giá trị trả về (hàm kiểu **void**):

	Đối với hàm kiểu **void**, từ khóa **return** chỉ có chức năng kết thúc công việc của hàm tại thời điểm sử dụng. Ví dụ:

		void doSomething()
		{
			return; //Terminates this function
			cout << "This line will not be displayed" << endl;
		}

	Khi gặp từ khóa return trong hàm, các dòng lệnh đứng sau nó sẽ không được thực thi vì chương trình lúc này đã thoát khỏi khối lệnh của hàm. Chúng ta có thể xác định một số trường hợp cụ thể dẫn tới việc kết thúc hàm bằng một vài cấu trúc điều kiện. Ví dụ:

		void getValueFromKeyboard()
		{
			int32_t value;
			cin >> value;
			if(value < 0)
				return;
			else
				cout << value << endl;
		}

- Đối với hàm có giá trị trả về (hàm kiểu khác **void**):
	
	Đối với hàm có kiểu trả về khác **void**, từ khóa **return** là bắt buộc phải có. Từ khóa **return** trong trường hợp này có chức năng kết thúc công việc của hàm và trả về kết quả (**output** của hàm), vì thế chúng ta cần có 1 giá trị (hoặc 1 biến) đi kèm với từ khóa **return**.

		int return5()
		{
			return 5;
			cout << "The end of the function" << endl;
		}

	Lấy ví dụ như hàm **return5** ở trên, một khi hàm này được gọi từ khối lệnh khác, giá trị 5 sẽ được trả về. Dòng lệnh đứng sau câu lệnh **return** sẽ không được thực thi.

###Hàm main

Đã đến lúc chúng ta nhìn lại hàm **main** mà chúng ta vẫn khai báo hằng ngày để xem nó hoạt động thật sự như thế nào.

Khi chương trình C++ được thực thi, hệ điều hành thực hiện 1 lời gọi hàm đến địa chỉ của hàm **main**, và những mã lệnh bên trong hàm **main** được thực thi lần lượt từ trên xuống dưới. Cuối cùng, hàm main **return** 1 giá trị số nguyên (thường là 0) trở lại cho hệ điều hành. Đây là lý do hàm **main** được định nghĩa là ```int main() {  }```.

Tại sao hệ điều hành cần lấy được giá trị trả về của hàm **main**? Giá trị trả về của hàm **main** được gọi là **status code**, nó thông báo với hệ điều hành rằng chương trình có được thực hiện thành công hay không. Lập trình viên chúng ta thường quy ước rằng giá trị 0 nghĩa là thành công, giá trị âm nghĩa là có lỗi xảy ra trong chương trình.

Chúng ta có thể xem được **status code** sau khi debug chương trình bằng Visual studio 2015.

![](4.png)

Việc sử dụng từ khóa **return** trong vòng lặp **for** đã giúp mình biết rằng có vấn đề xảy ra bên trong đoạn lệnh đó, như thế mình có thể sửa lỗi dễ dàng hơn.

###Nguyên mẫu hàm (Function prototype)

Trong C++, mọi hàm muốn được sử dụng thì phải có đủ 2 phần: khai báo và định nghĩa. Trong phần khai báo, chúng ta cung cấp cho chương trình tên hàm, kiểu trả về, danh sách tham số đầu vào. Và phần định nghĩa chính là khối lệnh đứng sau phần khai báo hàm.

Ở những ví dụ trên, mình chọn cách vừa khai báo vừa định nghĩa hàm. Bên cạnh đó, C++ còn hổ trợ cho chúng ta tách 2 phần khai báo và định nghĩa ra thành 2 phần riêng biệt. Trong đó, phần khai báo nằm riêng gọi là nguyên mẫu hàm (**function prototype**).

	int add(int value1, int value2); //function prototype

Mình lấy ví dụ trên đây là một function prototype. Phần định nghĩa của hàm này vẫn chưa có, vì vậy, nếu các bạn thực hiện gọi hàm **add(int, int)** thì chương trình sẽ báo lỗi.

#####Định nghĩa cho function prototype

Việc định nghĩa cho nguyên mẫu hàm cần đảm bảo rằng các bạn ghi đúng thông tin các bạn đã cung cấp trong phần khai báo. Phần định nghĩa phải đặt ở đâu đó phía dưới phần khai báo.

	int add(int i1, int i2)
	{
		return i1 + i2;
	}

Vậy là mình vừa định nghĩa xong cho nguyên mẫu hàm **add(int, int)** mà mình vừa khai báo ở trên. Các bạn có thấy điều gì đặc biệt không? Đó chính là trong nguyên mẫu hàm mình đặt tên cho 2 tham số là **value1** và **value2** nhưng khi định nghĩa mình lại đối tên chúng thành **i1** và **i2**. Điều này không quan trọng. **Khi khai báo nguyên mẫu hàm các bạn có thể chưa cần cung cấp tên biến của tham số, mà chỉ cần quan tâm đến kiểu dữ liệu của mỗi tham số.**

	int add(int, int); // receive 2 integer as input

#####Tại sao lại phải sử dụng function prototype?

Việc sử dụng **function prototype** hay không không quan trọng. Điều này là tùy vào mỗi người. Nhưng sử dụng function prototype có thể giúp chương trình của các bạn rõ ràng hơn.

Đặt trường hợp chương trình của bạn có rất nhiều hàm cần được xử lý, thế rồi các bạn định nghĩa hàm tràn lan ra file mã nguồn. Đến khi nhìn lại mã nguồn sẽ rất rối mắt. Thay vào đó, chúng ta khai báo hết các nguyên mẫu hàm cần sử dụng phía trên cùng của file mã nguồn, sau đó phần định nghĩa nằm bên dưới. Lúc cần tìm xem chương trình của chúng ta có những hàm nào, chỉ cần kéo lên trên để xem là được.

Ví dụ:

	float add(float, float);
	float sub(float, float);
	void doSomething();
	//...............

	float add(float f1, float f2) { return f1 + f2; }
	
	float sub(float f1, float f2) { return f1 - f2; }

	void doSomeThing()	{ //do something }

#####Phím tắt trong Visual studio 2015 khi thao tác với function prototype

- Để chuyển đến phần định nghĩa của nguyên mẫu hàm, các bạn click chuột trái vào tên hàm của nguyên mẫu hàm và nhấn phím **F12**, Visual studio sẽ tự động di chuyển con trỏ đến phần định nghĩa.

- Trường hợp nguyên mẫu hàm chưa được định nghĩa, con trỏ sẽ không di chuyển đi đâu cả sau khi nhấn phím **F12**. Visual studio 2015 có thể giúp bạn tạo ra mẫu định nghĩa nguyên mẫu hàm tự động bằng cách click chuột trái vào tên hàm của nguyên mẫu hàm, nhấn tổ hợp phím **Ctrl + >** và nhấn **Enter**.

- Ngược lại, nếu các bạn đang ở phần định nghĩa hàm và muốn tìm đến vị trí khai báo nguyên mẫu hàm, các bạn click vào tên hàm của phần định nghĩa và nhấn phím **F12**. Visual studio sẽ chuyển con trỏ đến vị trí nguyên mẫu hàm nếu có.

###Thử định nghĩa lại một số hàm toán học thông dụng

Bây giờ chúng ta cùng thử định nghĩa lại một số hàm cơ bản trong thư viện **cmath** mà các bạn đã được học trong các bài học trước.

*(Mình làm điều này chỉ để giúp các bạn hiểu hơn về cách khai báo, định nghĩa, và sử dụng hàm cơ bản. Bài học này chỉ giúp các bạn có cái nhìn đầu tiên về hàm (function) trong C++, mình sẽ làm rõ các phần chi tiết về hàm trong những bài học tiếp theo).*

- Hàm **pow:**

	Hàm **pow** trong thư viện **cmath** giúp chúng ta tính lũy thừa của một cơ số (base) với số mũ (exponential) cho trước. Các bạn tính lũy thừa không sử dụng công cụ hổ trợ tính toán như thế nào? Cách chúng ta thường sử dụng là nhân exponential lần giá trị base lại với nhau.

		float myPow(float base, int32_t exponential)
		{
			float result = 1;
			//calculate power of base
			for(int32_t i = 1; i <= exponential; i++)
				result *= base;

			return result;
		}

	Trong thân hàm, mình sử dụng biến result để lưu trữ giá trị tính toán, sau khi thực hiện trả về giá trị lũy thừa đã tính, biến result sẽ bị hủy và kết thúc công việc của hàm **myPow**.

- Hàm **abs:**

	Tương tự đối với hàm **abs** trong thư viện **cmath**, hàm này sẽ trả về giá trị là giá trị tuyệt đối của một giá trị đầu vào. Vì thế, hàm này sẽ có kiểu dữ liệu trả về khác kiểu **void**.

		float myAbs(float value)
		{
			if(value < 0)
				return -value;
			else
				return value;
		}

Như vậy chúng ta đã có một số hàm cơ bản như tính lũy thừa, tính giá trị tuyệt đối, chúng ta có thể gọi trực tiếp hàm **myPow** hoặc **myAbs** mà không cần phải thực hiện include thư viện **cmath** vào nữa.

***Tuy nhiên, mình không khuyên các bạn làm lại những thứ đã có sẵn.***

##
###Tổng kết

**Function** (hàm) là một khái niệm quan trọng giúp các bạn thiết kế chương trình một cách đơn giản hơn. Trong bài này, chúng ta chỉ mới có cái nhìn đầu tiên về cách khai báo, định nghĩa và sử dụng hàm. Mình sẽ hướng dẫn các bạn cách tổ chức chương trình với các hàm một cách cụ thể trong các bài học tiếp theo.

**Hẹn gặp lại các bạn trong bài học tiếp theo trong khóa học lập trình C++ hướng thực hành.**

Mọi ý kiến đóng góp hoặc thắc mắc có thể đặt câu hỏi trực tiếp tại diễn đàn.

[www.daynhauhoc.com](www.daynhauhoc.com "DayNhauHoc")
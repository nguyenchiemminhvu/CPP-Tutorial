Xin chào các bạn học viên đang theo dõi khóa học lập trình trực tuyến ngôn ngữ C++.

Trong bài học này, chúng ta cùng nhau tìm hiểu câu lệnh được xây dựng sẵn trong ngôn ngữ lập trình C++ cũng được đưa vào dạng cấu trúc rẽ nhánh có điều kiện. Đó là câu lệnh được tạo nên bởi từ khóa **switch** và **case**, còn gọi là **switch case statement**.

**switch case statement** thường được dùng để thay thế cho **if statement** trong trường hợp số lượng trường hợp cần so sánh quá dài. Mặc dù chúng ta có thể sử dụng kỹ thuật **chaining if statement** để nối các trường hợp cần kiểm tra lại với nhau, nhưng nó khiến chương trình khó đọc. Ví dụ:

	int main()
	{
		cout << "1: BLACK\n2: BLUE\n3: GREEN\n4: YELLOW\n5: WHITE" << endl;
		cout << "Enter your favorite color: ";
		int color;
		cin >> color;

		if (color == 1)
			cout << "You like BLACK color" << endl;
		else if (color == 2)
			cout << "You like BLUE color" << endl;
		else if (color == 3)
			cout << "You like GREEN color" << endl;
		else if (color == 4)
			cout << "You like YELLOW color" << endl;
		else if (color == 5)
			cout << "You like WHITE color" << endl;
		else
			cout << "Unknown" << endl;

		system("pause");
		return 0;
	}

Cũng với ví dụ mẫu này, mình sẽ chuyển nó về cấu trúc switch ... case để các bạn có cái nhìn đầu tiên về **switch case statement**:

	int main()	
	{
		cout << "1: BLACK\n2: BLUE\n3: GREEN\n4: YELLOW\n5: WHITE" << endl;
		cout << "Enter your favorite color: ";
		int color;
		cin >> color;

		switch (color)
		{
			case 1:
				cout << "You like BLACK color" << endl;
				break;
			case 2:
				cout << "You like BLUE color" << endl;
				break;
			case 3:
				cout << "You like GREEN color" << endl;
				break;
			case 4:
				cout << "You like YELLOW color" << endl;
				break;
			case 5:
				cout << "You like WHITE color" << endl;
				break;
			default:
				cout << "Unknown" << endl;
				break;
		}

		system("pause");
		return 0;
	}

Các bạn có thể hiểu cấu trúc rẽ nhánh với **switch case statement** như sau: **switch** nhận vào 1 biến hoặc 1 biểu thức có giá trị kiểu số nguyên, mỗi nhãn **case** sẽ gắn kèm với 1 số nguyên cụ thể và chúng sẽ được lần lượt so sánh bằng (equality) với giá trị của biến (hoặc biểu thức) trong **switch**. Nếu nhãn case nào có giá trị tương xứng với biến hoặc biểu thức trong **switch**, những câu lệnh đứng sau nhãn đó sẽ được thực thi. Nếu không có nhãn nào có giá trị tương xứng, các câu lệnh đứng sau nhãn **default** sẽ được thực thi.

Như vậy, chúng ta có thể đưa ra khuôn dạng của **switch case statement** như sau:

	switch ( <variable> ) 
	{
	case this-value:
		//Code to execute if <variable> == this-value
		break;
	case that-value:
		Code to execute if <variable> == that-value
		break;
	//.......................
	default:
		//Code to execute if <variable> does not equal the value following any of the cases
		break;
	}

- **switch statement** được bắt đầu bởi từ khóa **switch**, theo sau đó là một giá trị số nguyên (thường là một biến đơn), có thể là một biểu thức **(ví dụ 3 * 2 + 5)**. Một hạn chế của switch statement là biểu thức điều kiện chỉ có thể thuộc 1 trong số các kiểu số nguyên **(char, short, int, long, int32_t, enum, ...).**
- **case label** được định nghĩa thông qua từ khóa **case**, theo sau từ khóa case là một hằng số, một giá trị cụ thể. **Lưu ý: Các nhãn case khác nhau phải được theo sau bởi các giá trị khác nhau.** Ví dụ:

		switch (x)
		{
			case 1:
			case 1: //illegal
		}

- **default label** được định nghĩa thông qua từ khóa **default**. Những câu lệnh đứng sau nhãn này chỉ được thực thi nếu không có nhãn **case** nào có giá trị tương ứng với biểu thức điều kiện của **switch**. Lưu ý: cấu trúc switch ... case có thể không cần sử dụng nhãn **default**.

- **break** là một từ khóa trong ngôn ngữ C/C++, khi sử dụng trong **switch case statement** sẽ khiến chương trình thoát ra khỏi khối lệnh của cấu trúc **switch**. Chúng ta cần đặt từ khóa **break** tại cuối các câu lệnh của mỗi nhãn **case** để ngăn cách các **case** riêng biệt. Chúng ta cùng nhìn vào ví dụ sau khi không sử dụng từ khóa **break** thì điều gì sẽ xảy ra:

		switch (2)
		{
		   case 1: // Does not match
		       std::cout << 1 << '\n'; // skipped
		   case 2: // Match!
		       std::cout << 2 << '\n'; // Execution begins here
		   case 3:
		       std::cout << 3 << '\n'; // This is also executed
		   case 4:
		       std::cout << 4 << '\n'; // This is also executed
		   default:
		       std::cout << 5 << '\n'; // This is also executed
		}

	Với ví dụ này, kết quả in ra sẽ là:

		2
		3
		4
		5

	Đây là kết quả ngoài ý muốn, trường hợp này được gọi là **fall-through**. Để khắc phục trường hợp này, chúng ta cần sử dụng thêm từ khóa **break** đặt tại cuối mỗi nhãn **case**:

		switch (2)
		{
		   case 1: // Does not match
		       std::cout << 1 << '\n'; // skipped
			   break;
		   case 2: // Match!
		       std::cout << 2 << '\n'; // Execution begins here
		   	   break;
		   case 3:
		       std::cout << 3 << '\n'; // This is also executed
			   break;
		   case 4:
		       std::cout << 4 << '\n'; // This is also executed
			   break;
		   default:
		       std::cout << 5 << '\n'; // This is also executed
		}

#####Khai báo và khởi tạo biến trong case statement

Chúng ta có thể khai báo biến bên trong mỗi case statement, nhưng chúng ta không thể khởi tạo giá trị cho chúng.

	switch (x)
	{
	    case 1:
	        int y; // declaration is allowed
	        y = 4; // this is an assignment
	        break;
	 
	    case 2:
	        y = 5; // y was declared above, so we can use it here too
	        break;
	 
	    case 3:
	        int z = 4; // illegal, you can't initialize new variables in the case statements
	        break;
	 
	    default:
	        std::cout << "default case" << std::endl;
	        break;
	}

Nhưng chúng ta nên tránh khai báo biến bên trong case statement, nó sẽ khiến chương trình chúng ta khó đọc hơn. Chúng ta có nhiều giải pháp thay thế dễ hiểu hơn, nếu có dịp mình sẽ hướng dẫn cho các bạn.

----------------------

###Tổng kết

Vậy là chúng ta đã làm quen thêm một dạng cấu trúc rẽ nhánh có điều kiện khác. If statement được sử dụng khi muốn kiểm tra tính đúng sai của một hoặc một số mệnh đề. Switch case statement được sử dụng khi muốn kiểm tra một giá trị số nguyên. Đối với trường hợp số lượng biểu thức điều kiện cần so sánh là quá nhiều, chúng ta ưu tiên sử dụng **switch case statement** hơn vì cú pháp rõ ràng hơn.

###Bài tập cơ bản

Viết chương trình nhập vào tháng, in ra tháng đó có bao nhiêu ngày.

Gợi ý: Nhập vào tháng

- Nếu là tháng 1, 3, 5, 7, 8, 10, 12 thì có 30 ngày.
- Nếu là tháng 4, 6, 9, 11 thì có 31 ngày.
- Nếu là tháng 2 thì có 28 ngày (vì chúng ta chưa xét đến năm).

Lợi dụng trường hợp **fall-through** để tổ chức chương trình ngắn gọn hơn.

--------------------------------------

P/s: **Hẹn gặp lại các bạn trong bài học tiếp theo trong khóa học lập trình C++ hướng thực hành.**


Mọi ý kiến đóng góp hoặc thắc mắc có thể đặt câu hỏi trực tiếp tại diễn đàn 

**www.daynhauhoc.com**

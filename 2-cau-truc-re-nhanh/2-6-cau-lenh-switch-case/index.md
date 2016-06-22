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


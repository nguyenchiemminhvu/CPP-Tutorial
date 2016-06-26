Xin chào các bạn học viên đang theo dõi khóa học lập trình trực truyến ngôn ngữ C++.

Trong bài học này, chúng ta sẽ cùng nhau tìm hiểu về cấu trúc điểu khiển **Jump** mà mình đã giới thiệu sơ lược đến các bạn. Sau bài học này, các bạn sẽ biết cách sử dụng từ khóa **break, continue** trong cấu trúc vòng lặp hoặc cấu trúc rẽ nhánh với **switch case statement**.

---------------------------

###Break

Từ khóa **break** được dùng để kết thúc vòng lặp, hoặc cấu trúc **switch**.

#####Break a switch

Khi sử dụng trong switch case statement, từ khóa break thường được đặt tại cuối mỗi khối lệnh mỗi nhãn case.

	switch (character)
	{
		case '+':
			cout << "addition" << endl;
			break;
		case '-':
			cout << "subtraction" << endl;
			break;
		case '*':
			cout << "multiplication" << endl;
			break;
		case '/':
			cout << "division" << endl;
			break;
	}

#####Break a loop

Khi sử dụng trong các dạng vòng lặp khác nhau, từ khóa break đều có cùng mục đích là kết thúc sớm quá trình thực thi của vòng lặp.

	for (int i = 10; i >= 0; i--)
	{
		cout << "Count down: " << i << endl;
		if (i <= 5)
			break;
	}

Đoạn chương trình này thực hiện đếm ngược từ 10 về 0, nhưng khi đếm về 5 thì biểu thức điều kiện của lệnh **if** bên trong vòng lặp **for** đúng, nên chương trình sẽ **break** vòng lặp for.

Từ khóa break thường được dùng để dừng vòng lặp vô hạn:

	bool running = true;
	while (true)
	{
		// do something on running variable

		if(!running)
			break;
	}

###Continue

Từ khóa **continue** thường được sử dụng trong vòng lặp **for** để chuyển đến bước cuối cùng trong 1 lần lặp (**update variable**). Cùng nhìn lại 4 bước thực thi cơ bản của 1 lần lặp của vòng lặp **for**:

**(1) Initialize loop variables**

**(2) Check condition expression**

**(3) Execute the statements**

**(4) Update variables**

Mỗi khi bắt gặp từ khóa continue trong bước (3), chương trình sẽ bỏ qua phần còn lại của bước (3) để chuyển đến thực hiện bước (4), và bắt đầu 1 lần lặp mới từ bước (1).

	for (int i = 0; i <= 20; i++)
	{
		if (i % 5 == 0)
			continue;

		cout << i << " ";
	}

Đoạn chương trình này sẽ in ra tất cả các số nguyên từ 0 đến 20, ngoại trừ các số chia hết cho 5 như 0, 5, 10, 15.

Từ khóa **continue** ít được sử dụng trong vòng lặp **while** hoặc **do-while** bởi một số hạn chế của nó.

	int i = 0; // (1)
	while (i <= 20) // (2)
	{
		if (i % 5 == 0) // (3)
			continue;

		cout << i << " ";
		i++; // (4)
	}

Cũng với ví dụ mẫu trên, nhưng được chuyển sang sử dụng cấu trúc của vòng lặp **while**. Như các bạn thấy, vòng lặp này vẫn thực hiện đủ 4 bước như vòng lặp **for** ở trên. Nhưng kết quả chỉ in ra được: 

	0 1 2 3 4 

Và sau đó, vòng lặp này lặp vô hạn vì biến i sẽ không bao giờ được tăng lên nữa sau khi câu lệnh if được thực thi, vì bước (4) đặt trong vòng lặp **while** được coi như thuộc bước (3) của vòng lặp **for**. Do đó, khi gặp từ khóa **continue**, bước 4 của vòng lặp **while** cũng bị bỏ qua luôn, mà dòng lệnh ```i++``` sẽ không bao giờ được thực thi nữa.

Vì thế mà chúng ta thường xuyên sử dụng vòng lặp **for** hơn, và cũng thường đặt từ khóa **continue** trong vòng lặp **for** hơn.

------------------------

###Tổng kết

**break** và **continue** là 2 từ khóa tiêu biểu cho cấu trúc điều khiển Jump mà ngôn ngữ C++ cung cấp. Các bạn nên tránh lạm dụng 2 từ khóa này vì nó dễ gây sai sót cho chương trình.

--------------------------------------

P/s: **Hẹn gặp lại các bạn trong bài học tiếp theo trong khóa học lập trình C++ hướng thực hành.**


Mọi ý kiến đóng góp hoặc thắc mắc có thể đặt câu hỏi trực tiếp tại diễn đàn 

**www.daynhauhoc.com**

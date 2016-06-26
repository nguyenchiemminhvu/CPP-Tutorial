Chào các bạn học viên đang theo dõi khóa học lập trình trực tuyến ngôn ngữ C++.

Trong các bài học trước, chúng ta đã cùng nhau tìm hiểu các cấu trúc điều khiển chương trình, trong đó có 2 bài học mình đề cập đến cấu trúc vòng lặp **while** và **do-while**. Hai cấu trúc lặp này tuy có khác nhau, nhưng chúng đều được sử dụng khi chưa biết được số lần lặp lại công việc tại thời điểm **run-time**.

Trong bài học này, mình sẽ giới thiệu đến các bạn vòng lặp **for** (**for loops**), cũng là vòng lặp cơ bản cuối cùng trong ngôn ngữ lập trình C++.

#####Một số đặc điểm của vòng lặp for: 

- Vòng lặp for có cú pháp phức tạp hơn, nhưng ngắn gọn hơn các vòng lặp **while** hay **do-while** khi sử dụng.
- Vòng lặp **for** hoàn toàn có thể thay thế vòng lặp **while**.
- Vòng lặp for thường được sử dụng cho các trường hợp biết trước số lần lặp lại khối công việc.

#####Cú pháp vòng lặp for

	for (variable_initialization; condition; variable_update)
	{
		statements;
	}

Mình lấy 1 ví dụ trước khi giải thích các thành phần của vòng lặp **for**:

	for (int count = 1; count <= 10; count++)
	{
		cout << "count = " << count << endl;
	}

Vòng lặp for được định nghĩa bởi từ khóa **for** và được chia làm 3 phần chính, mỗi phần được ngăn cách bởi dấu chấm phẩy:

- **Variable initialization (phần khởi tạo biến)**

	Khác với vòng lặp while và do-while, biến vòng lặp có thể được khai báo và khởi tạo giá trị ngay bên trong phần khởi tạo của vòng lặp **for**. Như ở ví dụ trên, biến count được khai báo và khởi tạo với giá trị 0.

	Phần khởi tạo biến được thực thi đầu tiên và chỉ thực thi 1 lần duy nhất trong vòng lặp **for**.

- **Condition (biểu thức điều kiện)**

	Phần này tương tự như vòng lặp **while**, khối lệnh của vòng lặp for sẽ được thực hiện nếu biểu thức điều kiện cho giá trị đúng. Vòng lặp **for** kiểm tra biểu thức điều kiện trước khi thực hiện khối lệnh.

- **Variable update (cập nhật biến vòng lặp)**

	Phần này sẽ được thực thi cuối mỗi lần lặp, sau khi khối lệnh của vòng lặp **for** được thực thi. Phần này thường chịu trách nhiệm thay đổi giá trị biến vòng lặp được sử dụng trong biểu thức điều kiện (nhằm tránh tình trạng lặp vô hạn). Sau khi thực thi xong phần cập nhật biến vòng lặp, chương trình quay trở lại đánh giá biểu thức điều kiện của vòng lặp **for** và cứ như thế.

Vậy chúng ta rút ra được các bước thực hiện vòng lặp **for** như sau:

```initialize loop variables --> check condition expression --> execute statements --> update loop variables```.

	for (int count = 1; count <= 10; count++)
	{
		cout << count << " ";
	}

Ví dụ trên có thể được chuyển về dưới dạng vòng lặp while như sau:

	int count = 1; //variable initialization
	while (count <= 10) //condition
	{
		cout << count << " "; //statements
		
		count++; //variable update
	}

Nhìn có vẻ dài dòng hơn vòng lặp for, nhưng vẫn có đủ 3 thành phần: **variable initialization, condition và variable update.**

Những lập trình viên mới học đến vòng lặp **for** sẽ cảm thấy khó đọc hơn vòng lặp **while**. Tuy nhiên, khi sử dụng thành thạo, vòng lặp **for** có nhiều tiện ích hơn.

#####Một số ví dụ về vòng lặp for

Dưới đây là một ví dụ sử dụng vòng lặp for để in ra tất cả các số chẵn từ 0 đến 10. Chúng ta đã biết trước rằng biến vòng lặp sẽ đi từ 0 đến 10, nên việc sử dụng vòng lặp for là phù hợp.

	for (int i = 0; i <= 10; i++)
	{
		if (i % 2 == 0)
			cout << i << " ";
	}

Mình vừa sử dụng vòng lặp **for** để cho biến i tăng giá trị từ 1 đến 10, cứ mỗi lần lặp, mình kiểm tra giá trị hiện tại của biến i, nếu giá trị hiện tại của i chẵn, mình thực hiện in biến i ra màn hình.

Vòng lặp này có thể được rút gọn lại như sau:

	for (int i = 0; i <= 10; i += 2)
	{
		cout << i << " ";
	}

Chúng ta biết rằng số chẵn tiếp theo sẽ cách số chẵn trước đó 2 đơn vị, do đó, mình thực hiện cộng thêm 2 đơn vị cho biến i tại phần **variable update**. Nhờ đó, mình không cần thực hiện kiểm tra giá trị của biến i trong vòng lặp nữa.

Bây giờ, thay vì chúng ta thực hiện lặp từ 0 đến 10, chúng ta có thể đi ngược lại từ 10 về 0 như sau:

	for (int i = 10; i >= 0; i -= 2)
	{
		cout << i << " ";
	}

Kết quả in ra sẽ là:

	10 8 6 4 2 0

---------------------

###Tổng kết

###Bài tập cơ bản

--------------------------------------

P/s: **Hẹn gặp lại các bạn trong bài học tiếp theo trong khóa học lập trình C++ hướng thực hành.**


Mọi ý kiến đóng góp hoặc thắc mắc có thể đặt câu hỏi trực tiếp tại diễn đàn 

**www.daynhauhoc.com**
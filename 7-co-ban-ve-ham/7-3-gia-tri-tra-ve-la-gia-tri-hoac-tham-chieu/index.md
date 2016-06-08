Chào các bạn! Chúng ta lại tiếp tục đồng hành trong khóa học lập trình trực tuyến ngôn ngữ C++.

Trong bài học trước, các bạn đã tìm hiểu về cách hoạt động của việc truyền đối số vào hàm. Đến với bài học này, chúng ta sẽ tìm hiểu cách hoạt động của việc trả về giá trị qua 2 phương thức khác nhau:

- Trả về giá trị là giá trị (return by value)
- Trả về giá trị là tham chiếu (return by reference)

Như các bạn đã biết, hàm muốn trả về giá trị thì hàm có phải được khai báo có kiểu dữ liệu khác **void**, và sử dụng từ khóa return để trả về giá trị cho người gọi hàm. Giá trị trả về chính là đầu ra (output) của hàm.

Bên cạnh đó, từ khóa return còn thực hiện việc kết thúc hàm. Lúc đó, mọi biến cục bộ hoạt động bên trong hàm (kể cả các tham số) đều bị hủy. Chúng ta sẽ xem xét những tác động có thể mang lại trên mỗi loại kiểu trả về.

##
###Trả về giá trị là giá trị (return by value)

Định nghĩa hàm có giá trị trả về là giá trị cũng là cách mà các bạn thường sử dụng, nó đơn giản và an toàn khi sử dụng. Giá trị trả về có thể là 1 giá trị cụ thể, 1 biểu thức, 1 biến.

	string returnString(int num_of_character)
	{
		string str(num_of_character, ' ');
		return str;
	}

Mình lấy ví dụ hàm returnString ở trên, tham số là 1 số nguyên đại diện cho số kí tự khoảng trắng mà string trong hàm sẽ tạo ra.

Vì kiểu trả về của hàm này là giá trị, một bản sao của biến str (có kiểu dữ liệu string) sẽ được tạo ra khi gặp dòng lệnh ```return str;``` và bản sao này sẽ được trả về cho lời gọi hàm, không có vấn đề gì xảy ra khi biến **str** trong hàm **returnString** ra khỏi phạm vi tại dấu ngoặc nhọn kết thúc hàm.

	string myStr = returnString(5); //function call

Lời gọi hàm và gán giá trị trả về cho biến như trên cũng tương đương với lệnh:

	string myStr = "     "; // 5 blank space characters.

Bởi vì giá trị được trả về khi gọi hàm **returnString** với đối số là 5 cũng là một biến kiểu **string** được khởi tạo với 5 kí tự trắng.

Thêm một ví dụ khác:

	int doubleValue(int value)
	{
		int newValue= value * 2;
		return newValue;
	}

	// ..............
	// function call
	int result = doubleValue(10);

Giá trị trả về của lời gọi hàm **doubleValue(10)** là bản sao giá trị của biến newValue được khai báo khi gọi hàm. Sau khi dùng từ khóa **return** để trả về giá trị của biến **newValue**, chương trình đi ra khỏi phạm vi của hàm và biến **newValue** cũng bị hủy luôn. Thứ còn lại chỉ là bản sao giá trị của nó được gán lại cho biến result.

###Trả về giá trị là tham chiếu (return by reference)

Cũng tương tự như việc truyền đối số cho hàm là tham chiếu, giá trị trả về khi dùng phương thức này phải là một biến (không thể trả về 1 giá trị cụ thể hay 1 biểu thức).

Khi 1 giá trị trả về là tham chiếu, 1 tham chiếu sẽ được tạo ra và trả về cho lời gọi hàm. Chúng ta có thể sử dụng tham chiếu được trả về để tiếp tục thay đổi dữ liệu bên trong vùng nhớ được tham chiếu đến.

	int & returnReference()
	{
		int var = 0;
		return var;
	}

	// ................
	// function call
	int & myRef = returnReference();

Khi gọi hàm **returnReference**, biến var có kiểu **int** được tạo ra bên trong hàm. Nhưng hàm này trả về 1 tham chiếu đến vùng nhớ của biến var khi mà biến var đã bị hủy ngay sau khi **return**, điều này có nghĩa myRef đã tham chiếu đến 1 vùng nhớ rác.

Trong đa số trường hợp, biến myRef tham chiếu đến tham chiếu được trả về ngay lập tức sau lời gọi hàm, nên mặc dù biến var đã bị hủy, nhưng chưa có chương trình nà khác sử dụng vùng nhớ do biến var giải phóng, nên biến myRef vẫn tham chiếu vào đó được. Nhưng một số compiler sẽ đưa ra cảnh báo cho hành động này.

Thay vào đó, chúng ta nên trả về một tham chiếu thực sự khi sử dụng phương thức trả về này.

	int & doubleValue(int &ref)
	{
		ref *= 2;
		return ref;
	}

Hàm doubleValue trên nhận vào tham số một tham chiếu kiểu int, giá trị bên trong vùng nhớ được tham chiếu đến sẽ tăng gấp 2 lần sau khi gọi hàm. Một điểm đáng chú ý là chúng ta trả về cho lời gọi hàm một tham chiếu thực sự, vì thế, chúng ta có thể tiếp tục sử dụng tham chiếu trả về để thay đổi giá trị.

	int arr[] = { 1, 2, 3, 4, 5 };
	arr[2] = doubleValue(arr[2]);

	for (int i = 0; i < 5; i++)
		cout << arr[i] << " ";
	cout << endl;

Đoạn chương trình này truyền vào hàm một tham chiếu đến phần tử thứ 2 trong mảng **arr**, và gán lại giá trị trả về cho phần tử thứ 2, vậy thì mảng **arr** cuối cùng của chúng ta sẽ là: **1 2 6 4 5**

Bây giờ chúng ta thử thay đổi một chút như sau:

	int arr[] = { 1, 2, 3, 4, 5 };
	doubleValue(arr[2]) = 100;
	
	for (int i = 0; i < 5; i++)
		cout << arr[i] << " ";
	cout << endl;

Vì giá trị trả về của hàm doubleValue là 1 tham chiếu, nên mình đã sử dụng tham chiếu đó để thay đổi giá trị thành 100. Lúc này, mảng kết quả của chúng ta sẽ là: **1 2 100 4 5**

##
###Tổng kết

Thông thường, chúng ta vẫn ưu tiên sử dụng kiểu trả về là giá trị bởi vì nó an toàn và dễ hiểu hơn, nhưng nó gặp phải một số hạn chế khi làm việc với các kiểu dữ liệu lớn, dữ liệu cấp phát động... Trong trường hợp này, chúng ta sẽ sử dụng phương thức trả về giá trị là tham chiếu.

**Hẹn gặp lại các bạn trong bài học tiếp theo trong khóa học lập trình C++ hướng thực hành.**

Mọi ý kiến đóng góp hoặc thắc mắc có thể đặt câu hỏi trực tiếp tại diễn đàn.

[www.daynhauhoc.com](www.daynhauhoc.com "DayNhauHoc")
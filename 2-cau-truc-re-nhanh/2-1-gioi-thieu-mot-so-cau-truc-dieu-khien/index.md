Chào các bạn! Rất vui khi được gặp lại các bạn trong khóa học lập trình trực tuyến ngôn ngữ C++.

Như chúng ta đã tìm hiểu, khi chạy một chương trình C++, CPU bắt đầu thực thi các câu lệnh tại điểm trên cùng của hàm **main**, thực hiện lần lượt các câu lệnh từ trên xuống dưới, và kết thúc tại điểm dưới cùng của hàm **main**. Chuỗi các câu lệnh được CPU thực thi gọi là **program's path**. Phần lớn các chương trình mà bạn từng thấy được thực thi theo dạng **straight-line** (tuần tự từ trên xuống dưới). Tuy nhiên, trong một số trường hợp, đây không phải là điều chúng ta muốn.

Ví dụ nếu chúng ta yêu cầu người dùng đưa ra một lựa chọn, và người dùng nhập vào lựa chọn không phù hợp, chúng ta nên yêu cầu người dùng đưa ra một lựa chọn khác. Với cấu trúc chương trình dạng **straight-line**, điều này là bất khả thi.

Một trường hợp khác, chúng ta muốn chương trình thực hiện lặp đi lặp lại một công việc nào đó với số lần thực hiện chưa biết trước. Ví dụ chúng ta muốn in ra điểm số của một trò chơi trên màn hình cho đến khi trò chơi kết thúc, chúng ta không thể biết chính xác thời điểm kết thúc trò chơi là khi nào.

Do đó, ngôn ngữ C++ cung cấp các cấu trúc điều khiển **(control flow statements)** nó cho phép lập trình viên thay đổi hướng đi của chương trình. Có một số dạng cấu trúc điều khiển khác nhau và mình sẽ giới thiệu sơ lược để các bạn có sự hình dung ban đầu.

###Halt

Cấu trúc điều khiển dừng (**halt**) là một cấu trúc thường gặp, nó yêu cầu chương trình ngừng làm việc ngay lập tức. Trong C++, cấu trúc **Halt** có thể được thực hiện thông qua hàm **exit()** trong thư viện **cstdlib**. Hàm exit nhận vào một giá trị số nguyên và nó sẽ được trả về cho hệ điều hành như một mã kết thúc chương trình, tương tự như giá trị trả về của hàm **main**.

Đây là đoạn chương trình mẫu cho việc thực hiện cấu trúc điều khiển **Halt**:

	#include <iostream>
	#include <cstdlib>
	using namespace std;

	int main()
	{
		cout << "This line is printed out." << endl;
		exit(-1); //Terminate and return -1 to operating system. 
		cout << "This line will never be printed out." << endl;

		system("pause");
		return 0;
	}

###Jumps

Cấu trúc điều khiển tiếp theo mình muốn đề cập đến là **Jump**. Cấu trúc Jump không điều kiện khiến CPU nhảy đến thực thi một số các câu lệnh khác. **goto, break, continue** là các từ khóa được sử dụng trong cấu trúc Jump, chúng có kiểu Jump khác nhau, chúng ta sẽ được tìm hiểu chi tiết trong các bài học sắp tới.

###Cấu trúc rẽ nhánh có điều kiện

Cấu trúc rẽ nhánh có điều kiện khiến chương trình thay đổi hướng thực thi dựa trên giá trị của biểu thức điều kiện (hoặc các mệnh đề). Tiêu biểu cho cấu trúc rẽ nhánh là **câu lệnh if**. 

	int main()
	{
		//do A

		if(expression)	
			//do B;
		else
			//do C;

		//do D

		return 0;
	}

Chương trình này có 2 hướng có thể đi. Nếu biểu thức expression cho kết quả đúng (**true**), chương trình sẽ thực thi A rồi đến B và đến D. Nếu biểu thức expression cho kết quả sai (**false**), chương trình sẽ đi theo hướng A đến C rồi đến D. Cấu trúc này không còn dạng **straight-line** nữa mà là dạng cấu trúc rẽ nhánh (**conditional branches**).

###Cấu trúc vòng lặp (Loops)

Một cấu trúc vòng lặp khiến chương trình thực hiện lặp đi lặp lại một chuỗi các câu lệnh cho đến khi không còn thõa mãn một điều kiện nào đó.

	int main()
	{
		//do A
		//do B 0 or more times
		//do C
	}

Chương trình này có thể thực hiện theo hướng ABC, ABBC, ABBBC, ABBB...BBBC, hoặc cũng có thể là AC. Như các bạn thấy, một lần nữa đây không phải là **straight-line program**, hướng thực thi các câu lệnh phụ thuộc vào số lần các câu lệnh trong vòng lặp được thực thi.

**while, do...while, for** là 3 cấu trúc vòng lặp mà ngôn ngữ C/C++ cung cấp. Chuẩn C++11 còn cung cấp cho chúng ta thêm cấu trúc vòng lặp tên là **for each**.

###Exceptions

Cuối cùng, **exceptions** là một cơ chế xử lý lỗi xảy ra bên trong hàm. Nếu một lỗi xảy ra bên trong hàm mà hàm không thể xử lý, hàm đó ném ra một ngoại lệ (exception). Điều này khiến chương trình nhảy đến khối lệnh chuyên dùng để xử lý ngoại lệ có kiểu tương ứng với ngoại lệ được hàm ném ra.

Xử lý ngoại lệ là một đặc trưng khá mới được hổ trợ trong ngôn ngữ C++.

##
###Kết luận

Mình vừa giới thiệu đến các bạn một số cấu trúc điều khiển thông dụng trong ngôn ngữ C++. Trong chương này, chúng ta sẽ tập trung nói về cấu trúc rẽ nhánh. Các phần còn lại sẽ được bàn đến trong các chương tiếp theo.

--------------------------------------

P/s: **Hẹn gặp lại các bạn trong bài học tiếp theo trong khóa học lập trình C++ hướng thực hành.**


Mọi ý kiến đóng góp hoặc thắc mắc có thể đặt câu hỏi trực tiếp tại diễn đàn 

**www.daynhauhoc.com**

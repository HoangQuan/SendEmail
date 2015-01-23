# SendEmail

Giống như SMSAndroid cũng hỗ trợ email.Ứng dụng Gmail -Email trong Android cho phép bạn cấu hình tài khoản email sử dụng POP3 và IMAP. trước tiên hãy làm một ví dụ:

Views:

<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    tools:context="com.example.sendemail.MainActivity" >

    <Button
        android:id="@+id/btnSend"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:text="Send email" />

</RelativeLayout>

Logic:
// định nghĩa một phương thức để send email
private void sendEmail(String[] emailAddresses,
			String[] carbonCopies, String subject, String message ){
		Intent emailIntent = new Intent(Intent.ACTION_SEND);
		emailIntent.setData(Uri.parse("mailto:"));
		String[] to = emailAddresses;
		String[] cc = carbonCopies;
		emailIntent.putExtra(Intent.EXTRA_EMAIL, to);
		emailIntent.putExtra(Intent.EXTRA_CC, cc);
		emailIntent.putExtra(Intent.EXTRA_SUBJECT, subject);
		emailIntent.putExtra(Intent.EXTRA_TEXT, message);
		emailIntent.setType("message/rfc822");
		startActivity(Intent.createChooser(emailIntent, "Email"));
	}

// gọi hàm send email

btnSend = (Button) findViewById(R.id.btnSend);
		btnSend.setOnClickListener(new View.OnClickListener() {
			
			public void onClick(View arg0) {
			  String[] to = {"hoang.van.quan@framgia.com"};
			  String[] cc = {"hoang.van.quan@framgia.com"};
			  sendEmail(to, cc, "Hello", "Hello my friend!");
				
			}
		});

Kết qủa :



Nhấn vào nút send email:


Giải thích ví dụ:


Trong ví dụ trên tôi đã sử dụng một ứng dụng được built-in trong Android để send email. bạn chỉ cần gọi intent của nó lên bằng phương thức setData() và set parameters cho nó bằng phương thức putExtra() và setType cho nó là Xong. 

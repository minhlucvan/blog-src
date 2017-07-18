---
title: Một button trị giá 300 triệu đô - Cái nhìn khác về UI và chức năng
date: 2016-06-13 04:26:31
thumbnail: /image/posts/Mot-button-tri-gia-300-trieu-do-Cai-nhin-khac-ve-UI-va-chuc-nang/1.jpg 
categories: ["chuyện nghề"]
tags: ["UI/UX", "E-comence", "web"]
---
![ ](/image/posts/Mot-button-tri-gia-300-trieu-do-Cai-nhin-khac-ve-UI-va-chuc-nang/1.jpg)

### ngày xửa ngày xưa có một trang web bán hàng... 
 
Câu chuyện của chúng ta bắt đầu ở chức năng “Thanh toán”, khi người dùng đã cho hết hàng vào giỏ, một form nho nhỏ xinh xinh hiện ra, với 2 trường username và password, 2 nút Login và Register, một link Quên mật khẩu. Thế nhưng, chính cái form be bé xinh xinh này đã gây thiệt hại đến 300.000.000$/năm cho trang web bán hàng.
<!--more-->

![ ](2.jpg)

Vấn đề ở chỗ, người dùng phải đăng nhập trước khi muốn thanh toán. Đội lập trình nghĩ rằng “Chỉ cần đăng ký tài khoản, thông tin người dùng có thể được lưu lại, ở những lần sau họ không cần nhập địa chỉ, thông tin thanh toán nữa. Người dùng tiết kiệm được thời gian, web cũng khuyến khích được người dùng quay lại mua hàng, hai bên cùng có lợi còn gì?”.


### Lũ lập trình viên luôn nghĩ rằng mình hiểu người dùng

Đội ngũ UI/UX đã làm một cuộc thử nghiệm, đưa tiền cho người dùng để họ thực hiện quá trình mua hàng – thanh toán. Đối với những khách hàng mới của trang web, họ phát hiện ra một điều: **người dùng rất ghét việc đăng ký**, với suy nghĩ “Mình muốn mua hàng, chứ không phải muốn đăng ký đăng kiếc gì cả”. Chưa kể, người dùng còn sợ bị mất thông tin cá nhân, bị gửi mail spam hộp thư.

Với những người dùng quay lại lần 2,3 – đối tượng mà developer nhắm tới, tình cảnh cũng chẳng khá hơn. Họ không nhớ được username/mật khẩu của mình. Mặc dù chức năng “Quên password” vẫn hoạt động, đến tận 160.000 người dùng chức năng này mỗi ngày, **75% trong số đó không tiếp tục quá trình thanh toán sau khi đã request mật khẩu**.

![ ](3.jpg)

Chiếc form nho nhỏ xinh xinh kia, hóa ra lại là thứ ngăn cản người dùng mua hàng – rất nhiều người dùng. Thế mới biết, developer lúc nào cũng nghĩ mình hiểu được người dùng, nhưng thật ra không phải vậy.

### Chiếc button trị giá 300 triệu đô la

Đội ngũ designer đã giải quyết vấn đề này một cách vô cùng đơn giản. Họ bỏ đi nút Register, thay vào đó bằng nút Continue và dòng chữ “Bạn không cần đăng ký, hãy bấm nút Continue để thanh toán. Để thanh toán nhanh hơn ở những lần sau, bạn có thể đăng ký một tài khoản vào lúc thanh toán”.

Kết quả: Lượng thanh toán của khách hàng tăng lên đến **45%**. Sau tháng đầu tiên, doanh số tăng **15.000.000$**. Sau năm đầu tiên, thu nhập của web tăng đến tận 300 triệu đô la. Tất cả những việc mà họ đã làm là gì? Chỉ là thay **một button** mà thôi.

![ ](4.jpg)

### Một cái nhìn khác về UI/UX và chức năng

Một số bạn còn nhầm lẫn về hai khái niệm này, nên mình xin đưa ra một khái niệm tổng quát:

- **UI (User Interface) – Giao diện người dùng**: Đây là những gì người dùng nhìn thấy, tương tác được (Form, button, website).
- **UX (User Experience) – Trải nghiệm người dùng**: Đây là những gì người dùng trải nghiệm, bao gồm cảm xúc, suy nghĩ, quá trình. UI chỉ là một phần của UX. VD như khi bạn mua hàng trên tiki. Các trang web thanh toán, web mua hàng chính là UI. Quá trình mua hàng/nhận hàng, sự thoải mái khi thanh toán, sự hỗ trợ của Tiki với khách hàng chính là UX.

Trong câu chuyện trên, bằng cách thay đổi UI (Thay một button), họ đã trực tiếp cải thiện UX (Thay đổi trải nghiệm mua hàng, mua nhanh hơn, không cần đăng ký), từ đó làm tăng doanh số bán hàng.

![ ](5.jpg)

Hẳn nhiều bạn lập trình viên vẫn còn suy nghĩ: Chức năng mới là quan trọng, còn mấy thứ ruồiiii bu như giao diện thì làm thế nào cũng được (Một phần chắc là do lúc mới học lập trình toàn phải viết chương trình Console, trước đây mình cũng vậy). Đây là một suy nghĩ hoàn toàn sai lầm.

Nếu chỉ viết vài tool đơn giản cho chính mình hoặc bạn bè xài thì đúng là giao diện không quan trọng. Nhưng nếu đã tạo ra sản phẩm, hướng tới người dùng, thì UI/UX là những thứ quan trọng nhất nhì, có khi hơn cả chức năng.

Nếu không tin, bạn hãy thử đọc **The Inmates Are Running the Asylum** – cuốn “thánh kinh” của dân thiết kế UI/UX, để hiểu rõ hơn về tầm quan trọng của hai thứ này. Hãy nhớ một điều mình muốn nói qua câu chuyện này: **Đôi khi chỉ một button nho nhỏ lại có giá trị đến 300 triệu đô đấy**.

<h3 style="color:  #e74c3c"><i class="fa fa-heart"></i>&nbsp;cảm nhận</h3>

bất kể một sản phẩm công nghệ nào cũng đều hướng đến mục đích phục vụ người dùng, đứng trên góc độ người làm kỹ thuật nhiều lúc developer thường bị bệnh "**trung tâm vũ trụ**" mặc định coi khách hàng ở vị trí của mình có sở thích, hiểu công nghệ như mình hặc đôi khi cố tình chọn những thứ lạ hoắc để thể hiện bản thân, điều đó thực sự tồi tệ nếu cứ cố gữi cái suy nghĩ chủ quan răng "**khách hàng như giông mình**" và "**ta đây hiêu khách hàng**" như vạy sẽ chỉ dẫn đến một kết cục là sản phẩm build ra sẻ chỉ có dev - team sử dụng được thôi :D

mấy năng trở lại đây cán cân của của cả nền công nghệp phần mềm dang nghiên dần về phía đầu cuối - phía người dùng. một sản phẩm có chức năng tốt nhưng trải nghiệm tồi  chưa chắc được người dùng lựa chọn thay vào đó họ sẵn sàng lựa chọn sản phẩm khác ít chức năng hơn nhưng tạo được một trải nghiệm tốt hơn. **UX - WIN** :cherry_blossom: :sunflower: :bouquet:

UX cũng là một môn khoa học về con người, nên rõ ràng mấy bác dev không thể chỉ ngồi code rồi vênh mặt lên rằng ta đây hiểu người dùng, rằng người dùng thích mầu này không thích làm thế nọ tất cả đểu cần đưa lên bàn cần. thể mới sinh ra cái gọi là khảo sát người dùng. chả nới đâu xa chính những ông lớn như google, facebook cũng hằng ngày hàng giờ  thực hiện những cuộc khảo sát ngầm như vậy. để chọn được màu link như hiện tại google đã thử nghiệp hằng trăm sắc thái màu khác nhau và chọn ra màu link có tỉ lệ người click cao nhất :mask:. 
 
 
bài viết từ [techtalk.vn](http://techtalk.vn) 
link bài viết gốc : http://techtalk.vn/mot-button-tri-gia-300-trieu-do-cai-nhin-khac-ve-ui-va-chuc-nang.html
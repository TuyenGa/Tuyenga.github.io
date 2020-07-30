---
layout: post
title: "Internet hoạt động như thế nào?"
author: tuyen
comments: false
categories: [internet, how-to, backend, roadmap]
image: assets/images/roadmap/internet-feature.jpg
---

## Giao thức là gì? (Protocol)

Giao thức là một bộ quy tắc chỉ định cách mà các máy tính nên giao tiếp với nhau qua mạng Internet. Ví dụ: Giao thức điều khiển vận chuyển có một quy tắc là nếu một máy tính gửi dữ liệu đến một máy tính khác, máy đích sẽ cho máy tính nguồn biết nếu có dữ liệu nào bị thiếu để máy tính nguồn có thể gửi lại. Hoặc Giao thức Internet chỉ định máy tính định tuyến thông tin đến các máy tính khác bằng cách đính kèm địa chỉ vào dữ liệu mà nó gửi.

Cụ thể hơn, khi sử dụng trình duyệt Web để kết nối tới một Website, trình duyệt dựa vào giao thức HTTP hay HTTPS để liên lạc với máy chủ của Website đó. QUá trình liên lạc thông tin này lại dựa vào các giao thức khác nữa.

<p style="display: flex;"><img style="margin: 5px auto;" src="{{ site.baseurl }}/assets/images/roadmap/https-work.png" alt="Ví dụ hoạt động của https" /></p>

Theo như ảnh trên giao thức HTTPS nhờ vào giao thức TLS để thực hiện việc mã hoá thông tin chuyển tải, để các thông tin này giữ được độ bí mật và không bị thay đổi khi chuyển tải qua mạng. Bản thân giao thức TLS lại dựa vào giao thức TCP để đảm bảo thông tin không bị mất mát hay biến thái trong quá trình chuyển tải. Cuối cùng, giao thức TCP dựa vào giao thức IP để thực hiện việc phân chia dữ liệu tới đúng địa chỉ cần thiết. Trong khi sử dụng giao thức mã hoá HTTPS, máy tính của bạn vẫn dùng giao thức không mã hoá DNS để nhận địa chỉ IP của tên miền mình muốn. Giao thức DNS sử dụng giao thức UDP để đánh dấu yêu cầu kết nối qua một tuyến truyền cần thiết tới một máy chủ DNS, và UDP thì lại dùng giao thức IP cho việc truyền dữ liệu cuối cùng tới nơi cần tới. Do các mối tương quan theo tầng giữa các giao thức. Ngươi ta thường nói đến các giao thức kết nối mạng như một hệ thống các lớp. Mỗi giao thức tại một tầng, hay lớp, có trách nhiệm thực thi một quy trình hay yếu tố đó trong toàn bộ các chức năng chuyển tải thông tin.

## Port

Các máy tính nối mạng với nhau bằng giao thức TCP và kết nối được đảm bảo trong khoảng thời gian nhất định nhằm cho phép các giao thức ở tầng cao hơn thực hiện chức năng của mình. TCP áp dụng hệ thống các cổng (PORT) được đánh số để quản lý các kết nối đồng thời phân biệt các kết nối với nhau. Việc sử dụng các cổng có đánh số như vậy cho phép máy tính có thể quyết định phần mềm nào được vận hành để xử lý đối với một yêu cầu cụ thể hay một dạng dữ liệu nhất định. IANAA - Internet Asigned Name Authority (Giới chức Đặt tên Cổng Internet) có chức năng đặt tên và cung cấp cổng cho một số cổng giao thức tầng cao được sử dụng bởi các dịch vụ ứng dụng. Một số các ví dụ cổng với số được gán như sau:

20 và 21 - FTP (chuyển tập tin)

22 - SSH (shell an toàn truy cập từ xa)

23 - Telnet (truy cập từ xa không bảo mật)

25 - SMTP (gửi thư điện tử)

53 - DNS (gán tên miền của một máy với một địa chỉ IP)

80 - HTTP (lướt mạng thông thường, đôi khi sử dụng cho một bộ đếm (Proxy))

110 - POP3 (nhận thư điện tử)

143 - IMAP (gửi/nhận thư điện tử)

443 - HTTPS (kết nối Web có bảo mật)

993 - IMAP có bảo mật

995 - POP3 có bảo mật

1080 - Bộ đệm SOCKS

1194 - Mạng VPN (Virtual Private Network - mạng riêng ảo)

3128 - Bộ đệm Squid

8080 - Bộ đệm giao thức HTTP tiêu chuẩn

Sử dụng các con số cụ thể nói trên của các cổng thông thường không phải là yêu cầu kỹ thuật bắt buộc của các giao thức. Thực tế, bất cứ một hình  thái dữ liệu nào cũng có thể được gửi qua mọi loại cổng (và sử dụng các cổng phi tiêu chuẩn lại có thể trở thành một kỹ thuật tránh vượt kiểm duyệt hữu dụng). Tuy thế, các con số được gán cho các loại cổng ở trên là các sắp đặt mặc định để thuận tiện cho việc sử dụng. Ví dụ, trình duyệt Web của bạn biết rằng nếu kết nối tới một trang mạng nhất định mà không đặt các cổng cụ thể thì sẽ tự động chạy qua cổng số 80. Các phần mềm khác cũng có các cách bố trí số cổng mặc định tương tự, do đó bạn có thể sử dụng dịch vụ Internet một cách bình thường mà không cần biết hay nhớ các số cổng cụ thể liên hệ tới các dịch vụ mà mình dùng.

## Gói tin là gì?

Dữ liệu được gửi qua Internet được gọi là một thông điệp. Trước khi một thông điệp được gửi, nó được chia thành nhiều phần được gọi là các gói(package). Các gói này được gửi độc lập với nhau. Kích thước gói tối đa điển hình là từ 1000 đến 3000 ký tự. Giao thức Internet chỉ định cách các thông điệp nên được đóng gói.

## Bộ định tuyến là gì?

Router hay còn gọi là các thiết bị định tuyến hoặc bộ định tuyến, là thiết bị mạng máy tính dùng để chuyển các gói dữ liệu qua một liên mạng và đến các thiết bị đầu cuối, thông qua một tiến trình gọi là định tuyến.

## Những bộ định tuyến Internet này đến từ đâu? Ai sở hữu chúng?

Các bộ định tuyến này có nguồn gốc từ những năm 1960 với ARPANET, một dự án của quân đội với mục tiêu là một mạng máy tính được phân cấp để chính phủ có thể truy cập và phân phối thông tin trong trường hợp thảm khốc. Kể từ đó, một số tập đoàn cung cấp dịch vụ Internet (ISP) đã thêm bộ định tuyến vào các bộ định tuyến Internet này, mà là nhiều chủ sở hữu: Các cơ quan chính phủ và trường đại học liên kết với ARPANET trong những ngày đầu và các tập đoàn ISP như AT&T và Verizon sau này. Hỏi ai sở hữu Internet cũng giống như hỏi ai sở hữu tất cả các đường dây điện thoại . Không một thực thể nào sở hữu tất cả, nhiều thực thể khác nhau sở hữu các bộ phận của chúng.

Giống như nhiều dự án kỹ thuật phức tạp khác, Internet được chia thành các thành phần độc lập nhỏ hơn, hoạt động cùng nhau thông qua các giao diện được xác định rõ. Các thành phần này được gọi là Internet Layerr và chúng bao gồm lớp liên kết (Link layer), Lớp Internet (Internet Layer), Lớp vận chuyển (Transport layer) và lớp ứng dụng (Application layer). Chúng được gọi là các lớp vì chúng được xây dựng chồng lên nhau, mỗi lớp sử dụng các khả năng của các lớp bên dưới nó mà không phải lo lắng các chi tiết thực hiện của nó.

<p style="display: flex;"><img style="margin: 5px auto;" src="{{ site.baseurl }}/assets/images/roadmap/Internet-layer.jpeg" alt="Các lớp của Internet" /></p>

Các ứng dụng Internet hoạt động ở tầng ứng dụng và không cần lo lắng về các chi tiết trong các lớp bên dưới. Ví dụ, một ứng dụng kết nối với một ứng dụng khác trên mạng thông qua TCP bằng cách sử dụng cấu trúc được gọi là socket, nó trừu tượng hoá các chi tiết nghiệt ngã của các gói định tuyến và lắp ráp lại các gói thành tin nhắn.

## Mỗi lớp Internet này làm gì?

Ở cấp độ thấp nhất là lớp liên kết (Link layer), là lớp vật lý của Internet. Lớp liên kết liên quan đến việc truyền các bit dữ liệu thông qua một số phương tiện vật lý như cáp quang hoặc tín hiệu vô tuyến wifi.

Trên lớp liên kết là lớp Internet (Internet layer). Lớp Internet liên quan đến việc định tuyến các gói đến đích của chúng. Giao thức Internet (IP) được đề cập trước đó tồn tại trong lớp này. IP tự động điều chỉnh và định tuyến lại các gói dựa trên tải mạng hoặc mất điện. Lưu ý rằng  nó không đảm bảo các gói luôn đi đến đích, nó chỉ cố gắng tốt nhất có thể.

Trên lớp Internet là lớp vận chuyển (Transport). Lớp này để bù đắp cho thực tế là dữ liệu có thể bị mất trong các lớp Internet và liên kết bên dưới. Giao thức điều khiển vận chuyển (TCP) và nó hoạt động chủ yế để tập hợp lại các gói vào các thông điệp ban đầu của chúng và cũng truyền lại các gói bị mất.

Lớp ứng dụng (Application layer) nằm  trên cùng. Lớp này sử dụng tất cả các lớp bên dưới nó để xử lý các chi tiết phức tạp trong việc di chuyển các gói trên Internet. Nó cho phép các ứng dụng dễ dàng thực hiện kết nối với các ứng dụng khác trên Internet đơn giản như ổ cắm. Giao thức HTTP chỉ định cách trình duyệt web và máy chủ web sẽ tương tác với nhau trong lớp ứng dụng. Giao thức IMAP chỉ định cách ứng dụng email khách truy xuất email trong lớp ứng dụng. Giao thức FTP chỉ định giao thức truyền tệp giữa các máy khách tải xuống tệp và máy chủ lưu trữ tệp nằm trong lớp ứng dụng.

## Làm thế nào để dữ liệu như thẻ tín dụng được truyền an toàn qua Internet?

Trong những ngày đầu của Internet, nó đủ để đảm bảo rằng các bộ định tuyến và liên kết mạng nằm ở những vị trí an toàn về mặt vật lý. Nhưng khi Internet tăng kích thước, nhiều  bộ định tuyến hơn có nghĩa là nhiều điểm dễ bị tổn thương hơn. Hơn nữa, với sự ra đời của các công nghệ không dây như wifi, tin tặc có thể chặn các gói tin trong không khí, chỉ đảm bảo phần cứng mạng là an toàn về mặt vật lý. Giải pháp cho vấn đề này là mã hoá và xác thực thông qua SSL/TLS.

## SSL/TLS là gì?

SSL là viết tắt của Secured Sockets Layer(Lớp cổng bảo mật). TLS là viết tắt của Transport Layer Security(Bảo mật tầng vận tải). SSL được Netscape phát triển lần đầu tiên vào năm 1994 nhưng phiên bản an toàn hơn về sau đã được phát minh và đổi tên thành TLS. SSL/TLS là lớp tuỳ chọn nằm giữa lớp vận chuyển và lớp ứng dụng. Nó cho phép truyền thông tin nhạy cảm thông qua mã hoá và xác thực. Mã hoá có nghĩa là máy khách có thể yêu cầu kết nối TCP đến máy chủ được  mã hoá. Điều này có nghĩa tất cả các tin nhắn được gửi giữa máy khách và máy chủ sẽ được mã hoá trước khi chia nó thành các gói. Nếu tin tặc chặn các gói này, chúng sẽ không thể tái tạo lại tin nhắn ban đầu. Xác thực có nghĩa khách hàng có thể tin tưởng rằng máy chủ là người mà nó tuyên bố. Điều này bảo vệ chống lại các cuộc tấn công trung gian, đó là khi một bên độc hại chặn kết noois giữa máy khách và máy chủ để nghe lén hoặc giả mạo thông tin liên lạc của họ. SSL hoạt động bất cứ khi nào một bên truy cập các trang web hỗ trợ nó. Khi trình duyệt yêu cầu một trang web sử dụng HTTPS thay vì HTTP, nó sẽ kết nối máy chủ web hỗ trợ SSL, kết nối được mã hoá an toàn sẽ được tạo và sẽ có biểu tượng khoá bên cạnh thanh địa chỉ trên trình duyệt.

# Tóm lược về Internet.

- Internet bắt đầu bởi ARPANET vào những năm 1960 với mục tiêu là một mạng máy tính phi tập trung.
- Về mặt vật lý, Internet là một tập hợp các máy tính di chuyển các bit với nhau thông qua dây dẫn, dây cáp và tín hiệu vô tuyến.
- Giống như nhiều dự án kỹ thuật phức tạp, Internet được chia thành nhiều lớp khác nhau, mỗi lớp chỉ liên quan đến việc giải quyết một vấn đề nhỏ hơn. Các lớp này kết nối với nhau trong các Interface được xác định rõ ràng.
- Có nhiều giao thức xác định cách thức Internet và các ứng dụng của nó hoạt động ở các lớp khác nhau: HTTP, IMAP, SSH, TCP, UDP, IP, v.v.. </br> Theo nghĩa này, Internet là tập hợp nhiều quy tắc cho cách thức máy tính và các chương trình nên hoạt động vì nó là một mạng máy tính vật lý.
- Với sự phát triển của Internet, sự ra đời của WIFI và nhu cầu thương mại điện tử, SSL/TLS đã được phát triển để giải quyết mối quan tâm về bảo mật.
# Nhóm 9 _ Môn điện toán đám mây chiều thứ 7
## Thành viên nhóm:
1. Tôn Thất Gia Bảo - 19133009
2. Võ Đình Vĩnh Chương - 19133012
3. Nguyễn Đức Toàn - 1913358
## Hướng dẫn sử dụng
### Chuẩn bị dịch vụ điện toán đám mây
* Ở đây sử dụng dịch vụ điện toán đám mây của AWS
1. Thực hiện chọn Amazon Machine Image (AMI)

![image](https://user-images.githubusercontent.com/69313033/147343129-23a07ca5-43af-49aa-8fc5-fb9d39e24442.png)
2. Chọn cấu hình cho máy ảo 

![image](https://user-images.githubusercontent.com/69313033/147343518-18d78fe6-9bd9-4cc7-8966-fc7a2888a591.png)
3. Cấu hình chi tiết máy ảo

![image](https://user-images.githubusercontent.com/69313033/147343655-c8978211-c285-4948-86c4-2bf7b1747fcf.png)
4. Cấu hình bộ nhớ máy ảo

![image](https://user-images.githubusercontent.com/69313033/147343771-7ac49331-d401-4a18-ae40-22356bf1689a.png)
5. Tạo nhãn cho máy ảo

![image](https://user-images.githubusercontent.com/69313033/147343818-3b3cd80a-e700-4523-a206-670493e9e03d.png)
6. Cấu hình cổng kết nối cho máy ảo

![image](https://user-images.githubusercontent.com/69313033/147343862-6aafcc68-6abc-4950-a1b9-6c0be9b2a322.png)
- Ở đây ta thấy có cổng mặc định 22 là cổng kết nối SSH.
7. Xem lại các cài đặt của máy ảo 

![image](https://user-images.githubusercontent.com/69313033/147343962-034e590b-e608-4500-90ba-a2d4ed8477a8.png)
- Khi chọn Launch AWS sẽ yêu cầu ta sử dụng private key có sẵn hoặc tạo private key mới.

![image](https://user-images.githubusercontent.com/69313033/147344083-fa790fdf-06d5-4f3f-aa21-0a9bcaf44759.png)
- Chọn tạo key mới, ta phải nhập tên key và tải về máy

![image](https://user-images.githubusercontent.com/69313033/147344258-e533117a-87ef-41d2-8021-493a1dcc2035.png)
- Tạo thành công ta chọn View Instance để kết nối và sử dụng máy ảo

![image](https://user-images.githubusercontent.com/69313033/147344377-bd1fb62a-3abd-4952-8695-11d9321e9541.png)
### Chuẩn bị docker images
1. Docker images sẵn có.
+ Truy cập [MyDockerImages](https://hub.docker.com/r/19110455/cloud/tags). 
2. Tuỳ chỉnh Docker images.
+ Truy cập Code trên GitHub [MyGitHubCode](https://github.com/fongto2811/nhom9_cloud) và Clone về máy.
+ Thư mục có dạng như sau:

![image](https://user-images.githubusercontent.com/69313033/147349861-c3e5309b-ca2f-4949-b1d8-979fef155931.png)
- Các thư mục python, gcc, csc, java dùng để chứa chương trình nhập vào và kết quả chạy chương trình.
- Thư mục templates chứa giao diện web viết bằng Flask Python.
- Dockerfile cài đặt các cấu hình khi tạo Docker Images.
- Sau khi cấu hình theo ý muốn, Build Image từ Dockerfile bằng lệnh `docker build <PATH Dockerfile>`
- Và push lên DockerHub bằng lệnh `docker tag <ImagesID> <your_dockerHub_UserName>/<your_repo>:tag` và `docker push <your_dockerHub_UserName>/<your_repo>:tag`
### Kết nối SSH
1. Truy cập Instances của dịch vụ EC2

![image](https://user-images.githubusercontent.com/69313033/147345937-6b82294c-8ce2-4456-893e-416d7cc70fec.png)
2. Chọn máy ảo sử dụng -> chọn Connect -> chọn kết nối SSH client

![image](https://user-images.githubusercontent.com/69313033/147346251-e603e559-b2e5-4639-b63a-ee5723b3a667.png)
- Làm theo hướng dẫn để kết nối SSH, sử dụng Command Prompt đối với Windows hoặc Terminal đối với Linux, Bash đối với MacOs.
- Chuyển đến thư mục chứa key <ten>.pem tải về ở bước 1.
- Coppy lệnh trong Example và chạy trong cmd,terminal,bash.

![image](https://user-images.githubusercontent.com/69313033/147347148-56ef3af2-fec3-4ffa-9444-39389e02b8b0.png)
3. Pull Images từ DockerHub về trong máy ảo EC2.
- Sử dụng lệnh `docker pull 19110455/cloud:1.2` hoặc `docker pull <your_dockerHub_UserName>/<your_repo>:tag`
 
![image](https://user-images.githubusercontent.com/69313033/147351115-b9f98b16-2ab7-4d62-9a89-2606468e570c.png)
- Chạy lệnh `docker images` để xem các images đã pull về 
- Chạy docker images đã pull về bằng lệnh `docker run -it -p 8080:80 <Repository>:<Tag>`
- Với -p là chọn port cho Container và phải chọn port đúng với cổng kết nối mở trên máy ảo EC2.
 
![image](https://user-images.githubusercontent.com/69313033/147351625-fb72975c-684e-4028-bc47-abdc0afdbb9d.png)

# [WEB DEMO - EC2 & DOCKER](http://ec2-54-210-84-211.compute-1.amazonaws.com:8080/)

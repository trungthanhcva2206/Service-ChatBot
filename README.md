# Service-ChatBot
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

Service dùng xây dựng chat AI cho ứng dụng quản lý lịch hẹn phòng khám. ChatAI hỗ trợ lễ tân có thể lựa chọn bác sỹ khám cho bệnh nhân dựa vào các mô tả về sức khỏe của bệnh nhân

Nền tảng công nghệ LCDP sử dụng: **N8N**

## Changelog

### v1.0
- **Node WebHook**:  
  - Dùng để kết nối đến các service khác của ứng dụng, node này sẽ lắng nghe và nhận đầu vào input chat của người dùng từ service khác

- **Node AI Agent**:  
  - Nhận input chat đầu vào và đưa ra câu trả lời. Câu trả lời sau đó sẽ được chuyển lại service đó để đưa ra cho người dùng
  - Trong Node AI Agent có các thành phần sau:
    - OpenAI Chat Model: Mô hình của OpenAI được sử dụng để hiểu và tạo phản hồi cho người dùng
    - Window Buffer Memory: Dữ liệu cuộc trò chuyện trước đó được lưu trữ tạm thời để giúp chatbot ghi nhớ ngữ cảnh cuộc trò chuyện
    - Pinecone Vector Store: Đây là cơ sở dữ liệu lưu trữ các embedding vector, được sử dụng để lưu trữ và truy xuất thông tin từ tài liệu
    - Vector Store Tool:
      - Công cụ dùng để truy cập và thao tác dữ liệu trong Pinecone
      - Truy vấn Pinecone để lấy dữ liệu cần thiết, chẳng hạn như thông tin ngữ nghĩa
      - Cập nhật hoặc thêm dữ liệu mới vào Pinecone khi cần
    - Embeddings OpenAI:
      - Nơi OpenAI tạo embedding từ input chat của người dùng
      - Tạo Embedding từ input chat của người dùng để so khớp và tìm kiếm các phản hồi tương ứng trong Pinecone

## Hướng dẫn cài đặt
### 1. Yêu cầu hệ thống  
- **Tài khoản OpenAI**: Để sử dụng mô hình tạo embedding.  
- **Tài khoản Pinecone**: Để lưu trữ và truy vấn vector.
- **N8N**: Phiên bản >=1.66.0

### 2. Cài đặt dữ án
#### Bước 1: Tải mã nguồn từ bản phát hành
1. Truy cập trang phát hành chính thức tại: [Releases](https://github.com/trungthanhcva2206/Service-ChatBot/releases).
2. Chọn phiên bản phù hợp với nhu cầu của bạn.
3. Trong phần **Assets**, tải tệp:
   - `Source code (zip)` hoặc
   - `Source code (tar.gz)`.

#### Bước 2: Giải nén và truy cập thư mục
```bash
# Giải nén file đã tải
unzip Service-ChatBot.zip
cd Service-ChatBot
```
#### Bước 3: Import vô N8N 
1. Tạo 1 workflow trong N8N
2. Import file Agent.json, file này lấy được ở trong thư mục Service-ChatBot

#### Bước 4: Chỉnh sửa các tài khoản dịch vụ
Ở trong các node OpenAI, Pinecone sẽ có phần **Credential to connect with**, có thể chỉnh sửa các tài khoản dịch vụ của mình ở đây. 

## Tác giả
- Nguyễn Lê Trung Thành
- Trần Tuấn Anh
- Lê Văn Quang

# License
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

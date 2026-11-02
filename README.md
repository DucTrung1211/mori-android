<div align="center">

# Mori — Memory Map

Lưu ảnh, gắn địa điểm và xem lại những nơi mình đã đi qua.

**Android · Kotlin · Jetpack Compose**

</div>

## Overview

Mori là ứng dụng Android để lưu những bức ảnh cùng địa điểm và thời gian chụp. Bạn có thể xem lại ký ức trên bản đồ, theo dòng thời gian hoặc tìm một kỷ niệm cụ thể.

Dự án đang được phát triển. Các luồng lưu và xem ảnh hiện dùng dữ liệu cục bộ; những phần chia sẻ với bạn bè vẫn chưa hoàn thiện.

## Project overview

| Item | Details |
| --- | --- |
| App | Mori — Memory Map |
| Platform | Android |
| Language | Kotlin |
| UI | Jetpack Compose |
| Minimum Android version | Android 8.0 — API 26 |
| Status | Đang phát triển |

## Features

- **Chụp và lưu ký ức:** chụp ảnh, xem trước và lưu vào bộ nhớ riêng của ứng dụng.
- **Bản đồ ký ức:** hiển thị những ảnh đã gắn tọa độ trên bản đồ.
- **Dòng thời gian:** xem lại các ký ức đã lưu.
- **Chi tiết và tìm kiếm:** mở lại từng ký ức, tìm theo nội dung và tên địa điểm khi có.
- **Tài khoản:** đăng ký, đăng nhập và quản lý phiên bằng Firebase Authentication.
- **Tên địa điểm:** dùng Geocoder của Android; nếu không lấy được tên thì hiển thị tọa độ.
- **Thanh điều hướng:** năm mục Bản đồ, Dòng thời gian, Camera, Bạn bè và Cá nhân. Camera mở luồng chụp ảnh.

Có mã triển khai không có nghĩa mọi tính năng đã được kiểm thử đầy đủ trên thiết bị thật. Giao diện, hiệu năng, khả năng truy cập và một số luồng đăng nhập vẫn cần kiểm tra thêm.

## Planned

Bạn bè, ký ức dùng chung, đồng bộ ảnh lên cloud, nhập ảnh và chia sẻ còn nằm trong kế hoạch phát triển. Việc có nút hoặc màn hình trong thiết kế không có nghĩa phần xử lý tương ứng đã hoàn tất.

## Tech stack

| Area | Technology |
| --- | --- |
| UI | Jetpack Compose, Material 3 |
| State management | ViewModel, StateFlow, Kotlin Coroutines |
| Camera | CameraX |
| Map | MapLibre Native, Vietmap raster tiles |
| Authentication | Firebase Authentication, Credential Manager |
| Local storage | App-private photo files and JSON index |
| Place names | Android Geocoder |
| Build | Gradle Wrapper |

## Getting started

Hướng dẫn dưới đây áp dụng sau khi mã nguồn Android được đưa lên repository. Hiện repository mới có README; các tính năng được mô tả ở trên thuộc bản source cục bộ đang phát triển.

### Prerequisites

- Android Studio và Android SDK phù hợp với cấu hình trong repository.
- JDK 21.
- Máy Android hoặc emulator từ API 26 trở lên.
- Cấu hình Firebase và khóa Vietmap dành cho môi trường phát triển của bạn.

### Setup

1. Clone repository:

   ```bash
   git clone https://github.com/DucTrung1211/mori-android.git
   cd mori-android
   ```

2. Mở dự án bằng Android Studio.
3. Tạo cấu hình SDK cục bộ trong `local.properties` nếu Android Studio chưa tạo.
4. Đặt cấu hình Firebase của bạn tại `app/google-services.json`. Cấu hình cần khớp với application ID `com.mori.memorymap`.
5. Thêm `VIETMAP_TILEMAP_KEY` vào `local.properties` bằng khóa của bạn.
6. Đồng bộ Gradle và chạy module `app`.

Không đưa các file cấu hình riêng, khóa API hoặc thông tin ký ứng dụng lên Git.

### Build and test

Trên Windows:

```powershell
.\gradlew.bat :app:testDebugUnitTest :app:assembleDebug
```

Trên macOS hoặc Linux:

```bash
./gradlew :app:testDebugUnitTest :app:assembleDebug
```

Build thành công chỉ xác nhận phần build và test đã chạy. Kiểm tra camera, bản đồ và hiệu năng cần thực hiện trên thiết bị hoặc emulator phù hợp.

## Privacy

Ảnh và chỉ mục ký ức hiện được lưu trong bộ nhớ riêng của ứng dụng. Bản đồ cần kết nối tới Vietmap để tải dữ liệu khi chưa có cache.

Geocoder của Android có thể gửi tọa độ tới nhà cung cấp của thiết bị để lấy tên địa điểm. Vì vậy, không nên coi toàn bộ việc xử lý vị trí là chỉ diễn ra trên máy.

## Development workflow

Sau khi mã nguồn được đưa lên, `main` sẽ giữ bản phát triển đã được tích hợp và kiểm tra theo phạm vi được ghi nhận. Mỗi branch `feat/...` tập trung vào một tính năng chính; `fix/...` dành cho lỗi và `docs/...` dành cho tài liệu.

Branch vẫn chứa toàn bộ dự án và lịch sử phụ thuộc. Các branch tính năng không phải những ứng dụng độc lập.

Tên branch, tên file, code identifiers, thuật ngữ kỹ thuật và commit message dùng tiếng Anh. Phần giới thiệu và hướng dẫn dùng tiếng Việt. Commit message theo dạng `feat:`, `fix:`, `docs:` hoặc `chore:`.

Chi tiết tiến độ, kết quả kiểm tra và những phần chưa xác minh được ghi trong `docs/MORI_REPORT.md` của bản source cục bộ. Báo cáo này sẽ được đưa lên cùng mã nguồn.

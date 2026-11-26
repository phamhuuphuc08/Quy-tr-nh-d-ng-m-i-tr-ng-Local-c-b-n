# Quy trình dựng môi trường Local cơ bản

> Tài liệu dành cho Intern Developer khi tiếp cận một dự án mới.

## 1. Kiến thức nền tảng

| Kiến thức | Yêu cầu |
| --- | --- |
| Git/GitHub | Clone, pull, checkout, branch, commit |
| Terminal | Di chuyển thư mục, chạy lệnh, quản lý tiến trình |
| Runtime | Node.js, Python, PHP, Java, .NET |
| Package Manager | npm, pnpm, yarn, pip, Composer |
| Database | MySQL, PostgreSQL, SQLite, MongoDB |
| Environment | Cấu hình `.env`, API URL, Database URL |
| Docker | Image, Container, Volume, Docker Compose |
| Networking | Localhost, Port, HTTP, HTTPS |
| Debugging | Đọc log, xác định và xử lý lỗi |

## 2. Quy trình dựng Local

### Bước 1: Clone source code

```bash
git clone <repository-url>
cd <project-name>
git branch -a
git switch <branch-name>
```

### Bước 2: Đọc tài liệu dự án

Kiểm tra `README.md`, cấu trúc thư mục, công nghệ sử dụng, phiên bản runtime, package manager và các dịch vụ cần thiết.

### Bước 3: Kiểm tra môi trường

Ví dụ đối với dự án Node.js:

```bash
node -v
npm -v
pnpm -v
```

Chỉ cài đặt những công cụ cần thiết và đúng phiên bản dự án yêu cầu.

### Bước 4: Cài đặt dependencies

Sử dụng package manager tương ứng với lockfile của dự án. Ví dụ:

```bash
pnpm install
```

### Bước 5: Cấu hình biến môi trường

Sao chép `.env.example` thành `.env` nếu dự án cung cấp file mẫu.

```bash
cp .env.example .env
```

Trên Windows PowerShell:

```powershell
Copy-Item .env.example .env
```

Cấu hình port, database, API URL và các biến bắt buộc theo tài liệu. Không commit mật khẩu, token hoặc file `.env` chứa thông tin bí mật.

### Bước 6: Khởi tạo database

- Khởi động dịch vụ database nếu cần.
- Tạo database và cấu hình kết nối.
- Chạy migration và seed theo hướng dẫn của dự án.
- Không chạy migration hoặc seed thử nghiệm trên production.

### Bước 7: Khởi động dự án

Chạy frontend, backend và các dịch vụ liên quan theo README hoặc scripts của dự án. Ví dụ:

```bash
pnpm dev
```

Nếu dự án hỗ trợ Docker Compose:

```bash
docker compose up -d --build
docker compose ps
docker compose logs -f
```

Dừng dịch vụ bằng `docker compose down` khi cần.

### Bước 8: Kiểm tra và xử lý lỗi

- Truy cập địa chỉ localhost được ghi trong log.
- Kiểm tra giao diện, API và kết nối database.
- Kiểm tra Console và Network trong DevTools.
- Ghi lại lỗi và cách xử lý để có thể tái hiện.

## 3. Các lệnh dựng Local theo công nghệ

| Công nghệ | Cài đặt | Khởi chạy |
| --- | --- | --- |
| React / Vite | `npm install` | `npm run dev` |
| Next.js | `pnpm install` | `pnpm dev` |
| NestJS | `npm install` | `npm run start:dev` |
| ExpressJS | `npm install` | `npm start` |
| VueJS | `npm install` | `npm run dev` |
| Angular | `npm install` | `npx ng serve` |
| Python Django | `pip install -r requirements.txt` | `python manage.py runserver` |
| Python FastAPI | `pip install -r requirements.txt` | `uvicorn main:app --reload` |
| PHP Laravel | `composer install` | `php artisan serve` |
| Java Spring Boot | `mvn install` | `mvn spring-boot:run` |
| ASP.NET Core | `dotnet restore` | `dotnet run` |
| Go | `go mod download` | `go run .` |
| Rust | `cargo build` | `cargo run` |
| Docker Compose | `docker compose build` | `docker compose up -d` |

> Các lệnh trên là ví dụ phổ biến, không phải quy định chung. Ưu tiên README, lockfile và scripts thực tế của dự án. Với Python nên sử dụng môi trường ảo (venv).

## 4. Nhận biết công nghệ qua cấu trúc source code

| File nhận diện | Công nghệ |
| --- | --- |
| `package.json` | Node.js / JavaScript / TypeScript |
| `next.config.ts` | Next.js |
| `nest-cli.json` | NestJS |
| `vite.config.ts` | Vite |
| `angular.json` | Angular |
| `requirements.txt`, `pyproject.toml` | Python |
| `manage.py` | Django |
| `composer.json` | PHP |
| `artisan` | Laravel |
| `pom.xml` | Java Maven |
| `build.gradle` | Gradle |
| `.csproj` | .NET |
| `go.mod` | Go |
| `Cargo.toml` | Rust |
| `Dockerfile` | Docker |
| `compose.yml`, `docker-compose.yml` | Docker Compose |
| `.env.example` | Mẫu cấu hình môi trường |
| `pnpm-lock.yaml` | pnpm |
| `yarn.lock` | Yarn |
| `package-lock.json` | npm |

## 5. Các lỗi thường gặp

| Lỗi | Hướng xử lý |
| --- | --- |
| Port already in use | Kiểm tra tiến trình chiếm port hoặc đổi port |
| Module not found | Kiểm tra và cài dependencies |
| Command not found | Kiểm tra công cụ và PATH |
| Database connection refused | Kiểm tra dịch vụ database, host và port |
| Access denied | Kiểm tra tài khoản và quyền truy cập |
| Version incompatible | Sử dụng đúng phiên bản runtime |
| Missing environment variable | Kiểm tra file `.env` |
| Migration failed | Kiểm tra cấu trúc và kết nối database |
| Docker build failed | Đọc log build và kiểm tra Dockerfile |
| CORS error | Kiểm tra cấu hình frontend và backend |
| Git merge conflict | Kiểm tra và xử lý xung đột source code |

## 6. Checklist đánh giá năng lực Intern

- [ ] Biết clone một repository mới.
- [ ] Biết xác định công nghệ từ cấu trúc source code.
- [ ] Biết cài đặt đúng phiên bản môi trường.
- [ ] Biết sử dụng Git và chuyển branch.
- [ ] Biết cấu hình file `.env`.
- [ ] Biết khởi tạo database, migration và seed.
- [ ] Biết chạy frontend và backend.
- [ ] Biết dựng dự án bằng Docker Compose.
- [ ] Biết kiểm tra API bằng Postman.
- [ ] Biết đọc log và tự tìm nguyên nhân lỗi.
- [ ] Biết debug bằng DevTools.
- [ ] Biết viết tài liệu hướng dẫn dựng Local.

## 7. Mục tiêu

Intern không cần thuộc lòng tất cả các lệnh. Điều quan trọng là có khả năng tự đọc tài liệu, xác định công nghệ, cài đặt môi trường, khởi chạy dự án và chủ động xử lý các lỗi cơ bản khi được giao một source code mới.

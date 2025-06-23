# 📋 Aplikasi Magang DPU Banten - Panduan Kolaborasi (PHP Native)

## 👥 Tim Developer
- **Developer 1**: [Nama] - Frontend & UI/UX
- **Developer 2**: [Nama] - Backend & Database

## 🗂️ Struktur Folder Project

```
magang-dpu-banten/
├── 📁 assets/
│   ├── 📁 css/
│   │   ├── bootstrap.min.css
│   │   ├── style.css
│   │   ├── dashboard.css
│   │   └── responsive.css
│   ├── 📁 js/
│   │   ├── jquery.min.js
│   │   ├── bootstrap.min.js
│   │   ├── sweetalert2.min.js
│   │   ├── datatables.min.js
│   │   └── main.js
│   ├── 📁 images/
│   │   ├── 📁 logo/
│   │   ├── 📁 avatars/
│   │   └── 📁 backgrounds/
│   └── 📁 fonts/
├── 📁 config/
│   ├── database.php
│   ├── config.php
│   └── constants.php
├── 📁 includes/
│   ├── header.php
│   ├── sidebar.php
│   ├── footer.php
│   ├── navbar.php
│   └── functions.php
├── 📁 modules/
│   ├── 📁 auth/
│   │   ├── login.php
│   │   ├── logout.php
│   │   ├── register.php
│   │   └── forgot-password.php
│   ├── 📁 dashboard/
│   │   ├── index.php
│   │   ├── stats.php
│   │   └── widgets.php
│   ├── 📁 peserta/
│   │   ├── index.php
│   │   ├── add.php
│   │   ├── edit.php
│   │   ├── delete.php
│   │   ├── detail.php
│   │   └── ajax-handler.php
│   ├── 📁 institusi/
│   │   ├── index.php
│   │   ├── add.php
│   │   ├── edit.php
│   │   └── riwayat.php
│   ├── 📁 jadwal/
│   │   ├── index.php
│   │   ├── create.php
│   │   ├── pembimbing.php
│   │   └── calendar.php
│   ├── 📁 laporan/
│   │   ├── index.php
│   │   ├── input.php
│   │   ├── validasi.php
│   │   └── export.php
│   ├── 📁 idcard/
│   │   ├── index.php
│   │   ├── generator.php
│   │   ├── template.php
│   │   └── print.php
│   ├── 📁 arsip/
│   │   ├── alumni.php
│   │   ├── riwayat-penempatan.php
│   │   └── riwayat-laporan.php
│   └── 📁 pengaturan/
│       ├── index.php
│       ├── akun.php
│       ├── template.php
│       └── notifikasi.php
├── 📁 api/
│   ├── auth.php
│   ├── peserta.php
│   ├── institusi.php
│   ├── jadwal.php
│   ├── laporan.php
│   └── upload.php
├── 📁 uploads/
│   ├── 📁 documents/
│   ├── 📁 photos/
│   ├── 📁 exports/
│   └── 📁 temp/
├── 📁 vendor/
│   ├── 📁 phpmailer/
│   ├── 📁 dompdf/
│   ├── 📁 phpqrcode/
│   └── 📁 mpdf/
├── 📁 database/
│   ├── magang_dpu.sql
│   ├── migration.sql
│   └── seeders.sql
├── 📁 docs/
│   ├── database-schema.md
│   ├── api-documentation.md
│   └── user-manual.md
├── 📄 index.php
├── 📄 .htaccess
├── 📄 .gitignore
├── 📄 README.md
└── 📄 CHANGELOG.md
```

## 🎨 Design System & Template

### Color Palette
```css
:root {
  /* Primary Colors - DPU Banten */
  --primary-blue: #1E40AF;
  --primary-green: #059669;
  --primary-dark: #1F2937;
  
  /* Secondary Colors */
  --secondary-light: #F3F4F6;
  --secondary-gray: #6B7280;
  --accent-orange: #F59E0B;
  
  /* Status Colors */
  --success: #10B981;
  --warning: #F59E0B;
  --error: #EF4444;
  --info: #3B82F6;
  
  /* Background */
  --bg-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}
```

### CSS Framework
```html
<!-- Bootstrap 5.1.3 -->
<link href="assets/css/bootstrap.min.css" rel="stylesheet">
<!-- Font Awesome 6.0 -->
<link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
<!-- Custom CSS -->
<link href="assets/css/style.css" rel="stylesheet">
```

### File Naming Convention
```php
// ✅ BENAR - Kebab Case untuk file
peserta-add.php
laporan-export.php
id-card-generator.php

// ✅ BENAR - Snake Case untuk variabel & function
$peserta_data = [];
function get_peserta_by_id($id) {}
function validate_user_input($data) {}

// ❌ SALAH  
PesertaAdd.php
laporanExport.php
idCardGenerator.php
```

### PHP Standards
```php
<?php
// File header wajib
/**
 * Aplikasi Magang DPU Banten
 * Module: Peserta Management
 * Author: [Nama Developer]
 * Created: [Tanggal]
 */

// Selalu cek session
session_start();
require_once '../config/database.php';
require_once '../includes/functions.php';

// Cek login
if (!isset($_SESSION['user_id'])) {
    header('Location: ../auth/login.php');
    exit();
}

// Class naming - PascalCase
class PesertaManager {
    private $db;
    
    public function __construct($database) {
        $this->db = $database;
    }
    
    // Method naming - camelCase
    public function getPesertaById($id) {
        // Implementation
    }
}
?>
```

## 🗄️ Database Schema

### Tabel Utama
```sql
-- users
CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    username VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    password VARCHAR(255) NOT NULL,
    role ENUM('admin', 'koordinator', 'mahasiswa') NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- institusi
CREATE TABLE institusi (
    id INT PRIMARY KEY AUTO_INCREMENT,
    nama_institusi VARCHAR(200) NOT NULL,
    jenis ENUM('universitas', 'sekolah') NOT NULL,
    alamat TEXT,
    kontak VARCHAR(50),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- peserta
CREATE TABLE peserta (
    id INT PRIMARY KEY AUTO_INCREMENT,
    user_id INT,
    institusi_id INT,
    nama_lengkap VARCHAR(150) NOT NULL,
    nim_nis VARCHAR(50),
    jurusan VARCHAR(100),
    semester INT,
    foto VARCHAR(255),
    status ENUM('aktif', 'selesai', 'berhenti') DEFAULT 'aktif',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (user_id) REFERENCES users(id),
    FOREIGN KEY (institusi_id) REFERENCES institusi(id)
);
```

## 🔄 Git Workflow & Branch Strategy

### Branch Naming Convention
```bash
# Feature branches
feature/login-system
feature/dashboard-stats
feature/peserta-crud

# Bugfix branches
bugfix/login-validation
bugfix/upload-error

# Database branches
database/migration-v1
database/add-table-laporan
```

### Commit Message Format
```bash
# Format: [type]: description

feat: add peserta registration form
fix: resolve file upload validation
database: add laporan_harian table
ui: update dashboard responsive design
docs: add API documentation
```

## 📋 Pembagian Tugas

### 👨‍💻 Developer 1 (Frontend & UI)
**Week 1:**
- [ ] Setup project structure & assets
- [ ] Create base templates (header, sidebar, footer)
- [ ] Design login & dashboard interface
- [ ] Build peserta management UI

**Week 2:**
- [ ] Develop institusi management pages
- [ ] Create jadwal & calendar interface
- [ ] Build laporan kegiatan forms
- [ ] Design ID card templates

**Week 3:**
- [ ] Complete arsip & pengaturan pages
- [ ] Responsive design optimization
- [ ] Cross-browser testing
- [ ] UI/UX improvements

### 👨‍💻 Developer 2 (Backend & Database)
**Week 1:**
- [ ] Database design & creation
- [ ] Setup PHP configurations
- [ ] Authentication system & sessions
- [ ] User management functions

**Week 2:**
- [ ] Peserta CRUD operations
- [ ] File upload & validation
- [ ] Institusi management backend
- [ ] Jadwal & penempatan logic

**Week 3:**
- [ ] Laporan system & export features
- [ ] ID card generation (PDF/Image)
- [ ] Email notifications
- [ ] API endpoints & security

## 🛠️ PHP Libraries & Tools

### Required Libraries
```php
// Composer dependencies
composer require:
- phpmailer/phpmailer (Email)
- dompdf/dompdf (PDF Generation)
- endroid/qr-code (QR Code)
- intervention/image (Image Processing)
```

### Manual Libraries (vendor/)
- **PHPExcel/PhpSpreadsheet** - Excel export
- **TCPDF/mPDF** - Advanced PDF generation
- **PHPQRCode** - QR Code generation
- **PHPMailer** - Email sending

## 🔒 Security Best Practices

### Input Validation
```php
// Sanitize input
function sanitize_input($data) {
    $data = trim($data);
    $data = stripslashes($data);
    $data = htmlspecialchars($data);
    return $data;
}

// Prepared statements untuk database
$stmt = $pdo->prepare("SELECT * FROM peserta WHERE id = ?");
$stmt->execute([$id]);
$result = $stmt->fetch();
```

### File Upload Security
```php
// config/config.php
define('MAX_FILE_SIZE', 5 * 1024 * 1024); // 5MB
define('ALLOWED_EXTENSIONS', ['jpg', 'jpeg', 'png', 'pdf', 'doc', 'docx']);
define('UPLOAD_PATH', 'uploads/');

// Validation function
function validate_file_upload($file) {
    // Check file size, extension, MIME type
    // Return true/false
}
```

### Environment Variables (.env)
```php
// config/config.php
define('DB_HOST', 'localhost');
define('DB_NAME', 'magang_dpu');
define('DB_USER', 'root');
define('DB_PASS', '');

define('MAIL_HOST', 'smtp.gmail.com');
define('MAIL_USERNAME', 'your-email@gmail.com');
define('MAIL_PASSWORD', 'your-app-password');

define('JWT_SECRET', 'your-secret-key-here');
define('SITE_URL', 'http://localhost/magang-dpu-banten');
```

## 📋 Code Standards & Review

### PHP Code Standards
```php
<?php
// ✅ BENAR
class PesertaManager 
{
    private $database;
    
    public function __construct($db) 
    {
        $this->database = $db;
    }
    
    public function getAllPeserta() 
    {
        try {
            $query = "SELECT * FROM peserta ORDER BY created_at DESC";
            $stmt = $this->database->prepare($query);
            $stmt->execute();
            return $stmt->fetchAll(PDO::FETCH_ASSOC);
        } catch (PDOException $e) {
            error_log("Error: " . $e->getMessage());
            return false;
        }
    }
}

// HTML Template struktur
include 'includes/header.php';
include 'includes/sidebar.php';
?>

<div class="main-content">
    <div class="container-fluid">
        <!-- Content here -->
    </div>
</div>

<?php
include 'includes/footer.php';
?>
```

### File yang WAJIB di .gitignore
```gitignore
# Configuration
config/database.php
.env

# Uploads
uploads/*
!uploads/.gitkeep

# Logs
logs/*.log
error.log

# Cache
cache/*
!cache/.gitkeep

# IDE
.vscode/
.idea/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db

# Backup files
*.bak
*.backup
*~
```

## 🚀 Development & Deployment

### Local Development
```bash
# XAMPP/WAMP/LAMP setup
- Apache 2.4+
- PHP 7.4+ (recommended 8.0+)
- MySQL 5.7+
- phpMyAdmin

# Virtual Host setup
<VirtualHost *:80>
    DocumentRoot "C:/xampp/htdocs/magang-dpu-banten"
    ServerName magang-dpu.local
</VirtualHost>
```

### Production Checklist
- [ ] Remove all debug code & error displays
- [ ] Enable error logging
- [ ] Secure file permissions (755 for directories, 644 for files)
- [ ] SSL certificate setup
- [ ] Database backup strategy
- [ ] Remove default credentials

## 📞 Communication & Workflow

### Daily Progress Report
**Format WhatsApp:**
```
📅 [Tanggal]
👨‍💻 Developer: [Nama]

✅ Completed:
- Login system validation
- Peserta table CRUD

🔄 In Progress:
- Dashboard statistics

❌ Blocked:
- File upload issues

📋 Next:
- Export PDF functionality
```

### Code Review Process
1. **Self Review**: Test di local, cek syntax
2. **Create PR**: Describe changes, screenshot jika UI
3. **Peer Review**: Check functionality, security, standards
4. **Merge**: Setelah approve dari partner

---

**🔥 PENTING**: 
- Selalu backup database sebelum migration
- Test semua fitur di local sebelum push
- Jangan commit file config dengan password asli
- Gunakan prepared statements untuk semua query database

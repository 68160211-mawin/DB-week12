# Database Management | Week: PHP Login / Logout + GitHub

## Based on last week's Resume CRUD Lab

This code extends the previous CRUD project, retaining `skills.php`, `skill_create.php`, `skill_edit.php`, `skill_delete.php` and `index.php`.

### Setup (local XAMPP / Angsila)
1. Backup the existing MySQL database in phpMyAdmin first.
2. Keep previous tables `profile`, `education`, `skill`, `training`. **Do not re-import the previous setup.sql**: it contains DROP TABLE commands.
3. In phpMyAdmin, select your existing database and run `database/this_week_migration.sql` (creates `users` only).
4. Configure `config/db.php` using your assigned MySQL credentials and database name (use environment variables on shared servers).
5. Upload files to a dedicated folder on web server (for Angsila, follow instructor's permitted deployment path).
6. Open `register.php`, sign up with a unique email and password >= 10 characters.
## Student Info
- Name: วชิรวิชญ์ ชลมารค
- Student ID: 68160211
- GitHub: https://github.com/68160211-mawin/DB-week12

## Completed Tasks
- TODO 1–5: `login.php` ใช้ prepared statement ดึง user จาก email, ตรวจรหัสผ่านด้วย `password_verify`, เรียก `session_regenerate_id(true)`, เก็บ `user_id`/`profile_id`/`email` ใน session แล้ว redirect ไป `skills.php`
- TODO 6: `logout.php` ตรวจ CSRF token, ล้าง `$_SESSION`, ลบ session cookie, `session_destroy()` แล้ว redirect ไป `login.php`

## How Login/Logout Works
1. ผู้ใช้กรอก email/password ที่ `login.php` (POST + CSRF token)
2. ระบบค้น user ด้วย email แล้วใช้ `password_verify` เทียบกับ hash ในฐานข้อมูล
3. ถ้าถูกต้อง สร้าง session ใหม่และเก็บข้อมูลผู้ใช้ จากนั้นหน้าอื่นเรียก `require_login()` เพื่อตรวจ session
4. ตอน logout ระบบลบ session ทั้งหมด หน้าส่วนตัวจะเข้าไม่ได้อีก
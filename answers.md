
# Lab L1 Answers

## Q1: Tools

Flutter doctor แจ้งว่าไม่ได้ติดตั้ง Visual Studio แต่เนื่องจากงานนี้พัฒนาแอป Android จึงไม่จำเป็นต้องติดตั้ง Visual Studio โดย Android Toolchain ผ่านการตรวจสอบแล้ว

ฉันใช้คำสั่ง flutter emulators เพื่อเปิด Android Emulator และ flutter devices เพื่อตรวจสอบการเชื่อมต่อ

นอกจากนี้ยังพบปัญหา Android Gradle Plugin และ Gradle เวอร์ชันเก่า จึงปรับเวอร์ชันในไฟล์ settings.gradle.kts และ gradle-wrapper.properties เพื่อให้ Build แอปได้สำเร็จ

## Q2: Hot Reload and Hot Restart

เมื่อกด Like 3 ครั้ง จะได้ Likes: 3

- Hot Reload (r): เปลี่ยนข้อความ Title ได้ แต่ Likes ยังคงเป็น 3 เพราะยังรักษา State เดิมไว้
- Hot Restart (R): แอปเริ่มทำงานใหม่ ทำให้ Likes กลับเป็น 0 เพราะค่าเริ่มต้นของ _likes คือ 0

## Q3: Code and Git

setState() ใช้แจ้ง Flutter ว่ามีการเปลี่ยนแปลง State เพื่อให้เรียก build() ใหม่และแสดงจำนวน Likes ที่อัปเดตแล้วบนหน้าจอ

ตัวอย่าง Commit:
"Add like counter with setState"

เป็นการเพิ่มตัวแปร _likes ฟังก์ชัน _like() และปุ่ม Like เพื่อให้ผู้ใช้สามารถเพิ่มจำนวน Likes ได้

## Test Results

| Type | Input / Action | Expected Result | Actual Result |
|---|---|---|---|
| Normal | Open app | Title, icon, name, Likes: 0 | ผ่าน |
| Normal | Press Like once | Likes: 1 | ผ่าน |
| Boundary | Press Like 20 times quickly | Likes: 20, no error | ผ่าน |
| Boundary | Rotate to landscape | Centered, no overflow | ผ่าน |
| Reload | Press 3 times, then r and R | 3 after r, 0 after R | ผ่าน |
| Failure | Close emulator and run flutter | No device message | พบ Windows, Chrome และ Edge และแสดงรายการให้เลือกอุปกรณ์ |

## AI Usage

ใช้ ChatGPT ช่วยอธิบายขั้นตอนการทำงาน Flutter วิเคราะห์ข้อผิดพลาด และแนะนำการแก้ไขโค้ด รวมถึงช่วยอธิบาย Hot Reload และ Hot Restart โดยได้ทดลองแก้ไขและทดสอบโปรแกรมด้วยตนเอง

# คู่มือการใช้งาน Google Clasp (Command Line Apps Script Projects)

Google Clasp เป็นเครื่องมือ Command Line Interface (CLI) ที่พัฒนาโดย Google เพื่อให้นักพัฒนาสามารถพัฒนาโปรเจกต์ Google Apps Script (GAS) บนเครื่องคอมพิวเตอร์ของตัวเอง (Local environment) ได้ โดยใช้ Code Editor ที่ชื่นชอบ (เช่น VS Code) และสามารถใช้งานร่วมกับ Version Control System อย่าง Git ได้

## สารบัญ
1. [สิ่งที่ต้องเตรียมพร้อม (Prerequisites)](#สิ่งที่ต้องเตรียมพร้อม-prerequisites)
2. [ขั้นตอนการติดตั้งและเริ่มใช้งาน (Step-by-Step)](#ขั้นตอนการติดตั้งและเริ่มใช้งาน-step-by-step)
    * [การติดตั้ง Clasp](#1-การติดตั้ง-clasp)
    * [การเข้าสู่ระบบ (Login)](#2-การเข้าสู่ระบบ-login)
    * [การสร้างโปรเจกต์ใหม่ (Create)](#3-การสร้างโปรเจกต์ใหม่-create)
    * [การโคลนโปรเจกต์ที่มีอยู่ (Clone)](#4-การโคลนโปรเจกต์ที่มีอยู่-clone)
3. [คำสั่งที่ใช้บ่อยในการพัฒนา](#คำสั่งที่ใช้บ่อยในการพัฒนา)
4. [การใช้งานร่วมกับ TypeScript](#การใช้งานร่วมกับ-typescript-แนะนำ)
5. [การเพิ่มประสิทธิภาพด้วย AI (Gemini CLI และ Claude AI)](#5-การเพิ่มประสิทธิภาพด้วย-ai-gemini-cli-และ-claude-ai)

---

## สิ่งที่ต้องเตรียมพร้อม (Prerequisites)

1.  **Node.js และ npm:** ติดตั้ง Node.js ในเครื่องคอมพิวเตอร์ของคุณ (ดาวน์โหลดได้ที่ [nodejs.org](https://nodejs.org/))
2.  **เปิดใช้งาน Apps Script API:** คุณต้องเปิดใช้งาน API เพื่อให้ Clasp สามารถเข้าถึงโปรเจกต์ของคุณได้
    *   เข้าไปที่ [script.google.com/home/settings](https://script.google.com/home/settings)
    *   เปลี่ยนสถานะ **Google Apps Script API** ให้เป็น **ON**

---

## ขั้นตอนการติดตั้งและเริ่มใช้งาน (Step-by-Step)

### 1. การติดตั้ง Clasp
เปิด Terminal หรือ Command Prompt แล้วใช้คำสั่ง npm เพื่อติดตั้งแบบ Global:

```bash
npm install -g @google/clasp
```

### 2. การเข้าสู่ระบบ (Login)
เพื่อเชื่อมต่อ Clasp กับบัญชี Google ของคุณ:

```bash
clasp login
```
*ระบบจะเปิด Browser ให้คุณเลือกบัญชี Google และกดยืนยันการเข้าถึง*

### 3. การสร้างโปรเจกต์ใหม่ (Create)
หากคุณต้องการเริ่มโปรเจกต์ใหม่จากเครื่องคอมพิวเตอร์:

```bash
clasp create --title "My Awesome Project" --type sheet
```
*คุณสามารถระบุประเภทได้ เช่น `standalone`, `docs`, `sheets`, `slides`, `forms`, `webapp`*

### 4. การโคลนโปรเจกต์ที่มีอยู่ (Clone)
หากคุณมีโปรเจกต์ใน Google Apps Script Editor อยู่แล้ว และต้องการดึงลงมาแก้ไข:

```bash
clasp clone <scriptId>
```
*หา `scriptId` ได้จาก Project Settings ในหน้า Apps Script Editor*

---

## คำสั่งที่ใช้บ่อยในการพัฒนา

*   **ดึงโค้ดล่าสุดลงมา (Pull):** ใช้เมื่อมีการแก้ไขบน Browser แล้วต้องการอัปเดตไฟล์ในเครื่อง
    ```bash
    clasp pull
    ```
*   **อัปโหลดโค้ดขึ้นไป (Push):** ใช้เมื่อแก้ไขโค้ดในเครื่องเสร็จแล้วต้องการส่งขึ้นไปยัง Google Apps Script
    ```bash
    clasp push
    ```
*   **เปิดหน้า Apps Script Editor บน Browser:**
    ```bash
    clasp open
    ```
*   **สร้าง Version ใหม่ (Deploy):**
    ```bash
    clasp deploy --description "First Version"
    ```

---

## การใช้งานร่วมกับ TypeScript (แนะนำ)
Clasp รองรับ TypeScript โดยอัตโนมัติ เมื่อคุณ `clasp push` ไฟล์ `.ts` จะถูกแปลงเป็นโค้ดที่ Apps Script เข้าใจโดยอัตโนมัติ

**วิธีเริ่มใช้งาน TypeScript:**
1. ติดตั้ง Types สำหรับ Google Apps Script:
   ```bash
   npm install --save-dev @types/google-apps-script
   ```
2. สร้างไฟล์ `tsconfig.json` ในโฟลเดอร์โปรเจกต์ของคุณ

## 5. การเพิ่มประสิทธิภาพด้วย AI (Gemini CLI และ Claude AI)

การใช้งาน Clasp ร่วมกับเครื่องมือ AI อย่าง **Gemini CLI** และ **Claude AI** จะช่วยให้คุณเขียน Google Apps Script ได้รวดเร็วและแม่นยำยิ่งขึ้น

### ประโยชน์ของการใช้ AI ร่วมกับ Clasp
*   **Generate Boilerplate:** ให้ AI เขียนโครงสร้างฟังก์ชันพื้นฐาน เช่น การเชื่อมต่อ Google Sheets, การส่งอีเมลอัตโนมัติ หรือการสร้าง Custom Menu
*   **Refactor & Debug:** ส่งโค้ดที่ติด Error ให้ AI ช่วยวิเคราะห์และแก้ไขได้ทันที
*   **TypeScript Support:** ให้ AI ช่วยแปลง JavaScript เป็น TypeScript พร้อมระบุ Types ที่ถูกต้องสำหรับ GAS

### Workflow การทำงาน
1.  **ถาม AI:** ใช้ Gemini หรือ Claude ช่วยเขียนโค้ดตามโจทย์ที่ต้องการ (เช่น "เขียนฟังก์ชันดึงข้อมูลจาก Sheet A ไปสรุปผลใน Sheet B")
2.  **Copy & Paste:** นำโค้ดที่ได้มาใส่ในไฟล์ `.js` หรือ `.ts` ในเครื่องของคุณผ่าน VS Code
3.  **Validate:** ตรวจสอบความถูกต้องและปรับแต่งโค้ดตามความต้องการ
4.  **Push:** ใช้คำสั่ง `clasp push` เพื่อส่งโค้ดขึ้นไปยัง Google Apps Script ทันที

### ตัวอย่างคำสั่ง (Prompt) ที่แนะนำ
*   *"ช่วยเขียน Google Apps Script (TypeScript) สำหรับสร้าง Sidebar ใน Google Sheets โดยใช้ HTML5"*
*   *"Refactor โค้ด GAS นี้ให้ทำงานเร็วขึ้นโดยใช้ Batch Operations (setValues)"*
*   *"ตรวจสอบ Error ในฟังก์ชัน onChange นี้หน่อยว่าทำไม Trigger ไม่ทำงาน"*

---
*จัดทำโดย Gemini CLI*

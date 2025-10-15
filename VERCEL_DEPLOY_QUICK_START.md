# ⚡ Quick Start: Deploy บน Vercel ใน 5 นาที

## 🚀 ขั้นตอนง่ายๆ

### 1️⃣ เตรียม Code

```bash
# ตรวจสอบว่า build สำเร็จ
npm run build

# ✅ ถ้าสำเร็จให้ไปขั้นตอนถัดไป
```

### 2️⃣ Push ไป GitHub

```bash
# ถ้ายังไม่ได้ init git
git init
git add .
git commit -m "Ready for deployment"

# สร้าง repo ใหม่บน GitHub แล้ว push
git remote add origin https://github.com/YOUR_USERNAME/slip-ocr.git
git branch -M main
git push -u origin main
```

### 3️⃣ Deploy บน Vercel

**วิธีที่ 1: ผ่าน Dashboard (ง่ายสุด)**

1. ไปที่: https://vercel.com
2. Sign in with GitHub
3. Click "Add New Project"
4. Import your repository
5. Click "Deploy" (ไม่ต้องแก้ไขอะไร)
6. รอ 2-3 นาที ✅ Done!

**วิธีที่ 2: ผ่าน CLI (สำหรับ Developer)**

```bash
# ติดตั้ง
npm install -g vercel

# Login
vercel login

# Deploy
vercel --prod
```

---

## 🎯 หลัง Deploy สำเร็จ

คุณจะได้ URL แบบนี้:
```
https://your-project-name.vercel.app
```

**ทดสอบทันที**:
- ✅ อัปโหลดสลิป
- ✅ ทดสอบ QR Code scanning
- ✅ ทดสอบ OCR
- ✅ ทดสอบ Copy JSON

---

## 💡 Tips

### Auto Deploy
ทุกครั้งที่ push ไป GitHub, Vercel จะ deploy ให้อัตโนมัติ!

```bash
git add .
git commit -m "Update feature"
git push
# ✨ Auto deploy!
```

### Custom Domain
1. ไปที่ Vercel Dashboard
2. Project Settings > Domains
3. Add your domain
4. Follow DNS instructions

### Preview Deploy
```bash
vercel
# ได้ preview URL สำหรับทดสอบ
```

---

## 🐛 แก้ปัญหาเร็ว

**Build Error?**
```bash
# ทดสอบ local ก่อน
npm run build

# แก้ error แล้ว push ใหม่
git add .
git commit -m "Fix build error"
git push
```

**Page not found?**
- รอ deploy เสร็จก่อน (2-3 นาที)
- Refresh browser
- เช็ค Vercel Dashboard > Deployments

---

## 📊 Monitor

**Vercel Dashboard**:
- ดู Analytics
- ดู Logs
- ดู Performance
- ดู Deployments history

---

## ✅ Checklist

- [ ] `npm run build` สำเร็จ
- [ ] Push code ไป GitHub
- [ ] Deploy บน Vercel
- [ ] ทดสอบทุกฟีเจอร์
- [ ] แชร์ URL

---

**🎉 ใช้เวลาแค่ 5 นาที โปรเจคคุณพร้อมใช้งานแล้ว!**

สำหรับข้อมูลเพิ่มเติม ดูที่ [DEPLOY.md](./DEPLOY.md)

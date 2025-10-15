# 🚀 คู่มือการ Deploy บน Vercel

## วิธีที่ 1: Deploy ผ่าน Vercel Dashboard (แนะนำสำหรับมือใหม่)

### ขั้นตอนที่ 1: เตรียม Git Repository

```bash
# สร้าง Git repository (ถ้ายังไม่มี)
git init

# เพิ่มไฟล์ทั้งหมด
git add .

# Commit
git commit -m "Initial commit - Bank Slip Reader"

# Push ไปยัง GitHub
# สร้าง repository ใหม่บน GitHub แล้ว push
git remote add origin <your-github-repo-url>
git branch -M main
git push -u origin main
```

### ขั้นตอนที่ 2: Deploy บน Vercel

1. **ไปที่**: https://vercel.com
2. **Sign In** ด้วย GitHub account
3. **Click**: "Add New Project"
4. **Import Repository**: เลือก repository ของคุณ
5. **Configure Project**:
   - Framework Preset: Next.js (จะถูกตั้งค่าอัตโนมัติ)
   - Root Directory: `./`
   - Build Command: `npm run build` (default)
   - Output Directory: `.next` (default)
6. **Environment Variables**: ไม่ต้องตั้งค่า (project นี้ไม่ใช้ env variables)
7. **Click**: "Deploy"

### ขั้นตอนที่ 3: รอ Deployment เสร็จสิ้น

- Vercel จะ build และ deploy โปรเจคของคุณ
- ใช้เวลาประมาณ 2-5 นาที
- เมื่อเสร็จจะได้ URL เช่น: `https://your-project.vercel.app`

---

## วิธีที่ 2: Deploy ผ่าน Vercel CLI (สำหรับ Developer)

### ขั้นตอนที่ 1: ติดตั้ง Vercel CLI

```bash
npm install -g vercel
```

### ขั้นตอนที่ 2: Login

```bash
vercel login
```

### ขั้นตอนที่ 3: Deploy

```bash
# Deploy to production
vercel --prod

# หรือ deploy to preview
vercel
```

### ขั้นตอนที่ 4: ตอบคำถาม

```
? Set up and deploy "~/slip-ocr"? [Y/n] y
? Which scope do you want to deploy to? Your Name
? Link to existing project? [y/N] n
? What's your project's name? slip-ocr
? In which directory is your code located? ./
```

### ขั้นตอนที่ 5: รอ Deployment เสร็จสิ้น

Vercel CLI จะแสดง URL ของโปรเจคที่ deploy แล้ว

---

## 🔧 การตั้งค่าเพิ่มเติม

### Custom Domain (ถ้าต้องการ)

1. ไปที่ Vercel Dashboard
2. เลือก Project ของคุณ
3. ไปที่ Settings > Domains
4. เพิ่ม custom domain ของคุณ
5. ตั้งค่า DNS ตามคำแนะนำ

### Environment Variables (สำหรับการตั้งค่าในอนาคต)

1. ไปที่ Vercel Dashboard
2. เลือก Project > Settings > Environment Variables
3. เพิ่ม key และ value
4. Redeploy โปรเจค

---

## 📊 การตรวจสอบ Deployment

### ตรวจสอบสถานะ

```bash
# ดู deployment ล่าสุด
vercel ls

# ดู logs
vercel logs <deployment-url>
```

### ตรวจสอบผ่าน Dashboard

1. ไปที่ https://vercel.com/dashboard
2. เลือกโปรเจคของคุณ
3. ดู Deployments, Analytics, และ Logs

---

## 🚨 การแก้ไขปัญหา

### Build Error

**ปัญหา**: Build failed
**วิธีแก้**:
```bash
# ทดสอบ build ใน local ก่อน
npm run build

# ตรวจสอบ error และแก้ไข
# จากนั้น commit และ push ใหม่
```

### Deployment Error

**ปัญหา**: Deployment failed
**วิธีแก้**:
1. ตรวจสอบ logs บน Vercel Dashboard
2. ตรวจสอบว่า `package.json` ถูกต้อง
3. ตรวจสอบว่า dependencies ครบถ้วน
4. ลอง redeploy ใหม่

### 404 Error

**ปัญหา**: หน้าเว็บแสดง 404
**วิธีแก้**:
1. ตรวจสอบว่า build สำเร็จ
2. ตรวจสอบ routes ใน Next.js
3. ตรวจสอบ `vercel.json` config

---

## 🔄 การ Redeploy

### อัตโนมัติ (แนะนำ)

ทุกครั้งที่ push ไปยัง main branch:
```bash
git add .
git commit -m "Update features"
git push origin main
```

Vercel จะ deploy อัตโนมัติ

### Manual Redeploy

1. ไปที่ Vercel Dashboard
2. เลือก Project > Deployments
3. Click "Redeploy" บน deployment ที่ต้องการ

---

## 📈 การเพิ่มประสิทธิภาพ

### Build Optimization

Already configured in `next.config.ts`:
- Webpack aliases สำหรับ canvas และ encoding
- Production build optimization

### Vercel Configuration

Already configured in `vercel.json`:
- Security headers
- Singapore region (`sin1`) สำหรับ SEA users
- Framework detection

---

## 📝 Checklist ก่อน Deploy

- [ ] ทดสอบ `npm run build` สำเร็จ
- [ ] ทดสอบ `npm start` ทำงานได้
- [ ] ตรวจสอบ `.gitignore` ครบถ้วน
- [ ] Commit และ Push code ล่าสุด
- [ ] README.md อัปเดตแล้ว
- [ ] ลบ console.log ที่ไม่จำเป็นออก
- [ ] ทดสอบทุกฟีเจอร์ทำงานได้

---

## 🎉 หลัง Deploy สำเร็จ

✅ โปรเจคพร้อมใช้งานแล้ว!

**สิ่งที่ควรทำ**:
1. ทดสอบทุกฟีเจอร์บน production
2. แชร์ URL ให้เพื่อนทดลองใช้
3. ตรวจสอบ Analytics บน Vercel Dashboard
4. เพิ่ม custom domain (ถ้าต้องการ)
5. อัปเดต README.md ด้วย production URL

---

## 🔗 ลิงก์ที่เป็นประโยชน์

- [Vercel Documentation](https://vercel.com/docs)
- [Next.js Deployment](https://nextjs.org/docs/app/building-your-application/deploying)
- [Vercel CLI Documentation](https://vercel.com/docs/cli)
- [Custom Domains](https://vercel.com/docs/concepts/projects/custom-domains)

# 🚀 دليل Deployment للمشروع

## 📋 المتطلبات
- GitHub repository
- حساب على Railway/Render (للـ Backend)
- حساب على Vercel/Netlify (للـ Frontend)
- MongoDB Atlas (قاعدة البيانات)

## 🔧 إعداد Backend (Node.js)

### 1. Railway (مستحسن - مجاني)
1. اذهب إلى [railway.app](https://railway.app)
2. سجل دخول بـ GitHub
3. اضغط "New Project" → "Deploy from GitHub repo"
4. اختر الـ repository
5. اختر مجلد `backend`
6. أضف متغيرات البيئة:
   ```
   MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/kkhdb
   JWT_SECRET=your_super_secret_key_here
   NODE_ENV=production
   PORT=5000
   ```

### 2. Render (بديل)
1. اذهب إلى [render.com](https://render.com)
2. سجل دخول بـ GitHub
3. اضغط "New" → "Web Service"
4. اختر الـ repository
5. إعدادات:
   - Build Command: `cd backend && npm install`
   - Start Command: `cd backend && npm start`
   - Environment: Node

## 🎨 إعداد Frontend (Angular)

### 1. Vercel (مستحسن - مجاني)
1. اذهب إلى [vercel.com](https://vercel.com)
2. سجل دخول بـ GitHub
3. اضغط "New Project"
4. اختر الـ repository
5. إعدادات:
   - Framework Preset: Angular
   - Root Directory: `front/kkh`
   - Build Command: `npm run build`
   - Output Directory: `dist/kkh`

### 2. Netlify (بديل)
1. اذهب إلى [netlify.com](https://netlify.com)
2. سجل دخول بـ GitHub
3. اضغط "New site from Git"
4. اختر الـ repository
5. إعدادات:
   - Base directory: `front/kkh`
   - Build command: `npm run build`
   - Publish directory: `dist/kkh`

## 🗄️ إعداد MongoDB Atlas

1. اذهب إلى [mongodb.com/atlas](https://mongodb.com/atlas)
2. أنشئ حساب مجاني
3. أنشئ cluster جديد
4. احصل على connection string
5. أضف الـ connection string في متغيرات البيئة للـ backend

## 🔗 ربط Frontend بـ Backend

بعد deployment الـ backend، ستحتاج إلى تحديث الـ API URL في الـ frontend:

1. في `front/kkh/src/environments/environment.prod.ts`:
```typescript
export const environment = {
  production: true,
  apiUrl: 'https://your-backend-url.railway.app/api'
};
```

2. في `front/kkh/src/environments/environment.ts`:
```typescript
export const environment = {
  production: false,
  apiUrl: 'http://localhost:5000/api'
};
```

## 📧 إعداد البريد الإلكتروني

1. في Gmail، فعّل "App Passwords"
2. أنشئ App Password جديد
3. أضف متغيرات البيئة للـ backend:
```
EMAIL_USER=your-email@gmail.com
EMAIL_PASS=your-app-password
```

## ✅ خطوات التحقق

1. ✅ Backend يعمل على Railway/Render
2. ✅ Frontend يعمل على Vercel/Netlify
3. ✅ قاعدة البيانات متصلة
4. ✅ البريد الإلكتروني يعمل
5. ✅ يمكن تسجيل الدخول وإنشاء طلبات

## 🎉 تهانينا!

مشروعك الآن متاح على الإنترنت ويمكن للجميع الوصول إليه!

# Render Dashboard Configuration Guide

## 🚀 Step-by-Step: Add Environment Variables to Render

### Step 1: Go to Render Dashboard
1. Open: https://dashboard.render.com
2. Select your backend service (should be named `lendhub-backend` or similar)
3. Click on it to open settings

### Step 2: Navigate to Environment Variables
1. In the service details page, find the **Environment** section (left sidebar)
2. Click **Environment** → You'll see existing variables

### Step 3: Add All These Variables

Add each one individually by clicking "Add Environment Variable":

```
MONGODB_URI = REDACTED_SECRET

HASHPAY_API_KEY = REDACTED_SECRET

HASHPAY_API_SECRET = REDACTED_SECRET

HASHPAY_BASE_URL = https://api.hashpay.co.ke

HASHPAY_CALLBACK_URL = https://api.lendhub.render.com/api/payments/callback

HASHPAY_ENVIRONMENT = production
```

### Step 4: After Adding All Variables
1. Scroll down and click **Save** (or **Deploy**)
2. Render will **automatically redeploy** your app with the new variables

### Step 5: Test Again
1. Wait 2-3 minutes for deployment to complete
2. Try payment again
3. It should now work!

---

## ✅ Complete Environment Variables for Render

Copy and paste all of these (your current .env values):

```env
NODE_ENV=production
PORT=5000
ALLOWED_ORIGINS=https://lendhub.vercel.app,https://www.lendhub.vercel.app
ALLOWED_BASE_DOMAIN=lendhub.vercel.app
MONGODB_URI=REDACTED_SECRET
JWT_SECRET=REDACTED_SECRET
TALA_EXTRA_JWT_FALLBACK=xvzs6TGf7xKo3qZIHSGXz0cRYeI4G37c2uGosSsFufueiVnQtnUcZ2IBXBfmS3WR
JWT_EXPIRE=7d
PAYMENT_PROVIDER=hashpay
HASHPAY_API_KEY=REDACTED_SECRET
HASHPAY_API_SECRET=REDACTED_SECRET
HASHPAY_ENVIRONMENT=production
HASHPAY_BASE_URL=https://api.hashpay.co.ke
HASHPAY_CALLBACK_URL=https://api.lendhub.render.com/api/payments/callback
VAPID_PUBLIC_KEY=BDaQbOY3galc_WwK38D52o5GrXgaa01I1vWp6JgDRMWRndWTONGdQXu4T5JiJE2DXozEMb9bOreSOJfRUAplB2M
VAPID_PRIVATE_KEY=REDACTED_SECRET
VAPID_SUBJECT=mailto:admin@extracash.mkopaji.com
APP_NAME=LendHub
APP_PUBLIC_URL=https://api.lendhub.render.com
LOAN_MIN_AMOUNT=5500
LOAN_MAX_AMOUNT=150000
LOAN_INTEREST_RATE=0.1
LOAN_TERMS_DAYS=30,60,90
PROCESSING_FEE=120
PROCESSING_FEE_MIN=120
PROCESSING_FEE_MAX=3500
LOG_LEVEL=info
```

---

## 🔍 How to Verify Variables Are Set

1. In Render dashboard, go to your service
2. Click **Logs** tab
3. Look for this line in startup logs:
   ```
   [Hashpay] ✅ Hashpay configured for production
   ```
   - ✅ If you see this → Variables are correctly set
   - ❌ If you see warning → Some variables are missing

---

## ⚠️ Important Notes

- **DO NOT commit `.env` with secrets to GitHub**
- Always set sensitive values in Render dashboard, not in code
- After adding variables, Render will auto-redeploy (takes 2-3 minutes)


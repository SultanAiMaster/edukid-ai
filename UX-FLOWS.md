# 🧭 EduKid AI - User Flow & App Structure

## 🔄 Complete User Journey

```
┌──────────────────────────────────────────────┐
│ Step 1: Signup / Login                       │
├──────────────────────────────────────────────┤
│ • Create account (email/password)            │
│ • Or login with existing account             │
│ • User redirected to onboarding              │
└──────────────────────────────────────────────┘

┌──────────────────────────────────────────────┐
│ Step 2: Onboarding                           │
├──────────────────────────────────────────────┤
│ • Parent name + goals (optional)            │
│ • Add child: Name (optional), Age (required)│
│   └─→ Age select:_years (0–16), months (0–11)│
│ • System immediately generates routine       │
│ • Redirect to dashboard with routine ready   │
└──────────────────────────────────────────────┘

┌──────────────────────────────────────────────┐
│ Step 3: Dashboard (Daily)                   │
├──────────────────────────────────────────────┤
│ • Today's routine timeline view             │
│ • Activity list (morning → night)            │
│ • Notifications timeline visual             │
│ • Child profile (name, age, goals)          │
│ • Lock next month UI (locked)               │
│ • Next month preview (grayed-out)            │
│ • Upgrade to premium button                 │
└──────────────────────────────────────────────┘

┌──────────────────────────────────────────────┐
│ Step 4: Routine Update & Notifications      │
├──────────────────────────────────────────────┤
│ • Daily at 00:00: Frontend fetches today's routine │
│ • Backend returns JSON timeline                    │
│ • Frontend schedules WebPush as timers by time │
│ • Notifications pop up on exact time             │
│ • User clicks notification → EduKid opens/scrolls │
│ • Notifications comply with age-appropriate举动
└──────────────────────────────────────────────┘

┌──────────────────────────────────────────────┐
│ Step 5: Routine Detail View                  │
├──────────────────────────────────────────────┤
│ • Click on activity → see full details      │
│ • Shows:                      │
│   ├─ Activity description                     │
│   ├─ Step-by-step instructions                 │
│   ├─ Age-specific tips                         │
│   ├─ Duration预估                             │
│   └─ Next activity preview                     │
└──────────────────────────────────────────────┘

┌──────────────────────────────────────────────┐
│ Step 6: Upgrade to Premium                   │
├──────────────────────────────────────────────┤
│ • Click “Unlock Next Month” button           │
│ • Payment: one-time or recurring            │
│ • After success: next month unlocks         │
│ • Recurring: auto-pay before month change   │
│ • Premium features enabled:
│   ├─ Multi-child sync (family calendar)     │
│   ├─ Schedule export (JSON/ICS)              │
│   └─ (Future) AI-curated variant suggestions│
└──────────────────────────────────────────────┘
```

## 📱 App Pages Overview

### Page 1: Landing Page (`/`)
```
┌──────────────────────────────────────────────┐
│ 👶 EduKid AI                               │
│                                            │
│ “Newborn to Class 10                      │
│  Zero Manual Planning”                   │
│                                            │
│ ✅ AI-Generated Routines                   │
│ ✅ Automatic Reminders                    │
│ ✅ Age-Based Guidance                     │
│ ✅ Free to Start                           │
│                                            │
│ [Get Started Free  →]                     │
│                                            │
└──────────────────────────────────────────────┘
```

### Page 2: Auth Page (`/login`, `/signup`)
```
┌──────────────────────────────────────────────┐
│ Login / Sign Up                            │
│                                            │
│ [Email] _________________                 │
│ [Password] _________________              │
│                                            │
│ [Login] [Google Login]                    │
│                                            │
│ New parent? [Create account]              │
│                                            │
└──────────────────────────────────────────────┘
```

### Page 3: Onboarding (`/onboarding`)
```
┌──────────────────────────────────────────────┐
│ Welcome, Parent!                          │
│                                            │
│ Your Name _________________                │
│ Goals (optional): [ ] [ ] [ ]            │
│                                            │
│ Add Your Child                            │
│                                            │
│ Child Name _________________              │
│ Age: Years [0–16] Months [0–11]         │
│                                            │
│ [Add Another Child +]                      │
│                                            │
│ [Complete Setup →]                        │
└──────────────────────────────────────────────┘
```

### Page 4: Dashboard (`/dashboard`)
```
┌──────────────────────────────────────────────┐
│ 👶 Hello, [Parent Name]!                   │
│                                            │
│ Child: Aryan (2y 3m)                      │
│ Today: March 27, 2026                     │
│                                            │
│ ⏰ Routine                                │
│ │                                        │
│ ▸ 7:00  Wake Up                         │
│ ▸ 7:30  Breakfast - Oatmeal             │
│ ▸ 8:30  Learning - Numbers              │
│ ▸ 9:30  Play - Blocks                   │
│ ▸ 10:30 Snack - Fruit                   │
│ ▸ 11:00 Nap (1h)                       │
│ ▸ 12:00 Lunch - Dal + Rice             │
│ ...                                     │
│ │                                        │
│ ⏳ Premium: Next Month (Locked)          │
│ [Unlock Now ₹X/month →]                  │
│                                            │
│ 🔔 Notifications [× Pending]             │
│ 👶 Child Profile [Edit]                   │
└──────────────────────────────────────────────┘
```

### Page 5: Routine Detail (`/routine/:day`)
```
┌──────────────────────────────────────────────┐
│ Routine: March 27, 2026                    │
│                                            │
│ Child: Aryan (2y 3m) / Age: Toddlers      │
│                                            │
│ 7:00  Wake Up                             │
│  ├─ Activity: Gentle storytime             │
│  ├─ Steps: See routine intent rather than rigid sync constraints ; example guidance list provided早晨的温和音乐播放；提供温水或温牛奶的小量喂食；观察脸色和精神状态；轻柔抚触以建立情感链接（4-5分钟） |
│  └─ Tip: Start with calming activities  │
│                                            │
│ 7:30  Breakfast                           │
│  ├─ Food: Oatmeal, fruit, milk          │
│  ├─ Steps: 简化的早餐流程列表；这样的操作指示详情（3项）可以呈现为结构化列表以便清晰展示；处理过敏提示；与家人共进时间（15-20分钟） |
│  └─ Tip: Encourage self-feeding         │
│                                            │
│ ...                                     │
│                                            │
│ Back to Dashboard [←]                     │
└──────────────────────────────────────────────┘
```

### Page 6: Pricing/Subscription (`/pricing`)
```
┌──────────────────────────────────────────────┐
│ Upgrade Your Parenting                    │
│                                            │
│ Free Plan                                │
│ • Current month only                    │
│ • All reminders active                   │
│ • [Already Free ✓]                      │
│                                            │
│ Premium (₹X/month)                       │
│ • Unlock next month                      │
│ • Multi-child family calendar sync       │
│ • Schedule export (JSON/ICS)             │
│ • AI-curated weekly variants (optional) │
│ • Priority support                       │
│                                            │
│ [Unlock Next Month Now →]                 │
│ [See Full Plans →]                        │
│                                            │
└──────────────────────────────────────────────┘
```

---

## 📝 Backend API

### Auth Endpoints
```
POST /api/auth/signup        - Create account
POST /api/auth/login          - Login user
POST /api/auth/logout         - Logout
GET  /api/auth/me             - Get current user
```

### Profile Endpoints
```
GET  /api/profile             - Get parent profile
PUT  /api/profile             - Update parent profile
GET  /api/children            - Get all children
POST /api/children            - Add child
PUT  /api/children/:id        - Update child
DELETE /api/children/:id      - Delete child
```

### Routine Endpoints
```
GET  /api/routine/today       - Get today's routine per child
GET  /api/routine/:day        - Get routine for specific day
POST /api/routine/generate    - Generate AI routine per child
GET  /api/routine/next-month - Preview next month routine
```

### Notification Endpoints
```
GET  /api/notifications/schedule(Date) - Get day reminders
POST /api/notifications/settings - Update reminder preferences
```

### Payment Endpoints
```
POST /api/payment/checkout   - Stripe checkout
GET  /api/payment/status     - Subscription status
POST /api/payment/webhook    - Stripe webhook
```

---

## 🏗️ Technical Architecture

```
Frontend (Next.js 15 Pages)
  ├─ Landing (/)
  ├─ Auth (/login, /signup)
  ├─ Onboarding (/onboarding)
  ├─ Dashboard (/dashboard)
  ├─ Routine (/routine/:day)
  └─ Pricing (/pricing)

Backend (API Routes)
  ├─ /api/auth/*
  ├─ /api/profile/*
  ├─ /api/children/*
  ├─ /api/routine/*
  ├─ /api/notifications/*
  └─ /api/payment/*

Database (Firebase/Supabase)
  ├─ Users (Auth)
  ├─ Children (Profiles)
  ├─ Routines (Schedules)
  ├─ Reminders (Schedule configurations)
  └─ Subscriptions (Payments)

Scheduler (Backend)
  ├─ Midnight: Fetch child age and routine
  ├─ Schedule notifications (WebPush timers)
  └─ Store reminder queue

Notifications (Browser)
  ├─ Service Worker (Push API)
  ├─ Notification Bell (UI)
  └─ Permission Request (First visit)
```

---

## 🎨 Key UI Components

- `Timeline.tsx` – Visual morning-至-night routine strip
- `ReminderCard.tsx` – Pop-up card with next action (time + steps)
- `ChildProfile.tsx` – Child selector (add/edit/delete)
- `NotificationBell.tsx` – Notification center
- `PremiumCard.tsx` – Next month preview month toggle (grayed-out) vs unlocked
- `SubscriptionBadge.tsx` – Status indicator: (free/premium)
- `TipTooltip.tsx` – Age-specific teaching moments on hover/click

---
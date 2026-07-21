# 💳 RupeeCraft Ledger

> **A Light-Themed, Tactile Skeuomorphic Web Application for Daily Financial Tracking, Predictive Analytics, and Market Intelligence in Sri Lanka.**

https://rupeecraft-ledger.netlify.app/

<img width="1917" height="916" alt="Screenshot 2026-07-21 085521" src="https://github.com/user-attachments/assets/2a1a658f-5e4a-4115-97ab-5fca99db7ac2" />

---

## 📌 Table of Contents
1. [Executive Summary](#-executive-summary)
2. [System Architecture](#-system-architecture)
3. [Key Feature Breakdown](#-key-feature-breakdown)
4. [UI/UX Design Specification (Skeuomorphic Light Theme)](#-uiux-design-specification)
5. [Data Models & Schema](#-data-models--schema)
6. [Core Algorithms & Intelligence Engine](#-core-algorithms--intelligence-engine)
7. [API Specifications](#-api-specifications)
8. [Installation & Local Setup](#-installation--local-setup)
9. [Future Roadmap](#-future-roadmap)

---

## 📖 Executive Summary

**RupeeCraft Ledger** is a personal financial management web application designed to bring back the physical feel of traditional accounting ledgers while leveraging modern web technologies and AI predictions.

Tailored for users needing granular control over daily income and expenditures, the system incorporates:
*   **Tactile Light Skeuomorphism:** Embossed cards, soft inner shadow inputs, leather-textured headers, and physical paper textures.
*   **Smart Reserve Pots:** Dedicated visual savings vaults with automated allocation logic.
*   **Visual Health Calendar:** Day-by-day color-coded heatmap tracking daily spending vs. income.
*   **Localized News & Analytics:** Real-time extraction of Sri Lankan financial news (fuel/LPG prices, VAT/tax policies) integrated with predictive inflation models.
*   **PDF Archival Engine:** Vector-rendered, paper-styled financial reports exportable for record keeping.

---

## 🏗 System Architecture

The application follows a clean **Client-Side First (SPA)** architecture with modular service layers for external AI integrations, localized search grounding, and client-side persistence.


```

┌───────────────────────────────────────────────────────────────────────┐
│                        PRESENTATION LAYER (UI/UX)                       │
│   Skeuomorphic Light Design • Tailwind CSS / CSS Modules • Lucide Icons │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │
                                    ▼
┌────────────────────────────────────────────────────────────────────────┐
│                   APPLICATION LOGIC & STATE ENGINE                      │
│   ┌───────────────────┬──────────────────────┬──────────────────────┐  │
│   │ Transaction Engine│ Reserve Allocation   │ Budget Thresholds    │  │
│   ├───────────────────┼──────────────────────┼──────────────────────┤  │
│   │ Calendar Engine   │ PDF Generation Engine│ Predictive Analytics │  │
│   └───────────────────┴──────────────────────┴──────────────────────┘  │
└───────────────────────────────────┬────────────────────────────────────┘
                           │
┌──────────────────────────┼──────────────────────────┐
▼                          ▼                          ▼
┌──────────────────┐      ┌──────────────────┐      ┌──────────────────┐
│ PERSISTENCE LAYER│      │ REAL-TIME NEWS   │      │ AI PREDICTION    │
│  IndexedDB /     │      │ GROUNDING API    │      │ ENGINE           │
│  LocalStorage /  │      │ (Gemini Search / │      │ (Gemini Flash)   │
│  PostgreSQL      │      │ Local RSS Feeds) │      │                  │
└──────────────────┘      └──────────────────┘      └──────────────────┘

```

### Layer Responsibilities

1. **Presentation Layer**: Implements a light-mode skeuomorphic design system featuring physical paper textures, debossed inputs, tactile toggle switches, pressable rubberized buttons, and physical stamps.
2. **State & Logic Engine**: Calculates net balances, applies spending limit warnings, categorizes monthly cash flows, and builds daily health scores for the calendar view.
3. **Intelligence Layer**: Interacts with LLM/Search engines to summarize real-time economic conditions in Sri Lanka and project financial runway based on historical burn rates.
4. **Persistence Layer**: Handles atomic writes for transactions, budget configurations, and reserve pot allocations.

---

## ✨ Key Feature Breakdown

### 1. Daily Transaction & Cash Flow Ledger
*   **Instant Entry:** Log daily income or expense entries with category, payment method, date, and optional tags/notes.
*   **Physical Stamp Feedback:** Visual "APPROVED", "PAID", or "OVER-BUDGET" ink stamps generated dynamically on transaction receipt components.
*   **Filters & Search:** Real-time filtering by date range, category, type (income/expense), or keyword.

### 2. Spending Limits & Reserve Pots
*   **Thermometer Progress Bars:** Visual limit meters that change from warm teal → amber → deep crimson as spending approaches maximum monthly allocations.
*   **Visual Savings Jars:** Dedicated reserve pots (e.g., Emergency Vault, Goal Reserves) that isolate cash from discretionary balances.

### 3. Visual Health Calendar
*   Each calendar day displays a soft neumorphic backlight glow based on net daily cash flow:
    *   🟢 **Green Glow:** Net positive day (Income > Expense).
    *   🔴 **Red Glow:** High expenditure day (Exceeds daily average threshold).
    *   🟡 **Yellow Glow:** Moderate expenditure within safe limits.
    *   ⚪ **Neutral Gray:** No spending / zero net balance.
*   **Hover/Tap Detail:** Quick inspection modal showing itemized breakdown for that day.

### 4. PDF Report Generator
*   Generates formal, printable monthly summary statements.
*   Includes cash flow pie charts, category breakdowns, reserve deposits, and risk metrics rendered in high-resolution PDF format using vector canvas tools (e.g., `jspdf` + `html2canvas`).

### 5. Sri Lanka Financial Intel Tab
*   Fetches and summarizes real-time financial news specifically impacting Sri Lankan consumers:
    *   **Fuel & Energy:** Petrol/Diesel (Ceypetco, LIOC, Sinopec) revision alerts.
    *   **LPG & Power:** Litro and Laugfs gas prices, electricity tariffs.
    *   **Fiscal Policies:** Central Bank (CBSL) interest rate revisions, VAT changes, income tax brackets.
*   Provides impact tags: `High Inflation Risk`, `Cost Reduction`, `Policy Change`.

### 6. Predictive Analysis Tab ("FutureSight Engine")
*   Calculates 30, 60, and 90-day cash flow projections based on historical $n$-month moving averages.
*   Computes **Financial Runway** (Months of remaining capital under current burn rate).
*   Generates personalized actionable advice for spending adjustments.

---

## 🎨 UI/UX Design Specification

### Design Style: Modern Light Skeuomorphism

*   **Color Palette:**
    *   **Base Surface:** Off-white / Cream `#F9F8F3` (Parchment background feel).
    *   **Card Surface:** Clean Paper `#FFFFFF` with double-layered subtle drop shadows (`box-shadow: 0 10px 25px -5px rgba(0,0,0,0.05), inset 0 1px 0 rgba(255,255,255,1)`).
    *   **Primary Accents:**
        *   Emerald Green (`#059669` / `#10B981`) for Income & Reserves.
        *   Crimson Red (`#DC2626` / `#EF4444`) for Expenditures & Warnings.
        *   Warm Amber (`#D97706`) for Limits & Approaching Thresholds.
        *   Royal Slate (`#1E293B`) for Primary Typography.
*   **Typography:** Clean sans-serif primary font (`Inter`, `System-UI`) paired with tabular monospaced numbers (`JetBrains Mono`, `Roboto Mono`) for precise financial alignment.
*   **Interactive Elements:**
    *   **Buttons:** Soft bevels with active `transform: translateY(2px)` and inset shadows to emulate physical keypresses.
    *   **Inputs:** Inset shadows (`inset 0 2px 4px rgba(0,0,0,0.06)`) simulating cut-out form fields.

---

## 🗄 Data Models & Schema

### 1. Transaction Model (`Transaction`)
```typescript
interface Transaction {
  id: string;
  type: 'INCOME' | 'EXPENSE';
  amount: number; // Stored in minor units or double precision float
  currency: 'LKR' | 'USD' | string;
  category: string; // e.g., 'Groceries', 'Utilities', 'Salary', 'Fuel'
  paymentMethod: 'CASH' | 'CARD' | 'BANK_TRANSFER' | 'MOBILE_PAY';
  date: string; // ISO 8601 (YYYY-MM-DD)
  notes?: string;
  isRecurring: boolean;
  createdAt: string;
}

```

### 2. Budget & Spending Limit Model (`BudgetLimit`)

```typescript
interface BudgetLimit {
  categoryId: string;
  monthlyLimit: number;
  alertThresholdPercentage: number; // e.g., 80 for 80% warning
}

```

### 3. Reserve Pot Model (`ReservePot`)

```typescript
interface ReservePot {
  id: string;
  name: string;
  targetAmount: number;
  currentAmount: number;
  icon: string;
  colorHex: string;
}

```

### 4. Daily Health Aggregator (`CalendarDaySummary`)

```typescript
interface CalendarDaySummary {
  date: string; // YYYY-MM-DD
  totalIncome: number;
  totalExpense: number;
  netBalance: number;
  healthStatus: 'GREAT' | 'MODERATE' | 'HIGH_SPEND' | 'NEUTRAL';
}

```

---

## 🧮 Core Algorithms & Intelligence Engine

### 1. Health Calendar Grading Logic

For any given day $d$:

$$\text{Net Balance}(d) = \sum \text{Income}(d) - \sum \text{Expense}(d)$$

$$\text{Daily Average Expense}(\bar{E}) = \frac{\sum_{i=1}^{M} \text{Expense}(i)}{\text{Days in Month}}$$

* **If** $\text{Net Balance}(d) > 0$: Grade = `GREAT` (Green)
* **Else If** $\text{Expense}(d) > 1.5 \times \bar{E}$: Grade = `HIGH_SPEND` (Red)
* **Else If** $\text{Expense}(d) > 0$: Grade = `MODERATE` (Yellow)
* **Else**: Grade = `NEUTRAL` (Gray)

### 2. Predictor Algorithm (Weighted Moving Average)

Predicting future monthly expenditure ($\hat{E}_{t+1}$) given historical monthly expenses $E_t, E_{t-1}, E_{t-2}$:

$$\hat{E}_{t+1} = (w_1 \cdot E_t) + (w_2 \cdot E_{t-1}) + (w_3 \cdot E_{t-2})$$

*Where weights prioritize recent spending behavior ($w_1 = 0.5, w_2 = 0.3, w_3 = 0.2$).*

---

## 📡 API Specifications

### Real-Time Financial News Retrieval

* **Endpoint:** Internal Serverless Worker / Direct Grounded Fetch
* **Query Focus:** `Sri Lanka fuel prices, Litro gas, electricity tariff, CBSL interest rate, VAT tax updates`
* **Response Format:**

```json
{
  "lastUpdated": "2026-07-21T00:00:00Z",
  "articles": [
    {
      "id": "news_001",
      "title": "Ceylon Petroleum Corporation Revises Auto Diesel Rates",
      "category": "Fuel / Energy",
      "summary": "CPC announced a revision in retail fuel prices effective midnight. Auto Diesel decreased by LKR 10 per liter.",
      "impact": "POSITIVE",
      "source": "Local News / Grounded Search",
      "date": "2026-07-20"
    }
  ]
}

```

---

## 💻 Installation & Local Setup

### Prerequisites

* Node.js (`v18.x` or higher)
* npm or yarn package manager

### Steps

1. **Clone the Repository**
```bash
git clone [https://github.com/your-username/rupeecraft-ledger.git](https://github.com/your-username/rupeecraft-ledger.git)
cd rupeecraft-ledger

```


2. **Install Dependencies**
```bash
npm install

```


3. **Configure Environment Variables**
Create a `.env.local` file in the root directory:
```env
VITE_APP_TITLE="RupeeCraft Ledger"
VITE_DEFAULT_CURRENCY="LKR"
VITE_GEMINI_API_KEY="YOUR_GEMINI_API_KEY"

```


4. **Run Development Server**
```bash
npm run dev

```


Open `http://localhost:5173` in your browser.
5. **Build for Production**
```bash
npm run build

```



---

## 🚀 Future Roadmap

* [ ] **Bank SMS Auto-Parsing:** Read incoming transaction notifications via browser Web API / PWA permissions to auto-fill entry forms.
* [ ] **Multi-Currency Support:** Auto-convert USD/EUR/GBP expenses into LKR based on real-time exchange rates.
* [ ] **Export to CSV/Excel:** Enable tabular data dumps for tax preparation and external accounting software.
* [ ] **Offline Sync (PWA):** Full offline capability with Service Worker caching and automatic background sync when connection returns.

---

*Crafted for precision, elegance, and financial mastery.* 🇱🇰

```

```

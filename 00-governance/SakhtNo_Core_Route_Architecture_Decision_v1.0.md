# SakhtNo Core Route Architecture Decision

**Document ID:** `SN-DEC-001`  
**Version:** `1.0`  
**Status:** Superseded  
**Decision Type:** Business & Financial Architecture  
**Impact:** Major  
**Approval Date:** 2026-09-10  
**Superseded By:** `SN-DEC-001 v1.1`  
**Affected Baselines:** Vision / Business Model / Financial Model / Operating Model / Product & PRD / Architecture

## 1. مسئله

معماری قبلی ساخت‌نو سه مسیر اصلی را با عناوینی نظیر **B2C/C2B، B2B و Project** تعریف می‌کرد. این طبقه‌بندی دو مفهوم متفاوت را با یکدیگر ترکیب می‌کرد: B2C/B2B بیانگر نوع رابطه یا Actor/Customer Archetype هستند، در حالی که Project بیانگر ماهیت عملیاتی و اقتصادی یک فعالیت است.

در نتیجه یک مشتری واحد می‌تواند بسته به نیاز خود در چند وضعیت متفاوت قرار گیرد و Customer Type به‌تنهایی قادر به تعیین Route مناسب نیست. بنابراین Customer Type نمی‌تواند مبنای پایدار Route Architecture ساخت‌نو باشد.

## 2. تصمیم اصلی

> **Route در ساخت‌نو بر اساس ماهیت اقتصادی و عملیاتی نیاز و Transaction تعیین می‌شود؛ نه بر اساس نوع مشتری، محصول مالی، تأمین‌کننده مالی یا نقطه ورود کاربر.**

پنج مفهوم زیر از یکدیگر مستقل نگه داشته می‌شوند:

- Actor / Customer Archetype
- Need / Intent
- Operational Route
- Financial Product
- Financial Provider

ارتباط آنها از طریق Need Intelligence، Transaction Context و Eligibility برقرار می‌شود.

## 3. چهار Route اصلی ساخت‌نو

### R1 — Procurement & Consumption

**هدف:** تأمین کالا یا خدمت برای مصرف یا یک نیاز مشخص.

نمونه‌ها شامل خرید مصالح، تجهیزات، خدمات، نصب، تعمیر و بازسازی محدود است.

**Core Objects:** Order / Service Case / Delivery / Acceptance

**Financial Product Families:** Purchase Credit / Installment Purchase / BNPL / Consumer Credit / Merchant Finance / Service Finance / Closed-loop Credit

### R2 — Trade & Working Capital

**هدف:** پشتیبانی از تجارت، خرید و فروش تکرارشونده و نیازهای سرمایه در گردش فعالان زنجیره ساخت.

**Core Objects:** Business Account / PO / Invoice / Trade / Receivable / Inventory

**Financial Product Families:** Working Capital / Revolving Credit / Trade Credit / PO Finance / Invoice Finance / Receivables Finance / Factoring / Reverse Factoring / Supplier Finance / Supply Chain Finance / Inventory Finance / Distributor & Dealer Finance

### R3 — Project & Development

**هدف:** ایجاد، توسعه، اجرا، تکمیل یا بازسازی پروژه‌ای که دارای ساختار پروژه، قرارداد، بودجه، پیشرفت و کنترل است.

**Core Objects:** Project / Contract / WBS / Work Package / Progress / QC / Certificate

**Financial Product Families:** Construction Finance / Project Facility / Progress-Based Finance / Contractor Finance / Certificate Finance / Project Procurement Finance / Project SCF / Development Finance / Bridge Finance / Milestone Finance / SPV & Structured Project Finance

### R4 — Property & Asset

**هدف:** تملک، نگهداری، بهره‌برداری، بازتأمین مالی یا آزادسازی ارزش اقتصادی زمین و دارایی ملکی.

**Core Objects:** Property / Land / Asset / Ownership / Valuation / Lien / Collateral

**Financial Product Families:** Land Acquisition Finance / Property Acquisition Finance / Mortgage / Asset-backed Finance / Refinance / Equity Release / Sale & Leaseback / Property-related Leasing

## 4. Route با Customer Segment یکسان نیست

Actorهای مختلف می‌توانند وارد Routeهای مختلف شوند. Individual می‌تواند در R1، R3 یا R4 باشد؛ Supplier می‌تواند در R2 فعالیت کند و در پرونده‌ای دیگر از R4 استفاده کند؛ Contractor می‌تواند برای سرمایه در گردش وارد R2 و برای یک قرارداد پروژه وارد R3 شود؛ Developer می‌تواند برای تملک زمین در R4، برای اجرای پروژه در R3 و برای فعالیت تجاری عمومی در R2 قرار گیرد.

> **Actor identifies who the party is; Route identifies what economic/operational activity is being performed.**

## 5. Route با Financial Product یکسان نیست

Financial Product یک Route مستقل ایجاد نمی‌کند. BNPL، SCF، Mortgage، Working Capital، Project Finance و سایر ابزارها، محصول یا سازوکار مالی قابل اتصال به Route هستند.

یک Financial Product در صورت داشتن Eligibility و Underlying Transaction مناسب می‌تواند در بیش از یک Route قابل استفاده باشد. بنابراین Product Catalog باید مستقل از Route Catalog نگهداری شود و Mapping میان آنها از طریق Rules انجام شود.

## 6. Route با Provider یکسان نیست

بانک، مؤسسه اعتباری، صندوق، Leasing، Fintech، Investor، Supplier Credit Provider یا سایر منابع مالی، Provider محسوب می‌شوند. اضافه‌شدن یا حذف Provider نباید Route Architecture را تغییر دهد.

ساخت‌نو باید بتواند محصولات چند Provider را در یک Financial Product Catalog استاندارد دریافت و بر اساس Eligibility و Transaction Context مقایسه کند.

## 7. Route با Journey یکسان نیست

یک Customer Journey می‌تواند شامل یک یا چند Route باشد. برای مثال Land Acquisition → Construction → Sale/Refinance می‌تواند به صورت R4 → R3 → R4 اجرا شود و Property Acquisition → Major Renovation می‌تواند R4 → R3 باشد.

Route Transition مجاز است، اما Transaction History، Evidence، Contract و Financial Exposure باید قابل ردیابی باقی بمانند.

## 8. Route با Homepage Entry Point یکسان نیست

چهار Route بخشی از Internal Business Architecture ساخت‌نو هستند و نباید الزاماً به‌صورت چهار انتخاب مستقیم به کاربر نمایش داده شوند. Homepage و Need Discovery باید از Intent و Need کاربر شروع شود.

ورودی می‌تواند از طریق Search، Guided Drill-down، AI Conversation، Document Upload و Existing Project Context ایجاد شود. سپس Need Intelligence ساختار لازم برای Route Classification را ایجاد می‌کند.

## 9. Target Decision Flow

**Actor + Intent + Context + Evidence**

→ **Need Intelligence**

→ **Transaction Formation / Identification**

→ **Route Classification**

→ **Financing Need**

→ **Eligibility**

→ **Financial Product Matching**

→ **Multi-provider Matching**

→ **Offer**

→ **Journey**

→ **Controlled Execution / Payment / Settlement**

در صورت نبود شرایط کافی، خروجی می‌تواند **Not Ready Yet** باشد و سیستم باید Preparation Journey مناسب را ارائه کند.

## 10. Marketplace Position

Marketplace یکی از قابلیت‌های ساخت‌نو برای **Transaction Formation** است و Route مستقل یا تعریف کل پلتفرم محسوب نمی‌شود.

در برخی Journeyها Transaction از Marketplace ساخت‌نو ایجاد می‌شود و در برخی دیگر Transaction از قبل وجود دارد؛ مانند Invoice، Contract، Property، Project یا Supplier موجود. بنابراین ورود به فرآیند تأمین مالی نباید به ایجاد Transaction در Marketplace وابسته باشد.

## 11. Embedded Finance

Embedded Finance یک Route مستقل یا نام محصول مشتری نیست. Embedded Finance روش قرار دادن قابلیت‌های مالی در متن یک Transaction واقعی و قابل اثبات است.

هر Financing Offer باید به Underlying Need، Transaction، Evidence و Repayment Logic قابل ردیابی باشد.

## 12. استقلال Routeها

هر Route باید حداقل استقلال لازم را در موارد زیر داشته باشد:

- State Model
- Contract Model
- Evidence Requirements
- Risk Policy
- Economic Unit / P&L
- Financial Ledger Context
- Eligibility Rules

در عین حال Routeها از Core مشترک ساخت‌نو استفاده می‌کنند:

- Identity & Authority
- Construction Network
- Evidence Ledger
- Risk Infrastructure
- Financial Product Catalog
- Payment & Settlement
- Asset Intelligence
- Data / IAM / Event / Audit Infrastructure

## 13. قواعد Classification

Classification باید حداقل بر اساس عوامل زیر انجام شود:

- Underlying Economic Activity
- Transaction Object
- Purpose of Funding
- Source of Repayment
- Lifecycle
- Evidence Structure

Customer Type می‌تواند بر Eligibility اثر بگذارد، اما به‌تنهایی Route را تعیین نمی‌کند.

## 14. Boundary Rule

اگر یک Need به چند Route مرتبط باشد:

> **Primary Route بر اساس Transaction اصلی و Purpose اصلی تعیین می‌شود و سایر Routeها به‌عنوان Linked Context یا Route Transition ثبت می‌شوند.**

مثال: خرید آسانسور برای یک Project موجود دارای Need = Procurement، Context = Project، Primary Route = R3 و Financing Need = Project Procurement Finance است. صرف وجود Purchase آن را الزاماً وارد R1 نمی‌کند.

## 15. Architectural Extensibility

هدف این چهار Route پوشش فضای اصلی **Construction Commerce, Finance, Project Execution and Property/Asset Finance** است.

محصول مالی جدید، بانک جدید، نوع مشتری جدید یا کانال جدید نباید به‌تنهایی باعث ایجاد Route پنجم شود.

Route جدید تنها زمانی مجاز است که یک فعالیت اقتصادی/عملیاتی جدید دارای Transaction Object مستقل، Lifecycle مستقل، State Model مستقل، Risk/Evidence Model مستقل و Economic Logic مستقل باشد و در چهار Route موجود قابل مدل‌سازی نباشد.

## 16. اثر تصمیم بر Baseline موجود

تصویب این Decision یک **Major Architecture Change** محسوب می‌شود.

در نتیجه اسناد زیر باید وارد چرخه Major Review شوند:

- Vision v1.x → Vision v2.0
- Business Model v3.x → Business Model v4.0
- Financial Model v2.x → Financial Model v3.0

Operating Model نیز پس از تثبیت سه سند فوق برای Impact Assessment و در صورت لزوم Major Revision بررسی می‌شود.

نسخه‌های Current موجود تا زمان تصویب نسخه جایگزین، Current باقی خواهند ماند.

## 17. تصمیمات تثبیت‌شده

**D1.** ساخت‌نو دارای چهار Route اصلی در سطح Business Architecture است.

**D2.** Route بر اساس ماهیت اقتصادی و عملیاتی Transaction تعیین می‌شود، نه Customer Type.

**D3.** Customer Archetype، Need، Route، Financial Product و Provider مفاهیم مستقل هستند.

**D4.** Financial Products زیر Routeها Mapping می‌شوند ولی خودشان Route نیستند.

**D5.** Multi-provider Finance جزء معماری است و Provider مستقل از Route است.

**D6.** یک Journey می‌تواند از چند Route عبور کند.

**D7.** Homepage و Need Discovery بر اساس Intent طراحی می‌شوند، نه نمایش مستقیم Route Architecture.

**D8.** Marketplace یک Transaction Formation Capability است، نه تعریف کل ساخت‌نو و نه شرط ورود به Finance.

**D9.** Embedded Finance روش ارائه Finance در متن Transaction است، نه Route مستقل یا Product Brand.

**D10.** اضافه‌شدن Financial Product، Provider، Customer Type یا Channel جدید به‌تنهایی مجوز ایجاد Route جدید نیست.

## 18. Approval

این Decision در تاریخ 2026-09-10 توسط Product Owner تأیید و به‌عنوان مبنای بازنگری Major اسناد مرجع ساخت‌نو تثبیت شد.

این نسخه با `SN-DEC-001 v1.1` تکمیل و جایگزین شده است.

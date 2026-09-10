# SakhtNo Core Route Architecture Decision

**Document ID:** `SN-DEC-001`  
**Version:** `1.1`  
**Status:** Superseded  
**Decision Type:** Business & Financial Architecture  
**Impact:** Minor clarification of approved architecture  
**Approval Date:** 2026-09-10  
**Superseded Date:** 2026-09-10  
**Superseded By:** `SN-DEC-001 v2.0`  
**Supersedes:** `SN-DEC-001 v1.0`  
**Affected Baselines:** Vision / Business Model / Financial Model / Operating Model / Product & PRD / Architecture

## 1. مسئله

معماری قبلی ساخت‌نو سه مسیر اصلی را با عناوینی نظیر **B2C/C2B، B2B و Project** تعریف می‌کرد. این طبقه‌بندی دو مفهوم متفاوت را با یکدیگر ترکیب می‌کرد: B2C/B2B بیانگر نوع رابطه یا Actor/Customer Archetype هستند، در حالی که Project بیانگر ماهیت عملیاتی و اقتصادی یک فعالیت است.

در نتیجه یک مشتری واحد می‌تواند بسته به نیاز خود در چند وضعیت متفاوت قرار گیرد و Customer Type به‌تنهایی قادر به تعیین Route مناسب نیست. همچنین لازم است Marketplace، Logistics، Fulfillment، Data Gathering، Inspection و سایر خدمات اکوسیستم به‌صورت صریح از Routeها تفکیک شوند تا توسعه قابلیت‌های آینده باعث آشفتگی Route Architecture نشود.

## 2. تصمیم اصلی

> **Route در ساخت‌نو بر اساس ماهیت اقتصادی و عملیاتی نیاز و Transaction تعیین می‌شود؛ نه بر اساس نوع مشتری، محصول مالی، تأمین‌کننده مالی، سرویس اکوسیستم یا نقطه ورود کاربر.**

ابعاد زیر مستقل نگه داشته می‌شوند:

- Actor / Customer Archetype
- Need / Intent
- Operational Route
- Ecosystem Capability / Service
- Financial Product
- Financial Provider

ارتباط آنها از طریق Need Intelligence، Transaction Context، Evidence و Eligibility برقرار می‌شود.

## 3. چهار Route اصلی ساخت‌نو

### R1 — Procurement & Consumption

**هدف:** تأمین کالا یا خدمت برای مصرف یا یک نیاز مشخص.

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

Actorهای مختلف می‌توانند وارد Routeهای مختلف شوند. Customer Type می‌تواند بر Eligibility، Risk و Journey اثر بگذارد، اما به‌تنهایی Route را تعیین نمی‌کند.

> **Actor identifies who the party is; Route identifies what economic/operational activity is being performed.**

## 5. Route با Financial Product یکسان نیست

Financial Product یک Route مستقل ایجاد نمی‌کند. Product Catalog باید مستقل از Route Catalog نگهداری شود و Mapping میان آنها بر اساس Transaction Context، Eligibility، Risk و Provider Rules انجام شود.

## 6. Route با Provider یکسان نیست

بانک، مؤسسه اعتباری، صندوق، Leasing، Fintech، Investor، Supplier Credit Provider یا سایر منابع مالی، Provider محسوب می‌شوند. اضافه‌شدن یا حذف Provider نباید Route Architecture را تغییر دهد.

## 7. Route با Journey یکسان نیست

یک Customer Journey می‌تواند شامل یک یا چند Route باشد. Route Transition مجاز است، اما Transaction History، Evidence، Contract، Exposure و Settlement باید قابل ردیابی باقی بمانند.

## 8. Route با Homepage Entry Point یکسان نیست

چهار Route بخشی از Internal Business Architecture ساخت‌نو هستند و نباید الزاماً به‌صورت چهار انتخاب مستقیم به کاربر نمایش داده شوند. Homepage و Need Discovery باید از Intent و Need کاربر شروع شود.

## 9. Marketplace & Network Position

Marketplace در ساخت‌نو **لایه کشف، تطبیق و شکل‌دهی معامله برای کالا، خدمات و ارائه‌دهندگان اکوسیستم** است.

Marketplace می‌تواند شامل حداقل دو حوزه اصلی باشد:

- **Goods Marketplace** برای مصالح، تجهیزات، قطعات، ماشین‌آلات و سایر اقلام مرتبط با ساخت؛
- **Services Marketplace** برای خدمات فنی، اجرایی، نصب، تعمیر، طراحی، مهندسی، بازرسی، آزمایشگاه، حمل‌ونقل، ارزیابی و سایر خدمات تخصصی.

Marketplace می‌تواند Transaction را ایجاد، تکمیل یا برای آن Counterparty مناسب پیدا کند، اما:

> **Marketplace یک Route مستقل نیست و استفاده از سایر قابلیت‌های ساخت‌نو الزاماً به تشکیل Transaction در Marketplace وابسته نیست.**

Transaction ممکن است از قبل در قالب Invoice، PO، Contract، Project، Property، Supplier Relationship یا سایر اشیای عملیاتی وجود داشته باشد.

## 10. Ecosystem Capability Layer

ساخت‌نو علاوه بر Routeها، مجموعه‌ای از قابلیت‌ها و خدمات Cross-Route دارد که برای تشکیل، اجرا، اثبات، حفاظت، پرداخت یا تکمیل Transaction استفاده می‌شوند.

نمونه‌های اصلی:

- Goods Marketplace
- Services Marketplace
- Supplier / Contractor Network
- Logistics & Fulfillment
- Inspection & Quality Services
- Data Gathering & Field Evidence
- Professional Services
- Document & Contract Services
- Valuation & Asset Services
- Payment & Collection Services

در آینده قابلیت‌هایی مانند Insurance، Warranty، Escrow، Equipment Rental، Warehousing، Laboratory Services، Surveying، BIM Services، Legal Services، Maintenance، Energy Services، Waste Management، Asset Management و Facility Management نیز می‌توانند به این لایه افزوده شوند.

> **Ecosystem Capability describes how a Transaction is formed, executed, verified, protected or supported; it does not by itself define the Route.**

## 11. Logistics & Fulfillment

Logistics & Fulfillment یک قابلیت Cross-Route است و می‌تواند شامل Pickup، Transportation، Fleet/Carrier Matching، Shipment، Tracking، Site Delivery، Proof of Delivery، Receiving، Quantity/Condition Confirmation، Return و Reverse Logistics باشد.

در Transactionهای مناسب، رویدادهای لجستیکی و Proof of Delivery می‌توانند Evidence معتبر برای State Transition، Payment Release، Financing Settlement یا Risk Monitoring باشند.

نمونه جریان:

**PO → Supplier Acceptance → Dispatch → Shipment → Site Delivery → Acceptance → Payment Release**

## 12. Data Gathering & Evidence Acquisition

Data Gathering از Evidence Ledger تفکیک می‌شود.

**Data Gathering / Evidence Acquisition** وظیفه جمع‌آوری داده و شواهد از دنیای واقعی یا سامانه‌های بیرونی را دارد؛ در حالی که **Evidence Management / Evidence Ledger** وظیفه استانداردسازی، اعتبارسنجی، نگهداری و اتصال Evidence به Transaction را بر عهده دارد.

منابع Data Gathering می‌توانند شامل موارد زیر باشند:

- User / Supplier / Contractor Applications
- Photo / Video
- GPS / Geolocation
- Shipment & Delivery Events
- Progress Reports & Certificates
- Inspectors / Supervisors / Field Agents
- Laboratories
- IoT / Sensors
- Drones
- ERP / Accounting Systems
- Banks / Financial Providers
- Logistics Providers
- Government / Registry Systems
- Uploaded Documents

جریان هدف:

**Real-world Event → Data Gathering → Validation → Evidence → Transaction State Change → Risk / Finance / Payment Decision**

## 13. Embedded Finance

Embedded Finance یک Route مستقل یا Product Brand نیست؛ بلکه روش قرار دادن قابلیت‌های مالی در متن یک Transaction واقعی و قابل اثبات است.

هر Financing Offer باید به Underlying Need، Transaction، Evidence، Beneficiary، Repayment Logic و Settlement قابل ردیابی باشد.

## 14. Target Decision & Execution Flow

جریان سطح بالا به شکل زیر تثبیت می‌شود:

**Actor + Intent + Context**

→ **Need Intelligence**

→ **Market / Network Discovery**

→ **Transaction Formation / Identification**

→ **Route Classification**

→ **Fulfillment / Execution**

↕ **Continuous Data Gathering & Evidence**

→ **Financing Need & Risk Assessment**

→ **Eligibility**

→ **Financial Product Matching**

→ **Multi-provider Matching**

→ **Offer / Decision**

→ **Controlled Payment**

→ **Delivery / Progress / Acceptance**

→ **Settlement & Learning**

Finance الزاماً یک مرحله خطی و یک‌باره نیست و می‌تواند در طول Lifecycle Transaction چند Decision Point داشته باشد.

## 15. Shared Trust & Data Core

چهار Route و قابلیت‌های اکوسیستم بر Core مشترک زیر تکیه می‌کنند:

- Identity & Authority
- Construction Network
- Need & Transaction Intelligence
- Transaction Graph
- Evidence Ledger
- Risk Infrastructure
- Financial Product Catalog
- Provider Integration
- Payment & Settlement
- Asset Registry / Asset Intelligence
- Data / IAM / Event / Audit Infrastructure
- Integration / API Layer

Shared Core نباید استقلال State، Contract، Risk، Evidence و Economics هر Route را از بین ببرد.

## 16. استقلال Routeها

هر Route باید حداقل استقلال لازم را در موارد زیر داشته باشد:

- State Model
- Transaction Object
- Contract Model
- Evidence Requirements
- Eligibility Rules
- Risk Policy
- Economic Unit / P&L
- Settlement Logic

## 17. Boundary Rule

اگر یک Need به چند Route مرتبط باشد:

> **Primary Route بر اساس Transaction اصلی و Purpose اصلی تعیین می‌شود و سایر Routeها به‌عنوان Linked Context یا Route Transition ثبت می‌شوند.**

وجود یک Ecosystem Service مانند حمل‌ونقل، بازرسی یا Marketplace نیز Route اصلی را تغییر نمی‌دهد.

## 18. Architectural Extensibility

هدف چهار Route پوشش فضای اصلی Construction Commerce، Trade & Working Capital، Project Execution & Development و Property/Asset Activity است.

اضافه‌شدن Product، Provider، Customer Type، Channel یا Ecosystem Service جدید به‌تنهایی مجوز ایجاد Route جدید نیست.

Route جدید تنها زمانی موجه است که فعالیت اقتصادی/عملیاتی جدید دارای Transaction Object مستقل، Lifecycle مستقل، State Model مستقل، Risk/Evidence Model مستقل و Economic Logic مستقل باشد و در چهار Route موجود قابل مدل‌سازی نباشد.

## 19. اثر تصمیم بر Baseline موجود

این Decision مبنای بازنگری Major اسناد زیر است:

- Vision v1.x → Vision v2.0
- Business Model v3.x → Business Model v4.0
- Financial Model v2.x → Financial Model v3.0

Operating Model نیز پس از تثبیت اسناد فوق برای Impact Assessment بررسی می‌شود.

## 20. تصمیمات تثبیت‌شده

**D1.** ساخت‌نو دارای چهار Route اصلی در سطح Business Architecture است.  
**D2.** Route بر اساس ماهیت اقتصادی و عملیاتی Transaction تعیین می‌شود، نه Customer Type.  
**D3.** Customer Archetype، Need، Route، Ecosystem Capability، Financial Product و Provider مفاهیم مستقل هستند.  
**D4.** Financial Products زیر Routeها Mapping می‌شوند ولی خودشان Route نیستند.  
**D5.** Multi-provider Finance جزء معماری است و Provider مستقل از Route است.  
**D6.** یک Journey می‌تواند از چند Route عبور کند.  
**D7.** Homepage و Need Discovery بر اساس Intent طراحی می‌شوند، نه نمایش مستقیم Route Architecture.  
**D8.** Marketplace لایه کشف، تطبیق و شکل‌دهی Transaction برای کالا، خدمات و Providerهای اکوسیستم است؛ Route مستقل نیست و Finance الزاماً به Marketplace وابسته نیست.  
**D9.** Embedded Finance روش ارائه Finance در متن Transaction است، نه Route مستقل یا Product Brand.  
**D10.** اضافه‌شدن Financial Product، Provider، Customer Type یا Channel جدید به‌تنهایی مجوز ایجاد Route جدید نیست.  
**D11.** Marketplace، Logistics، Fulfillment، Data Gathering، Inspection و سایر Ecosystem Services قابلیت‌های Cross-Route هستند؛ توسعه آنها Route جدید ایجاد نمی‌کند مگر اینکه خود فعالیت واجد معیارهای ایجاد Route مستقل باشد.  
**D12.** Data Gathering / Evidence Acquisition از Evidence Ledger تفکیک می‌شود: اولی داده و شواهد را جمع‌آوری می‌کند و دومی آنها را اعتبارسنجی، نگهداری و به Transaction متصل می‌کند.  
**D13.** Fulfillment و Evidence می‌توانند مستقیماً State Transition، Risk Decision، Payment Release و Financing Settlement را تغذیه کنند.

## 21. Change Summary — v1.0 → v1.1

این نسخه بدون تغییر چهار Route اصلی، معماری را در حوزه‌های زیر تکمیل می‌کند:

- ارتقای تعریف Marketplace از یک Transaction Formation Capability ساده به Marketplace & Network Layer؛
- تفکیک صریح Goods Marketplace و Services Marketplace؛
- افزودن Ecosystem Capability Layer؛
- تثبیت Logistics & Fulfillment به‌عنوان قابلیت Cross-Route؛
- تفکیک Data Gathering / Evidence Acquisition از Evidence Ledger؛
- افزودن رابطه Fulfillment و Evidence با State، Risk، Finance و Payment؛
- توسعه Target Flow به جریان غیرخطی Commerce + Execution + Evidence + Finance؛
- افزودن Decisions D11 تا D13.

## 22. Lifecycle Status

این نسخه در تاریخ 2026-09-10 تأیید و به‌عنوان Current Decision جایگزین `SN-DEC-001 v1.0` شد. در همان تاریخ، پس از تصویب Major Revision، توسط `SN-DEC-001 v2.0` جایگزین و **Superseded** شد.
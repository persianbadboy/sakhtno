# SakhtNo Core Ecosystem Architecture Decision

**Document ID:** `SN-DEC-001`  
**Version:** `2.0`  
**Status:** `Approved / Current`  
**Decision Type:** Core Business, Ecosystem, Data & Financial Architecture  
**Change Type:** Major Revision  
**Approval Date:** 2026-09-10  
**Supersedes:** `SN-DEC-001 v1.1`  
**Affected Baselines:** Vision / Business Model / Financial Model / Operating Model / Product & PRD / Technical Architecture

## 1. هدف و دامنه تصمیم

این Decision معماری سطح‌بالای ساخت‌نو را تعیین می‌کند و مشخص می‌کند:

ساخت‌نو چه نقشی در اکوسیستم ساخت دارد؛ فعالیت‌های اقتصادی چگونه طبقه‌بندی می‌شوند؛ Need، Transaction، Marketplace، Services، Data، Evidence، Risk، Finance و Collateral چگونه به یکدیگر متصل می‌شوند؛ و مرز مسئولیت ساخت‌نو با بانک‌ها، مؤسسات مالی، مراجع رسمی و سایر Providerهای دارای صلاحیت کجاست.

این Decision وارد جزئیات Implementation، API Specification، Credit Policy هر بانک، قراردادهای حقوقی، State Machineهای تفصیلی یا PRD نمی‌شود.

این موارد باید در اسناد پایین‌دستی بر اساس اصول این Decision طراحی شوند.

## 2. تز اصلی معماری

ساخت‌نو یک **Construction Ecosystem Platform** است.

نقش اصلی آن:

**Discovery**  
**Structuring**  
**Matching**  
**Intelligence**  
**Coordination**  
**Transaction Enablement**  
**Evidence Enablement**  
و **Controlled Execution**

در زنجیره اقتصادی و عملیاتی ساخت است.

ساخت‌نو باید بتواند:

**Need → Market → Transaction → Execution → Evidence → Risk → Finance → Payment → Settlement → Outcome**

را در یک Journey قابل ردیابی به یکدیگر متصل کند.

اما:

> **ساخت‌نو جایگزین اختیار قانونی، تصمیم تخصصی یا مسئولیت نهادی بازیگران دارای صلاحیت نمی‌شود.**

هر جا تصمیم یا عملیات نیازمند مجوز، اختیار قانونی یا صلاحیت تخصصی باشد، مسئولیت نهایی نزد نهاد یا Provider دارای صلاحیت باقی می‌ماند.

## 3. اصل تفکیک مفاهیم

معماری ساخت‌نو مفاهیم زیر را مستقل نگه می‌دارد:

**Actor / Customer Archetype**

≠ **Need / Intent**

≠ **Transaction**

≠ **Operational Route**

≠ **Journey**

≠ **Financial Product**

≠ **Financial Provider**

≠ **Collateral / Security**

≠ **Ecosystem Service**

هیچ‌یک نباید جای دیگری به‌عنوان مبنای Classification استفاده شود.

## 4. چهار Route اقتصادی و عملیاتی

Route مشخص می‌کند **ماهیت اصلی فعالیت اقتصادی و عملیاتی چیست**.

### R1 — Procurement & Consumption

تأمین کالا یا خدمت برای مصرف یا نیاز مشخص.

**Core Objects:** Order / Service Case / Delivery / Acceptance

### R2 — Trade & Working Capital

تجارت، خرید و فروش حرفه‌ای و تکرارشونده، Inventory، Receivable و Working Capital.

**Core Objects:** Business Account / PO / Invoice / Trade / Inventory / Receivable

### R3 — Project & Development

ایجاد، توسعه، اجرا، تکمیل یا بازسازی پروژه دارای ساختار پروژه، قرارداد، بودجه، Work Package، پیشرفت و کنترل.

**Core Objects:** Project / Contract / WBS / Work Package / Progress / QC / Certificate

### R4 — Property & Asset

تملک، نگهداری، بهره‌برداری، انتقال، بازتأمین مالی یا آزادسازی ارزش زمین و دارایی.

**Core Objects:** Property / Land / Asset / Ownership / Valuation / Lien / Collateral

## 5. قاعده Route Classification

> **Route بر اساس ماهیت اقتصادی و عملیاتی Transaction اصلی تعیین می‌شود؛ نه Customer Type، Financial Product، Provider، Collateral یا Homepage Entry Point.**

Classification حداقل باید موارد زیر را در نظر بگیرد:

Underlying Economic Activity  
Transaction Object  
Purpose  
Lifecycle  
Evidence Structure  
Purpose of Funding  
Source of Repayment

Customer Type می‌تواند Risk و Eligibility را تغییر دهد، ولی به‌تنهایی Route را تعیین نمی‌کند.

## 6. Boundary Rule

اگر یک Need با چند Route مرتبط باشد:

> **Primary Route بر اساس Transaction اصلی و Purpose اصلی تعیین می‌شود و سایر Routeها به‌عنوان Linked Context یا Route Transition ثبت می‌شوند.**

مثلاً خرید آسانسور برای پروژه فعال:

Need = Procurement  
Context = Project  
Primary Route = R3

و صرف Purchase بودن Transaction آن را الزاماً R1 نمی‌کند.

## 7. Journey مستقل از Route است

یک Journey می‌تواند Multi-route باشد.

مثلاً:

**Land Acquisition → Construction → Sale / Refinance**

می‌تواند:

**R4 → R3 → R4**

باشد.

در Route Transition باید:

Transaction History  
Contract  
Evidence  
Asset  
Financial Exposure  
Security/Collateral Context  
Settlement

قابل ردیابی باقی بمانند.

## 8. Need-First Discovery

کاربر نباید برای استفاده از ساخت‌نو Route Architecture را بداند.

ورود باید از **Need و Intent** شروع شود.

کانال‌های Discovery می‌توانند شامل:

Search  
Guided Drill-down  
AI Conversation  
Document Upload  
Existing Transaction  
Existing Project  
Existing Property / Asset

باشند.

خروجی این مرحله یک **Structured Need Object** است.

## 9. Need Intelligence

Need Intelligence وظیفه دارد ورودی اولیه را به Context قابل تصمیم تبدیل کند.

Need Object می‌تواند شامل:

Actor  
Intent  
Need Object  
Scope / Quantity  
Location  
Timing  
Budget  
Project Context  
Property Context  
Existing Transaction  
Existing Contract  
Existing Asset  
Financing Need  
Available Evidence  
Constraints

باشد.

Need Intelligence نقطه اتصال Discovery با Route Classification، Marketplace، Services، Risk و Finance است.

## 10. Marketplace & Construction Network

Marketplace یکی از Capabilityهای بنیادی ساخت‌نو است، اما:

> **Marketplace نه Route است و نه تعریف کل ساخت‌نو.**

Marketplace حداقل شامل دو حوزه است:

### Goods Marketplace

مصالح، تجهیزات، ماشین‌آلات، قطعات و سایر کالاهای صنعت ساخت.

### Services Marketplace

خدمات اجرا، نصب، تعمیر، طراحی، مهندسی، پیمانکاری، بازرسی، آزمایشگاه، ارزیابی، حمل و سایر خدمات تخصصی.

Marketplace به Construction Network متصل است.

این Network می‌تواند شامل:

Supplier  
Manufacturer  
Distributor  
Contractor  
Subcontractor  
Professional Service Provider  
Carrier  
Warehouse  
Inspector  
Laboratory  
Valuer

و سایر بازیگران باشد.

وظایف اصلی:

**Discovery → Matching → Qualification → Transaction Formation**

Transaction می‌تواند داخل یا خارج Marketplace ایجاد شده باشد.

## 11. Ecosystem Services

ساخت‌نو می‌تواند مجموعه‌ای از Capabilityهای Cross-Route داشته باشد که Transaction را:

**Form**  
**Execute**  
**Fulfill**  
**Verify**  
**Protect**  
یا **Finance**

می‌کنند.

از جمله:

Logistics & Fulfillment  
Warehousing  
Inspection & Quality  
Data Gathering  
Professional Services  
Valuation Services  
Document & Contract Services  
Equipment Services  
Insurance Integration  
Maintenance / Facility Services

اضافه‌شدن این Capabilityها به‌تنهایی Route جدید ایجاد نمی‌کند.

## 12. Logistics & Fulfillment

Logistics بخشی از Execution و در موارد مناسب بخشی از Evidence Chain است.

مدل نمونه:

**Pickup → Dispatch → Transportation → Tracking → Delivery → Receiving → Acceptance**

اطلاعاتی مانند:

Proof of Dispatch  
Proof of Delivery  
Quantity  
Condition  
Location  
Custody

می‌توانند بر اساس Rules تعریف‌شده در:

Transaction State  
Payment  
Risk  
Finance  
Collateral Monitoring

مصرف شوند.

## 13. Data Gathering Architecture

Data Gathering وظیفه جمع‌آوری داده از دنیای واقعی و منابع دیجیتال را دارد.

منابع می‌توانند شامل:

User/Supplier/Contractor Apps  
Documents  
Photo/Video  
GPS  
Logistics Systems  
Warehouse Systems  
Inspector  
Laboratory  
ERP/Accounting  
IoT/Sensors  
Financial Providers  
Official Registries

باشند.

اما:

> **Data ≠ Evidence**

هر Data Point الزاماً Evidence معتبر نیست.

## 14. Evidence & Trust Architecture

داده باید بر اساس Source، Authority، Context و قابلیت Verification طبقه‌بندی شود.

حداقل سه Trust Source باید از یکدیگر تفکیک شوند:

### First-party Data / Evidence

داده تولیدشده توسط Actor یا Transaction در ساخت‌نو.

### Third-party / Ecosystem Evidence

داده Providerهایی مانند Carrier، Warehouse، Inspector، Laboratory یا Valuer.

### Authoritative / Official Data

داده دریافت‌شده از مرجع رسمی یا Provider مجاز.

بنابراین:

**Real-world Event**

→ **Data Gathering**

→ **Validation / Verification**

→ **Evidence**

→ **Transaction State / Risk / Finance / Payment / Security Decision Support**

## 15. Official Data, Trust & Regulatory Integration

ساخت‌نو باید Capability مشخصی برای اتصال کنترل‌شده به **Authoritative Sources** داشته باشد.

این Capability می‌تواند خانواده‌های زیر را پشتیبانی کند:

KYC  
KYB  
Credit Bureau / Credit Scoring  
Banking & Financial Data  
Payment / Cheque-related Services  
Corporate / Business Registry  
Property / Ownership Registry  
Collateral Registry  
Tax-related Data  
Insurance-related Data  
و سایر مراجع مجاز.

Integration باید تابع:

Legal Authority  
Consent  
Purpose Limitation  
Provider Contract  
Data Access Rules  
Security & Privacy Requirements

باشد.

## 16. Provider Abstraction

Business Architecture نباید به API یک Provider خاص Hard-code شود.

مثلاً در Implementation ممکن است:

`SakhtNo → Provider X API`

باشد، اما معماری باید:

**SakhtNo → Credit Intelligence Interface → Authorized Provider(s)**

باشد.

همین اصل برای:

KYC  
KYB  
Credit Bureau  
Property Registry  
Collateral Registry  
Banking Services

اعمال می‌شود.

تغییر Provider نباید Core Business Architecture را تغییر دهد.

## 17. تفکیک Credit Data، Risk Intelligence و Credit Decision

سه مفهوم باید مستقل باشند:

### Official / Authorized Credit Information

گزارش، Score یا اطلاعات دریافت‌شده از مرجع یا Provider مجاز.

### SakhtNo Risk Intelligence

تحلیل ساخت‌نو از مجموعه:

Transaction  
Evidence  
Behavior  
Project  
Asset  
Delivery  
Collateral Context  
و سایر داده‌های مجاز.

### Financial Provider Credit Decision

تصمیم نهایی درباره:

Approval / Rejection  
Limit  
Pricing  
Tenor  
Conditions  
Collateral Acceptance

نزد Financial Provider دارای صلاحیت باقی می‌ماند.

بنابراین:

> **Official Credit Score ≠ SakhtNo Risk Intelligence ≠ Financial Provider Credit Decision**

## 18. Financial Architecture

Finance یکی از Capabilityهای بنیادی ساخت‌نو است ولی Route مستقل نیست.

ساخت‌نو Financing Need را از Context واقعی Transaction استخراج می‌کند و آن را با Financial Productهای مناسب Match می‌کند.

Financial Product Catalog مستقل از Route Catalog است.

Product Mapping بر اساس:

Need  
Transaction  
Route  
Eligibility  
Risk  
Repayment Logic  
Security Requirement  
Provider Policy

انجام می‌شود.

## 19. Multi-provider Finance

معماری مالی ساخت‌نو Multi-provider است.

Provider می‌تواند شامل:

Bank  
Credit Institution  
Leasing  
Fund  
Fintech  
Investor  
Supplier Credit Provider

باشد.

هر Provider می‌تواند مستقل داشته باشد:

Product Catalog  
Eligibility Rules  
Pricing  
Risk Appetite  
Security Requirements  
Collateral Policy  
Documentation Rules

ساخت‌نو این تفاوت‌ها را Standardize و Match می‌کند، اما تصمیم نهایی Provider را جایگزین نمی‌کند.

## 20. Embedded Finance

Embedded Finance Route یا Customer Segment نیست.

Embedded Finance روش قراردادن قابلیت مالی در Context یک Transaction واقعی و قابل اثبات است.

هر Financing Case باید تا حد لازم به:

Need  
Transaction  
Evidence  
Beneficiary  
Purpose of Funding  
Repayment Logic  
Settlement

قابل ردیابی باشد.

## 21. Controlled Payment & Settlement

هدف صرفاً Approval یک Facility نیست.

در Productهایی که ساختار آن اقتضا می‌کند:

**Verified Transaction → Financial Decision → Controlled Payment → Verified Beneficiary → Execution Evidence → Settlement**

مدل پایه است.

Cash-out مستقل از Underlying Transaction حالت پیش‌فرض ساخت‌نو نیست.

## 22. Security، Collateral، Guarantee و Credit Enhancement

این چهار مفهوم مترادف نیستند.

### Collateral — وثیقه

دارایی، حق یا Claimی که مطابق ساختار حقوقی مربوط برای تأمین تعهد استفاده می‌شود.

### Guarantee — ضمانت

تعهد شخص یا نهاد دیگر برای ایفای تعهد تحت شرایط مشخص.

### Security

مفهوم وسیع‌تر سازوکارهای حقوقی و قراردادی تأمین تعهد.

### Credit Enhancement — تقویت اعتبار

سازوکاری برای بهبود Risk Profile یک Financing که الزاماً Collateral عینی نیست.

یک Security Package می‌تواند ترکیبی از این موارد باشد.

## 23. Security, Collateral & Credit Enhancement Intelligence

ساخت‌نو باید Capability مستقلی برای **شناسایی، ساختاربندی، تطبیق و آماده‌سازی گزینه‌های تأمین تعهد** داشته باشد.

این Capability می‌تواند:

Asset  
Right  
Claim  
Guarantee  
Existing Security

را شناسایی کند و اطلاعات لازم برای مقایسه با Provider Requirements را آماده کند.

اما:

> **ساخت‌نو به‌صورت پیش‌فرض نهاد وثیقه‌پذیر نیست.**

## 24. Role Boundary در وثایق و تضامین

ساخت‌نو می‌تواند:

Candidate Security را شناسایی کند؛  
اطلاعات و Evidence آن را گردآوری کند؛  
Valuation Requirement را مشخص کند؛  
Provider Rules را اعمال کند؛  
Security Package پیشنهادی بسازد؛  
Collateral Gap را شناسایی کند؛  
و Journey لازم را هماهنگ کند.

اما به‌صورت پیش‌فرض:

**Collateral را قبول یا رد نمی‌کند؛**

**ارزش‌گذاری رسمی را جایگزین نمی‌کند؛**

**وثیقه را رأساً توثیق نمی‌کند؛**

**ثبت رسمی وثیقه را انجام نمی‌دهد مگر با اختیار قانونی مشخص؛**

**Collateral را آزاد یا جایگزین نمی‌کند؛**

**Enforcement قانونی را انجام نمی‌دهد؛**

و **Credit Decision نهایی نمی‌گیرد.**

این اختیارات نزد Financial Provider و سایر نهادهای دارای صلاحیت باقی می‌ماند.

## 25. Security Candidate Architecture

یک Security Candidate می‌تواند بسته به مقررات و Provider Policy شامل مواردی نظیر:

Land / Property  
Project-related Rights  
Completed / Partially Completed Units  
Machinery / Equipment  
Inventory  
Warehouse Stock  
Receivable  
Invoice / Certified Claim  
Deposit / Cash Collateral  
Guarantee  
Contractual Right

باشد.

قرارگرفتن یک مورد در این فهرست به معنی پذیرش قانونی یا بانکی آن نیست.

## 26. Collateral ≠ Underlying Asset

Underlying Transaction Asset و Collateral Asset الزاماً یکی نیستند.

مثلاً Transaction اصلی می‌تواند Construction Project باشد ولی Security Package شامل:

Project Land  
External Property  
Inventory  
Receivable  
Guarantee

باشد.

بنابراین معماری باید:

**Internal Security**

و

**External Security**

را پشتیبانی کند.

## 27. Collateral Pool / Security Package

یک Financing Case می‌تواند بیش از یک Security داشته باشد.

بنابراین ساخت‌نو باید بتواند:

**Security Package / Collateral Pool**

را مدل کند.

برای مثال:

**Project Land + External Property + Receivable + Guarantee**

می‌تواند یک Proposed Security Package باشد.

پذیرش کل یا بخشی از Package متعلق به Provider است.

## 28. Dynamic Security

Security در Construction Lifecycle می‌تواند تغییر کند.

برای مثال:

Land

→ Construction Progress

→ Inventory at Site

→ Completed Units

→ Receivables

و در طول Facility ممکن است Security:

Revalued  
Substituted  
Released  
یا Supplemented

شود.

ساخت‌نو باید این Lifecycle را قابل ردیابی کند، بدون اینکه اختیار قانونی این عملیات را به خود منتسب کند.

## 29. Inventory as Security Candidate

Inventory و Construction Materials می‌توانند در صورت وجود مبنای قانونی و پذیرش Provider به‌عنوان Candidate مطرح شوند.

برای تصمیم‌پذیرشدن آنها، اطلاعاتی مانند:

Ownership  
Identity / SKU  
Quantity  
Location  
Warehouse / Custody  
Movement  
Valuation  
Insurance where required  
Prior Security / Encumbrance  
Evidence

اهمیت دارند.

بنابراین Logistics، Warehouse، Evidence و Collateral Intelligence مستقیماً به یکدیگر متصل می‌شوند.

## 30. Receivables & Claims

Receivable، Invoice یا Certified Claim نیز در صورت امکان قانونی و پذیرش Provider می‌توانند بخشی از Security/Credit Structure باشند.

حداقل باید:

Debtor  
Underlying Transaction  
Amount  
Due Date  
Evidence  
Assignment Status  
Previous Financing  
Payment Status

قابل بررسی باشند.

این قابلیت برای جلوگیری از Financing تکراری یک Claim نیز اهمیت دارد.

## 31. Project as Dynamic Security Context

در R3، خود Project می‌تواند **Security Context** ایجاد کند، اما:

> **Project Value به‌صورت خودکار Collateral Value نیست.**

Security Package پروژه ممکن است از ترکیب:

Land  
Legal Rights  
Construction Progress  
Completed Units  
Inventory  
Receivables  
External Security  
Guarantees

شکل گیرد.

هر جزء باید بر اساس الزامات قانونی و Provider Policy مستقل بررسی شود.

## 32. Security Intelligence Flow

جریان هدف:

**Asset / Right / Claim / Guarantee**

→ **Ownership / Authority Evidence**

→ **Official / External Verification where available**

→ **Existing Encumbrance Information**

→ **Required Valuation**

→ **Provider Policy Compatibility**

→ **Indicative LTV / Haircut / Advance Rate**

→ **Proposed Security Package**

→ **Financial Provider Review**

→ **Provider Acceptance / Rejection**

→ **Authorized Perfection / Registration**

→ **Monitoring / Revaluation**

→ **Authorized Substitution / Release / Enforcement**

عبارات Indicative یا Proposed در این Flow عمدی هستند؛ ساخت‌نو تصمیم حقوقی نهایی را نمی‌گیرد.

## 33. Collateral Gap & Preparation Journey

اگر Provider برای Financing به Security نیاز داشته باشد، ساخت‌نو باید بتواند Gap را شناسایی کند.

اما نتیجه فقط نباید `Rejected` باشد.

سیستم می‌تواند گزینه‌های Preparation را بررسی کند:

Additional Collateral  
Additional Guarantee  
Collateral Substitution  
Different Product  
Different Provider  
Lower Facility  
Additional Evidence  
Alternative Financing Structure

خروجی می‌تواند:

**Not Ready Yet + Preparation Journey**

باشد.

## 34. Iran Legal & Regulatory Execution Model

هر Capability مالی، اعتباری، داده‌ای، وثیقه‌ای یا نظارتی باید علاوه بر Technical Feasibility دارای **Legal Execution Status** باشد.

سه وضعیت پایه:

### A — Executable under Current Framework

مبنای حقوقی و سازوکار اجرایی لازم وجود دارد و سایر الزامات مربوط قابل تأمین است.

### B — Conditional Execution

اجرا منوط به شرط‌هایی مانند:

Provider Acceptance  
License  
Consent  
Contract  
Official API Access  
Qualified Valuation  
Registry Connection  
Authorized Intermediary  
Specific Documentation

است.

### C — Future / Regulatory-dependent

Capability از نظر Business/Technology پیش‌بینی می‌شود ولی اجرای آن نیازمند تغییر یا تکمیل:

Law  
Regulation  
Directive  
License  
Official Infrastructure  
یا Legal Mechanism

است.

> **Technical Feasibility ≠ Legal Executability**

## 35. Legal Gap & Activation Rule

هر Capability که در وضعیت Conditional یا Future قرار گیرد باید حداقل دارای:

**Legal Gap**

**Required Authority**

**Required Regulatory/Contractual Condition**

**Activation Trigger**

باشد.

در نتیجه ساخت‌نو می‌تواند Capability آینده را در Architecture پیش‌بینی کند بدون اینکه پیش از فراهم‌شدن مبنای حقوقی آن را Operational اعلام کند.

این Decision اجازه دورزدن محدودیت حقوقی یا جایگزینی تفسیر حقوقی با طراحی فنی را نمی‌دهد.

## 36. Shared Core Architecture

Capabilityهای ساخت‌نو باید بر Core مشترک قرار گیرند:

**Identity & Authority**

**Need Intelligence**

**Actor / Organization Graph**

**Construction Network**

**Transaction Graph**

**Product & Service Catalog**

**Data Gathering Infrastructure**

**Evidence Ledger**

**Asset Intelligence**

**Security / Collateral Information Model**

**Risk Infrastructure**

**Financial Product Catalog**

**Provider Policy & Rules**

**Payment & Settlement**

**Official Data Integration**

**Event & Audit Infrastructure**

**Integration / API Infrastructure**

توجه مهم:

`Security / Collateral Information Model` در این مرحله الزاماً به معنی «سامانه رسمی ثبت وثیقه ساخت‌نو» نیست.

## 37. Integration & API Infrastructure

API Layer خود Business Capability نیست.

این لایه روش فنی اتصال به:

Financial Providers  
Official Sources  
Credit Information Providers  
KYC/KYB Services  
Registries  
Logistics  
Warehouses  
Insurers  
Valuers  
و سایر Systems

را فراهم می‌کند.

Business Layer مشخص می‌کند:

**چه داده‌ای، از چه مرجعی، برای چه Purpose، با چه Authority/Consent و با چه Trust Levelی**

مجاز و مورد نیاز است.

Technical Integration Layer مشخص می‌کند **چگونه** این اتصال اجرا شود.

## 38. نقش ساخت‌نو در برابر بازیگران دارای صلاحیت

اصل عمومی:

> **SakhtNo prepares, structures, matches, coordinates and provides intelligence; authorized institutions decide or execute wherever independent legal authority is required.**

بنابراین بسته به موضوع:

Financial Provider → Credit / Facility Decision

Collateral-taking Institution → Collateral Acceptance

Qualified Valuer → Required Official/Accepted Valuation

Official Registry → Authoritative Registration / Status

Credit Information Provider → Authorized Credit Information

Bank / PSP / Authorized Payment Actor → Regulated Financial Execution

Qualified Inspector / Laboratory → تخصص و Certification مربوط

ساخت‌نو این بازیگران را به Journey متصل می‌کند و نتیجه را قابل ردیابی می‌سازد.

## 39. End-to-End Target Architecture

مدل جامع هدف:

**Actor + Intent + Context**

↓

**Need Discovery**

↓

**Need Intelligence**

↓

**Official Identity / KYC / KYB where required**

↓

**Market & Network Discovery**

↓

**Transaction Formation / Identification**

↓

**Route Classification**

↓

**Execution / Fulfillment Context**

↕️

**Continuous Data Gathering**

↕️

**Evidence & Trust**

↓

**Financing Need**

↓

**Official Credit Information where required**

↓

**SakhtNo Risk & Eligibility Intelligence**

↓

**Financial Product Matching**

↓

**Security Requirement Analysis**

↓

**Security / Collateral / Credit Enhancement Intelligence**

↓

**Provider Policy Compatibility**

↓

**Multi-provider Matching**

↓

**Provider Credit & Security Decision**

↓

**Offer OR Not Ready Yet / Preparation Journey**

↓

**Controlled Execution / Payment**

↕️

**Execution + Evidence + Security Monitoring**

↓

**Settlement / Reconciliation / Authorized Release**

↓

**Outcome & Learning**

## 40. Architectural Extensibility

اضافه‌شدن موارد زیر به‌تنهایی Route جدید ایجاد نمی‌کند:

Customer Type  
Financial Product  
Financial Provider  
Collateral Type  
Guarantee Type  
Marketplace Category  
Ecosystem Service  
Official Data Source  
API Provider  
Channel

Route جدید فقط زمانی قابل طرح است که فعالیت جدید دارای:

Transaction Object مستقل  
Lifecycle مستقل  
State Model مستقل  
Evidence/Risk Model مستقل  
Economic Logic مستقل

باشد و در چهار Route فعلی قابل مدل‌سازی نباشد.

## 41. تصمیمات تثبیت‌شده

**D1.** ساخت‌نو یک Construction Ecosystem Platform با نقش هماهنگ‌سازی، Intelligence، Matching و Transaction Enablement است.

**D2.** ساخت‌نو جایگزین اختیارات قانونی یا تخصصی Providerها و مراجع دارای صلاحیت نمی‌شود.

**D3.** چهار Route اصلی R1 Procurement & Consumption، R2 Trade & Working Capital، R3 Project & Development و R4 Property & Asset هستند.

**D4.** Route بر اساس ماهیت اقتصادی و عملیاتی Transaction تعیین می‌شود.

**D5.** Actor، Need، Transaction، Route، Journey، Product، Provider، Security و Ecosystem Service مفاهیم مستقل‌اند.

**D6.** Journey می‌تواند Multi-route باشد.

**D7.** تجربه ورودی Need-first است و Route Architecture الزاماً به کاربر نمایش داده نمی‌شود.

**D8.** Marketplace شامل Goods و Services است، Cross-Route عمل می‌کند و کل تعریف ساخت‌نو نیست.

**D9.** Construction Network یکی از Capabilityهای بنیادی اکوسیستم است.

**D10.** Logistics، Fulfillment، Warehousing، Inspection و سایر Ecosystem Services Cross-Route هستند.

**D11.** Data Gathering و Evidence Management مستقل‌اند.

**D12.** First-party، Third-party و Authoritative Data/Evidence از نظر Trust Source تفکیک می‌شوند.

**D13.** ساخت‌نو دارای Official Data, Trust & Regulatory Integration Capability است.

**D14.** Business Architecture به Provider یا API خاص Hard-code نمی‌شود.

**D15.** Official Credit Information، SakhtNo Risk Intelligence و Financial Provider Credit Decision مستقل‌اند.

**D16.** Finance Multi-provider است و Financial Product مستقل از Route است.

**D17.** Embedded Finance روش ارائه قابلیت مالی در Context Transaction است، نه Route.

**D18.** Controlled Payment و Settlement به Underlying Transaction و Evidence متصل می‌شوند.

**D19.** Collateral، Guarantee، Security و Credit Enhancement مفاهیم مستقل و قابل ترکیب‌اند.

**D20.** Security, Collateral & Credit Enhancement Intelligence یک Capability Cross-Route است.

**D21.** ساخت‌نو به‌صورت پیش‌فرض نهاد وثیقه‌پذیر، Official Valuer، Registration Authority یا Final Credit Decision-maker نیست.

**D22.** Security Package می‌تواند از Internal و External Security تشکیل شود.

**D23.** Dynamic Security و Collateral Pool باید قابل مدل‌سازی باشند.

**D24.** Inventory، Receivables، Project-related Assets، Property و سایر Assets/Rights صرفاً Candidate هستند و پذیرش آنها تابع قانون و Provider Policy است.

**D25.** Provider Matching در Financingهای Secured باید Security Compatibility را نیز در نظر بگیرد.

**D26.** Collateral Gap می‌تواند به Preparation Journey منجر شود.

**D27.** Security Monitoring به Data، Evidence و Event Infrastructure متصل است.

**D28.** KYC، KYB، Credit Information و سایر داده‌های رسمی از طریق Authoritative/Authorized Sources و تحت Authority/Consent لازم دریافت می‌شوند.

**D29.** Technical Feasibility به معنی Legal Executability نیست.

**D30.** هر Capability حساس مالی/حقوقی دارای Legal Execution Status خواهد بود: Current، Conditional یا Future/Regulatory-dependent.

**D31.** Capabilityهای Conditional/Future باید Legal Gap و Activation Trigger مشخص داشته باشند.

**D32.** Product، Provider، Collateral Type، Ecosystem Service، Data Source یا Channel جدید به‌تنهایی Route جدید ایجاد نمی‌کند.

## 42. اثر بر Baselineها

Approval این Decision یک **Major Architecture Baseline** جدید ایجاد می‌کند.

بنابراین:

**Vision v2.0** باید بر اساس `SN-DEC-001 v2.0` اصلاح شود.

**Business Model v4.0** باید این معماری را به Business Architecture، Value Creation و Economics تبدیل کند.

**Financial Model v3.0** باید Product، Provider، Risk، Eligibility، Security/Collateral، Controlled Payment و Settlement را تفصیلی کند.

**Operating Model** پس از آن باید Impact Assessment شود.

سپس Product/PRD و Technical Architecture باید از Baselineهای فوق مشتق شوند.

## 43. موضوعاتی که عمداً در این Decision نهایی نمی‌شوند

این سند **اصل معماری** را تثبیت می‌کند، نه جزئیات پایین‌دستی.

بنابراین موارد زیر باید جداگانه طراحی شوند:

فرمول Credit/Risk Scoring؛  
Eligibility Rules هر Product؛  
Collateral Haircut/LTV؛  
Bank-specific Credit Policy؛  
API Specification؛  
KYC/KYB Provider Selection؛  
Credit Bureau Provider Selection؛  
جزئیات Legal Opinion برای هر Security Type؛  
قراردادهای توثیق/ضمانت؛  
Enforcement Process؛  
Privacy/Data Retention Policy؛  
State Machineهای تفصیلی؛  
و Data Model فنی.

این تفکیک برای جلوگیری از تبدیل Architecture Decision به PRD یا Legal Manual ضروری است.

## 44. Change Summary — v1.1 → v2.0

این نسخه Patch قبلی نیست؛ **بازتعریف ساختاری Decision** است.

v1.1 عمدتاً Route Architecture را تثبیت کرده و Marketplace، Ecosystem Services، Logistics و Data Gathering را به آن افزوده بود.

v2.0 معماری را به یک **Core Ecosystem Architecture** ارتقا می‌دهد و به‌صورت منظم در کنار Routeها تعریف می‌کند:

Need Intelligence؛  
Marketplace & Construction Network؛  
Ecosystem Services؛  
Data/Evidence/Trust؛  
Official & Regulatory Integrations؛  
Risk Intelligence؛  
Multi-provider Finance؛  
Security/Collateral/Credit Enhancement؛  
Legal Execution Model؛  
و Role Boundaries.

همچنین اصل بنیادین زیر را تثبیت می‌کند:

> **ساخت‌نو اطلاعات، Transaction و گزینه‌های اجرایی و مالی را ساختارمند، Match و هماهنگ می‌کند؛ اما هر تصمیم یا عملیات نیازمند اختیار قانونی مستقل نزد نهاد دارای صلاحیت باقی می‌ماند.**

## 45. Approval

این نسخه در تاریخ 2026-09-10 تأیید و به‌عنوان **Current Architecture Decision** جایگزین `SN-DEC-001 v1.1` شد.
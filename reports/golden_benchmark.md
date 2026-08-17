# Lab 17 Golden Set Report

- Implementation: `student`
- Kind: `golden`
- Cases: **20**
- Passed: **18/20**
- Evidence hit rate: **90.0%**
- Average retrieval latency: **1339.2 ms**
- Average token reduction vs full source context: **5.2%**
- Golden bonus: **0/10** (100% required)

| Case | Layer | Pass | Latency ms | Retrieved tokens | Token reduction | Missing / Error |
| --- | --- | --- | ---: | ---: | ---: | --- |
| G01 | short_term | PASS | 0.2 | 227 | 0.0% |  |
| G02 | short_term | PASS | 0.0 | 133 | 0.0% |  |
| G06 | long_term | PASS | 1246.7 | 665 | 0.0% |  |
| G09 | semantic | PASS | 291.8 | 418 | 8.9% |  |
| G10 | semantic | PASS | 380.4 | 270 | 41.2% |  |
| G14 | mixed | PASS | 5334.0 | 581 | 0.0% |  |
| G03 | long_term | PASS | 2049.1 | 840 | 0.0% |  |
| G04 | long_term | PASS | 1628.8 | 843 | 0.0% |  |
| G07 | episodic | PASS | 303.3 | 208 | 5.9% |  |
| G08 | episodic | PASS | 300.8 | 233 | 0.0% |  |
| G11 | mixed | PASS | 2492.9 | 581 | 0.0% |  |
| G13 | mixed | FAIL | 694.1 | 494 | 12.6% | missing=ClientSession |
| G15 | mixed | PASS | 1958.0 | 778 | 0.0% |  |
| G16 | mixed | PASS | 1515.6 | 581 | 0.0% |  |
| G17 | mixed | PASS | 2234.2 | 581 | 0.0% |  |
| G18 | mixed | FAIL | 867.9 | 461 | 18.4% | missing=connection churn, BUDGET-10-4-3-3 |
| G19 | mixed | PASS | 1391.3 | 537 | 5.0% |  |
| G05 | long_term | PASS | 1129.4 | 838 | 0.0% |  |
| G12 | mixed | PASS | 1476.7 | 560 | 11.4% |  |
| G20 | mixed | PASS | 1489.1 | 756 | 0.0% |  |

## Evidence excerpts

### G01 - short_term

`<SESSION_SUMMARY> user: Constraint HOLD-ALPHA-0900: standup is 09:00 sharp and must not be forgotten. | assistant: Noted standup constraint. | user: Constraint HOLD-BETA-STAGING: writes go to staging DB only. | assistant: Noted staging constraint. | user: Filler A about button padding. | assistant: Filler A. | user: Filler B about color tokens. | assistant: Filler B. | user: Filler C about copy tone. | assistant: Filler C. </SESSION_SUMMARY> <DURABLE_NOTES> - user: Constraint HOLD-ALPHA-0900: standup is 09:00 sharp and must not be forgotten. - assistant: Noted standup constraint. - user: Constraint HOLD-BETA-STAGING: writes go to staging DB only. - assistant: Noted staging constraint. </DURA`

### G02 - short_term

`<RECENT_TURNS> user: Ten du an ca nhan cua toi la ORCHID-27. Toi thich Python va khong thich Java. Khi giai thich code, hay dung vi du ngan. assistant: Da hieu: demo ca nhan ORCHID-27, uu tien Python, tranh Java, vi du ngan. user: Toi dang hoc async/await va hay nham coroutine voi Task. Neu sau nay gap chu de nay, hay giai thich bang timeline. assistant: Toi se uu tien timeline khi giai thich coroutine va Task. user: TODO: hoan thanh benchmark report truoc thu Sau luc 16:00. Day la open loop LAB-REPORT-1600. </RECENT_TURNS>`

### G06 - long_term

`<USER_SUMMARY> Lan Tran's project is LOTUS-88, for which they prioritize Java and Spring Boot for backend examples.  Lan Tran prefers to use Java and Spring Boot for backend development. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-01 11:00:00     Source: message     Content: [user] {   "user_id": "lan-lab17",   "first_name": "Lan",   "last_name": "Tran",   "user_alias": "Lan Tran" }: Toi la Lan. Du an cua toi la LOTUS-88. Toi uu tien Java va Spring Boot, va khong dung Python trong vi du backend.   - Created At: 2026-08-01 11:00:20     Source: message     Content: Lab Assistant (assistant): Da hieu: LOTUS-88, J`

### G09 - semantic

`EPISODE: {"id":"kb-payment-retry","entity":"Payment API Retry Policy","summary":"For POST /payments, every retryable request MUST send the same Idempotency-Key. Retry only HTTP 429 or transient 5xx errors, use exponential-backoff, and stop after max-3-retries. Marker: PAYMENT-RULE-3.","source":"internal-api-guideline-v3","updated_at":"2026-08-10T00:00:00Z"} metadata= EPISODE: For POST /payments, every retryable request MUST send the same Idempotency-Key. Retry only HTTP 429 or transient 5xx errors, use exponential-backoff, and stop after max-3-retries. Marker: PAYMENT-RULE-3. metadata= EPISODE: {"id":"kb-memory-privacy","entity":"Agent Memory Privacy Rule","summary":"Do not persist personal `

### G10 - semantic

`EPISODE: {"id":"kb-memory-privacy","entity":"Agent Memory Privacy Rule","summary":"Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL.","source":"memory-governance-policy","updated_at":"2026-08-12T00:00:00Z"} metadata= EPISODE: Do not persist personal data without explicit opt-in. A deletion request must remove user-scoped memory and be verified across every store. Marker: DELETE-VERIFY-ALL. metadata= EPISODE: {"id":"kb-context-budget","entity":"Memory Context Budget","summary":"Reserve bounded context for memory. This lab uses short-term 10 percent, long-term 4 percent, episodi`

### G14 - mixed

`<LONG_TERM> <USER_SUMMARY> Lan Tran's project is LOTUS-88, for which they prioritize Java and Spring Boot for backend examples.  Lan Tran prefers to use Java and Spring Boot for backend development. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-01 11:00:00     Source: message     Content: [user] {   "user_id": "lan-lab17",   "first_name": "Lan",   "last_name": "Tran",   "user_alias": "Lan Tran" }: Toi la Lan. Du an cua toi la LOTUS-88. Toi uu tien Java va Spring Boot, va khong dung Python trong vi du backend.   - Created At: 2026-08-01 11:00:20     Source: message     Content: Lab Assistant (assistant): Da hieu:`

### G03 - long_term

`<USER_SUMMARY> Minh Nguyen's personal project is named ORCHID-27, for which Python is preferred. The company project BLUEBIRD-42 uses TypeScript with NestJS for its backend. Minh has an upcoming deadline for the benchmark report open loop LAB-REPORT-1600 by Friday at 4 PM. Minh is currently debugging async HTTP requests and has tried increasing the timeout to 60s without success, with the efficient approach being to reuse an aiohttp ClientSession and set concurrency to 20. The main issue was connection churn, related to the ASYNC-FIX-20 incident.  Minh Nguyen likes Python and dislikes Java. When explaining code, use short examples. When discussing async/await and coroutines vs. Tasks, explai`

### G04 - long_term

`<USER_SUMMARY> Minh Nguyen's personal project is named ORCHID-27, for which Python is preferred. The company project BLUEBIRD-42 uses TypeScript with NestJS for its backend. Minh has an upcoming deadline for the benchmark report open loop LAB-REPORT-1600 by Friday at 4 PM. Minh is currently debugging async HTTP requests and has tried increasing the timeout to 60s without success, with the efficient approach being to reuse an aiohttp ClientSession and set concurrency to 20. The main issue was connection churn, related to the ASYNC-FIX-20 incident.  Minh Nguyen likes Python and dislikes Java. When explaining code, use short examples. When discussing async/await and coroutines vs. Tasks, explai`

### G07 - episodic

`EPISODE: Cuoi tuan minh ngoi mot minh lam demo rieng, khong hop team. Truoc khi chon template, nhac lai: khi lam viec ca nhan minh uu tien ngon ngu nao, va ma du an demo ca nhan la gi? Chi  EPISODE: Hom nay toi debug async HTTP. Toi da thu tang timeout len 60s nhung van fail. EPISODE: Cach hieu qua la reuse aiohttp ClientSession va dat concurrency=20. Reflection: loi chinh la connection churn, khong phai timeout threshold. Ma su co ASYNC-FIX-20. EPISODE: Chuan bi demo ca nhan: ten/ma project rieng cua Minh la gi, va lan async HTTP truoc minh reuse client nhu the nao (kem ma su co)? Khong can policy domain chung, chi memory cua Minh EPISODE: Toi nay minh viet tool ca nhan de tai hien su co HT`

### G08 - episodic

`EPISODE: Minh con mot open-loop phai nop truoc deadline, dong thoi muon ghi chu retry payment dung so lan toi da theo policy. Nac lai ma task/deadline con dang do, va gioi han retry chinh t EPISODE: Cach hieu qua la reuse aiohttp ClientSession va dat concurrency=20. Reflection: loi chinh la connection churn, khong phai timeout threshold. Ma su co ASYNC-FIX-20. EPISODE: Chuan bi demo ca nhan: ten/ma project rieng cua Minh la gi, va lan async HTTP truoc minh reuse client nhu the nao (kem ma su co)? Khong can policy domain chung, chi memory cua Minh EPISODE: Minh sap viet script ca nhan de tai hien su co latency, muon code dung ngon ngu minh thich khi lam mot minh, dong thoi bam sat playbook in`

### G11 - mixed

`<LONG_TERM> <USER_SUMMARY> Minh Nguyen's personal project is named ORCHID-27, for which Python is preferred. The company project BLUEBIRD-42 uses TypeScript with NestJS for its backend. Minh has an upcoming deadline for the benchmark report open loop LAB-REPORT-1600 by Friday at 4 PM. Minh is currently debugging async HTTP requests and has tried increasing the timeout to 60s without success, with the efficient approach being to reuse an aiohttp ClientSession and set concurrency to 20. The main issue was connection churn, related to the ASYNC-FIX-20 incident.  Minh Nguyen likes Python and dislikes Java. When explaining code, use short examples. When discussing async/await and coroutines vs. T`

### G13 - mixed

`<EPISODIC> EPISODE: Minh con mot open-loop phai nop truoc deadline, dong thoi muon ghi chu retry payment dung so lan toi da theo policy. Nac lai ma task/deadline con dang do, va gioi han retry chinh t EPISODE: Minh sap giai thich coroutine cho ban, dong thoi can nhac policy retry payment vao vi du. Minh hoc kieu nao thi de nho? Va request retry payment phai mang header nao? Dung lay styl EPISODE: Cong ty yeu cau chinh context window cho agent tren dung backend du an cong ty. Minh can biet stack bat buoc cua BLUEBIRD va ty le budget bon tang nho trong lab de cau hinh cho dun EPISODE: Trong thread nay minh vua nhac constraint gio standup. Lat nua minh se them retry payment vao dung backend du `

### G15 - mixed

`<LONG_TERM> <USER_SUMMARY> Minh Nguyen's personal project is named ORCHID-27, for which Python is preferred. The company project BLUEBIRD-42 uses TypeScript with NestJS for its backend. Minh has an upcoming deadline for the benchmark report open loop LAB-REPORT-1600 by Friday at 4 PM. Minh is currently debugging async HTTP requests and has tried increasing the timeout to 60s without success, with the efficient approach being to reuse an aiohttp ClientSession and set concurrency to 20. The main issue was connection churn, related to the ASYNC-FIX-20 incident.  Minh Nguyen likes Python and dislikes Java. When explaining code, use short examples. When discussing async/await and coroutines vs. T`

### G16 - mixed

`<LONG_TERM> <USER_SUMMARY> Minh Nguyen's personal project is named ORCHID-27, for which Python is preferred. The company project BLUEBIRD-42 uses TypeScript with NestJS for its backend. Minh has an upcoming deadline for the benchmark report open loop LAB-REPORT-1600 by Friday at 4 PM. Minh is currently debugging async HTTP requests and has tried increasing the timeout to 60s without success, with the efficient approach being to reuse an aiohttp ClientSession and set concurrency to 20. The main issue was connection churn, related to the ASYNC-FIX-20 incident.  Minh Nguyen likes Python and dislikes Java. When explaining code, use short examples. When discussing async/await and coroutines vs. T`

### G17 - mixed

`<LONG_TERM> <USER_SUMMARY> Minh Nguyen's personal project is named ORCHID-27, for which Python is preferred. The company project BLUEBIRD-42 uses TypeScript with NestJS for its backend. Minh has an upcoming deadline for the benchmark report open loop LAB-REPORT-1600 by Friday at 4 PM. Minh is currently debugging async HTTP requests and has tried increasing the timeout to 60s without success, with the efficient approach being to reuse an aiohttp ClientSession and set concurrency to 20. The main issue was connection churn, related to the ASYNC-FIX-20 incident.  Minh Nguyen likes Python and dislikes Java. When explaining code, use short examples. When discussing async/await and coroutines vs. T`

### G18 - mixed

`<EPISODIC> EPISODE: Cong ty yeu cau chinh context window cho agent tren dung backend du an cong ty. Minh can biet stack bat buoc cua BLUEBIRD va ty le budget bon tang nho trong lab de cau hinh cho dun EPISODE: Cuoi tuan minh ngoi mot minh lam demo rieng, khong hop team. Truoc khi chon template, nhac lai: khi lam viec ca nhan minh uu tien ngon ngu nao, va ma du an demo ca nhan la gi? Chi  EPISODE: Toi nay minh viet tool ca nhan de tai hien su co HTTP roi sua dung playbook. Can ba manh: ngon ngu minh thich khi lam mot minh, ma su co async lan truoc, va buoc playbook truoc khi EPISODE: Chuan bi demo ca nhan: ten/ma project rieng cua Minh la gi, va lan async HTTP truoc minh reuse client nhu the `

### G19 - mixed

`<LONG_TERM> <USER_SUMMARY> Minh Nguyen's personal project is named ORCHID-27, for which Python is preferred. The company project BLUEBIRD-42 uses TypeScript with NestJS for its backend. Minh has an upcoming deadline for the benchmark report open loop LAB-REPORT-1600 by Friday at 4 PM. Minh is currently debugging async HTTP requests and has tried increasing the timeout to 60s without success, with the efficient approach being to reuse an aiohttp ClientSession and set concurrency to 20. The main issue was connection churn, related to the ASYNC-FIX-20 incident.  Minh Nguyen likes Python and dislikes Java. When explaining code, use short examples. When discussing async/await and coroutines vs. T`

### G05 - long_term

`<USER_SUMMARY> Minh Nguyen's personal project is named ORCHID-27, for which Python is preferred. The company project BLUEBIRD-42 uses TypeScript with NestJS for its backend. Minh has an upcoming deadline for the benchmark report open loop LAB-REPORT-1600 by Friday at 4 PM. Minh is currently debugging async HTTP requests and has tried increasing the timeout to 60s without success, with the efficient approach being to reuse an aiohttp ClientSession and set concurrency to 20. The main issue was connection churn, related to the ASYNC-FIX-20 incident.  Minh Nguyen likes Python and dislikes Java. When explaining code, use short examples. When discussing async/await and coroutines vs. Tasks, explai`

### G12 - mixed

`<LONG_TERM> <USER_SUMMARY> Minh Nguyen's personal project is named ORCHID-27, for which Python is preferred. The company project BLUEBIRD-42 uses TypeScript with NestJS for its backend. Minh has an upcoming deadline for the benchmark report open loop LAB-REPORT-1600 by Friday at 4 PM. Minh is currently debugging async HTTP requests and has tried increasing the timeout to 60s without success, with the efficient approach being to reuse an aiohttp ClientSession and set concurrency to 20. The main issue was connection churn, related to the ASYNC-FIX-20 incident.  Minh Nguyen likes Python and dislikes Java. When explaining code, use short examples. When discussing async/await and coroutines vs. T`

### G20 - mixed

`<SHORT_TERM> <SESSION_SUMMARY> user: Constraint HOLD-ALPHA-0900: standup is 09:00 sharp and must not be forgotten. | assistant: Noted standup constraint. | user: Filler about dashboard widgets. | assistant: Filler. | user: Filler about CSS variables. | assistant: Filler. | user: Filler about copy review. | assistant: Filler. </SESSION_SUMMARY> <DURABLE_NOTES> - user: Constraint HOLD-ALPHA-0900: standup is 09:00 sharp and must not be forgotten. - assistant: Noted standup constraint. </DURABLE_NOTES> <RECENT_TURNS> user: Filler about empty charts. assistant: Filler. user: Filler about telemetry. assistant: Filler. user: Filler about a11y labels. assistant: Filler. </RECENT_TURNS> </SHORT_TERM>`

# Lab 17 Benchmark Report

- Implementation: `student`
- Kind: `practice`
- Cases: **11**
- Passed: **5/11**
- Evidence hit rate: **45.5%**
- Average retrieval latency: **611.7 ms**
- Average token reduction vs full source context: **67.4%**

| Case | Layer | Pass | Latency ms | Retrieved tokens | Token reduction | Missing / Error |
| --- | --- | --- | ---: | ---: | ---: | --- |
| E01 | short_term | PASS | 0.0 | 133 | 0.0% |  |
| E06 | semantic | PASS | 977.1 | 148 | 67.8% |  |
| E09 | long_term | PASS | 1170.4 | 599 | 0.0% |  |
| E10 | short_term | PASS | 0.2 | 195 | 0.0% |  |
| E02 | long_term | FAIL | 914.2 | 0 | 100.0% | ApiError: headers: {'date': 'Mon, 17 Aug 2026 09:22:54 GMT', 'content-type': 'application/json; charset=utf-8', 'transfer-encoding': 'chunked', 'connection': 'keep-alive', 'vary': 'Origin', 'x-content-type-options': 'nosniff', 'x-ratelimit-increment': '1', 'x-ratelimit-limit': '300', 'x-ratelimit-remaining': '293', 'x-ratelimit-reset': '1786958580', 'strict-transport-security': 'max-age=2592000', 'cf-cache-status': 'DYNAMIC', 'content-encoding': 'gzip', 'server': 'cloudflare', 'cf-ray': 'a2c79df02b8c3dd5-SIN'}, status_code: 404, body: {'message': 'user not found', 'request_id': '51bb7f04-059b-4d91-a284-9a8da568d170'} |
| E03 | long_term | FAIL | 1098.1 | 0 | 100.0% | ApiError: headers: {'date': 'Mon, 17 Aug 2026 09:22:55 GMT', 'content-type': 'application/json; charset=utf-8', 'transfer-encoding': 'chunked', 'connection': 'keep-alive', 'vary': 'Origin', 'x-content-type-options': 'nosniff', 'x-ratelimit-increment': '1', 'x-ratelimit-limit': '300', 'x-ratelimit-remaining': '291', 'x-ratelimit-reset': '1786958580', 'strict-transport-security': 'max-age=2592000', 'cf-cache-status': 'DYNAMIC', 'content-encoding': 'gzip', 'server': 'cloudflare', 'cf-ray': 'a2c79df748333dd5-SIN'}, status_code: 404, body: {'message': 'user not found', 'request_id': 'dd5ae7bc-1e35-4e90-8b06-e3796b23ab7e'} |
| E04 | episodic | FAIL | 388.2 | 0 | 100.0% | ApiError: headers: {'date': 'Mon, 17 Aug 2026 09:22:55 GMT', 'content-type': 'application/json; charset=utf-8', 'transfer-encoding': 'chunked', 'connection': 'keep-alive', 'vary': 'Origin', 'x-content-type-options': 'nosniff', 'x-ratelimit-increment': '1', 'x-ratelimit-limit': '300', 'x-ratelimit-remaining': '290', 'x-ratelimit-reset': '1786958580', 'strict-transport-security': 'max-age=2592000', 'cf-cache-status': 'DYNAMIC', 'content-encoding': 'gzip', 'server': 'cloudflare', 'cf-ray': 'a2c79df8a90f3dd5-SIN'}, status_code: 404, body: {'message': 'not found', 'request_id': 'c4a3b528-66d8-4b35-9b33-22dc306166d8'} |
| E05 | episodic | FAIL | 533.1 | 0 | 100.0% | ApiError: headers: {'date': 'Mon, 17 Aug 2026 09:22:56 GMT', 'content-type': 'application/json; charset=utf-8', 'transfer-encoding': 'chunked', 'connection': 'keep-alive', 'vary': 'Origin', 'x-content-type-options': 'nosniff', 'x-ratelimit-increment': '1', 'x-ratelimit-limit': '300', 'x-ratelimit-remaining': '289', 'x-ratelimit-reset': '1786958580', 'strict-transport-security': 'max-age=2592000', 'cf-cache-status': 'DYNAMIC', 'content-encoding': 'gzip', 'server': 'cloudflare', 'cf-ray': 'a2c79dfb1af83dd5-SIN'}, status_code: 404, body: {'message': 'not found', 'request_id': '5a9d74f0-372a-4279-95f6-215b7db33d9c'} |
| E07 | mixed | FAIL | 479.0 | 0 | 100.0% | ApiError: headers: {'date': 'Mon, 17 Aug 2026 09:22:56 GMT', 'content-type': 'application/json; charset=utf-8', 'transfer-encoding': 'chunked', 'connection': 'keep-alive', 'vary': 'Origin', 'x-content-type-options': 'nosniff', 'x-ratelimit-increment': '1', 'x-ratelimit-limit': '300', 'x-ratelimit-remaining': '287', 'x-ratelimit-reset': '1786958580', 'strict-transport-security': 'max-age=2592000', 'cf-cache-status': 'DYNAMIC', 'content-encoding': 'gzip', 'server': 'cloudflare', 'cf-ray': 'a2c79dffefc33dd5-SIN'}, status_code: 404, body: {'message': 'user not found', 'request_id': '665e0254-e572-48a5-bd14-cd2fb871925e'} |
| E11 | semantic | PASS | 280.1 | 146 | 74.2% |  |
| E08 | long_term | FAIL | 888.6 | 0 | 100.0% | ApiError: headers: {'date': 'Mon, 17 Aug 2026 09:22:57 GMT', 'content-type': 'application/json; charset=utf-8', 'transfer-encoding': 'chunked', 'connection': 'keep-alive', 'vary': 'Origin', 'x-content-type-options': 'nosniff', 'x-ratelimit-increment': '1', 'x-ratelimit-limit': '300', 'x-ratelimit-remaining': '284', 'x-ratelimit-reset': '1786958580', 'strict-transport-security': 'max-age=2592000', 'cf-cache-status': 'DYNAMIC', 'content-encoding': 'gzip', 'server': 'cloudflare', 'cf-ray': 'a2c79e075d7e3dd5-SIN'}, status_code: 404, body: {'message': 'user not found', 'request_id': 'baeb1710-8624-4afa-943f-13db81d40b60'} |

## Evidence excerpts

### E01 - short_term

`<RECENT_TURNS> user: Ten du an ca nhan cua toi la ORCHID-27. Toi thich Python va khong thich Java. Khi giai thich code, hay dung vi du ngan. assistant: Da hieu: demo ca nhan ORCHID-27, uu tien Python, tranh Java, vi du ngan. user: Toi dang hoc async/await va hay nham coroutine voi Task. Neu sau nay gap chu de nay, hay giai thich bang timeline. assistant: Toi se uu tien timeline khi giai thich coroutine va Task. user: TODO: hoan thanh benchmark report truoc thu Sau luc 16:00. Day la open loop LAB-REPORT-1600. </RECENT_TURNS>`

### E06 - semantic

`EPISODE: {"id":"kb-payment-retry","entity":"Payment API Retry Policy","summary":"For POST /payments, every retryable request MUST send the same Idempotency-Key. Retry only HTTP 429 or transient 5xx errors, use exponential-backoff, and stop after max-3-retries. Marker: PAYMENT-RULE-3.","source":"internal-api-guideline-v3","updated_at":"2026-08-10T00:00:00Z"} metadata= EPISODE: For POST /payments, every retryable request MUST send the same Idempotency-Key. Retry only HTTP 429 or transient 5xx errors, use exponential-backoff, and stop after max-3-retries. Marker: PAYMENT-RULE-3. metadata=`

### E09 - long_term

`<USER_SUMMARY> Lan Tran's project is LOTUS-88, for which they prioritize Java and Spring Boot for backend examples.  Lan Tran prefers to use Java and Spring Boot for backend development. </USER_SUMMARY>  <EPISODES> Episodes are source message or document excerpts shown in selection order.   - Created At: 2026-08-01 11:00:20     Source: message     Content: Lab Assistant (assistant): Da hieu: LOTUS-88, Java + Spring Boot cho backend examples.   - Created At: 2026-08-01 11:00:00     Source: message     Content: [user] {   "user_id": "lan-lab17",   "first_name": "Lan",   "last_name": "Tran",   "user_alias": "Lan Tran" }: Toi la Lan. Du an cua toi la LOTUS-88. Toi uu tien Java va Spring Boot, va`

### E10 - short_term

`<SESSION_SUMMARY> user: Constraint: REVIEW-DEADLINE-1600 - project review is Friday at 16:00 and must not be forgotten. | assistant: Acknowledged review constraint. | user: Filler turn 1 about UI spacing. | assistant: Filler answer 1. | user: Filler turn 2 about naming. | assistant: Filler answer 2. | user: Filler turn 3 about logging. | assistant: Filler answer 3. </SESSION_SUMMARY> <DURABLE_NOTES> - user: Constraint: REVIEW-DEADLINE-1600 - project review is Friday at 16:00 and must not be forgotten. - assistant: Acknowledged review constraint. </DURABLE_NOTES> <RECENT_TURNS> user: Filler turn 4 about tests. assistant: Filler answer 4. user: Filler turn 5 about docs. assistant: Filler answe`

### E02 - long_term

``

### E03 - long_term

``

### E04 - episodic

``

### E05 - episodic

``

### E07 - mixed

``

### E11 - semantic

`EPISODE: {"id":"kb-async-http","entity":"Async HTTP Incident Playbook","summary":"When async HTTP calls time out, inspect connection pooling, downstream saturation and concurrency before increasing timeout. Reuse a long-lived client session where possible. Marker: CONN-POOL-FIRST.","source":"incident-playbook-2026","updated_at":"2026-08-11T00:00:00Z"} metadata= EPISODE: When async HTTP calls time out, inspect connection pooling, downstream saturation and concurrency before increasing timeout. Reuse a long-lived client session where possible. Marker: CONN-POOL-FIRST. metadata=`

### E08 - long_term

``

# K6 lab results 
  
## Part 0 
- Step 0.1, http_req_duration: avg=min=med=max=p(90)=p(95)=388.58 ms (1 request)
- Step 0.2, requests, rate and p(95), and why the rate stays below 5: จำนวนคำขอ = 71 คำขอ, อัตรา = 3.25 คำขอต่อวินาที, p(95) = 1.06 วินาที สาเหตุที่อัตราต่ำกว่า 5 คำขอต่อวินาที เนื่องจากผู้ใช้จำลองแต่ละคนส่งคำขอหนึ่งครั้งแล้วหยุดพักตามคำสั่ง sleep(1) เป็นเวลา 1 วินาที ดังนั้นการทำงานหนึ่งรอบจึงใช้เวลาเท่ากับเวลาตอบสนองรวมกับ 1 วินาที (ค่าเฉลี่ยของ iteration_duration คือ 1.48 วินาที) ผู้ใช้หนึ่งคนจึงส่งคำขอได้น้อยกว่า 1 คำขอต่อวินาที และผู้ใช้ 5 คนจึงส่งได้น้อยกว่า 5 คำขอต่อวินาที
- Step 0.6, exit code of the normal run and of the run with P95=300: การรันปกติได้ exit code = 0 (p(95) = 393.56 ms ผ่านเกณฑ์ 1500 ms), การรันด้วย P95=300 ได้ exit code = 99 (p(95) = 373.81 ms ไม่ผ่านเกณฑ์ 300 ms)
- Step 0.7, rules that passed, p(95), p(99), exit code after your change: กฎที่ผ่านทั้งหมดในการรันตามข้อกำหนดจริง ได้แก่ p(95)<1000 (p(95) = 390.27 ms), p(99)<1500 (p(99) = 425.88 ms) และ http_req_failed<0.01 (0.00%) โดย exit code = 0; หลังเปลี่ยนเกณฑ์เป็น p(95)<10 กฎ p(95) ไม่ผ่าน (p(95) = 381.98 ms) และ exit code = 99
- Step 0.8, what was wrong, and how the checks showed it: 
  
## Part A results 
| Step | Test type    | Users | Req/s | p(95) | Max | Failed | Checks | 
| ---- | ------------ | ----- | ----- | ----- | --- | ------ | ------ | 
| A1   | Smoke        | 1     |       |       |     |        |        | 
| A2   | Average load | 3     |       |       |     |        |        | 
| A3   | Stress       | 5     |       |       |     |        |        | 
| A4   | Spike        | 5     |       |       |     |        |        | 
| A5   | Soak         | 2     |       |       |     |        |        | 
  
## Part B 
1. 
2. 
3. 
4. 
5. 
6. 
7. 
8. 
9.
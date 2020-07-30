---
title: 'HTTP Status Code คืออะไร?'
description: 'HTTP Status Code คือตัวเลขชุดหนึ่งประกอบด้วยตัวเลข 3 ตัว ซึ่งเป็นมาตรฐานที่แสดงขึ้นมาจากการตอบสนองของเซิฟเวอร์บนเว็บไซต์ต่างๆ โดยตัวเลขแต่ละชุดก็จะมีความหมายที่แตกต่างกันไป ที่พบเจอกันบ่อยเช่น 404 Page Not Found แล้วรู้หรือไม่ว่าหมายถึงอะไร'
slug: 'http_status_code'
img: 'https://assets.materialup.com/uploads/48274fcc-d127-4a6b-bcc5-516edc3a3f14/preview.png'
---

รูปแบบของ HTTP Status Code ประกอบไปด้วย 2 ส่วนหลักๆได้แก่ Status Code กับ ประโยคอธิบายความหมาย เช่น 404 คือ ตัวเลข 3 ตัวที่เป็น HTTP STATUS CODE Page Not Found คือ ประโยคอธิบายความหมายในที่นี้ก็คือ หน้าเว็บไซต์ที่เราพยายามจะเข้าถึงนั้นไม่มีอยู่บนเซิร์ฟเวอร์ และแน่นอนว่า status code ไม่ได้มีเพียงแค่ 404 Page Not Found เพียงอย่างเดียว ยังมี case อื่นมากมายที่อาจเกิดขึ้นได้

## 1xx (Informational)
Request ที่ Client ส่งไปยัง Server ถูกรับไปประมวลผลแล้วและสามารถทำงานไปยัง Process ต่อไป

- `100:` Continue — serverได้รับ request แล้วและ client สามารถส่ง request body ต่อได้
- `101:` Switching Protocols — client ต้องการเปลี่ยน protocol
- `102:` Checkpoint — server กำลังประมวลผล


## 2xx (Successful)
Request ที่ Client ส่งไปยัง Server ถูกประมวลผลเรียบร้อยและไม่มี Error ใดๆ มักจะ Response กับ Success นั้นเอง นิยมใช้ Status 200 ในการตอบกลับ

- `200:` OK — การส่ง request สำเร็จ
- `201:` Created — client create ข้อมูลลง data base สำเร็จ
- `202:` Accepted — request สำหรับแล้ว แต่ยัง server ยังประมวลผลไม่เสร็จ
- `203:` Non-Authoritative Information — server ประมวลผลเรียบร้อยแล้ว แต่กำลัง return ข้อมูลที่อาจมาจากแหล่งอื่น
- `204:` No Content — server ประมวลผลเรียบร้อยแล้ว แต่ไม่มีเนื้อหาส่งคืน
- `205:` Reset Content — server ได้ดำเนินการสำเร็จแล้ว แต่ไม่มีเนื้อหาส่งคืน ต่างจากรหัส 204 ตรงที่การตอบรับนี้ client จำเป็นต้อง reset document view
- `206:` Partial Content — serverส่งข้อมูลมาให้บางส่วน ตามที่ client ต้องการตาม header

## 3xx (Redirection)
Request ที่ Client ส่งไปยัง server นั้นถูก Redirect ไปประมวลผลที่อื่น เพื่อทำให้ Process สำเร็จ

- `300:` Multiple Choices — client สามารถเลือกลิงค์ที่จะ redirect ไป (ไม่เกิน 5 ลิงค์)
- `301:` Moved Parmanently — request ย้ายไป URL อื่นถาวร
- `302:` Found — request นี้ย้ายไป URL อื่นชั่วคราว
- `303:` See Other — request ที่เรียกนี้อยู่ภายใต้ URL อื่น
- `304:` Not Modified — request ที่เรียกนี้ยังมีเนื้อหายังไม่ได้แก้ไขตั้งแต่การเรียกครั้งล่าสุด 4xx (Client Error)

## 4xx (Client Error)
Status นี้จะเกิดขึ้นก็ต่อเมื่อมี Error ที่มาจาก Request Body ของ Client ผิดพลาด, URL ผิด หรือ Syntax ผิดก็ตาม

- `400:` Bad Request — client ส่ง syntax หรือ body request ไม่ถูกต้อง
- `401:` Unauthorized — client ยัง ไม่ได้ระบุตัวตน หรือไม่มี header
- `402:` Payment Required — มีการเรียกชำระเงิน (ใช้ในอนาคต)
- `403:` Forbidden — client ระบุตัวตนแล้วแต่ไม่มีสิทธิ์เข้าถึงส่วนนี้
- `404:` Not Found — ไม่พบหน้าที่ร้องขอ
- `405:` Method Not Allowed method — ไม่ถูกต้อง ดูให้ดีว่าใช้ get, post, put หรือ delete
- `406:` Not Acceptable — header ของ request ไม่สัมพันธ์กัน
- `413:` Request Entity Too Large — requestใหญ่เกินกว่าที่จะส่งได้
- `414:` Request-URI Too Long — URL ยาวเกินไป
- `415:` Unsupported Media Type — server ไม่รู้จักชนิดของรูปหรือสื่อที่เรียก

## 5xx (Server Error)
Status นี้จะเกิดขึ้นต่อเมื่อ Server มีปัญหาบางอย่าง

- `500:` Internal Server Error — มีข้อผิดพลาดบางอย่างภายใน server โดยไม่ทราบสาเหตุ
- `501:` Not Implemented — server ไม่เข้าใจ request หรือไม่สามารถทำงานตามคำสั่งได้
- `502:` Bad Gateway —server เป็น Gateway หรือ Proxy ได้รับ response ผิดพลาดจาก server อื่น
- `503:` Service Unavailable — ใช้งานเกินพิกัด(ล่ม) หรือกำลังปรับปรุง server
- `504:` Gateway Timeout — server ไม่ได้รับตอบสนองจาก server อื่น จนหมดเวลากันก่อน

### อ้างอิง
https://medium.com/i-gear-geek/http-status-code-%E0%B8%97%E0%B8%B5%E0%B9%88-software-developer-%E0%B8%84%E0%B8%A7%E0%B8%A3%E0%B8%A3%E0%B8%B9%E0%B9%89-6521603e7c75
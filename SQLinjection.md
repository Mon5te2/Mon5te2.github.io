![image](https://github.com/Mon5te2/Mon5te2.github.io/assets/135462462/c48474ae-99a7-4140-8da7-1e0121861297)

**_SQL Injection คืออะไร_**
SQL Injection เป็นช่องโหว่ด้านความปลอดภัยของ web application ที่ทำให้ Hacker สามารถแอบหาข้อมูล สืบค้น web application ของเรา โดยทำกับ Database มักจะช่วยให้ Hacker ดูข้อมูลที่เราไม่สามารถค้นได้ และเป็นข้อมูลส่วนตัวของผู้อื่น ยังไม่พอนะคะ Hacker สามารถแก้ไขหรือลบข้อมูลนี้ได้อีกด้วย
โดย Hacker จะใช้คำสั่ง common attack vector หรือ วิธีการที่ Hacker สามารถเข้าถึงคอมพิวเตอร์ หรือ เซิร์ฟเวอร์เครือข่ายเพื่อส่ง Payload ที่เป็นอันตรายมาให้ Hacker เพื่อใช้ในการโจมตี แล้วใช้ SQL code สำหรับ back-end database ทำการจัดการ access ข้อมูล เพื่อที่จะให้มีข้อมูลแสดงออกมา ข้อมูลในที่นี้คือ จำนวนตัวเลข รวมถึง ข้อมูลที่ sensitive ของบริษัท user list หรือ ข้อมูลส่วนตัวของลูกค้า
ผลลัพธ์ของการถูก attack คือสามารถดูข้อมูลส่วนตัวต่างๆ ที่ไม่ได้รับอนุญาติ และ Hacker สามารถลบ ตาราง entire บางเคส Hacker เป็น Admin ของ database ได้
SQLi สิ่งสำคัญคือ จะทำให้ความเชื่อมั่นของลูกค้าลดลง เพราะข้อมูลส่วนตัวของลูกค้า คือ เบอร์โทรศัพท์ ที่อยู่ เลขบัตรเคดิต จะถูกขโมยไปโดย Hacker
**_ในส่วนของ SQL queries_**
เป็น ภาษาของ SQL ที่ใช้ เข้าถึงและจัดการกับ databaseได้เพื่อที่จะใช้คำสั่งในการ execute หรือ เรียกข้อมูลกลับมา update Read Delete ข้อมูลได้ และสามารถดูข้อมูลของแต่ละ user ได้ อีกด้วย

**_ประเภท ของ SQL Injection_**

**1.In-band SQLi (Classic)**
Hacker ใช้ การสื่อสาร channel เดี่ยวกันในการ launch เพื่อได้รับผลลัพธ์ โดยประเภทนี้ เป็นแบบเรียบง่ายและมีประสิทธิภาพ เป็นประเภทที่ส่วนมากใช้ในการ attack ค่ะ ซึ่ง SQLi มี2 method ย่อย คือ
+ Error-based SQLi : Hacker ทำให้เกิด database error message และ Hacker สามารถใช้ data ของข้อมูล ภายใต้ข้อบังคับของ error message เพื่อรับข้อมูลเกี่ยวกับ Database Structure
+ Union-based SQLi :เป็นอีกเทคนิคที่ advantage ของ UNION SQL operator ซึ่งรวมคำสั่งการเลือกหลายรายการเข้าด้วยกันสร้างโดย database เพื่อรับ single HTTP response การตอบกลับ (response )อาจมีข้อมูลที่ Hacker สามารถใช้ประโยชน์ได้

**2.Inferential (Blind) SQLi**
Hacker ส่งข้อมูล payload ไปยัง server และสังเกตการ response เพื่อดูพฤติกรรมของ server แล้วเรียก blind SQLi เพราะข้อมูลที่ส่งไปไม่มีการถ่ายโอนข้อมูลจาก databaseเลย ดังนั้น Hackerจึงไม่สามารถเห็นข้อมูลเกี่ยวกับการ attack in-band ได้
Blind SQL injection ใช้การ response และดูรูปแบบพฤติกรรมของ server ดังนั้นโดยทั่วไปแล้ว server เหล่านี้จะทำงานได้ช้าลง แต่เป็นอันตรายได้ค่ะ แบ่งได้เป็น
+ Boolean : Hacker ส่ง SQL query ไปยัง database อย่างรวดเร็ว เพื่อให้ application ส่งผลลัพธ์กลับมา ผลลัพธ์จะแตกต่างกันไปขึ้นอยู่กับว่า SQL query เป็น True หรือ False แล้วดูผลลัพธ์ HTTP response โดยไม่ต้องอาศัยข้อมูลจาก database
+ Time-based : Hackerส่ง SQL query ไปยัง database ซึ่งทำให้ database รอ (เป็นระยะเวลาเป็นวินาที) ก่อนจึงจะสามารถตอบสนองกลับมาได้ Hacker สามารถเห็นได้จากเวลาที่ database ใช้ในการตอบกลับ ไม่ว่าคำค้นหาจะเป็น True หรือ False ก็ตาม ผลลัพธ์ HTTP response จะถูกสร้างขึ้นทันที หรือ หลังจากระยะเวลารอ

**3.Out-of-band SQLi**
Hacker สามารถทำการโจมตีรูปแบบนี้ได้ก็ต่อเมื่อเปิดใช้งาน features บางอย่างบน database server ที่ใช้โดย web application เท่านั้น Hacker รูปแบบนี้ส่วนใหญ่จะใช้เป็น alternative แทน SQLi แบบ in-band และ inferential SQLi
Out-of-band SQLi จะทำการเมื่อ Hacker ไม่สามารถใช้ช่องทางเดียวกันเพื่อเริ่มการโจมตีและรวบรวมข้อมูล เมื่อ Server ช้าเกินไปและไม่เสถียรสำหรับการทำการนี้ เทคนิคนี้ใช้ความจุของ Server ในการสร้างคำขอ DNS หรือ HTTP เพื่อส่งข้อมูลไปยัง Hacker

**ตัวอย่างของSQL injection**
Hacker ที่ต้องการทำ SQL injection จะใช้คำสั่ง standard SQL query เพื่อใช้ประโยชน์จากช่องโหว่ของ input ที่ไม่ได้รับการตรวจสอบใน database มีหลายวิธีในการดำเนินการ ในที่นี้เป็นตัวอย่างการทำงานของ SQLi ค่ะ
![image](https://github.com/Mon5te2/Mon5te2.github.io/assets/135462462/d70d3155-0b14-4390-8dbe-92204481aaa6)

ตัวอย่าง เมื่อดึงข้อมูล input ของผลิตภัณฑ์ มา ซึ่ง Hacker สามารถแก้ไขเพื่ออ่าน HTTPได้ เช่น http://www.store.com/items/items.asp?itemid=999 หรือ 1=1 เป็นผลให้แบบ SQL query ที่เกี่ยวข้องมีลักษณะดังนี้:

SELECT ItemName, ItemDescription
FROM Items
WHERE ItemNumber = 999 OR 1=1

และเนื่องจากคำสั่ง 1 = 1 เป็นจริงเสมอ การ query จะส่ง return product names และ descriptions ทั้งหมดใน database ถึงแม้ไม่มีสิทธิ์เข้าถึงก็ตาม

Hacker ยังสามารถใช้ประโยชน์จาก characters ที่กรองไม่ถูกต้องเพื่อแก้ไขคำสั่ง SQL รวมถึงการใช้ semicolon เพื่อแยกสองฟิลด์ออกจากกัน

ตัวอย่างเช่น input นี้ คือ http://www.store.com/items/iteams.asp?itemid=999; ผู้ใช้ DROP TABLE จะสร้าง SQL query ต่อไปนี้:

SELECT ItemName, ItemDescription
FROM Items
WHERE ItemNumber = 999; DROP TABLE USERS

ในการ DROP TABLE ทำให้ database ของ user ทั้งหมดสามารถถูกลบออกได้

อีกวิธีหนึ่งที่สามารถจัดการคำสั่ง SQL ได้ก็คือการใช้คำสั่ง UNION SELECT มันคือคำสั่งที่รวมการสืบค้นข้อมูลแล้ว SELECT เลือกที่ไม่เกี่ยวข้องสองรายการออกหลังจากนั้นดึงข้อมูลจากตาราง database ที่แตกต่างกัน

ตัวอย่างเช่น การป้อนข้อมูล http://www.store.com/items/items.asp?itemid=999 username UNION SELECT กับ password FROM USERS จะสร้าง SQL query ต่อไปนี้:

SELECT ItemName, ItemDescription
FROM Items
WHERE ItemID = ‘999’ UNION SELECT Username, Password FROM Users;

การใช้คำสั่ง UNION SELECT นี้จะเลือก request ของ ItemName ItemDescription และ ItemID เท่ากับ 999 แล้วดึงชื่อและรหัสผ่าน ของผู้ใช้ทุกคนใน database ได้ค่ะ

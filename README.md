# ตลาดหุ้นมีความสัมพันธ์กับGDP per capitaไหม จีนหรือสหรัฐที่มีความสัมพันธ์ของ GDP per capita และตลาดหุ้นกับประเทศอื่นมากกว่ากัน
# Author
สุชาวลี จีระธัญญาสกุล
ID: 6420422021
Subject: DADS5001
# Dataset Information
1. ข้อมูล GDP per capita ของแต่ละประเทศ  267 row, 66 column
2. ข้อมูลชื่อประเทศในแต่ละทวีป 235 row ,5 column
3. ข้อมูลStock market ของแต่ละประเทศ 152 row, 32 column
# Challenge
1. ข้อมูลของตลาดหุ้นแต่ละประเทศหายาก และน้อย มี null ค่อนข้างเยอะ เพราะบางประเทศก็เพิ่งมีตลาดหุ้น หรือบางประเทศเพิ่งมีตลาดหุ้นที่เปิดใหม่
2. การจัดการ Format ของตารางเพื่อสะดวกต่อการ Combine ข้อมูล ในการนำไปหา correlation
3. การ Plot Graph ที่ยังทำได้ไม่ดีเท่าที่ควร เนื่องจากข้อมูลมีหลายประเทศทำให้กราฟค่อนข้างอ่านยาก
# Code
1.	นำข้อมูลเข้า 3 ไฟล์ เป็นไฟล์ .csv โดยเป็นข้อมูล GDP per capita , ราคาตลาดหุ้นของแต่ละประเทศ และชื่อประเทศในแต่ละทวีป
<img width="1083" alt="image" src="https://user-images.githubusercontent.com/115640119/195871155-995e3aef-9796-43e9-b659-0d9cda083222.png">
<img width="1001" alt="image" src="https://user-images.githubusercontent.com/115640119/195871210-5b981c66-8fc8-40cd-8de9-e43ae1cdccd6.png">
<img width="1078" alt="image" src="https://user-images.githubusercontent.com/115640119/195871287-9a150a6f-0eb9-4046-b737-0ff35c11d159.png">

2.	มี 2 ไฟล์ที่มีข้อมูลที่ขาดหาย โดยเฉพาะไฟล์ราคาตลาดหุ้น โดยใช้ข้อมูลของปี 2007 - 2022 เนื่องจากบางประเทศตลาดหุ้นเปิดมาได้ไม่นาน หรือบางประเทศมีหลายตลาด และถ้านำข้อมูลจากในเว็บไซต์ทั่วไปจะทำให้ได้ประเทศค่อนข้างน้อย จึงทำการขอข้อมูลจากทางบริษัทให้ช่วยดึงข้อมูลจากโปรแกรม Bloomberg แต่ก็ยังไม่ครบ เนื่องจากบางประเทศไม่มีตลาดหุ้น และบางปีก็ไม่มีข้อมูล เนื่องจากเป็นตลาดใหม่ จึงทำการใส่ค่า 0 ลงไปในช่องว่าง และอีกไฟล์ที่มีข้อมูลว่างคือ GDP per capita เนื่องจากในไฟล์เก็บข้อมูลมาตั้งแต่ปี 1960 ทำให้มีข้อมูลขาดหายไปบ้าง แต่ช่วง 2007-2022 มีบางประเทศที่ไม่มีข้อมูล ก็ทำการใส่ค่าช่องว่างให้เป็น 0 เช่นกัน และชื่อประเทศของแต่ละไฟล์ มีตัวพิมพ์เล็ก และตัวพิมพ์ใหญ่ จึงดำเนินการทำให้ชื่อประเทศ ของทุกไฟล์เป็นตัวพิมพ์เล็ก เนื่องจากจะได้สะดวกต่อการ join ชื่อประเทศ และทวีป
<img width="1076" alt="image" src="https://user-images.githubusercontent.com/115640119/195871922-b87d8d7c-86d4-4e6e-8f21-1ec81f379d4f.png">
<img width="1073" alt="image" src="https://user-images.githubusercontent.com/115640119/195872002-ff7e546e-e306-41bf-a654-9ac47583194b.png">

3.	ทำการหาเปอร์เซ็นการเปลี่ยนแปลงของทั้งตลาดหุ้น และGDPPโดย GDPP ใช้ของปี 2005-2019 ส่วนของตลาดหุ้นใช้ปี 2006-2020 ที่ใช้ปีไม่เท่ากันเนื่องจากว่า GDPP ส่วนใหญ่แต่ละประเทศจะประกาศไตรมาสสุดท้ายของทุกปี ทำให้ตลาดหุ้นมักจะส่งผลหลังจากนั้น ทำให้ต้องใช้ข้อมูลของ GDPP ขยับขึ้นมาอีกปี และเมื่อได้ลองหาความสัมพันธ์แล้ว จะมีช่วง COVID-19 ทำให้ข้อมูลผิดปกติไปจากเดิมมาก ทั้งราคาตลาดหุ้น และ GDPP เนื่องจากเศรษฐกิจหยุดชะงัก เลยใช้ถึงแค่ปี 2020 เนื่องจาก COVID-19 เกิดช่วงสิ้นปี 2019
<img width="1081" alt="image" src="https://user-images.githubusercontent.com/115640119/195872302-a735832e-5939-4055-b382-98f4474eac8b.png">
<img width="1084" alt="image" src="https://user-images.githubusercontent.com/115640119/195872353-27d2726f-c5a7-46ff-bee6-83d8ac1ec6d0.png">

4.	ได้ทำการจัดรูปแบบของตารางใหม่ ทั้งของGDPP และราคาตลาดหุ้น ให้อยู่ในรูปแบบตารางให้เหมือนกัน เนื่องจากความสะดวกในการหา correlation และการ  join ของทั้งปีที่ต้องเหมือนกัน และชื่อประเทศที่ต้องเหมือนกัน
<img width="1076" alt="image" src="https://user-images.githubusercontent.com/115640119/195872503-75abc6af-1a28-4202-997f-94f6baed6fa3.png">
<img width="1074" alt="image" src="https://user-images.githubusercontent.com/115640119/195872577-60be1236-6184-4736-8347-9e4bff5ed2a2.png">


5.	ทำ inner join ของทั้ง 3 ไฟล์ โดยแบ่งเป็น 5 ส่วน คือ 

    5.1. GDPP เทียบกับตลาดหุ้นของแต่ละทวีป และแต่ละประเทศ Inner join ของไฟล์ GDPP ตลาดหุ้น และชื่อประเทศในแต่ละทวีป โดย join ตามปี และชื่อประเทศ
    <img width="1073" alt="image" src="https://user-images.githubusercontent.com/115640119/195872773-eab117f6-caa2-4363-8ca5-f544c37ae3bb.png">
  
  
    5.2. GDPP ของประเทศสหรัฐอเมริกาเทียบกับ GDPP ของแต่ละทวีป และแต่ละประเทศ Inner join ของไฟล์ GDPP โดยสร้างชื่อตัวแปรใหม่ว่า us เพื่อเก็บข้อมูลของแค่ประเทศสหรัฐอเมริกา 
    และ join กับประเทศในแต่ละทวีป โดย join ตามปี
    <img width="1071" alt="image" src="https://user-images.githubusercontent.com/115640119/195874605-07c6333a-f408-45cc-98e4-4efd60cf56bc.png">

    5.3. GDPP ของประเทศจีนเทียบกับ GDPP ของแต่ละทวีป และแต่ละประเทศ Inner join ของไฟล์ GDPP โดยสร้างชื่อตัวแปรใหม่ว่า china เพื่อเก็บข้อมูลของแค่ประเทศจีน 
    และ join กับประเทศในแต่ละทวีป โดย join ตามปี
    <img width="1073" alt="image" src="https://user-images.githubusercontent.com/115640119/195873182-814d649d-b60e-4b97-b299-39b0e3591f4b.png">

    5.4. ตลาดหุ้นของประเทศสหรัฐอเมริกาเทียบกับ ตลาดหุ้นของแต่ละทวีป และแต่ละประเทศ Inner join ของไฟล์ตลาดหุ้น โดยสร้างชื่อตัวแปรใหม่ว่า us เพื่อเก็บข้อมูลของแค่ประเทศสหรัฐอเมริกา 
    และ join กับประเทศในแต่ละทวีป โดย join ตามปี
    <img width="1072" alt="image" src="https://user-images.githubusercontent.com/115640119/195872899-61bec9c6-6f1c-4a22-8a56-34e94e0e5d9d.png">
  
    5.5. ตลาดหุ้นของประเทศจีนเทียบกับ ตลาดหุ้นของแต่ละทวีป และแต่ละประเทศ Inner join ของไฟล์ตลาดหุ้น โดยสร้างชื่อตัวแปรใหม่ว่า china เพื่อเก็บข้อมูลของแค่ประเทศจีนและ join 
    กับประเทศในแต่ละทวีป โดย join ตามปี
    <img width="1074" alt="image" src="https://user-images.githubusercontent.com/115640119/195874771-021621c0-3942-466e-8b0c-af15481e273a.png">


6.	ทำการหา correlation ของทั้ง 5 ส่วนด้านบนที่กล่าวมา โดยใช้การหาวิธี Spearman’s correlation เนื่องจาก Spearman’s correlation เป็นการวัดความแรงของความสัมพันธ์ monotonic ระหว่าง 2 ตัวแปร ซึ่งมีค่าตั้งแต่ -1 ถึง 1 โดยที่ข้อมูลไม่ต้องเป็นไปตามเงื่อนไข 
     1. ข้อมูลต้องเป็นแบบ interval หรือ ratio level 
     2. มีความสัมพันธ์เชิงเส้นตรง 
     3. ข้อมูลต้องมีการแจกแจงแบบปกติ
     
     และเนื่องจากข้อมูลไม่ได้เป็นทั้ง 2 ข้อที่กล่าวมา จึงทำการหาแบบ Spearman’s correlation ค่าที่ได้เป็น effect size และสามารถอธิบายความแรงของ correlation ได้ดังนี้
          .00 - .19 = very weak
          .20 - .39 = weak
          .40 - .59 = moderate
          .60 - .79 = strong
          .80 – 1.0 = very strong

7. พอได้ค่า Spearman’s correlation ออกมา จะนำไป plot heatmap เกิดปัญหาตรงที่กราฟอ่านค่ายาก เนื่องจากข้อมูลมีหลายประเทศ และเนื่องจากต้องการหาแค่ความสัมพันธ์ของแต่ละประเทศ จึงทำให้ต้องตัดข้อมูลที่ออกมาจาก Spearman’s correlation ไป 1 หลัก และตัดค่าที่เท่ากับ 1 ออก เนื่องจากค่าที่เป็น 1 คือค่าที่ตัวแปรเหมือนกัน มีความสัมพันธ์กันเอง ซึ่งการมีค่านี้ทำให้กราฟอ่านยากขึ้น หลังจากนั้นจึงเรียงข้อมูลจากมากไปน้อย ก็คือที่มีความสัมพันธ์กันมาก จนไปถึงน้อยและไม่มีความสัมพันธ์กัน และเลือกใช้สีแบบ coolwarm เนื่องจากเป็นโทนสีที่ตัดกัน จึงทำให้สามารถมองข้อมูลได้ง่ายขึ้น
<img width="1003" alt="image" src="https://user-images.githubusercontent.com/115640119/195882827-5a0fd1b4-8ad3-4b40-9ed9-f6465d7c5991.png">
<img width="996" alt="image" src="https://user-images.githubusercontent.com/115640119/195882896-6c80bd0c-700e-43b8-997b-4a66c96f797d.png">


# Analysis Question and Answer
1. ตลาดหุ้น และGDP per capita มีความสัมพันธ์กันไหม

ตอบ แทบจะไม่มีความสัมพันธ์กันในข้อมูลของแต่ละทวีป เนื่องจากค่าที่มากที่สุดที่หาแต่ละทวีปได้คือ Eastern Africa (0.15) ซึ่งอยู่ในเกณฑ์ very weak 
ส่วนของประเทศ มีประเทศ Ghana (0.58) มีความสัมพันธ์กันระดับ moderate , slovenia และ Bangladesh (0.34)  มีความสัมพันธ์กันระดับ weak และ united arab emirates (0.31) มีความสัมพันธ์กันระดับ weak

<img width="204" alt="image" src="https://user-images.githubusercontent.com/115640119/195862165-56251475-b052-4d56-9946-d38f12691a1a.png"> <img width="169" alt="image" src="https://user-images.githubusercontent.com/115640119/195862216-1ba6599b-f354-4c12-a8c3-d9f24d65bc41.png">

![image](https://user-images.githubusercontent.com/115640119/195881671-9f5d1325-f0d4-4373-9d71-c8304efe1ce8.png)
![image](https://user-images.githubusercontent.com/115640119/195881640-e71b7ff4-079a-43d0-9d56-f9069abb4bd7.png)


2. ตลาดหุ้นของประเทศสหรัฐหรือประเทศจีน ใครมีความสัมพันธ์กับประเทศอื่นมากกว่ากัน โดยเทียบจากค่ามากที่สุด

-	ถ้าเปรียบเทียบประเทศสหรัฐอเมริกากับแต่ละทวีป จะมี Australia and New Zealand (0.74)
Western Europe (0.71) Northern Europe (0.7) ที่มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ strong
-	ถ้าเปรียบเทียบประเทศสหรัฐอเมริกากับแต่ละประเทศ จะมี switzerland (0.90) sweden และ netherlands (0.80) nigeria (0.8) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ very strong
-	ถ้าเปรียบเทียบประเทศจีนกับแต่ละทวีป จะมี Southern Asia (0.6) Australia and New Zealand (0.6) Eastern Asia (0.58) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์แบบ strong
-	ถ้าเปรียบเทียบประเทศจีนกับแต่ละประเทศ จะมี slovenia (0.75) india (0.74) vietnam (0.72) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ strong

ตอบ แต่เมื่อเปรียบเทียบแล้ว ตลาดหุ้นของประเทศสหรัฐอเมริกามีความสัมพันธ์กับแต่ละทวีป และแต่ละประเทศที่สูงกว่า เมื่อเทียบกับประเทศจีน จากการเปรียบเทียบจากประเทศที่มีค่ามากที่สุด

<img width="196" alt="image" src="https://user-images.githubusercontent.com/115640119/195862705-ea5a77b0-05eb-4435-9213-2abec8ba0d1a.png"> <img width="226" alt="image" src="https://user-images.githubusercontent.com/115640119/195862731-045a1953-3c8a-4ec7-90d8-bb07d0823484.png">
<img width="221" alt="image" src="https://user-images.githubusercontent.com/115640119/195862746-ea599a42-4780-4744-94e1-6b54f4923a18.png"> <img width="177" alt="image" src="https://user-images.githubusercontent.com/115640119/195866211-5c069f4c-cb6e-4f32-961c-3e098a649e3b.png">
![image](https://user-images.githubusercontent.com/115640119/195881988-6d817229-a9d5-4c39-ada5-bc684fb81186.png)
![image](https://user-images.githubusercontent.com/115640119/195882002-058c4259-655c-458d-b7a5-c57e9a906f0d.png)
![image](https://user-images.githubusercontent.com/115640119/195882054-aa22c54d-c2b3-4692-8bdd-dc7db28ddd2e.png)
![image](https://user-images.githubusercontent.com/115640119/195882069-4b7c4fc3-54fb-46f9-bdd7-eed53d55145b.png)



3. GDP per capita ของประเทศสหรัฐหรือประเทศจีน ใครมีความสัมพันธ์กับประเทศอื่นมากกว่ากัน โดยเทียบจากค่ามากที่สุด

-	ถ้าเปรียบเทียบประเทศสหรัฐอเมริกากับแต่ละทวีป จะมี Australia and New Zealand (0.74)
Western Europe (0.71) Northern Europe (0.7) ที่มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ strong
-	ถ้าเปรียบเทียบประเทศสหรัฐอเมริกากับแต่ละประเทศ จะมี switzerland (0.90) sweden และ netherlands (0.80) nigeria (0.8) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ very strong
-	ถ้าเปรียบเทียบประเทศจีนกับแต่ละทวีป จะมี Southern Asia (0.6) Australia and New Zealand (0.6) Eastern Asia (0.58) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์แบบ strong
-	ถ้าเปรียบเทียบประเทศจีนกับแต่ละประเทศ จะมี slovenia (0.75) india (0.74) vietnam (0.72) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ strong

ตอบ แต่เมื่อเปรียบเทียบแล้ว GDP per capita ของประเทศจีน มีความสัมพันธ์กับแต่ละทวีป และแต่ละประเทศที่สูงกว่า เมื่อเทียบกับประเทศสหรัฐอเมริกา จากเปรียบเทียบจากค่าที่มากที่สุด

<img width="176" alt="image" src="https://user-images.githubusercontent.com/115640119/195866622-1b004cca-9f14-4597-899d-4cb7f9a101b2.png"><img width="245" alt="image" src="https://user-images.githubusercontent.com/115640119/195866648-fe2b1980-0338-465e-b28e-b8964daa940a.png">
<img width="207" alt="image" src="https://user-images.githubusercontent.com/115640119/195866688-b43a3da5-8cb9-4b2c-bb02-ce54c0bb3b4f.png">
<img width="207" alt="image" src="https://user-images.githubusercontent.com/115640119/195866725-8f82d338-24be-4efa-aa3f-67e28da47336.png">

![image](https://user-images.githubusercontent.com/115640119/195882113-1f00e6d1-f3dd-4978-8dd0-204aaa276852.png)
![image](https://user-images.githubusercontent.com/115640119/195882122-796e2f3f-a6f2-4fad-becf-14b9e34f24d2.png)
![image](https://user-images.githubusercontent.com/115640119/195882142-2ac51d28-9453-4381-86ff-62f926980eb7.png)
![image](https://user-images.githubusercontent.com/115640119/195882159-5e41d87a-edc9-4fbb-9ae4-df060804cb62.png)


# Conclusion
ตลาดหุ้นแทบจะไม่มีมีความสัมพันธ์กับGDP per capita ถ้าเทียบตามรายทวีป ต้องดูเป็นประเทศๆไป และจีนมีความสัมพันธ์ทาง GDP per capita มากกว่าสหรัฐ หากต้องการต้องการดู GDP per capita 
ควรดูจากจีน ว่าถ้าจีนโต มีโอกาสสูงที่ประเทศอื่นๆ จะโตตาม ส่วนตลาดหุ้นควรดูจากสหรัฐ เนื่องจากสหรัฐมีความสัมพันธ์กับประเทศอื่นมากกว่าจีน 
ดังนั้นถ้าตลาดหุ้นของสหรัฐสูงขึ้น มีโอกาสสูงที่ทำให้ตลาดหุ้นประเทศอื่นสูงตาม

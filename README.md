# ตลาดหุ้นมีความสัมพันธ์กับรายได้ต่อหัวไหม จีนหรือสหรัฐที่มีความสัมพันธ์กับรายได้ต่อหัว และตลาดหุ้นของประเทศอื่นมากกว่ากัน
# Author
สุชาวลี จีระธัญญาสกุล
ID: 6420422021
Subject: DADS5001
# Dataset Information
1. ข้อมูลรายได้ต่อหัว ของแต่ละประเทศ  267 row, 66 column
2. ข้อมูลชื่อประเทศในแต่ละทวีป 235 row ,5 column
3. ข้อมูลตลาดหุ้น ของแต่ละประเทศ 152 row, 32 column
# Challenge
1. ข้อมูลของตลาดหุ้นแต่ละประเทศหายาก และน้อย มี null ค่อนข้างเยอะ เพราะบางประเทศก็เพิ่งมีตลาดหุ้น หรือบางประเทศเพิ่งมีตลาดหุ้นที่เปิดใหม่
2. การจัดการ Format ของตารางเพื่อสะดวกต่อการรวมข้อมูล ในการนำไปหาความสัมพันธ์
3. การ Plot Graph ที่ยังทำได้ไม่ดีเท่าที่ควร เนื่องจากข้อมูลมีหลายประเทศทำให้กราฟค่อนข้างอ่านยาก
# Code
1.	นำข้อมูลเข้า 3 ไฟล์ เป็นไฟล์ .csv โดยเป็นข้อมูลรายได้ต่อหัว , ราคาตลาดหุ้นของแต่ละประเทศ และชื่อประเทศในแต่ละทวีป
<img width="1083" alt="image" src="https://user-images.githubusercontent.com/115640119/195871155-995e3aef-9796-43e9-b659-0d9cda083222.png">
<img width="1001" alt="image" src="https://user-images.githubusercontent.com/115640119/195871210-5b981c66-8fc8-40cd-8de9-e43ae1cdccd6.png">
<img width="1078" alt="image" src="https://user-images.githubusercontent.com/115640119/195871287-9a150a6f-0eb9-4046-b737-0ff35c11d159.png">

2.	มี 2 ไฟล์ที่มีข้อมูลที่ขาดหาย โดยเฉพาะไฟล์ราคาตลาดหุ้น โดยใช้ข้อมูลของปี 2007 - 2022 เนื่องจากบางประเทศตลาดหุ้นเปิดมาได้ไม่นาน หรือบางประเทศมีหลายตลาด และถ้านำข้อมูลจากในเว็บไซต์ทั่วไปจะทำให้ได้ประเทศค่อนข้างน้อย จึงทำการขอข้อมูลจากทางบริษัทให้ช่วยดึงข้อมูลจากโปรแกรม Bloomberg แต่ก็ยังไม่ครบ เนื่องจากบางประเทศไม่มีตลาดหุ้น และบางปีก็ไม่มีข้อมูล เนื่องจากเป็นตลาดใหม่ จึงทำการใส่ค่า 0 ลงไปในช่องว่าง และอีกไฟล์ที่มีข้อมูลว่างคือ รายได้ต่อหัว เนื่องจากในไฟล์เก็บข้อมูลมาตั้งแต่ปี 1960 ทำให้มีข้อมูลขาดหายไปบ้าง แต่ช่วง 2007-2022 มีบางประเทศที่ไม่มีข้อมูล ก็ทำการใส่ค่าช่องว่างให้เป็น 0 เช่นกัน และชื่อประเทศของแต่ละไฟล์ มีตัวพิมพ์เล็ก และตัวพิมพ์ใหญ่ จึงดำเนินการทำให้ชื่อประเทศ ของทุกไฟล์เป็นตัวพิมพ์เล็ก เนื่องจากจะได้สะดวกต่อการ join ชื่อประเทศ และทวีป
<img width="1076" alt="image" src="https://user-images.githubusercontent.com/115640119/195871922-b87d8d7c-86d4-4e6e-8f21-1ec81f379d4f.png">
<img width="1073" alt="image" src="https://user-images.githubusercontent.com/115640119/195872002-ff7e546e-e306-41bf-a654-9ac47583194b.png">

3.	ทำการหาเปอร์เซ็นการเปลี่ยนแปลงของทั้งตลาดหุ้น และรายได้ต่อหัวโดย รายได้ต่อหัวใช้ของปี 2005-2019 ส่วนของตลาดหุ้นใช้ปี 2006-2020 ที่ใช้ปีไม่เท่ากันเนื่องจากว่า รายได้ต่อหัวส่วนใหญ่แต่ละประเทศจะประกาศไตรมาสสุดท้ายของทุกปี ทำให้ตลาดหุ้นมักจะส่งผลหลังจากนั้น ทำให้ต้องใช้ข้อมูลของรายได้ต่อหัวขยับขึ้นมาอีกปี และเมื่อได้ลองหาความสัมพันธ์แล้ว จะมีช่วง COVID-19 ทำให้ข้อมูลผิดปกติไปจากเดิมมาก ทั้งราคาตลาดหุ้น และรายได้ต่อหัว เนื่องจากเศรษฐกิจหยุดชะงัก เลยใช้ถึงแค่ปี 2020 เนื่องจาก COVID-19 เกิดช่วงสิ้นปี 2019
<img width="1081" alt="image" src="https://user-images.githubusercontent.com/115640119/195872302-a735832e-5939-4055-b382-98f4474eac8b.png">
<img width="1084" alt="image" src="https://user-images.githubusercontent.com/115640119/195872353-27d2726f-c5a7-46ff-bee6-83d8ac1ec6d0.png">

4.	ได้ทำการจัดรูปแบบของตารางใหม่ ทั้งของรายได้ต่อหัว และราคาตลาดหุ้น ให้อยู่ในรูปแบบตารางให้เหมือนกัน เนื่องจากความสะดวกในการหา correlation และการ  join ของทั้งปีที่ต้องเหมือนกัน และชื่อประเทศที่ต้องเหมือนกัน
<img width="1076" alt="image" src="https://user-images.githubusercontent.com/115640119/195872503-75abc6af-1a28-4202-997f-94f6baed6fa3.png">
<img width="1074" alt="image" src="https://user-images.githubusercontent.com/115640119/195872577-60be1236-6184-4736-8347-9e4bff5ed2a2.png">


5.	ทำ inner join ของทั้ง 3 ไฟล์ โดยแบ่งเป็น 5 ส่วน คือ 

    5.1. รายได้ต่อหัวเทียบกับตลาดหุ้นของแต่ละทวีป และแต่ละประเทศ Inner join ของไฟล์ รายได้ต่อหัว ตลาดหุ้น และชื่อประเทศในแต่ละทวีป โดย join ตามปี และชื่อประเทศ
    <img width="1073" alt="image" src="https://user-images.githubusercontent.com/115640119/195872773-eab117f6-caa2-4363-8ca5-f544c37ae3bb.png">
  
  
    5.2. รายได้ต่อหัวของประเทศสหรัฐอเมริกาเทียบกับ รายได้ต่อหัวของแต่ละทวีป และแต่ละประเทศ Inner join ของไฟล์รายได้ต่อหัว โดยสร้างชื่อตัวแปรใหม่ว่า us เพื่อเก็บข้อมูลของแค่ประเทศสหรัฐอเมริกา 
    และ join กับประเทศในแต่ละทวีป โดย join ตามปี
    <img width="1071" alt="image" src="https://user-images.githubusercontent.com/115640119/195874605-07c6333a-f408-45cc-98e4-4efd60cf56bc.png">

    5.3. รายได้ต่อหัวของประเทศจีนเทียบกับรายได้ต่อหัวของแต่ละทวีป และแต่ละประเทศ Inner join ของไฟล์รายได้ต่อหัว โดยสร้างชื่อตัวแปรใหม่ว่า china เพื่อเก็บข้อมูลของแค่ประเทศจีน 
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

# Explain about color in graph
สีของกราฟจะแสดงความสัมพันธ์ โดยสีแดงคือมีความสัมพันธ์กัน และสีน้ำเงินคือไม่มีความสัมพันธ์ซึ่งกันและกัน ความเข้มของสีจะแสดงถึงระดับความรุนแรงของความสัมพันธ์ เข้มมากก็จะมีความสัมพันธ์กันมาก

# Analysis Question and Answer
1. ตลาดหุ้น และรายได้ต่อหัวมีความสัมพันธ์กันไหม

ถ้าเปรียบเทียบจากสีของกราฟกราฟที่มีความสัมพันธ์กันจะมีสีแดง และไม่มีความสัมพันธ์กันจะมีสีน้ำเงิน จะเห็นว่าเป็นสีฟ้าค่อนไปทางน้ำเงิน ยกเว้นประเทศ Ghana

<img width="438" alt="image" src="https://user-images.githubusercontent.com/115640119/196042334-d45a0617-55cb-4fee-b327-c11384329402.png"> <img width="434" alt="image" src="https://user-images.githubusercontent.com/115640119/196042342-8b6e5cc0-d8ce-4039-8e6a-b602730bc4b8.png">

ตอบ แทบจะไม่มีความสัมพันธ์กันในข้อมูลของแต่ละทวีป เนื่องจากค่าที่มากที่สุดที่หาแต่ละทวีปได้คือ Eastern Africa (0.15) ซึ่งอยู่ในเกณฑ์ very weak 
ส่วนของประเทศ มีประเทศที่มีความสัมพันธ์มากสุดคือประเทศ Ghana (0.58) มีความสัมพันธ์กันระดับ moderate จึงควรดูเป็นรายประเทศ

2. ตลาดหุ้นของประเทศสหรัฐหรือประเทศจีน ใครมีความสัมพันธ์กับประเทศอื่นมากกว่ากัน

-	ถ้าเปรียบเทียบประเทศสหรัฐอเมริกากับแต่ละทวีป มีค่าเฉลี่ยของความสัมพันธ์อยู่ที่ 0.53 โดยจะมี Australia and New Zealand (0.74)
Western Europe (0.71) Northern Europe (0.7) ที่มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ strong
-	ถ้าเปรียบเทียบประเทศสหรัฐอเมริกากับแต่ละประเทศ มีค่าเฉลี่ยของความสัมพันธ์อยู่ที่ 0.53 โดยมี switzerland (0.90) sweden และ netherlands (0.80) nigeria (0.8) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ very strong
-	ถ้าเปรียบเทียบประเทศจีนกับแต่ละทวีป จะมีค่าเฉลี่ยของความสัมพันธ์อยู่ที่ 0.47 โดยมี Southern Asia (0.6) Australia and New Zealand (0.6) Eastern Asia (0.58) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์แบบ strong
-	ถ้าเปรียบเทียบประเทศจีนกับแต่ละประเทศ มีค่าเฉลี่ยของความสัมพันธ์อยู่ที่ 0.47 โดยมี slovenia (0.75) india (0.74) vietnam (0.72) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ strong

<img width="267" alt="image" src="https://user-images.githubusercontent.com/115640119/196041588-b45f38ac-21d6-4197-9d03-8970dc68ac7c.png">


โดยสีแดงบ่งบอกถึงมีความสัมพันธ์กัน สีน้ำเงินไม่ม่ความสัมพันธ์ซึ่งกันและกัน โดยจะสังเกตว่าสีแดงของทางฝั่งสหรัฐจะเข้มกว่าของทางฝั่งจีน

<img width="361" alt="image" src="https://user-images.githubusercontent.com/115640119/196042549-ee1fd50d-288d-4d04-9b15-950b1117a63a.png"> <img width="373" alt="image" src="https://user-images.githubusercontent.com/115640119/196042563-bfb8ef5a-52c9-4e38-92f6-e565b72dbeee.png">
<img width="339" alt="image" src="https://user-images.githubusercontent.com/115640119/196042579-0aa1449a-aa17-47d7-9331-eecbff29824f.png"> <img width="377" alt="image" src="https://user-images.githubusercontent.com/115640119/196042593-51c47087-b306-4ed7-9017-160c6dbb3ff1.png">

![image](https://user-images.githubusercontent.com/115640119/196042643-7390f4b7-8143-4eb1-a330-1286179f0a30.png)


ตอบ ตลาดหุ้นของประเทศสหรัฐอเมริกามีความสัมพันธ์กับแต่ละทวีป และแต่ละประเทศที่สูงกว่า เมื่อเทียบกับประเทศจีน



3. รายได้ต่อหัวของประเทศสหรัฐหรือประเทศจีน ใครมีความสัมพันธ์กับประเทศอื่นมากกว่ากัน

-	ถ้าเปรียบเทียบประเทศสหรัฐอเมริกากับแต่ละทวีป มีค่าเฉลี่ยของความสัมพันธ์อยู่ที่ 0.28 โดยมี Australia and New Zealand (0.74)
Western Europe (0.71) Northern Europe (0.7) ที่มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ strong
-	ถ้าเปรียบเทียบประเทศสหรัฐอเมริกากับแต่ละประเทศ มีค่าเฉลี่ยของความสัมพันธ์อยู่ที่ 0.28 โดยมี switzerland (0.90) sweden และ netherlands (0.80) nigeria (0.8) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ very strong
-	ถ้าเปรียบเทียบประเทศจีนกับแต่ละทวีป มีค่าเฉลี่ยของความสัมพันธ์อยู่ที่ 0.56 โดยมี Southern Asia (0.6) Australia and New Zealand (0.6) Eastern Asia (0.58) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์แบบ strong
-	ถ้าเปรียบเทียบประเทศจีนกับแต่ละประเทศ มีค่าเฉลี่ยของความสัมพันธ์อยู่ที่ 0.56 โดยมี slovenia (0.75) india (0.74) vietnam (0.72) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ strong


<img width="263" alt="image" src="https://user-images.githubusercontent.com/115640119/196044054-6961ea51-dd7c-4223-97db-17934d22f52e.png">

โดยสีแดงบ่งบอกถึงมีความสัมพันธ์กัน สีน้ำเงินไม่ม่ความสัมพันธ์ซึ่งกันและกัน โดยจะสังเกตว่าสีแดงของทางฝั่งของจีนจะเข้ม และมีมากกว่าของทางฝั่งสหรัฐ

<img width="316" alt="image" src="https://user-images.githubusercontent.com/115640119/196044223-03e7bbd9-c98b-4b55-a3eb-9c6cba6ed221.png"><img width="302" alt="image" src="https://user-images.githubusercontent.com/115640119/196044218-0ca3276b-f230-446a-b483-b66e81af994e.png">

<img width="320" alt="image" src="https://user-images.githubusercontent.com/115640119/196044258-ee65717c-6223-46ea-9907-c99201644c89.png"> <img width="338" alt="image" src="https://user-images.githubusercontent.com/115640119/196044245-69c2f5cc-4ab1-4bd1-9b98-1e55c0f7de84.png"> 

![image](https://user-images.githubusercontent.com/115640119/196044313-708f3354-3e88-4e93-978e-317748f29513.png)


ตอบ รายได้ต่อหัวของประเทศจีน มีความสัมพันธ์กับแต่ละทวีป และแต่ละประเทศที่สูงกว่า เมื่อเทียบกับประเทศสหรัฐอเมริกา


# Conclusion
ตลาดหุ้นแทบจะไม่มีมีความสัมพันธ์กับรายได้ต่อหัว ถ้าเทียบตามรายทวีป ต้องดูเป็นประเทศๆไป และจีนมีความสัมพันธ์ทางรายได้ต่อหัว มากกว่าสหรัฐ หากต้องการต้องการดูรายได้ต่อหัว
ควรดูจากจีน ว่าถ้าจีนโต มีโอกาสสูงที่ประเทศอื่นๆ จะโตตาม ส่วนตลาดหุ้นควรดูจากสหรัฐ เนื่องจากสหรัฐมีความสัมพันธ์กับประเทศอื่นมากกว่าจีน 
ดังนั้นถ้าตลาดหุ้นของสหรัฐสูงขึ้น มีโอกาสสูงที่ทำให้ตลาดหุ้นประเทศอื่นสูงตาม

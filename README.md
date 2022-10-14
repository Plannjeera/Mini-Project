# ตลาดหุ้นมีความสัมพันธ์กับGDP per capitaไหม และเราควรดูจากประเทศจีนหรือสหรัฐหากต้องการดู GDP และตลาดหุ้น
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
# Analysis Question and Answer
1. ตลาดหุ้น และGDP per capita มีความสัมพันธ์กันไหม

ตอบ แทบจะไม่มีความสัมพันธ์กันในข้อมูลของแต่ละทวีป เนื่องจากค่าที่มากที่สุดที่หาแต่ละทวีปได้คือ Eastern Africa (0.15) ซึ่งอยู่ในเกณฑ์ very weak 
ส่วนของประเทศ มีประเทศ Ghana (0.58) มีความสัมพันธ์กันระดับ moderate , slovenia และ Bangladesh (0.34)  มีความสัมพันธ์กันระดับ weak และ united arab emirates (0.31) มีความสัมพันธ์กันระดับ weak

<img width="204" alt="image" src="https://user-images.githubusercontent.com/115640119/195862165-56251475-b052-4d56-9946-d38f12691a1a.png"> <img width="169" alt="image" src="https://user-images.githubusercontent.com/115640119/195862216-1ba6599b-f354-4c12-a8c3-d9f24d65bc41.png">
![image](https://user-images.githubusercontent.com/115640119/195864030-d6088df5-167e-4dab-87b4-750dfcac9d20.png)![image](https://user-images.githubusercontent.com/115640119/195864967-2ab66ee3-e19e-466d-b256-42a0f9e84c14.png)




2. ตลาดหุ้นของประเทศสหรัฐหรือประเทศจีน ใครมีความสัมพันธ์กับประเทศอื่นมากกว่ากัน โดยเทียบจากค่ามากที่สุด

-	ถ้าเปรียบเทียบประเทศสหรัฐอเมริกากับแต่ละทวีป จะมี Australia and New Zealand (0.74)
Western Europe (0.71) Northern Europe (0.7) ที่มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ strong
-	ถ้าเปรียบเทียบประเทศสหรัฐอเมริกากับแต่ละประเทศ จะมี switzerland (0.90) sweden และ netherlands (0.80) nigeria (0.8) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ very strong
-	ถ้าเปรียบเทียบประเทศจีนกับแต่ละทวีป จะมี Southern Asia (0.6) Australia and New Zealand (0.6) Eastern Asia (0.58) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์แบบ strong
-	ถ้าเปรียบเทียบประเทศจีนกับแต่ละประเทศ จะมี slovenia (0.75) india (0.74) vietnam (0.72) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ strong

ตอบ แต่เมื่อเปรียบเทียบแล้ว ตลาดหุ้นของประเทศสหรัฐอเมริกามีความสัมพันธ์กับแต่ละทวีป และแต่ละประเทศที่สูงกว่า เมื่อเทียบกับประเทศจีน โดยเปรียบเทียบจากประเทศที่มีค่ามากที่สุด

<img width="196" alt="image" src="https://user-images.githubusercontent.com/115640119/195862705-ea5a77b0-05eb-4435-9213-2abec8ba0d1a.png"> <img width="226" alt="image" src="https://user-images.githubusercontent.com/115640119/195862731-045a1953-3c8a-4ec7-90d8-bb07d0823484.png">
<img width="221" alt="image" src="https://user-images.githubusercontent.com/115640119/195862746-ea599a42-4780-4744-94e1-6b54f4923a18.png"> <img width="177" alt="image" src="https://user-images.githubusercontent.com/115640119/195866211-5c069f4c-cb6e-4f32-961c-3e098a649e3b.png">

![image](https://user-images.githubusercontent.com/115640119/195865235-6c087e3a-1b33-4b94-b3ff-715d43c67928.png)
![image](https://user-images.githubusercontent.com/115640119/195865541-42afa4b7-91cf-47b9-911f-f6e3c926b0dd.png)
![image](https://user-images.githubusercontent.com/115640119/195865623-91e528db-3461-4189-bd13-da6800c82a42.png)
![image](https://user-images.githubusercontent.com/115640119/195865659-3526c6ef-938d-49f8-815e-9b5c048d9e6c.png)


3. GDP per capita ของประเทศสหรัฐหรือประเทศจีน ใครมีความสัมพันธ์กับประเทศอื่นมากกว่ากัน โดยเทียบจากค่ามากที่สุด

-	ถ้าเปรียบเทียบประเทศสหรัฐอเมริกากับแต่ละทวีป จะมี Australia and New Zealand (0.74)
Western Europe (0.71) Northern Europe (0.7) ที่มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ strong
-	ถ้าเปรียบเทียบประเทศสหรัฐอเมริกากับแต่ละประเทศ จะมี switzerland (0.90) sweden และ netherlands (0.80) nigeria (0.8) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ very strong
-	ถ้าเปรียบเทียบประเทศจีนกับแต่ละทวีป จะมี Southern Asia (0.6) Australia and New Zealand (0.6) Eastern Asia (0.58) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์แบบ strong
-	ถ้าเปรียบเทียบประเทศจีนกับแต่ละประเทศ จะมี slovenia (0.75) india (0.74) vietnam (0.72) มีความสัมพันธ์กันมากสุด 3 อันดับแรก โดยมีความสัมพันธ์กันแบบ strong

ตอบ แต่เมื่อเปรียบเทียบแล้ว GDP per capita ของประเทศจีน มีความสัมพันธ์กับแต่ละทวีป และแต่ละประเทศที่สูงกว่า เมื่อเทียบกับประเทศสหรัฐอเมริกา เมื่อเปรียบเทียบจากค่าที่มากที่สุด

<img width="176" alt="image" src="https://user-images.githubusercontent.com/115640119/195866622-1b004cca-9f14-4597-899d-4cb7f9a101b2.png"><img width="245" alt="image" src="https://user-images.githubusercontent.com/115640119/195866648-fe2b1980-0338-465e-b28e-b8964daa940a.png">
<img width="207" alt="image" src="https://user-images.githubusercontent.com/115640119/195866688-b43a3da5-8cb9-4b2c-bb02-ce54c0bb3b4f.png">
<img width="207" alt="image" src="https://user-images.githubusercontent.com/115640119/195866725-8f82d338-24be-4efa-aa3f-67e28da47336.png">

![image](https://user-images.githubusercontent.com/115640119/195867008-fedde749-78e5-4b7a-a391-356bc2faab12.png)
![image](https://user-images.githubusercontent.com/115640119/195867026-31017265-c684-4bc2-8d58-01c8bd300ea7.png)
![image](https://user-images.githubusercontent.com/115640119/195867080-c2c00d98-8e29-4619-bcb2-0c5f82ab2779.png)
![image](https://user-images.githubusercontent.com/115640119/195867100-20847ac7-4cd3-4949-aba5-261798a0cdb7.png)



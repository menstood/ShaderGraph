#Unity Shader Graph

###แล้วมันคืออะไร 
  " *******ผิดพลาดตรงไหนขออภัยด้วยเขียนตามความเข้าใจของตัวเอง แต่คิดว่าไม่น่าพลาด*** "

Shader Editor ของตัว Unity เองเป็น Node Visual ซึ่งที่ผ่านมา Unity ไม่เคยมี Shader Editor ของตัวเอง
ทำให้การเขียน Shader เองนั้นทำได้ยากสำหรับผู้ที่ต้องการเริ่มต้นใหม่ Shader Graph จำเป็นต้องใช้คู่ไปกับ BuildPipeline ตัวใหม่ของ Unity 

# Pro/Cons
###ข้อดี
 * **BuildPipeline** อันใหม่ตรงตามการใข้งานของผู้ใช้ ด้วย Performance สูงสุด

 * **Base on HLSL** คือ Shader Graph เป็น HLSL(High Level Shader Language)ตั้งแต่แรก ซึ่งShader Languageเก่าของ Unityนั้นเป็น CG ซึ่งเวลานำไป 
     ใช้งานนั้น Program จะแปลงจาก CG ไปเป็น HLSL หรือ GLSL ตาม Platform ที่ใช้งานอยู่ดี และสุดท้ายคือ Nvidia เลิกซัพพอท CG แล้ว

 * **Native** เพราะเป็น Native ของUnityเอง ทำให้Community และการแก้บัคต่างๆ ได้รับการแก้ไขและพัฒนาเพิ่มตลอดเวลา
###ข้อเสีย
 * **Feature** ยังน้อยอยู่ยังทำบางอย่างไม่ได้ ในตอนนี้ต้องรออัพเดทในอนาคต
 * **Bug** ยังมีบัคแปลกๆบางอย่างที่ทำให้ตัว Editor มีปัญหาหรือ Node แสดงผลไม่ถูกต้องรอการแก้ไขต่อไป

***
# How to Install


Shader Graph นั้นเราต้องลงผ่าน **Package Manager**
และจำเป็นต้องลงRender Pipeline ตัวใหม่ก่อนมีให้เลือกระหว่าง

**Lightweight Render Pipeline**

**High-Definition Render Pipeline**

หลังจากนั้นค่อยลง **Shader Graph**

โดยไปที่ Menu Window > Package Manager 

หลังจากนั้น เลือก Advanceแล้วเลือก Show preview packages 

* ลง Package ของ RenderPipeline ที่อยากได้ (แนะนำ Lightwieght ก่อนสำหรับมือใหม่)
* ลง Package Shader Graph

ขั้นต่อมาเราจะทำการสร้าง RenderPipeline สำหรับProjectของเราเอง

 * Menu > Assets > Create > Rendering > Lightweight Render Pipeline Asset เราจะได้ ตัว PipelineAssetของเรามา ตั้งชื่อตามสะดวก

 * ไปที่ Project Setting 
 * เลือกหัวข้อ Graphics 
 * ช่อง Scriptable Render Pipeline Settings Browse ไปหา Pipeline Asset ที่เราสร้างเมื่อกี้


**Note** สำหรับคนขี้เกียจก็ Clone ลงไปเลย

***

#How to Create

 * Menu > Assets > Create > Shader > PBR Graph เราก็จะได้ไฟล์ Shader ของเรามา
 * ตั้งชื่อให้เรียบร้อย แล้วดับเบิลคลิ้ก หรือ **Open Shader Editor** ใน Inspector ของไฟล์Shader
 * ถ้าเราลง Pipeline ถูกต้อง Unityจะเปิดหน้า Editor ของ Shader ให้

***
#Shader Graph Editor

 เปิดมาเราจะเจอ Node แรกชื่อ **PBR Master** เราจะเรียก Node นี้ว่า Master Node 
  

###Master Node

เป็น Node ที่ประกอบไปด้วย Setting และ Output ของ Shader
 
**Setting** รูปเฟืองข้างหลัง Master Node 

 * WorkFlow คือ ลักษณะการสะท้องแสง
* Metalic พื้นผิวแบบโลหะ จะสะท้อนแสงตามปกติ แสงเข้ามาสีอะไรก็จะสะท้อนบนวัตถุเป็นสีนั้น
* Specular จะมีความมันวาวเป็นพิเศษ ใช้ควบคู่กับ Specular Map เพื่อควบคุมความมันวาวและสีที่สะท้อนออกไป

 * Surface ลักษณะพื้นผิว
* Opaque ทึบแสง
* Transparent โปร่งแสง

 * Blend Blend Mode ของ Shader
 * Two Sided ทำให้ Shaderของเรา Render Backface 

**Output**  *สำหรับ Metalic*

 * Albedo
 * Emission
 * Normal
 * Alpha















	 

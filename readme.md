#Unity Shader Graph

###แล้วมันคืออะไร 
  *" ผิดพลาดตรงไหนขออภัยด้วยเขียนตามความเข้าใจของตัวเอง แต่คิดว่าไม่น่าพลาด "*

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

* WorkFlow คือ การตั้งค่าของการสะท้อนแสงบนพื้นผิวของ Shader
    * Metalic พื้นผิวแบบโลหะ จะสะท้อนแสงตามปกติ แสงเข้ามาสีอะไรก็จะสะท้อนบนวัตถุเป็นสีนั้น
    * Specular จะมีความมันวาวเป็นพิเศษ ใช้ควบคู่กับ Specular Map เพื่อควบคุมความมันวาวและสีที่สะท้อนออกไป

*  Surface ลักษณะพื้นผิว

    * Opaque ทึบแสง
    * Transparent โปร่งแสง

* Blend Blend Mode ของ Shader
* Two Sided ทำให้ Shaderของเรา Render Backface 

**Output**

*เลือกมาเฉพาะที่ใช้บ่อย*

 * Albedo สีของวัตุถุ
 * Emission สีที่เรืองแสงออกมาจากวัตถุ
 * Normal ค่า Normal ของวัตถุ
 * Alpha ค่า Alpha ของ Obejct 
 * AlphaClipThreshold ค่า AlphaClip ของ Object 

###Node

เป็น Node ปกติที่เราจะใช้ สามารถสร้างโดยการ คลิ้งขวาในพื้นที่ว่างเลือก Create Node แบ่งออกเป็นหลายประเภทและ ถ้าเราทำบ่อยแล้วเราสามาถค้นหา Nodeที่ต้องการได้เลยในช่อง Seach 

**Input > Basic**
  *เลือกมาเฉพาะที่ใช้บ่อย*
 
 * **Vector 1 ,2 ,3 ,4** ค่า Vector แต่ละแบบที่ Unityแยกออกมาให้ ซึ่งแท้จริงแล้วใน HLSL มีแค่ Vector4 หมายความว่าต่อให้เราเลือก Vector1 สุดท้ายแล้วจะถูกแปลงให้เป็น (x,0,0,0) อยู่ดีจึงเป็นสิ่งที่ต้องระวังเล็กน้อยเวลาใช้ Vector

 * **Color** สี เป็นค่า Vector 4 ที่ถูกแปลงให้เป็น (R,G,B,A) 

 * **Time** ค่าเวลา Time มีให้เลือกหลายแบบแล้วแต่การใช้งานของเรา 

**Input > Texture**

 * **Texture 2D Asset** ค่า Texture2d ก็คือรูปปกติทั่วไป

 * **Sample Texture 2D** ค่า Texture2D ที่มีการเอามารวมกับ UV และ SamplerMode แล้วกลายเป็น RGBA และเราสามารถกำหนดโหมดของ Textureได้
  * Default คือ เอาค่าเริ่มต้นจาก Texture ที่รับมา
  * Normal คือ ใช้ Textureนี้เป็นค่า Normal











	 

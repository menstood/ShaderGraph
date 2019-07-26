#Unity Shader Graph

###คืออะไร 

Shader Editor ของตัว Unity เองเป็น Node Visual ซึ่งที่ผ่านมา Unity ไม่เคยมี Shader Editor ของตัวเอง
ทำให้การเขียน Shader เองนั้นทำได้ยากสำหรับผู้ที่ต้องการเริ่มต้นใหม่ Shader Graph จำเป็นต้องใช้คู่ไปกับ BuildPipeline ตัวใหม่ของ Unity 

### How to Install

Shader Graph นั้นเราต้องลงผ่าน **Package Manager**
และจำเป็นต้องลงRender Pipeline ตัวใหม่ก่อนมีให้เลือกระหว่าง

**Lightweight Render Pipline**

**High-Definition Render Pipeline**

หลังจากนั้นค่อยลง **Shader Graph**

โดยไปที่ Menu Window > Package Manager 

หลังจากนั้น เลือก Advanceแล้วเลือก Show preview packages 

* ลง Package ของ RenderPipline ที่อยากได้ (แนะนำ Lightwieght ก่อนสำหรับมือใหม่)
* ลง Package Shader Graph

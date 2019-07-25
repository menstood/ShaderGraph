=MasterNode=
+WorkFlow 
	- Metalic 
	- Specular **Require SpecularMap

+Surface
	- Opaque
	- Transparent
+Blend ** Transparent Only
+TwoSide
	
=Output=
+Albedo
+Emission
+Normal
+Alpha

=Input=
+Color
+Texture
+Vector
+HDR Color
+Time

=Method=
+SampleTexture2d
+Normal Strength
+Split
+Fresnel
+OneMinus
+Remap

=Math=
+Multiply
+Add
+Power
+Subtract
+Sine

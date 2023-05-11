# Raymarching
Ray marching is a technique used in computer graphics to render 3D scenes by iteratively marching along a ray and determining the distance to the nearest surface. The technique is particularly useful for rendering complex and detailed shapes, such as fractals and distance fields.

The basic idea behind ray marching is to define a distance function that returns the distance to the nearest surface at a given point in space. This distance function can be used to define a ray marching algorithm that iteratively moves along the ray, updating the position and distance to the nearest surface at each step.

One of the advantages of ray marching is that it can be easily parallelized, allowing for real-time rendering of complex scenes on modern graphics hardware. Additionally, the technique can be extended to support various lighting models and effects, such as shadows and reflections.

Overall, ray marching is a powerful technique for rendering complex scenes in computer graphics, and is an important tool for artists and developers working in the field.

by CharGPT

## 翻譯翻譯

- 從眼睛看出去的方向形成一條射線
- 從眼睛位置開始，沿著射線一步一步向前偵測，看是否有”碰撞到物體”
    - 如果有，則進行著色
    - 如果沒有且尚未到達前進步數上限，則繼續前進
    - 若以達到步數上限，放棄著色或以黑色替代
- 碰撞到物體
    - 採用 SDF(signed distance functions) 進行偵測
    - 請看 [Signed Distance Field(基础篇)](https://zhuanlan.zhihu.com/p/93901692)
- 實作上的認知
    - 先拋棄三角面組成的模型的概念，這些不存在 Raymarching 的世界中。
    - 模型在 Raymarching 的世界中都是用數學描述出來的。
    - 在 PixelShader 裡每個 fragment 的位置為“起點”，以 fragement 與 Camera 為方向，打出一條射線一步步向前偵測是否與“數學描述上的模型(SDF)”進行碰撞。

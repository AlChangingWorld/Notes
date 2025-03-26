

Unity中的ECS
Scene 存放实体和系统的容器
**Entity** 
hold component
实体，包含多个组件 至少需要包含一个Transform组件

**Component** 
hold data
Component只包含数据，比如Transform组件
BehaviorComponents 还包含逻辑 比如Camera,Renderer,ScriptComponent

**System**
control object data
System: 保持感兴趣的组件的引用 在onUpdate中处理组件中的数据
RendererSystem: 检查可视性、剔除等操作，在onRender中进行(管线)
RenderSystem: 渲染，在RendererSystem执行onRender之后(流水线)


给物体添加脚本 Conver To Entity
Entity Prefab Authoring 


package Manager中导入
**com.unity.entities**
这个包是 Unity 的实体组件系统（ECS）核心包，用于实现高效的游戏开发架构。它提供了 ECS 的基础设施，允许开发者使用结构化数据进行游戏开发，从而提高性能。它包括了与实体、组件和系统管理相关的功能，使得数据驱动的开发更加高效

**com.unity.entities Graphics**
这个包将实体系统（ECS）和图形渲染结合起来，主要用于通过 ECS 系统来管理和渲染图形对象。它提供了与渲染管线相关的功能，允许开发者更高效地使用 ECS 来处理图形数据和渲染工作。这可以帮助在大规模的图形渲染任务中实现更高效的性能。

**com.unity.burst**
com.unity.burst 是 Unity 的一个高性能编译器包，用于优化代码的执行效率。它主要通过将 C# 代码编译成原生机器码来实现性能提升，尤其适用于需要高性能计算的场景，比如大量数据处理、物理模拟等。

**com.unity.jobs**
com.unity.jobs 是 Unity 的一个包，提供了一种用于多线程编程的高效、轻量级的工作系统。它使得开发者能够更容易地编写并行和多线程代码，从而提高性能，尤其是在数据密集型的应用场景中。

**com.unity.mathematics**
这个包提供了一组高性能的数学库，通常用于游戏开发中的向量、矩阵运算和其他数学运算。它与传统的 UnityEngine.Vector 等 API 相比，在性能上做了优化，特别是在处理大量数据时（比如在 ECS 中）。它包含了像 float3, float4, quaternion 等结构体和数学函数，适合用于高效的数值计算。

**Unity Physics**
可以使用EntityManager 给组件加刚体


Authoring创作模式：即我们熟悉的方便操作的创建预制的模式
Runtime模式：运行模式，即在运行时，在subScene中对应的Entity模式

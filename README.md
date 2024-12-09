# 3DGS Unreal Plugin

# 目录

- [功能列表](#功能列表)
- [试用申请](#试用申请)
- [环境要求](#环境要求)
- [使用说明](#使用说明)
- - [安装步骤](#安装步骤)
- - [调色功能](#调色功能)
- - [运行时接口](#运行时接口)
- - [案例场景](#案例场景)
- - [注意事项](#注意事项)
- [更新日志](#更新日志)



#  功能列表

### 数据支持
- ply（完整的/去掉球谐法向的）
- splat

### 数据管理
- 运行时加载/卸载多个数据
- 支持在UE编辑器中预览，PIE 运行，编译打包运行多种模式。

### 渲染能力
- 支持调色功能
- 旋转/平移/缩放
- 控制相机内参
- 支持深度遮挡

### 外部集成能力
- 提供了一套蓝图和C++接口，方便上层用户集成和使用


#  试用申请
<img src=./doc/sensespace.jpg height=600 /> 



# 环境要求
- Windows 10 系统
- 16G 以上内存，推荐32G 内存
- Unreal Engine 5.1/5.2/5.3

# 使用说明
## 安装步骤
- 把 Sense3DGS 文件夹拷贝到 Engine\Plugins\Marketplace\ 或者工程目录下的Plugins文件夹下面
  
- 打开 Unreal 编辑器，确认插件已经被启用，如果没有，请勾选启用<br>
<br>
![](./Doc/enable_plugin.png)

- 把 3DGS Splat 文件拖放到 Unreal 内容浏览器中，插件会自动创建资产，然后保存<br>
<br>
![](./Doc/import.png)

- 把 3DGS 资产从内容浏览器拖放到场景中，稍等片刻，插件会加载渲染 3DGS 场景 <br>
  <br>
  ![](./Doc/create_actor.png)

## 调色功能
 该功能可以针对模型的色彩平衡进行调整，具体使用方式如：
- 把场景导入编辑器，并拖入放置到到场景中
- 选中要进行调色的模型<br>
<br>
![](./Doc/palette.png)
<br>
![](./Doc/palette2.png)

- 保存场景地图
  

## 运行时接口
- UObject* LoadModel(UObject*, const FString& ModelPath); 创建 3DGS 实例并加载 3DGS 模型
- LoadModelAsync(UObject*, const FString& ModelPath, FLoad3DGSModelCompleted Callback); 创建 3DGS 实例并异步加载 3DGS 模型
- bool RemoveModel(UObject*, UObject* Object) 移除 3DGS 模型
- bool Destroy(UObject*) 移除所有 3DGS 模型并销毁实例
- 具体请详见 SenseGaussianFunctionLibrary.h 注释


## 案例场景
Sense3DGS/Content/Examples/ExampleMap.umap。修改ExampleBP里面的ModelPath变量，指向splat文件
<br>
![](./Doc/model_path.png)



## 注意事项
- 3DGS 场景不受光照的影响
- 建议关闭UE引擎的自动曝光功能，否则颜色会偏白
  




# 更新日志
  ### v1.0.0 2024年9月10日
  - 支持 3DGS 场景在UE引擎中进行可视化预览，包括编辑器中预览，PIE 运行，编译打包运行。
  - 提供了一套蓝图和C++接口，方便上层用户集成和使用。
  - 支持对 3DGS 场景进行平移和旋转。
  - 支持加载多个 3DGS 场景。

  ### v1.1.0 2024年9月18日
  - 支持 ply 模型文件格式
  - 增加调色功能
  - Bug修复
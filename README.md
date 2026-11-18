# 尾流与脏空气 · 创作资源仓库

本仓库用于保存和分发玩家创作的车辆蓝图、地图与预览图。资源采用 JSON 文档格式；车辆体素使用编辑器的 RLE runs 编码。

## 目录约定

```
schemas/
  asset-v1.schema.json
  manifest-v1.schema.json
vehicles/<asset-id>/
  vehicle.json
  preview.png
maps/<asset-id>/
  map.json
  preview.png
```

- 车辆文件使用 `kind: voxvar.car`；地图文件使用 `kind: voxvar.map`。
- 地图保留道路、开放/闭合状态、样条类型、控制点高度、地形笔画、物件和赛事设置。
- 预览图可选；没有预览图时客户端可本地生成。
- 资源 ID 由服务端生成，上传内容不能指定任意文件路径。
- 不在资源文件中保存 GitHub Token、账号密码、个人隐私或可执行脚本。

## 游戏内共享的安全边界

正式的游戏内共享应通过独立上传/下载服务或 GitHub App 后端完成：客户端只获得短期、受限授权；服务端验证资源格式、大小、ID 和发布者权限后再写入仓库。

客户端必须先验证 JSON，再导入本地车库；不得执行资源中的代码。下载资源应设置大小上限、版本兼容检查和重复 ID 处理。

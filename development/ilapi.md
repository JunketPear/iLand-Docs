# API 接口文档

##### `ILAPI_CreateLand` - 创建领地
 - 传入参数
   - xuid - `string` 玩家XUID
   - startpos - `Vec3` 起点坐标
   - endpos - `Vec3` 终点坐标
   - dimid - `number` 维度ID
 - 返回值 `string` 成功创建返回对应的LandID

##### `ILAPI_DeleteLand` - 删除领地
 - 传入参数
   - landId - `string` 领地ID
 - 返回值 `bool` 是否成功删除

##### `ILAPI_GetPlayerLands` - 获取玩家拥有的领地
 - 传入参数
   - xuid - `string` 玩家XUID
 - 返回值
   - `table` 玩家拥有的领地的LandID表

##### `ILAPI_GetLand` - 取得一个领地的全部数据
 - 传入参数
   - landId - `string` 领地ID
 - 返回值
   - `table` 包含领地全部数据的表

##### `ILAPI_UpdatePermission` - 更新领地权限
 - 传入参数
   - landId - `string` 领地ID
   - permName - `string` 权限名
   - value - `bool` 允许或不允许
 - 返回值
   - `bool` 是否修改成功

##### `ILAPI_UpdateSetting` - 更新领地设定
 - 传入参数
   - landId - `string` 领地ID
   - settingName - `string` 设定名
   - value - `bool|table` 设置值
 - 返回值
   - `bool` 是否修改成功

##### `ILAPI_GetOwer` - 获取领地主人
 - 传入参数
   - landId - `string` 领地ID
 - 返回值
   - `string` 主人XUID

##### `ILAPI_PosGetLand` - 通过坐标查询领地
 - 传入参数
   - pos - `Vec4` 任意**整数**坐标
 - 返回值
   - `string` LandID，若没有返回`-1`

##### `ILAPI_GetChunk` - 获得一个区块内加载的领地列表
 - 传入参数
   - pos - `vec2` 任意坐标
   - dimid - `number` 维度ID
 - 返回值
   - `table` 区块内里的列表

##### `ILAPI_GetDistance` - 获取一个坐标与领地边框的最短距离
 - 传入参数
   - landId - `string` 领地ID
   - pos - `Vec4` 任意坐标
 - 返回值
   - `table` 距离

##### `ILAPI_IsPlayerTrusted` - 玩家是否被领地信任
 - 传入参数
   - landId - `string` 领地ID
   - xuid - `string` 玩家XUID
 - 返回值
   - `bool` 是否信任

##### `ILAPI_GetEdge` - 获取领地边框坐标
 - 传入参数
   - landId - `string` 领地ID
 - 返回值
   - `table` 领地边缘坐标数组

##### `ILAPI_IsLandOwner` - 玩家是否是领地主人
 - 传入参数
   - landId - `string` 领地ID
   - xuid - `string` 玩家XUID
 - 返回值
   - `bool` 是否是领地主人

注：此API比使用GetOwner后再判断要快得多，因为使用了反键值表的查询方法，若要判断玩家是否是领地主人应首选此接口。

##### `ILAPI_IsLandOperator` - 玩家是否是领地管理员
 - 传入参数
   - xuid - `string` 玩家XUID
 - 返回值
   - `bool` 是否是领地管理员

##### `ILAPI_GetLandDimension` - 获取领地维数
 - 传入参数
   - landId - `string` 领地ID
 - 返回值
   - `string` 2D或3D 

##### `ILAPI_GetAllTrustedLand` - 获取玩家被信任的领地列表
 - 传入参数
   - xuid - `string` 玩家XUID
 - 返回值
   - `table` 所有信任该玩家的领地LandID表

##### `ILAPI_GetVersion` - 获取iLand版本号
 - 传入参数 `无`
 - 返回值
   - `number` 版本号

##### `ILAPI_GetTpPoint` - 获取领地传送点
!> 此API将在近几个版本弃用，请使用`ILAPI_UpdateSetting`

 - 传入参数
   - landId - `string` 领地ID
 - 返回值
   - `Vec4` 传送点坐标

##### `ILAPI_GetNickname` - 获取领地昵称
!> 此API将在近几个版本弃用，请使用`ILAPI_UpdateSetting`

 - 传入参数
   - landId - `string` 领地ID
   - returnIdIfNameEmpty - `bool` 可选参数，为True时如果玩家的领地没有设定昵称，返回一个未命名提示符与LandID，否则只返回未命名提示符，默认为false。
 - 返回值 
   - `string` 未命名提示符或领地昵称

##### `ILAPI_GetDescribe` - 获取领地备注
!> 此API将在近几个版本弃用，请使用`ILAPI_UpdateSetting`

 - 传入参数
   - landId - `string` 领地ID
 - 返回值
   - `string` 领地备注（可能为空）


##### Example
```lua
-- 示例：调用ILAPI删除领地
cl = lxl.import("ILAPI_DeleteLand")
cl('1145141919810',{x=11,y=4,z=51},{x=41,y=91,z=98},1)

```
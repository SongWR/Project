# 三维API

### 场景加载

#####  :black_medium_small_square:  场景加载信息LoadInfo

接口说明

~~~html
myGameInstance.SendMessage("Connect", "LoadInfo", data);

 <param name="Connect">连接三维载体</param>

 <param name="LoadInfo">加载信息</param>

 <param name="data">传入json参数</param>
~~~

json字段说明

~~~json
{
    "ScenesName": "scene.ab",
    "ScenesPath": "http://192.168.11.106/pcAssetBundles/",
    "ScenesVersion": 0.1,
    "PrefabName": "prefab.ab",
    "PrefabPath": "http://192.168.11.106/pcAssetBundles/",
    "PrefabVersion": 0.2
}
~~~

| 字段          | 说明                           |
| ------------- | ------------------------------ |
| ScenesName    | 场景模型包名称                 |
| ScenesPath    | 场景模型包下载地址             |
| ScenesVersion | 场景模型包版本号               |
| PrefabName    | 预制体模型包名称（货物模型等） |
| PrefabPath    | 预制体模型包下载地址           |
| PrefabVersion | 预制体模型包版本号             |



### 创建元素

#### 	模型

可以创建的模型称为预制体模型，全部保存在**prefab.ab**预制体模型包中。

##### :black_medium_small_square: 创建模型SetModel:heavy_exclamation_mark:

 *（原接口 AddCargo，参数有修改）*

接口说明：

```html
myGameInstance.SendMessage("Connect", "SetModel", data);

 <param name="Connect">连接三维载体</param>

 <param name="SetModel">增加模型</param>

 <param name="data">传入json参数</param>
```

Json字段说明：

~~~json
[{"ID":"A-01-01","Type":"cargo1","Pos":{"X":0,"Y":0,"Z":0},"Angle":0,"LabelH":0,"Scale":{"X":1,"Y":1,"Z":1}}]
~~~

| 字段 | 说明                                                      |
| :----- | --------------------------------------------------------- |
| ID     | 唯一标识符                                                |
| Type   | 创建类型                                                  |
| Pos    | 创建位置                                                  |
| Angle  | 创建水平角度（不传默认0）                               |
| LabelH | 返回屏幕位置时使用，是转换坐标前离地面高度（不传默认0） |
| Scale | 缩放尺寸（不传默认1） |



##### :black_medium_small_square: 删除多个模型DeleteModel:heavy_exclamation_mark:

 *（原接口 deleteCargoForID，参数无修改）*

接口说明：

~~~html
myGameInstance.SendMessage("Connect", "DeleteModel", data);

 <param name="Connect">连接三维载体</param>

 <param name="DeleteModel">删除模型</param>

 <param name="data">传入json参数</param>
~~~

Json字段说明：

*demo*

~~~json
["A-01-01","A-01-02"]//模型ID
~~~



##### :black_medium_small_square:  删除所有模型DeleteAllModel:heavy_exclamation_mark:

*（原接口 deleteCargo，参数无修改）*

接口说明：

~~~html
myGameInstance.SendMessage("Connect", "DeleteAllPoints");

 <param name="Connect">连接三维载体</param>

 <param name="DeleteAllModel">删除模型</param>

~~~

##### :black_medium_small_square:  模型移动ModelMove

（原接口 MoveCargo，参数有修改）

控制模型按路径移动

接口说明

~~~html
myGameInstance.SendMessage("Connect", "ModelMove", data);

 <param name="Connect">连接三维载体</param>

 <param name="ModelMove">删除模型</param>

 <param name="data">传入json参数</param>
~~~

Json字段说明：

~~~json
{"ID":"A-01-01","Time":5,"Path":[[0,0,0],[1,1,1],[2,2,2]]}
~~~

| 字段 | 说明                                                |
| ---- | --------------------------------------------------- |
| ID   | 预制体唯一标识符                                    |
| Time | 移动时间                                            |
| Path | 移动路径，三个数为一组，可以通过GetClickPos方法获得 |

##### :black_medium_small_square:  模型鼠标点击监听ModelClick:heavy_exclamation_mark:

（原接口 model_click）

返回点击模型ID

         function ModelClick(data)
    	{
    			alert(data);
    	}
##### :black_medium_small_square:  模型鼠标进入监听MouseOver:heavy_exclamation_mark:

（原接口 model_mouseover）

返回鼠标进入模型ID

~~~html
	 function MouseOver(data)
	{
			alert(data);
	}
~~~

##### :black_medium_small_square:  模型鼠标进入监听MouseOut:heavy_exclamation_mark:

（原接口 model_mouseout）

返回鼠标离开模型ID

~~~html
	 function MouseOut(data)
	{
			alert(data);
	}
~~~

##### :black_medium_small_square:  高亮模型HighLightModel:heavy_exclamation_mark:

（原接口 HighlightCargo，参数有修改）

高亮生成模型

~~~html
myGameInstance.SendMessage("Connect", "HighLightModel", data);

 <param name="Connect">连接三维载体</param>

 <param name="HighLightModel">高亮模型</param>

 <param name="data">传入json参数</param>
~~~

Json字段说明：

~~~json
["A-01-01","A-01-03","A-01-02"]
~~~

##### :black_medium_small_square:  关闭高亮模型ColseHighForID

通过id关闭高亮模型

```html
myGameInstance.SendMessage("Connect", "ColseHighForID", data);

 <param name="Connect">连接三维载体</param>

 <param name="ColseHighForID">关闭高亮模型</param>

 <param name="data">传入json参数</param>
```

Json字段说明：

```json
["A-01-01","A-01-02"]
```

##### :black_medium_small_square:  关闭所有高亮模型ColseHighAll

关闭所有的高亮模型

```html
myGameInstance.SendMessage("Connect", "ColseHighAll");

 <param name="Connect">连接三维载体</param>

 <param name="ColseHighAll">关闭高亮模型</param>
```



#### 	线

#####   :black_medium_small_square: 创建线SetLines:heavy_exclamation_mark:

（原接口 SetLinePoints，参数无修改）

接口说明：

~~~html
myGameInstance.SendMessage("Connect", "SetLines", data);

 <param name="Connect">连接三维载体</param>

 <param name="SetLines">创建线</param>

 <param name="data">传入json参数</param>
~~~

Json字段说明：

*demo*

~~~json
[{"ID":"line_01","Color":"#62c680","Alpha":0.4,"LineR":1,"Type":"line","Points":[{"X":-32.5,"Y":0.3,"Z":20},{"X":-32.5,"Y":-84.99,"Z":2},{"X":21.5,"Y":-84.99,"Z":3}]}]
~~~

| 字段   | 说明                         |
| ------ | ---------------------------- |
| ID     | 唯一标识符                   |
| Color  | 颜色码                       |
| Alpha  | 透明度（1~0）                |
| LineR  | 线宽                         |
| Type   | 线类型（虚线，实线，方向线） |
| Points | 控制点位置                   |



##### :black_medium_small_square:  删除多个线DeleteLines:heavy_exclamation_mark:

（原接口 DeleteLine，参数无修改）

接口说明：

~~~html
myGameInstance.SendMessage("Connect", "DeleteLines", data);

 <param name="Connect">连接三维载体</param>

 <param name="DeleteLines">删除多个线</param>

 <param name="data">传入json参数</param>
~~~

Json字段说明：

~~~json
["line_01","line_02"]//线ID
~~~



##### :black_medium_small_square:  删除所有线DeleteAllLines:heavy_exclamation_mark:

（原接口 DeleteLines，参数无修改）

接口说明：

~~~html
myGameInstance.SendMessage("Connect", "DeleteAllLines");

 <param name="Connect">连接三维载体</param>

 <param name="DeleteAllLines">删除多个线</param>

~~~



#### 	面

##### :black_medium_small_square:  创建面SetAreas:heavy_exclamation_mark:

（原接口 SetAreaPoints，参数无修改）

接口说明：

~~~html
myGameInstance.SendMessage("Connect", "SetAreas", data);

 <param name="Connect">连接三维载体</param>

 <param name="SetAreas">创建面</param>

 <param name="data">传入json参数</param>
~~~

json字段说明：

*demo*

~~~json
[{"ID":"Area_01","Color":"#62c680","Alpha":0.3,"Points":[{"X":60,"Y":-80,"Z":0},{"X":-60,"Y":-80,"Z":-60},{"X":-60,"Y":-80,"Z":0},{"X":60,"Y":-80,"Z":-60}]}]
~~~

| 字段   | 说明       |
| ------ | ---------- |
| ID     | 唯一标识符 |
| Color  | 颜色码     |
| Alpha  | 透明度     |
| Points | 控制点位置 |



##### :black_medium_small_square:  删除多个面DeleteAreas:heavy_exclamation_mark:

（原接口 DeleteArea，参数无修改）

接口说明：

~~~html
myGameInstance.SendMessage("Connect", "DeleteAreas", data);

 <param name="Connect">连接三维载体</param>

 <param name="DeleteAreas">删除多个面</param>

 <param name="data">传入json参数</param>
~~~

json字段说明：

~~~json
["Area_01","Area_02"]//面ID
~~~



##### :black_medium_small_square: 删除所有面DeleteAllAreas:heavy_exclamation_mark:

（原接口 DeleteAreas，参数无修改）

接口说明：

~~~html
myGameInstance.SendMessage("Connect", "DeleteAllAreas");

 <param name="Connect">连接三维载体</param>

 <param name="DeleteAreas">删除所有面</param>
~~~

### Camer相机



#####  :black_medium_small_square:  读取相机位置ReadCamerPos:heavy_exclamation_mark:

（原接口 readCamerPos，参数无修改）

得到当前位置的Camer相机位置数据，通过GetCamerPos方法返回。

接口说明

~~~html
myGameInstance.SendMessage("Connect", "ReadCamerPos");

 <param name="Connect">连接三维载体</param>

 <param name="DeleteAreas">读取相机位置R</param>
~~~



#####  :black_medium_small_square:  得到相机位置GetCamerPos:heavy_exclamation_mark:

（原接口 getCamerPos，参数无修改）

返回ReadCamerPos方法读取的坐标json数据

返回json

~~~json
["-0.91","10.8","-8.03","39.63","350.95"]
~~~

Demo

~~~html
    	//得到相机的位置
    	 function GetCamerPos(data)
    	{
    			alert(data);
    	}
~~~



##### :black_medium_small_square:  设置相机位置SetCamerPos:heavy_exclamation_mark:

（原接口 setCamerPos，参数无修改）

相机移动到指定位置

接口说明

~~~html
myGameInstance.SendMessage("Connect", "ReadCamerPos", data);

 <param name="Connect">连接三维载体</param>

 <param name="DeleteAreas">设置相机位置</param>

 <param name="data">传入json参数</param>
~~~

json字段说明

~~~json
{"Loca":["-0.91","10.8","-8.03","39.63","350.95"],"Time":3}
~~~

| 字段 | 说明                          |
| ---- | ----------------------------- |
| Loca | GetCamerPos返回的相机坐标数据 |
| Time | 移动时间                      |



#####  :black_medium_small_square:  相机移动到模型CamerMoveForID:heavy_exclamation_mark:

（原接口 camerMoveForID，参数有修改）

接口说明

~~~html
myGameInstance.SendMessage("Connect", "CamerMoveForID", data);

 <param name="Connect">连接三维载体</param>

 <param name="CamerMoveForID">相机移动到模型</param>

 <param name="data">传入json参数</param>
~~~

json字段说明

~~~json
{"ID":"A-01-01","Dis":2,"Time":1}
~~~

| 字段 | 说明                 |
| ---- | -------------------- |
| ID   | 相机要移动到的模型ID |
| Dis  | 离模型的距离         |
| Time | 移动的时间           |



#####  :black_medium_small_square:  相机移动到坐标点CamerMoveForPos:heavy_exclamation_mark:

（原接口 setCamerPos，参数有修改）

将相机移动到指定点位置

接口说明

~~~html
myGameInstance.SendMessage("Connect", "CamerMoveForPos", data);

 <param name="Connect">连接三维载体</param>

 <param name="CamerMoveForPos">相机移动到指定点</param>

 <param name="data">传入json参数</param>
~~~

json字段说明

~~~json
{"Pos":[-1.53,0.61,-1.49],"Dis":2,"Time":1}
~~~

| 字段 | 说明                      |
| ---- | ------------------------- |
| Pos  | GetClickPos返回的json数据 |
| Dis  | 离该点的距离              |
| Time | 相机移动的时间            |



##### :black_medium_small_square:  得到点击地坐标点GetClickPos

返回鼠标右击地面，返回地面的坐标json数据

json

~~~json
[-1.53,0.61,-1.49]
~~~

Demo

~~~html
    	//得到右键点坐标
    	 function GetClickPos(data)
    	{
    			alert(data);
    	}
~~~





### 屏幕坐标转换

##### :black_medium_small_square:  设置预制体转换点SetPrefabPoint

使用预制体ID，注册转换点。注册后可以在GetScreenPoint方法里，返回该点的屏幕坐标。

接口说明

~~~html
myGameInstance.SendMessage("Connect", "SetPrefabPoint", data);

 <param name="Connect">连接三维载体</param>

 <param name="SetPrefabPoint">注册预制体转换点</param>

 <param name="data">传入json参数</param>
~~~

json

~~~json
[{"ID":"A-01-01"},{"ID":"A-01-02"}]
~~~



##### :black_medium_small_square:  设置转换点SetWorldPoint

使用任意点（点位可以通过GetClickPos获取），注册转换点。注册后可以在GetScreenPoint方法里，返回该点的屏幕坐标。

接口说明

~~~html
myGameInstance.SendMessage("Connect", "SetWorldPoint", data);

 <param name="Connect">连接三维载体</param>

 <param name="SetWorldPoint">注册任意点转换</param>

 <param name="data">传入json参数</param>
~~~

json

~~~json
[{"ID":"Point_1","Pos":[0,0,0]},{"ID":"Point_2","Pos":[30,0,20]}]
~~~



##### :black_medium_small_square:  删除转换点DeletePoint

通过ID注销转换点信息，注销后不会返回该ID的屏幕坐标信息。

接口说明

~~~html
myGameInstance.SendMessage("Connect", "DeletePoint", data);

 <param name="Connect">连接三维载体</param>

 <param name="DeletePoint">删除转换点</param>

 <param name="data">传入json参数</param>
~~~

json

~~~json
[{"ID":"Point_1"},{"ID":"Point_2"}]
~~~



#####  :black_medium_small_square: 得到转换坐标GetScreenPoint

得到注册转换点的屏幕坐标，只有注册了转换点，方法会一直返回数据。

返回json说明

~~~json
[{"ID":"Point_1","X":1087.08,"Y":364.38,"Z":13.8},{"ID":"Point_2","X":2236.83,"Y":797.82,"Z":25.38}]
~~~

| 字段 | 说明                              |
| ---- | --------------------------------- |
| ID   | 预制体ID;设置点ID                 |
| X    | 原点（0，0）为屏幕左下角，X是宽度 |
| Y    | X是高度                           |
| Z    | Z是深度，值越大，离摄像头越远     |

Demo

~~~html
    	 //得到屏幕坐标
    	 function GetScreenPoint(data)
    	{
    			alert(data);
    	}
~~~

### UI

##### :black_medium_small_square: 设置背景图片SetBackGroundImg

接口说明

~~~html
myGameInstance.SendMessage("Connect", "SetBackGroundImg", url);

 <param name="Connect">连接三维载体</param>

 <param name="SetBackGroundImg">设置背景图片</param>

 <param name="url">图片地址字符串</param>
~~~

Demo

~~~html
     function message() {
            myGameInstance.SendMessage('Connect', 'SetBackGroundImg', 'https://img.1ppt.com/uploads/allimg/1910/1_191025201728_2.jpg');
        }
~~~

### 场景模型控制

#####  :black_medium_small_square: ​打开建筑OpenWareHouse:heavy_exclamation_mark:

（原接口 openWareHouse）

接口说明

~~~html
myGameInstance.SendMessage("Connect", "OpenWareHouse", "id");

 <param name="Connect">连接三维载体</param>

 <param name="OpenWareHouse">打开建筑</param>

 <param name="id">建筑id</param>
~~~

建筑id说明

| id   | 建筑  |
| ---- | ----- |
| 0    | A仓库 |
| 1    | B仓库 |
| 2    | C仓库 |
| 3    | D仓库 |



##### :black_medium_small_square: 关闭建筑ClosenWareHouse:heavy_exclamation_mark:

（原接口 closeWareHouse）

接口说明

~~~html
myGameInstance.SendMessage("Connect", "ClosenWareHouse");

 <param name="Connect">连接三维载体</param>

 <param name="ClosenWareHouse">打开建筑</param>
~~~




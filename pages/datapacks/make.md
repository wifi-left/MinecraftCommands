# 制作数据包

想要制作数据包，您需要拥有以下条件：

1. 一台内存至少4GB的电脑（防止代码写着写着就内存超了）

2. 拥有Minecraft游戏

3. 一个脑子和一双手（哈哈）

# 第一步

打开开发工具，VSCode。

在需要创建数据包的地方新建一个文件夹。

在VSCode中打开此文件夹。

方法为：菜单“文件” - “打开文件夹”

打开后，在目录内新建文件，pack.mcmeta：

示例：

```json
{
    "pack": {
        "pack_format": 9,
        "description": "Datapacks 制作教程"
    }
}
```

新建目录data

在“data”中新建一个你喜欢的名字的文件夹（如果需要覆盖原版内容请使用minecraft）

但要保证只有英文、数字和下划线（和用户名一样哦）

> 请保证：
>
> 如果要打包为ZIP文件，那么在数据包内不存在中文名称文件！
>
> （因为我之前就吃过亏）
>
> （要问是什么原因，原因就是因为 java ZIP 解压函数的BUG） 

新建完毕后就会像这样： 

![VSCode 中的目录结构](datapacks/vscodestruct.webp)

```markdown
pack.mcmeta
pack.png
data
  advancements
  functions
  loot_tables
  predicates
  structures
  recipes
  item_modifiers
  tags
  dimension_type
  dimension
  worldgen
    biome
    configured_carver
    configured_feature
    configured_structure_feature
    configured_surface_builder
    noise_settings
    processor_list
    template_pool
```

![VSCode 中的结构](datapacks/vscodestruct_1.webp)

1. advancements

进度

（没错就是按下L出现的画面）

2. functions

函数（/function），（其实就是命令组）

3. loot_tables

战利品表（这个不推荐手写，实在太麻烦）

生成器 ：https://mc.metamo.cn//mc/tool/loottable.html

4. predicates

战利品表谓词名称（其实就是更高级的条件，支持选择器、execute调用）

5. structures

结构

后缀为.nbt

（建筑党：嗯？怎么这么熟悉？这不就是结构方块生成的嘛？）

没错，就是结构方块生成的文件。在地图内的structures文件夹内（默认保存位置）

6. recipes

配方（其实就是自定义合成辣！）

7. item_modifiers

物品修饰器（我也没接触过awa）

是1.17快照新增加的。

（Wiki原话：物品修饰器可用于在/item命令内为物品附加战利品表函数。）

tags

标签（你可以通过在选择器中调用，例如：/kill @e[type=#a]，#代表标签）

拥有特殊标签的生物、方块等会有特殊作用。

方块可以在fill 中 replace 后面 以及 物品NBT中的 CanDestroy 与 CanPlaceOn 中使用

（顺便说一声，这个可以套娃哦）

然后function加载需要在这个目录下的functions目录（需要自己新建）中的load.json中输入。

重复执行需要添加tick.json

8. dimension_type

维度类型（1.16新增加的，目前paper与bukkit不支持）

9. dimension

维度（一样的1.16）

10. worldgen

生物群系类型（也一样是1.16） 

# 那么，写好了，如何加载呢？
打开游戏，把文件夹（`pack.mcmeta`文件目录的上一级）复制进地图内的`datapacks`文件夹内，输入/reload重新加载后会默认加载。用`/datapack`可以禁用、启用、列举当前使用的数据包。（需要OP等级为3，及单人模式OP等级）
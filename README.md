***

name: skill-comic-drama-creator
description: AI漫剧剧本创作工具。当用户需要创建电影级剧本、生成分镜图片提示词或PromptRelay时序提示词时使用。支持根据标题、引子和内容生成完整剧本，自动生成分镜提示词（包含人物、场景、物品的详细描述以保持一致性），并生成中英文对照的PromptRelay块语法/内联语法时序提示词。适用于AI漫剧、动画短片、视觉小说等创作场景。
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

# AI漫剧剧本创作技能

## 一、技能概述

本技能用于帮助用户创建高质量的AI漫剧内容，包含以下核心功能：

1. **剧本生成**：根据用户提供的标题、引子和内容，生成电影级别的完整剧本
2. **分镜图片提示词生成**：根据剧本自动生成详细的文生图提示词，包含人物、场景、物品的详细描述
3. **图生视频提示词生成**：分析分镜提示词，生成对应的图生视频提示词
4. **中英文对照**：所有提示词均提供中英文对照版本

## 二、使用流程

```
用户输入 → 剧本生成 → 分镜提示词生成 → 图生视频提示词生成 → 输出结果
```

## 三、剧本生成模块

### 3.1 输入格式

用户需提供以下信息：

- **标题**：作品名称
- **引子**：故事背景或开场介绍
- **内容**：主要情节描述

### 3.2 剧本结构

生成的剧本包含以下部分：

- **场景标题**：每个场景的名称
- **时长**：该场景持续时间
- **画面描述**：详细的视觉描述
- **台词**：角色对话或旁白
- **运镜说明**：镜头运动方式

### 3.3 剧本示例

**输入**：

- 标题：《星空下的约定》
- 引子：在一个宁静的小镇，两个年轻人的命运交织在一起
- 内容：夏夜的星空下，少年和少女在古老的灯塔旁相遇，他们交换了彼此的梦想

**输出**：

```
场景1：小镇夏夜
- 时长：0:00-0:08
- 画面：宁静的小镇夜景，萤火虫在草地上飞舞，远处灯塔闪烁
- 台词：旁白："在这个被星光守护的小镇..."
- 运镜：全景缓慢推进

场景2：灯塔相遇
- 时长：0:08-0:18
- 画面：少年站在灯塔下仰望星空，少女从远处走来
- 台词：
  少年："今晚的星星真美..."
  少女："你也喜欢看星星吗？"
- 运镜：中景跟随
```

## 四、分镜图片提示词生成模块

### 4.1 提示词公式

```
[镜头类型] + [构图方式] + [主体描述] + [场景环境] + [风格指定] + [质量控制] + [技术参数]
```

### 4.1.1 风格一致性强制规则

**强制要求**：每张提示词**必须**包含风格指定，且同一剧本的所有提示词需保持风格统一。

**主风格选择**（根据题材二选一）：

- **武侠/动作题材**：中国武侠动漫风格，电影级画质
- **神话/仙侠题材**：中国传统神话风格，电影级画质

**风格一致性示例**：

- 武侠题材全片统一使用：`中国武侠动漫风格，电影级画质`
- 神话题材全片统一使用：`中国传统神话风格，电影级画质`

**禁止行为**：

- 不得省略风格指定
- 不得在同一剧本中混合使用多种主风格（如同时使用"中国武侠动漫风格"和"中国传统神话风格"）
- 风格描述必须位于提示词末尾，质量控制和技术参数之前

### 4.2 模块详解

| 模块       | 作用   | 示例          |
| -------- | ---- | ----------- |
| **镜头类型** | 定义景别 | 全景、中景、近景、特写 |
| **构图方式** | 画面布局 | 黄金分割、对称、三角形 |
| **主体描述** | 核心元素 | 人物、物品、动作    |
| **场景环境** | 时空背景 | 地点、时间、天气    |
| **风格指定** | 艺术风格 | 动漫风格、吉卜力风格  |
| **质量控制** | 画面品质 | 高清、细节丰富     |
| **技术参数** | 生成控制 | 比例、分辨率      |

### 4.3 人物描述规范

当剧本中涉及人物时，需按照以下格式描述：

- **括号内（固定基本描述）**：年龄、发型+发色、面部特征、服装款式+颜色+材质、配饰
- **括号外（特性描述）**：表情状态、眼神描述、动作姿态
- **示例**：林风（16岁，黑色马尾长发，浓眉大眼，青色劲装飘逸，腰间玉佩）手持青冥铁剑，眼神坚毅，衣袂飘动

**格式规则**：

1. 括号内为角色固定属性，同一剧本中所有提示词保持完全一致
2. 括号外为当帧特有的表情、眼神、动作描述
3. 括号内外用空格分隔，括号外描述需自然衔接

### 4.4 场景描述规范

- **地点类型**：室内/室外、具体地点
- **时间氛围**：白天/夜晚、季节、天气
- **环境细节**：建筑、植物、道具布置、空间布局
- **光影效果**：光源方向、阴影、特殊光效、氛围营造
- **示例**：竹林（茂密翠绿，阳光穿透叶隙，斑驳光影，古风意境）

### 4.5 物品描述规范

- **物品名称**：具体名称
- **外观特征**：颜色、材质、形状、尺寸
- **细节描述**：纹理、装饰、状态、特殊效果
- **示例**：青冥剑（古铜色剑鞘，银纹雕刻，剑身寒光闪烁，锋利逼人）

### 4.6 提示词组合规范

**核心规则**：人物、场景、物品的详细描述必须完整嵌入提示词中，确保生成一致性

**公式**：

```
[镜头类型] + [主体动作]，[人物1(详细描述)] 与 [人物2(详细描述)] + [物品(详细描述)] + [场景(详细描述)] + [氛围特效] + [风格指定] + [质量控制] + [技术参数]
```

**风格强制规则**：

1. **必须包含**：每张提示词末尾必须包含 `[风格指定] + [质量控制]`
2. **风格统一**：同一剧本所有提示词使用相同的风格描述
3. **风格位置**：风格指定必须位于提示词末尾，质量控制之前
4. **质量控制**：必须包含 `电影级画质` 或 `高清画质`

**风格选择优先级**：

| 题材类型        | 推荐风格     | 示例             |
| ----------- | -------- | -------------- |
| 武侠/江湖/动作    | 中国武侠动漫风格 | 中国武侠动漫风格，电影级画质 |
| 神话/仙侠/玄幻    | 中国传统神话风格 | 中国传统神话风格，电影级画质 |
| 混合题材（武侠+神话） | 中国仙侠动漫风格 | 中国仙侠动漫风格，电影级画质 |
| 都市/现代       | 现代动漫风格   | 现代动漫风格，电影级画质   |
| 历史/古装       | 中国古风动漫风格 | 中国古风动漫风格，电影级画质 |

**示例1**：

```
近景，青冥剑（古铜色剑鞘，银纹雕刻，剑身寒光闪烁，锋利逼人）直指山贼（30岁，满脸横肉刀疤脸，黑色劲装紧身，腰间皮质刀鞘）咽喉，对方眼神惊恐，面部因恐惧而扭曲，剑光映照面部，紧张对峙，中国武侠动漫风格，电影级画质，16:9比例
```

**示例2**：

```
中景打斗场面，林风（16岁，黑色马尾长发，浓眉大眼，青色劲装飘逸，腰间玉佩）手持青冥铁剑（古铜色剑鞘，银纹雕刻，寒光闪烁），眼神凌厉，衣袂飘动，与山贼头目（40岁，独眼虬髯，暗红披风，玄色劲装）交锋，对方手持狼牙棒（精钢打造，狼牙倒刺），剑光闪烁，竹叶纷飞，动态模糊，战斗张力，竹林（茂密翠绿，阳光穿透叶隙，斑驳光影，古风意境），中国武侠动漫风格，电影级画质，16:9比例
```

**示例3**：

```
中景，客栈对峙，苏婉（18岁，蓝色长裙飘逸，白色面纱遮面，腰间丝绦）手持玉笛（羊脂白玉质地，笛身云纹），眼神清冷，怒视掌柜（50岁，肥胖秃顶，灰色布衫，算盘在手），对方满脸堆笑眼神闪烁，阳光从窗棂射入，灰尘漂浮，紧张气氛，古风客栈（木质桌椅，灯笼高挂，酒旗飘扬），中国古风动漫风格，电影级画质，16:9比例
```

**示例4（陈小虎标准格式）**：

```
全景，凌云峰顶场景，陈小虎（20岁，寸头短发乌黑发亮，浓眉大眼英气勃发，土黄色僧袍宽大飘逸，腰间系白色布带，脚穿黑色布靴）双手握拳蓄力，眼神坚毅，衣袂猎猎作响
```

**示例5（陈小虎不同姿态）**：

```
近景，陈小虎（20岁，寸头短发乌黑发亮，浓眉大眼英气勃发，土黄色僧袍宽大飘逸，腰间系白色布带，脚穿黑色布靴）摆出罗汉拳起手式，眼神沉稳，双拳护于胸前
```

## 五、图生视频提示词生成模块

### 5.1 提示词公式

```
[运动类型] + [运动幅度] + [时间参数] + [平滑控制] + [风格保持] + [特效增强]
```

### 5.2 运动类型映射

根据剧本中的运镜说明，映射到以下运动类型：

| 运镜说明  | 运动类型 | 提示词                         |
| ----- | ---- | --------------------------- |
| 缓慢推进  | 推进   | push forward, gentle motion |
| 缓慢拉远  | 缩放   | zoom out, slow pull back    |
| 镜头切换  | 定格   | freeze frame, cut           |
| 从全景推近 | 缩放   | dolly shot forward          |
| 聚焦细节  | 特写   | focus on, subtle zoom       |

### 5.3 时间参数规则

- 场景时长 < 3秒：使用 minimal motion
- 场景时长 3-8秒：使用 subtle movement
- 场景时长 > 8秒：使用 gentle to moderate motion

## 六、中英文对照规则

所有提示词均需提供中英文对照版本，格式如下：

### 6.1 文生图提示词对照

**中文**：

```
中景，16岁亚洲少年，黑色短发，清澈的棕色眼睛，穿着蓝色牛仔夹克和白色T恤，站在古老的灯塔下，夜晚星空背景，萤火虫飞舞，吉卜力动画风格，高清细节，16:9比例
```

**英文**：

```
medium shot, 16-year-old Asian boy, black short hair, clear brown eyes, wearing blue denim jacket and white t-shirt, standing under ancient lighthouse, night sky with stars background, fireflies flying, Studio Ghibli animation style, HD detailed, 16:9 aspect ratio
```

### 6.2 图生视频提示词对照

**中文**：

```
缓慢推进，柔和运动，平滑过渡，每秒24帧，风格保持，自然缓入缓出，5秒时长
```

**英文**：

```
slow push forward, gentle motion, smooth transitions, 24 frames per second, style preservation, natural ease-in-out, 5 seconds duration
```

## 七、完整工作流程示例

### 7.1 输入

```
标题：《山海传说》
引子：在遥远的东方，有一片被迷雾笼罩的神秘山林
内容：少年林羽背着祖传的宝剑，来到山神庙前，准备踏上冒险之旅
```

### 7.2 剧本输出

```
场景1：迷雾山林
- 时长：0:00-0:06
- 画面：云雾缭绕的深山之中，古老的参天大树若隐若现
- 台词：旁白："在那遥远的东方，有一片被迷雾笼罩的神秘山林..."
- 运镜：全景缓慢推进

场景2：山神庙前
- 时长：0:06-0:14
- 画面：16岁的少年林羽背着宝剑站在破旧的山神庙前，表情坚毅
- 台词：林羽："我一定会找到传说中的宝藏！"
- 运镜：中景定格
```

### 7.3 分镜提示词输出

**镜头001（中文）**：

```
全景，深山古林场景，迷雾山林（参天古木，藤蔓缠绕，石阶斑驳，清晨薄雾弥漫），神秘东方意境，阳光穿透树冠，丁达尔光束，中国古风动漫风格，电影级画质，16:9比例
```

**镜头001（英文）**：

```
establishing shot, deep mountain ancient forest scene, misty woods (towering ancient trees, tangled vines, weathered stone steps, morning fog), mysterious oriental atmosphere, sunlight through canopy, Tyndall effect rays, Chinese ancient style animation, cinematic quality, 16:9 aspect ratio
```

**镜头002（中文）**：

```
中景，山神庙前场景，少年林羽（16岁，黑色短发，坚毅眼神，蓝色传统汉服，白色护腕，双手紧握）背着祖传长剑（古铜色剑鞘，云纹雕刻，流苏吊坠）站在破旧山神庙（木质结构，红漆剥落，石质台阶，门前香炉）前，表情坚定，中国古风动漫风格，电影级画质，16:9比例
```

**镜头002（英文）**：

```
medium shot, mountain temple entrance scene, 16-year-old Asian boy Lin Yu (black short hair, determined eyes, blue traditional Hanfu, white wrist guards, hands clenched) carrying ancestral sword (ancient bronze sheath with cloud patterns, tassel pendant) standing in front of dilapidated mountain temple (wooden structure, faded red paint, stone steps, incense burner), resolute expression, Chinese ancient style animation, cinematic quality, 16:9 aspect ratio
```

### 7.4 PromptRelay 时序提示词输出

**镜头001（中文 - 块语法）**：

```
Scene 1:
云雾缭绕的深山之中，古老的参天大树若隐若现，神秘东方意境
Scene 2:
少年林羽背着祖传宝剑出现在山间小径上，步伐坚定
Scene 3:
少年林羽来到破旧的山神庙前驻足，抬头仰望
```

**镜头001（英文 - 块语法）**：

```
Scene 1:
Mist-shrouded deep mountains, ancient towering trees faintly visible, mysterious oriental atmosphere
Scene 2:
Young Lin Yu carrying ancestral sword appears on the mountain path, stride determined
Scene 3:
Young Lin Yu stops in front of dilapidated mountain temple, looking up
```

**镜头002（中文 - 块语法）**：

```
Scene 1:
少年林羽站在山神庙前，双手紧握剑柄，神情坚毅
Scene 2:
他深吸一口气，推开山神庙斑驳的木门
Scene 3:
古旧寺庙内部，尘埃飞舞，一束阳光从破洞的屋顶射入
```

**镜头002（英文 - 块语法）**：

```
Scene 1:
Young Lin Yu stands before mountain temple, hands gripping sword hilt, expression resolute
Scene 2:
He takes a deep breath and pushes open the weathered wooden door
Scene 3:
Ancient temple interior, dust floating, a beam of sunlight shines through the broken roof
```

### 7.5 图生视频提示词输出

**镜头001（中文）**：

```
缓慢推进，柔和运动，平滑过渡，每秒24帧，风格保持，自然缓入缓出，6秒时长，漂浮的雾气粒子
```

**镜头001（英文）**：

```
slow push forward, gentle motion, smooth transitions, 24 frames per second, style preservation, natural ease-in-out, 6 seconds duration, floating mist particles
```

**镜头002（中文）**：

```
定格，轻微呼吸动画，衣物微动，头发轻摆，平滑帧插值，30帧每秒，6秒时长
```

**镜头002（英文）**：

```
freeze frame, subtle breathing animation, gentle clothing sway, slight hair movement, smooth frame interpolation, 30 FPS, 6 seconds duration
```

## 八、负向提示词模板

所有文生图提示词需附带以下负向提示词：

**中文**：

```
低质量，模糊，像素化，坏解剖结构，畸形四肢，多余手指，文字，水印，签名，丑陋，扭曲，残缺，画稿，未完成，出框，截断，单色，灰度，不当内容
```

**英文**：

```
low quality, blurry, pixelated, bad anatomy, deformed limbs, extra fingers, text, watermark, signature, ugly, distorted, disfigured, poorly drawn, sketch, unfinished, out of frame, cut off, monochrome, grayscale, nsfw
```

## 九、输出格式

最终输出采用以下结构化格式：

```
========================================
AI漫剧创作结果
========================================

【剧本】
场景X：[场景名称]
- 时长：[时间范围]
- 画面：[详细描述]
- 台词：[对话内容]
- 运镜：[镜头运动]

【分镜图片提示词】
镜头XX：
中文：[完整提示词，包含人物、场景、物品的详细描述]

英文：[完整提示词，与中文内容完全对应一致，包含相同详细程度的人物、场景、物品描述]

【PromptRelay 提示词】
镜头XX（中文 - 块语法）：
Scene 1:
[首段静态描述]
Scene 2:
[第二段动作/变化]
Scene 3:
[第三段动作/变化]

镜头XX（英文 - 块语法）：
Scene 1:
[首段静态描述英文]
Scene 2:
[第二段动作/变化英文]
Scene 3:
[第三段动作/变化英文]

【图生视频提示词】
镜头XX：
中文：[提示词]
英文：[提示词]

【人物/场景/物品设定】
- 人物：[姓名（年龄，外貌特征，服装描述，表情状态，动作姿态）]
- 场景：[场景名称（地点类型，时间氛围，环境细节，光影效果）]
- 物品：[物品名称（外观特征，细节描述，特殊效果）]

【负向提示词】
中文：低质量，模糊，像素化，坏解剖结构，畸形四肢，多余手指，文字，水印，签名，丑陋，扭曲，残缺，画稿，未完成，出框，截断，单色，灰度，不当内容
英文：low quality, blurry, pixelated, bad anatomy, deformed limbs, extra fingers, text, watermark, signature, ugly, distorted, disfigured, poorly drawn, sketch, unfinished, out of frame, cut off, monochrome, grayscale, nsfw

【Global Prompt】
[global_prompt内容]
========================================
```

## 十、人物描述强制规范

### 10.1 强制要求

- **任何角色出现时，必须提供完整的人物描述，不得省略或引用前文**
- **括号内（固定属性）必须包含**：年龄、发型+发色、面部特征、服装款式+颜色+材质、配饰
- **括号外（特性描述）必须包含**：表情状态、眼神描述、动作姿态
- **场景描述必须包含**：地点类型、具体地点、时间氛围、天气、建筑/植物/道具布置、空间布局、光源方向、阴影、特殊光效
- **物品描述必须包含**：物品名称、颜色、材质、形状、尺寸、纹理、装饰、状态、特殊效果

### 10.2 人物描述公式

```
[角色名称]（[年龄]岁，[发型]+[发色]，[面部特征]，[服装款式]+[颜色]+[材质]，[配饰]）[表情状态]，[眼神描述]，[动作姿态]
```

### 10.3 人物描述示例

```
陈小虎（20岁，寸头短发乌黑发亮，浓眉大眼英气勃发，土黄色僧袍宽大飘逸，腰间系白色布带，脚穿黑色布靴）表情专注凝重，眼神坚毅有神，双掌蓄力待发
```

### 10.4 一致性规则

- 同一剧本中，同一角色的括号内描述**必须**完全一致
- 括号外描述**可以**根据场景变化，描述当帧特有的表情、眼神、动作
- 括号内外用空格分隔，形成完整通顺的描述语句

## 十一、PromptRelay 提示词配置

### 11.1 PromptRelay 核心概念

PromptRelay 是 ComfyUI 的时序提示词控制插件，用于在图生视频（I2V）或文生视频任务中实现**分段提示词控制**。

| 概念                   | 说明    | 作用域   |
| -------------------- | ----- | ----- |
| **global\_prompt**   | 全局提示词 | 整个视频  |
| **local\_prompts**   | 分段提示词 | 各时间段落 |
| **segment\_lengths** | 每段帧数  | 各时间段落 |

### 11.2 语法类型

PromptRelay 支持两种语法：**内联语法（Inline）和**块语法（Block）。推荐使用块语法进行故事叙述。

#### 内联语法（Inline）

使用 `|` 分隔各段落，可选添加权重标签。

```
段落1文本 [权重范围] | 段落2文本 [权重范围] | 段落3文本 [权重范围]
```

#### 块语法（Block）- 推荐

每段前一行标题，格式：`词语 + 数字 + 冒号`

```
Scene 1:
段落1文本
Scene 2:
段落2文本
Scene 3:
段落3文本
```

### 11.3 权重计算规则

| 格式           | 含义           | 示例              |
| ------------ | ------------ | --------------- |
| `[n-m]`      | 范围权重 = m - n | `[0-50]` → 权重50 |
| `[n]`        | 单值权重 = n     | `[100]` → 权重100 |
| 无标签          | 等分权重 = 1     | 各段落权重1          |
| `Scene 1-3:` | 范围 = 结束-开始   | 3-1 = 2         |

> **注意**：`[ ]` 内的数字是**相对位置/权重比例**，不是帧数。

### 11.4 写作规则

**核心原则**：

1. **第一段只写静态描述**
   - 描述当前可见的状态
   - 不要写动作或运动
   - 不要写输入中不存在的内容
2. **后续段落只写变化**
   - 只描述该时间段内发生的变化或移动
   - 不要重复前面段落已描述的内容

| 错误写法          | 正确写法         |
| ------------- | ------------ |
| 第一段写了"走路"     | 第一段只写"站立/静态" |
| 后续段重复"他穿着..." | 后续段只写"变化"    |
| 混用两种语法        | 选择一种保持一致     |

### 11.5 PromptRelay 提示词公式

```
标题（可选）:
[核心主体描述]，[动作/变化]，[场景环境]，[氛围特效]
```

### 11.6 PromptRelay 提示词示例

**中文 - 块语法（推荐）**：

```
Scene 1:
陈小虎独自站在凌云峰顶，寸头短发乌黑发亮，土黄色僧袍随风轻摆，表情专注凝重
Scene 2:
陈小虎双掌蓄力，金色掌影渐渐显现，衣袂猎猎作响，眼神坚毅有神
Scene 3:
金色掌影与银色刀光猛然碰撞，爆发出耀眼火花，竹叶纷飞，动态模糊展现速度感
Scene 4:
陈小虎收招伫立，微微一笑，转身望向远方的天际线
```

**英文 - 块语法**：

```
Scene 1:
Chen Xiaohu stands alone atop Lingyun Peak, with short black hair, earth-yellow monk robe swaying in the wind, focused and solemn expression
Scene 2:
Chen Xiaohu gathers power in both palms, golden palm shadows gradually appear, robes fluttering, eyes resolute and spirited
Scene 3:
Golden palm shadows collide violently with silver blade lights, erupting dazzling sparks, bamboo leaves scattering, motion blur conveying speed
Scene 4:
Chen Xiaohu sheathes his move and stands still, slight smile, turns to gaze at the distant horizon
```

**内联语法示例**：

```
Chen Xiaohu stands on peak [0-50] | He gathers power in palms golden shadows appear [50-100] | Golden vs silver collision sparks fly [100-150] | He sheathes move and smiles [150-200]
```

### 11.7 PromptRelay 与 Global Prompt 的关系

- **Global Prompt**：定义整体风格基调，贯穿整个视频
- **Local Prompts（PromptRelay）**：描述各时间段的具变化，是 Global Prompt 的具体化
- **关系**：Global Prompt 提供统一的美学框架，Local Prompts 在此框架下描述具体动作场景

## 十二、Global Prompt 配置

### 12.1 Global Prompt 定义

- **全局提示词**：根据剧本内容进行深度分析和总结后生成的统一基础提示词，是对整个故事的艺术风格、视觉基调、情感氛围的系统性概括
- **作用**：
  - 确保全片风格高度统一、视觉质量一致
  - 传递故事的核心情感基调和世界观设定
  - 为所有分镜图片生成提供统一的创作指导框架
  - 强化角色造型、场景设计、色彩运用的连贯性
- **位置**：输出结果的最后部分，作为全局创作指导
- **特点**：基于具体剧本内容动态生成，而非固定模板，能够准确反映每部作品的独特风格

### 12.2 Global Prompt 生成规则

1. **主题提取**：分析剧本的核心主题（武侠/仙侠/都市/历史等）
2. **风格定位**：确定整体艺术风格（中国传统/现代/奇幻等）
3. **氛围概括**：总结故事的情感基调（紧张/温馨/神秘/悲壮等）
4. **视觉要素**：提炼关键视觉元素（场景类型、角色特征、色彩偏好等）
5. **质量标准**：统一技术参数（分辨率、画质级别、帧率要求等）

### 12.3 Global Prompt 公式

```
[故事题材]风格，[艺术流派]画风，[情感氛围]基调，[核心场景]设定，[角色特征]描述，[色彩方案]搭配，[光影风格]处理，[技术质量]标准
```

### 12.4 Global Prompt 示例

**根据《山海传说》剧本生成：**

**中文**：

```
中国古风仙侠风格，传统神话动画画风，神秘冒险基调，深山古林与神殿遗迹场景，少年侠客角色形象，青蓝紫色冷色调搭配，丁达尔光束与薄雾光影处理，电影级画质高清渲染
```

**英文**：

```
Chinese ancient style xianxia theme, traditional mythology animation style, mysterious adventure tone, deep mountain forest and ancient temple ruins settings, young hero character design, cool color palette of cyan blue purple, Tyndall effect beams with mist lighting, cinematic quality HD rendering
```

**根据武侠对决剧本生成：**

**中文**：

```
中国武侠动漫风格，江湖恩怨剧情基调，古战场与竹林场景，僧袍武僧与黑衣杀手角色，金棕与银白对比色搭配，动态模糊与刀光特效，电影级画质16:9高清渲染
```

**英文**：

```
Chinese martial arts anime style, jianghu feud story tone, ancient battlefield and bamboo forest settings, monk warrior vs black-clad assassins characters, gold-brown and silver-white contrasting colors, motion blur and blade light effects, cinematic quality 16:9 HD rendering
```

### 12.5 Global Prompt 输出格式

```
【Global Prompt】
中文：[根据剧本总结生成的完整全局提示词]
英文：[与中文完全对应的英文全局提示词]
```

## 十三、完整输出示例（含PromptRelay和Global Prompt）

### 13.1 分镜图片提示词输出示例

```
【分镜图片提示词】
镜头001：
中文：全景，古刹藏经阁前对峙场景，陈小虎（20岁，寸头短发乌黑发亮，浓眉大眼英气勃发，土黄色僧袍宽大飘逸，腰间系白色布带，脚穿黑色布靴）双手负后，眼神凝重，与幽冥护法（35岁，面如死灰眼角刀疤，黑色劲装绣银线蝙蝠，皮质护腕）对立，对方手持幽冥钩镰（精钢打造，泛冷光，弯刃带倒刺），表情阴狠，金色夕阳斜照，藏经阁红墙飞檐，石阶落叶，中国仙侠动漫风格，电影级画质，16:9比例

英文：establishing shot, confrontation scene at ancient temple scripture pavilion, Chen Xiaohu (20 years old, buzz cut black hair shiny, thick eyebrows and big eyes heroic, earth-yellow monk robe flowing and elegant, white cloth belt around waist, black cloth boots) with hands behind back, solemn gaze, facing Nether Guardian (35 years old, pale death face with corner eye scar, black outfit embroidered with silver thread bats, leather wrist guards), opponent holding dark Nether scythe (forged steel, cold glow, curved blade with barbs), menacing expression, golden sunset slanting, scripture pavilion with red walls and upturned eaves, fallen leaves on stone steps, Chinese xianxia anime style, cinematic quality, 16:9 aspect ratio

镜头002：
中文：中景打斗场面，陈小虎（20岁，寸头短发乌黑发亮，浓眉大眼英气勃发，土黄色僧袍宽大飘逸，腰间系白色布带，脚穿黑色布靴）僧衣飘动，眼神坚毅有神，掌风呼啸，与三名杀手（均为30岁左右，黑色夜行衣紧身，面戴黑色面罩）激战，对方手持银色弯刀（精钢打造，锋利逼人），金色掌影与银色刀光交错碰撞，气浪掀飞青灰色瓦片和枯黄落叶，碎石飞溅，动态模糊表现速度感，激烈对抗，古旧街道场景（青石板路，两侧木质店铺招牌褪色，飞檐翘角古建筑，黄昏时分），中国仙侠动漫风格，电影级画质，16:9比例

英文：medium shot battle scene, Chen Xiaohu (20 years old, buzz cut black hair shiny, thick eyebrows and big eyes heroic, earth-yellow monk robe flowing and elegant, white cloth belt around waist, black cloth boots) robe fluttering, determined eyes, palm wind whistling, fighting three assassins (all around 30 years old, black tight night clothes, black masks covering faces), opponents holding sharp silver curved blades (forged steel, razor sharp), golden palm shadows colliding with silver blade lights, air waves lifting gray tiles and yellow fallen leaves, flying debris, motion blur for speed effect, intense confrontation, ancient street scene (bluestone pavement, faded wooden shop signs on both sides, upturned eaves ancient buildings, dusk time), Chinese xianxia anime style, cinematic quality, 16:9 aspect ratio

镜头003：
中文：近景特写，陈小虎（20岁，寸头短发乌黑发亮，浓眉大眼英气勃发，土黄色僧袍宽大飘逸，腰间系白色布带，脚穿黑色布靴）僧衣无风自动，眼神坚毅，双掌合十后缓缓推出，金色佛光从掌心迸发，身后浮现巨大金色佛手虚影，地面青石板（灰色石材质地，纹理清晰，裂纹蔓延）碎裂悬浮，气浪波纹扩散，如来神掌起手式，神圣庄严，中国仙侠动漫风格，电影级画质，16:9比例

英文：close-up shot, Chen Xiaohu (20 years old, buzz cut black hair shiny, thick eyebrows and big eyes heroic, earth-yellow monk robe flowing and elegant, white cloth belt around waist, black cloth boots) robe moving without wind, firm gaze, slowly pushing out after palms together, golden Buddha light bursting from palms, giant golden Buddha hand apparition behind, ground bluestone slabs (gray stone texture, clear grain, spreading cracks) shattered and floating, air wave ripples spreading, Tathagata Palm starting stance, sacred and solemn, Chinese xianxia anime style, cinematic quality, 16:9 aspect ratio
```

### 13.2 PromptRelay 提示词输出示例

基于上述分镜，生成对应的时序提示词：

```
【PromptRelay 提示词】
镜头001（中文 - 块语法）：
Scene 1:
陈小虎独自站在古刹藏经阁前，双手负于身后，神情凝重地望着眼前的幽冥护法
Scene 2:
幽冥护法挥舞着泛着冷光的钩镰刀逼近，陈小虎眼神一凝
Scene 3:
陈小虎双掌蓄力，金色掌影隐隐显现，与幽冥护法的刀光对峙

镜头001（英文 - 块语法）：
Scene 1:
Chen Xiaohu stands alone before the ancient temple scripture pavilion, hands behind his back, gazing solemnly at the approaching Nether Guardian
Scene 2:
The Nether Guardian brandishes his cold-glowing scythe blade, pressing forward, Chen Xiaohu's eyes sharpen
Scene 3:
Chen Xiaohu gathers power in both palms, golden palm shadows faintly forming, confronting the Nether Guardian's blade light

镜头002（中文 - 块语法）：
Scene 1:
三名黑衣杀手从暗处冲出，挥舞银色弯刀向陈小虎砍去
Scene 2:
陈小虎身形闪动，掌风呼啸，金色掌影与银色刀光激烈碰撞
Scene 3:
气浪掀飞青石瓦片，碎石纷飞，战斗进入白热化

镜头002（英文 - 块语法）：
Scene 1:
Three black-clad assassins burst from the shadows, swinging silver curved blades at Chen Xiaohu
Scene 2:
Chen Xiaohu moves swiftly, palm wind whistling, golden palm shadows colliding violently with silver blade lights
Scene 3:
Air waves lift stone tiles, debris scatters, battle intensifies to its climax

镜头003（中文 - 块语法）：
Scene 1:
陈小虎双掌合十，金色佛光从掌心开始迸发
Scene 2:
巨大金色佛手虚影在身后缓缓浮现，光芒万丈
Scene 3:
地面青石碎裂悬浮，气浪波纹向四周扩散，神圣庄严

镜头003（英文 - 块语法）：
Scene 1:
Chen Xiaohu joins his palms together, golden Buddha light beginning to burst from his palms
Scene 2:
A giant golden Buddha hand apparition slowly forms behind him, radiating magnificent light
Scene 3:
Ground bluestone shatters and floats, air wave ripples spread outward in all directions, sacred and solemn
```

### 13.3 Global Prompt 输出示例

```
【Global Prompt】
中文：中国仙侠动漫风格，古风武侠动画画风，正邪对决剧情基调，古刹藏经阁与古旧街道场景，土黄色僧袍武僧与黑衣杀手角色，金色佛光与冷光武器特效，黄昏暖色调与冷光对比搭配，动态模糊与粒子光效处理，电影级画质16:9高清渲染
英文：Chinese xianxia anime style, ancient martial arts animation, good vs evil confrontation tone, ancient temple scripture pavilion and old street settings, earth-yellow monk robe warrior vs black-clad assassins, golden Buddha light vs cold weapon effects, dusk warm tones contrasting with cool lights, motion blur and particle effects, cinematic quality 16:9 HD rendering
```


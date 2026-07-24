# LTX 图生视频提示词工程：专业指南

> 从专业角度总结：如何编写提示词，确保画质流畅、动作连贯、衔接紧密、不生硬、不卡顿、人物不扭曲、不出现多余人物、没有PPT感

---

## 一、核心原则：完整故事画面理念

LTX视频生成模型解读提示词的方式如同摄影师阅读导演笔记，其核心原则是：**描绘一个从头到尾自然流动的完整故事画面**。

| 对比维度 | 图像生成 | 视频生成（LTX） |
|---------|---------|----------------|
| 核心 | 静态构图 | 时间流动和运动 |
| 内容 | 单一时刻 | 从头到尾的序列 |
| 形式 | 描述性列表 | 叙事性段落 |
| 元素 | 仅视觉元素 | 视觉+音频+运动 |
| 时态 | 任何时态 | **首选现在时** |

---

## 二、提示词黄金结构：七段式电影脚本

为确保画质流畅、动作连贯、衔接紧密，推荐采用"七段式电影脚本"结构：

```
1. 主体动作 → 核心动态
2. 动作细节 → 肢体语言和运动轨迹  
3. 外观特征 → 精确视觉描述
4. 环境背景 → 空间构成和元素分布
5. 镜头语言 → 相机角度、运动方式和焦距
6. 光影色彩 → 光线类型、色调和对比度
7. 情节变化 → 时间推移或突发事件
```

### 反例 vs 正例

**普通Prompt（效果差）：**
```
一个女孩在跳舞
```

**电影级Prompt（效果好）：**
```
芭蕾舞演员在舞台中央旋转跳跃，足尖点地时膝盖微屈，双臂呈天鹅状缓缓展开。
穿着白色蕾丝芭蕾舞裙，裙摆长度及膝，发丝随着动作在空中划出弧线。
木质舞台地板反射着顶灯的暖光，背景是暗红色丝绒幕布。
摄像机从低角度仰拍，缓慢环绕演员一周，焦距保持在中景。
舞台灯光聚焦在舞者身上形成聚光效果，周围环境渐暗。
舞者突然加快旋转速度，裙摆形成圆形光晕，最后以经典阿拉贝斯克姿势定格。
```

---

## 三、九大专业技巧

### 技巧1：单一连续段落
**规则**：用一个流畅的段落描述场景，避免换行、列表或碎片化思考。

**示例：**
```
A lone fisherman rows across a foggy lake before sunrise, the boat creaking softly as water laps at its sides. The camera glides overhead, tracking his slow progress.
```

### 技巧2：现在时态动作动词
**规则**：描述所有动作使用现在时。

| 错误 | 正确 |
|-----|-----|
| walked, tilted | walks, tilts |
| ran, flickered | runs, flickers |

**示例：**
```
A young boy runs barefoot across a wet stone courtyard as the first raindrops begin to fall.
```

### 技巧3：明确的相机行为
**规则**：清晰描述相机的视角、角度、运动和速度。

**专业术语参考：**
- 镜头类型：广角镜头、特写、极端特写、中景、全景
- 拍摄角度：低角度、高角度、鸟瞰图、仰视、俯视
- 运动方式：推轨、升降、环绕、推进、拉远、平移

**示例：**
```
The camera begins in a wide shot from across the street, then slowly pushes forward at shoulder height as pedestrians blur in the foreground.
```

### 技巧4：精确的物理细节
**规则**：使用可测量的微小动作、手势和姿势变化。

**示例：**
```
Her eyebrows lift approximately two millimeters as she hears a creak behind her, and the blade pauses mid-air.
```

### 技巧5：大气环境描述
**规则**：详细描述灯光、空气、纹理、声音和氛围元素。

**关键元素：**
| 类别 | 示例 |
|-----|-----|
| 灯光质量 | 黄金时段反射光、刺眼的头顶荧光灯、柔和的窗户光 |
| 色彩调色板 | 去饱和的蓝色和灰色、温暖的琥珀色调 |
| 大气条件 | 浓厚的晨雾、阳光中的尘埃粒子、小雨 |
| 质感细节 | 风化的砖墙、抛光的大理石地板、粗糙的木板 |

### 技巧6：流畅的时间流
**规则**：使用"as"、"then"、"while"等连接词确保动作自然衔接。

**示例：**
```
As the camera begins in a stationary wide shot, a tall alien figure steps forward through the haze. Then the camera glides sideways, following the alien's stride.
```

### 技巧7：类型特定语言
**规则**：匹配目标类型的语调和词汇（科幻、恐怖、浪漫、奇幻等）。

**科幻示例：**
```
A maintenance drone glides through a long tunnel inside a deep space cargo vessel, its circular frame rotating gently.
```

### 技巧8：角色特异性
**规则**：为角色赋予独特的特征和行为模式。

### 技巧9：展示，不要讲述情感
**规则**：通过动作、表情和环境来传达情感，而非直接说明。

---

## 四、避免常见问题的关键策略

### 问题1：动作不连贯/卡顿
**解决方案：**
- 使用连接词（as, then, while）建立时序关系
- 描述动作的开始、过程和结束
- 保持动作幅度的连续性

### 问题2：人物扭曲
**解决方案：**
- 提供精确的人体比例描述
- 明确肢体位置和关系
- 避免模糊的动作描述

### 问题3：出现多余人物
**解决方案：**
- 明确场景中的人物数量
- 精确描述人物位置和动作
- 使用负面提示词排除干扰元素

### 问题4：PPT感（帧间跳跃）
**解决方案：**
- 描述平滑的相机运动轨迹
- 加入过渡性动作
- 确保背景元素的连续性

### 问题5：细节模糊
**解决方案：**
- 添加微小的物理细节
- 描述纹理和材质
- 指定焦点和景深

---

## 五、参数调优建议

| 参数 | 推荐值 | 作用 |
|-----|-------|-----|
| Guidance Scale | 3.0-3.5 | 控制与Prompt的匹配度，过高导致画面扭曲 |
| Inference Steps | 20-40 | 质量与速度的平衡，蒸馏模型可用8步 |
| Resolution | 1216×704 | 官方推荐，需为32的倍数 |
| Num Frames | 257 | 需满足8n+1格式（如9, 17, 257） |
| Seed | 固定值 | 保存优秀结果的随机种子 |

---

## 六、实战案例

### 案例1：自然风景动画（图生视频）
```
阳光穿透云层洒在平静的湖面上，形成金色光斑随波浪轻微晃动。
湖水呈现青绿色，湖底可见光滑的鹅卵石。
远处是覆盖着墨绿色森林的山脉，山顶有少量积雪。
清晨时分，薄雾在水面上缓慢流动，几只白鹭掠过水面捕食。
广角镜头从湖岸向湖心缓慢推进，保持低角度拍摄。
柔和的侧逆光，水面反光强烈，整体色调偏冷蓝。
随着镜头推进，雾气逐渐散去，阳光强度逐渐增强。
```

### 案例2：人物动作控制（图生视频）
```
现代舞者在黑色舞台上表演即兴编舞，身体从蜷缩状态缓慢伸展至完全舒展，
手臂以8字形轨迹划动，脚步采用小碎步移动。
舞者穿着黑色紧身衣，皮肤呈小麦色，短发凌乱。
背景是纯黑色无缝幕布，地面有反光材质。
摄像机采用轨道移动拍摄，从正面中景逐渐推近至特写。
单一顶光形成强烈逆光轮廓，主体面部处于半阴影中。
舞者动作速度从慢到快，最后突然定格在身体扭曲的造型。
```

### 案例3：科幻场景
```
A maintenance drone glides through a long tunnel inside a deep space cargo vessel, its circular frame rotating gently. Pale blue emergency lights flicker at regular intervals along the curved walls. The camera follows the drone's path at a distance, maintaining a three-quarter view that captures both the vessel's interior architecture and the drone's subtle movements.
```

---

## 七、总结

| 维度 | 关键要点 |
|-----|---------|
| **结构** | 七段式电影脚本：动作→细节→外观→环境→镜头→光影→情节 |
| **时态** | 全程使用现在时态 |
| **语言** | 电影摄影专业术语 |
| **细节** | 精确到可测量的微小动作 |
| **流畅** | 使用连接词确保时序连续性 |
| **情绪** | 通过视觉元素传达，而非直接说明 |

---

## 八、参考来源

- LTX-2 Prompt Guide. RunDiffusion Learning Center.
- LTX-Video Prompt工程实战指南. CSDN技术博客.
- LTX官方文档：https://docs.ltx.io

---

*文档版本：1.0*  
*生成日期：2026年7月*

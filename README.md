![最好用的五笔输入法](https://github.com/KyleBing/rime-wubi86-jidan/blob/master/imgs/main.gif)

[![LICENSE](https://img.shields.io/badge/license-Anti%20996-blue.svg)](https://github.com/996icu/996.ICU/blob/master/LICENSE) [![996.icu](https://img.shields.io/badge/link-996.icu-red.svg)](https://996.icu)


## 前言

Rime 是一款跨平台的优秀输入法的内核，不同平台的名字也有不同：

- `Windows` - 小狼毫 (weasel)
- `macOS` - 鼠须管 (squirrel)
- `Linux` - 中州韵 (ibus-rime)

> 移动端推荐`手机百度输入法`，关闭词语联想，开启四码上屏，需要添加新词的时候，回到拼音输入法，输入词语就会新建这个词

已知的 Rime 在各平台上的词库配置是相同的，只是入口的配置文件的名字不一样。
Rime 输入法的优势在于它高度的可自定义化，不单单可以定义输入法码表，还可以定义输入法翻译码表的方式，标点对应等等等等。
高度自定义的特性也使得入门的门槛比较高一些。如果想自定义方案，需要有一定的编程基础，至少有一定的程序语言基础。


**用极点输入法的原因**

用久了五笔的都知道，喜欢五笔的因为是五笔的重码少，如果码表太多重码体验就很差了。
好词库的特点是：减少特殊词的数量，增加通用词的频率。

极点版是重码很少的，打起字来很爽，而且对标点的支持也很好，之前用的 `清歌输入法`。
<img src="https://github.com/KyleBing/rime-wubi86-jidan/blob/master/imgs/Rime%E4%BA%94%E7%AC%94%E8%BE%93%E5%85%A5%E6%B3%95.gif" width=600 title="Rime五笔输入法输入样子">


## 使用说明

### 1. 呼出菜单
在输入状态时，<kbd>control</kbd> + <kbd>0</kbd> 或者 <kbd>shift</kbd> + <kbd>control</kbd> + <kbd>0</kbd> 弹出菜单

> 如果第一个组合键不弹出菜单，就用第二个组合键，还不弹出就换个软件，进入输入状态再试
> 有时候是目前的软件环境屏蔽了这个组合键（如：MWeb 中 <kbd>control</kbd> + <kbd>0</kbd> 这个组合键就冲突），换个软件再按就可以了

### 2. 菜单内容
弹出的菜单中，处于第一位的是当前使用的输入法方案，其后跟着是该方案中的输入法菜单，有【半角 - 全角】【简 - 繁】等常见功能菜单，再后面是其它可选的输入法方案，对应 [`default.custom.yaml`](https://github.com/KyleBing/rime-wubi86-jidian/blob/master/default.custom.yaml) 中 `schema_list` 字段内容

### 3. 默认二三候选
默认的二三候选是 `;` `'` 两个键

### 4. 支持 简入繁出
<img src="https://github.com/KyleBing/rime-wubi86-jidan/blob/master/imgs/rime-tradition-output.gif" width=500 title="简入繁出">

是以切换输入方案的形式实现的，使用时，调出菜单，选择 `极点五笔繁体` 方案即可
> 以菜单实现有个弊端：在切换应用后繁体输出的设置并没有保留，也就是说不是全局的，以输入方案的形式就可以实现全局繁体输入。
> 如果不能实现简入繁出的效果，可能需要安装 `OpenCC`[[链接地址](https://github.com/BYVoid/OpenCC)] 库支持，具体不知道怎么操作，因为我配好 `schema` 后就可以用了，没有安装 `OpenCC`，`macOS` `Windows10` 都测试正常

### 5. 系统 `时间` 和 `日期`

输入对应词，获取当前日期和时间
- `date` 输出日期，格式 `2019年06月19日` `2019-06-19`
- `time` 输出时间，格式 `10:00` `10:00:00`

### 6. 支持大写数字输入：壹贰叁肆伍陆

本库中包含一个可以输入大写数字的方案，名叫 `大写数字`，呼出菜单选择该方案即可。
在这个模式下：具体可以看源文件 [`numbers.schema.yaml`](https://github.com/KyleBing/rime-wubi86-jidian/blob/master/numbers.schema.yaml)


| 键 | 对应值        |
|-------------|------------|
| 1234567890  | 壹贰叁肆伍陆柒捌玖零 |
| wqbsjfd.     | 万仟佰拾角分第点    |
| z           | 整之         |
| y           | 元月亿        |

| 键 (按住 shift)  | 对应值         |
|------------|-------------|
| 1234567890 | 一二三四五六七八九〇  |
| wqbsjfd.    | 万千百十角分点     |
| z          | 整之          |
| y          | 元月亿         |


输入案例：

<img title="大写数字输入案例" src="https://github.com/KyleBing/rime-wubi86-jidan/blob/master/imgs/input_number.gif" width="500">


## 安装

### 一、安装 鼠须管(macOS)
去 [官网下载](https://rime.im/download/)，按步骤安装即可


#### 1. 下载 五笔配置文件
也就是当前库，直接下载即可 [https://github.com/KyleBing/rime-wubi86-jidian](https://github.com/KyleBing/rime-wubi86-jidian)

其中的文件列表有：
```bash
.
├── README.md                               # 当前说明文档
├── numbers.schema.yaml                     # 输入方案 - 大写数字
├── rime.lua                                # 可以输出系统变量的函数
├── default.custom.yaml                     # 自定义一些输入法的功能：标点，二三候选等
├── pinyin_simp.dict.yaml                   # 简体拼音码表 - 五笔中拼音输入需要的
├── pinyin_simp.schema.yaml                 # 输入方案 - 简体拼音
├── squirrel.custom.yaml                    # 鼠须管（for macOS）输入法候选词界面
├── weasel.custom.yaml                      # 小狼毫（for Windows）输入法候选词界面
├── wubi86_jidian.dict.yaml                 # 极点 - 五笔码表
├── wubi86_jidian.schema.yaml               # 输入方案 - 极点五笔
├── wubi86_jidian_user.dict.yaml            # 扩展词库 - 用户个人词库
├── wubi86_jidian_extra_brand.dict.yaml     # 扩展词库 - 品牌
├── wubi86_jidian_extra_event.dict.yaml     # 扩展词库 - 事件相关
├── wubi86_jidian_extra_english.dict.yaml   # 扩展词库 - 常用英文
├── wubi86_jidian_extra_location.dict.yaml  # 扩展词库 - 地名
├── wubi86_jidian_extra_media.dict.yaml     # 扩展词库 - 影视名，音乐名
├── wubi86_jidian_extra_people.dict.yaml    # 扩展词库 - 名人
├── wubi86_jidian_extra_pro.dict.yaml       # 扩展词库 - 专业名词
├── wubi86_jidian_extra_game.dict.yaml      # 扩展词库 - 游戏
├── wubi86_jidian_pinyin.schema.yaml        # 输入方案 - 五笔拼音混输
└── wubi86_jidian_trad.schema.yaml          # 输入方案 - 五笔简入繁出
```


#### 2. 设置五笔输入法 macOS 鼠须管
1. macOS 上的 鼠须管 配置文件存放目录是 `~/Library/Rime` 
2. 把上面下载的文件移到该目录中，点击 <kbd>部署</kbd> 即可。

放的时候目录结构是这样的：
```bash
~/Library/
└── Rime
    ├── README.md
    ├── default.custom.yaml
    ├── numbers.schema.yaml 
    ├── pinyin_simp.dict.yaml
    ├── pinyin_simp.schema.yaml
    ├── squirrel.custom.yaml
    ├── weasel.custom.yaml
    ├── wubi86_jidian.dict.yaml
    ├── wubi86_jidian.schema.yaml
    ├── wubi86_jidian_user.dict.yaml
    ├── wubi86_jidian_extra_brand.dict.yaml
    ├── wubi86_jidian_extra_event.dict.yaml
    ├── wubi86_jidian_extra_english.dict.yaml
    ├── wubi86_jidian_extra_location.dict.yaml
    ├── wubi86_jidian_extra_media.dict.yaml
    ├── wubi86_jidian_extra_people.dict.yaml
    ├── wubi86_jidian_extra_pro.dict.yaml
    ├── wubi86_jidian_extra_game.dict.yaml
    ├── wubi86_jidian_pinyin.schema.yaml
    └── wubi86_jidian_trad.schema.yaml  
```
> **注意**：对于不熟悉命令行操作的朋友， `~` 代表的是当前用户的主目录，比如我的用户名是 `kyle`, `~` 就代表 `/Users/kyle/` 这个绝对路径。
> 需要将你下载的文件放入 `/Users/你用户名/Library/Rime` 这个目录下，了然否？


#### 3. 皮肤

<img title="skin" src="https://github.com/KyleBing/rime-wubi86-jidan/blob/master/imgs/skin.png" width=500 />


### 二、配置 小狼毫（Windows）

<img title="skin" src="https://github.com/KyleBing/rime-wubi86-jidan/blob/master/imgs/windows_skin.png" width=300 />

Windows 中的配置方法：
1. 点击【开始】
2. 打开刚刚安装的小狼毫输入法程序目录，打开【用户文件夹】
3. 把该项目中的文件复制到里面
4. 点击开始菜单中的【部署】即可


## 其它相关链接

**资源链接**
- 极点五笔方案(github)： [https://github.com/KyleBing/rime-wubi86-jidan](https://github.com/KyleBing/rime-wubi86-jidan)
- Rime github 地址：   [https://github.com/rime]( https://github.com/rime)
- Rime 输入方案集合：  [https://github.com/rime/plum]( https://github.com/rime/plum)
- Rime 官方五笔码表：  [https://github.com/rime/rime-wubi](https://github.com/rime/rime-wubi)
- Rime 简拼输入方案：  [https://github.com/rime/rime-pinyin-simp](https://github.com/rime/rime-pinyin-simp)

**配置教程链接**
- Rime 官网：   [https://rime.im/](https://rime.im/)
- Rime 输入方案参数详解：  [https://github.com/LEOYoon-Tsaw/Rime_collections/blob/master/Rime_description.md](https://github.com/LEOYoon-Tsaw/Rime_collections/blob/master/Rime_description.md)
- 中英切换自定义：[https://gist.github.com/lotem/2981316](https://gist.github.com/lotem/2981316)



## 关于自定义一些功能

所有配置说明都在配置文件中说明了，如果有其它问题可以在 `issue` 中提出，或者在群里（QQ群：878750538）讨论，有需要就 `@青枫`

### 1. 各文件作用说明

```bash
├── numbers.schema.yaml                     # 输入方案 - 大写数字
├── squirrel.custom.yaml                    # 鼠须管（for macOS）输入法候选词界面
├── weasel.custom.yaml                      # 小狼毫（for Windows）输入法候选词界面
├── default.custom.yaml                     # 自定义一些输入法的功能：标点，二三候选等
├── wubi86_jidian.schema.yaml               # 输入方案 - 极点五笔
├── wubi86_jidian_user.dict.yaml            # 扩展词库 - 用户个人词库
├── wubi86_jidian_extra_brand.dict.yaml     # 扩展词库 - 品牌
├── wubi86_jidian_extra_event.dict.yaml     # 扩展词库 - 事件相关
├── wubi86_jidian_extra_english.dict.yaml   # 扩展词库 - 常用英文
├── wubi86_jidian_extra_location.dict.yaml  # 扩展词库 - 地名
├── wubi86_jidian_extra_media.dict.yaml     # 扩展词库 - 影视名，音乐名
├── wubi86_jidian_extra_people.dict.yaml    # 扩展词库 - 名人
├── wubi86_jidian_extra_pro.dict.yaml       # 扩展词库 - 专业名词
├── wubi86_jidian_extra_game.dict.yaml      # 扩展词库 - 游戏
```

### 2. 开启五笔模式下的自动造词功能
默认是没有开启的，如果想开启需要手动编辑 `wubi86_jidian.schema.yaml` 文件，里面也有相关的说明

> 除了把文件中自动造词部分都设为 `true` 之外，还需要把 `speller` 那段的都注释掉，因为那里都是直接上屏的，直接上屏就无法造词了，所以需要注释掉。
> 造词功能是这样的，在输入一次之后，输入法会记住这个连词，打的时候后面会有图标指示，下次再输入这个词的时候，就会固定这个词，并在用户词典中新增这个词的词条。

你修改后的配置应该是这样的：

```yaml
speller:
#  max_code_length: 4                    # 四码上屏
#  auto_select: true                     # 自动上屏
#  auto_select_unique_candidate: true    # 无重码自动上屏

translator:
  # 开启自动造词相关设置
  enable_sentence: ture                # 是否开启句子输入模式
  enable_user_dict: ture               # 是否开启用户词典（用户词典记录动态字词频，用户词）
  enable_encoder: ture                 # 自动造词
  encode_commit_history: ture          # 是否对已上屏的词自动造词
```

效果如图：

<img title="1" src="https://github.com/KyleBing/rime-wubi86-jidan/blob/master/imgs/wubi-auto-1.png" width="500">

<img title="2" src="https://github.com/KyleBing/rime-wubi86-jidan/blob/master/imgs/wubi-auto-2.png" width="500">

<img title="3" src="https://github.com/KyleBing/rime-wubi86-jidan/blob/master/imgs/wubi-auto-3.png" width="500">

<img title="4" src="https://github.com/KyleBing/rime-wubi86-jidan/blob/master/imgs/wubi-auto-4.png" width="500">

### 3. 输出系统变量

自 Rime `v0.13` 之后可自定义输出系统变量，如日期等

文件 [`rime.lua`](https://github.com/KyleBing/rime-wubi86-jidian/blob/master/rime.lua) 盛放的是调用的方法，你需要在相应的 `XXXX.schema.yaml` 文件的 `engine`/`translators` 字段添加一些东西，可以参阅本库的 [`wubi86_jidian.schema.yaml`](https://github.com/KyleBing/rime-wubi86-jidian/blob/master/wubi86_jidian.schema.yaml) 文件。
具体 `rime.lua` 文件说明参阅这里： [https://github.com/hchunhui/librime-lua/blob/master/sample/lua/date.lua](https://github.com/hchunhui/librime-lua/blob/master/sample/lua/date.lua)


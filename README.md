# project-insight-lsz

给 `lsz` 用的批量注释 skill。

它的目标很单一：当一个目录下有很多项目、脚本、软件或资料时，帮用户快速识别内容，并生成一批可直接执行的 `lsz -s` 命令。

## 适用场景

- `~/Software`
- `~/Downloads`
- `~/work`
- 家目录下很多杂项目录
- 工具箱、脚本库、漏洞复现目录

## 设计原则

- 默认只输出 `lsz -s`
- 先判断备注有没有信息增益；没有就跳过
- 优先保留社区通用叫法
- 但如果名字容易让人记错用途，优先写用途
- 中文常用叫法比英文原名更直观时，优先中文
- 不把大家都认识的名字硬翻译成功能描述
- 中文为主，但常见短英文和缩写可以直接保留
- 除 `lsz -s` 外，其它动作都要先确认
- 只分析用户明确指定的目录范围，不默认扫所有目录

## 典型风格

更推荐这样：

- `BurpSuitePro` -> `Burp`
- `BiliBili` -> `哔哩哔哩`
- `Telegram` -> `电报`
- `Memos` -> `轻量笔记`
- `Listen_1` -> `聚合听歌`
- `YuQueDocFetch` -> `语雀文档批量下载`
- `misc` -> `杂项`

不推荐这样：

- `BurpSuitePro` -> `抓包测试工具`
- `nmap` -> `扫描工具`
- `Wireshark` -> `抓包软件`
- `Memos` -> `Memos`
- `Listen_1` -> `Listen1`
- `android-studio` -> `Android Studio`

如果备注和目录名几乎一样、没有增加辨识度，应该直接跳过，不写。

## 翻译与写入边界

如果用户明确要求翻译 README 或帮助文档，可以先输出翻译草稿。

默认不要直接写文件。以下动作都需要用户确认：

- `lsz -b ...`
- 写入 `README.md`
- 覆盖原文档
- 其它任何非 `lsz -s` 的落地操作

即使用户提到“这些项目很常用”，也应先确认，再决定是否生成 `lsz -b add ...`。

如果用户没有明确给出要处理的目录或路径，先让用户指定范围，不要默认从家目录或当前机器的所有目录开始扫。

## 输出示例

```bash
lsz -s "Burp" ~/Software/BurpSuitePro
lsz -s "nmap" ~/Software/nmap
lsz -s "Wireshark" ~/Software/Wireshark
lsz -s "语雀文档批量下载" ~/Software/YuQueDocFetch
```

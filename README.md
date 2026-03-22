# 透明 opencode 终端背景

## 给 OpenCode / AI 直接执行的说明

把下面整段话直接发给 OpenCode，即可让它帮你配置：

```text
请帮我安装这个 opencode 自定义主题，并确保它生效。

目标文件来源：
- 请按当前机器上的实际文件位置读取 `transparent.json`

请按下面要求执行：
1. 确认 `opencode` 的用户配置目录下存在 `themes` 文件夹；如果不存在就创建。
   推荐相对位置：`~/.config/opencode/themes/`
2. 把主题文件 `transparent.json` 复制到：
   `~/.config/opencode/themes/transparent.json`
3. 打开并修改：
   `~/.config/opencode/opencode.json`
4. 在 JSON 顶层加入或确认存在：
   `"theme": "transparent"`
5. 不要改动其他无关配置。
6. 修改完成后，重新读取目标文件并确认：
   - `~/.config/opencode/themes/transparent.json` 已存在
   - `~/.config/opencode/opencode.json` 顶层包含 `"theme": "transparent"`
7. 最后告诉我需要手动重启 `opencode` 才会生效。
```

如果你想把这整个说明文件路径直接发给 AI，也可以说：

```text
请阅读并执行这个说明文件，然后按其中的相对路径安装主题。
```

---

这是一个给 `opencode` CLI / TUI 使用的自定义主题文件，目标是：

- 尽量让 opencode 主界面背景透明
- 让宿主终端背景尽可能露出来
- 在 `/model` 这类菜单里保留一点极轻的菜单托底，避免完全混在一起

---

## 文件说明

本目录包含：

- `transparent.json`：opencode 自定义主题文件

---

## 放到哪里

把 `transparent.json` 放到用户配置目录下的这个位置：

`~/.config/opencode/themes/`

如果 `themes` 文件夹不存在，就手动新建。

最终路径应为：

`~/.config/opencode/themes/transparent.json`

---

## opencode 主配置怎么改

然后打开这个文件：

`~/.config/opencode/opencode.json`

在 JSON 顶层加入这一行：

```json
"theme": "transparent"
```

例如：

```json
{
  "$schema": "https://opencode.ai/config.json",
  "theme": "transparent",
  "mcp": {
    "chrome-devtools": {
      "command": ["npx", "-y", "chrome-devtools-mcp@latest"],
      "enabled": true,
      "type": "local"
    }
  }
}
```

注意：

- `"theme": "transparent"` 要和 `transparent.json` 的文件名一致
- 不要写成别的名字，除非你连文件名一起改

---

## 当前主题效果

当前这份主题的关键设置是：

- `background = transparent`
- `backgroundPanel = transparent`
- `backgroundElement = transparent`
- `backgroundMenu = #FFFAFA20`

含义：

- 主界面尽量透明
- 输入区 / 元素区尽量透明
- 菜单区域保留一层很轻的浅色托底
- `/model` 菜单和底部区域之间会有一点层次感

---

## 用法

1. 把 `transparent.json` 复制到：
   - `~/.config/opencode/themes/`
2. 修改：
   - `~/.config/opencode/opencode.json`
3. 确保顶层有：
   - `"theme": "transparent"`
4. 重启 `opencode`

---

## 如果没有生效

检查以下几项：

1. 文件名是否是：
   - `transparent.json`
2. 放置目录是否正确：
   - `~/.config/opencode/themes/`
3. `opencode.json` 顶层是否真的有：
   - `"theme": "transparent"`
4. 是否已经完全重启 `opencode`

---

## 重要说明

如果你已经把 opencode 背景改成透明，但界面下方仍然发黑，这通常不是主题 JSON 本身的问题，而更可能是：

- PowerShell / 宿主终端默认黑底
- 终端渲染层默认背景
- OpenTUI / CLI 更底层的默认清屏背景

也就是说：

这份主题能做的是“尽量让 opencode 不主动铺底色”，
但不能保证宿主终端本身就一定会透出你想要的玻璃背景。

---

## 跨平台说明

这份 README 使用的是相对用户目录写法：

- `~/.config/opencode/themes/transparent.json`
- `~/.config/opencode/opencode.json`

其中：

- Linux：通常可直接按这个路径使用
- macOS：如果你的 opencode 配置目录不同，请让 AI 先定位实际配置目录，再放到对应 `opencode/themes/` 下
- Windows：不同环境可能会把 `~` 映射到不同用户目录，原则上仍然是“用户目录下的 `.config/opencode/`”

重点不是某个固定绝对路径，而是：

1. 找到当前用户的 `opencode` 配置目录
2. 把主题文件放到该目录下的 `themes/transparent.json`
3. 在同级的 `opencode.json` 顶层设置 `"theme": "transparent"`

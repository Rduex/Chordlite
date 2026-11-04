# 排错

按顺序试，多数问题在第 1、2 步就解决。

---

## 第 1 步：确认文件夹完整

解压后的目录应该长这样：

```
chordlite\
  chordlite.exe          ← 双击这个
  start.bat              ← 备用启动
  check_env.bat          ← 自检
  app\
  models\
  venv\
  assets\
  INSTALL.md
  requirements.txt
```

**关键**：`venv\` 和 `models\` 必须和 exe 同级。

如果解压时只解出 `chordlite.exe`，说明解压软件把子目录丢了，换个解压工具（7-Zip / Bandizip）。

---

## 第 2 步：跑自检

双击 **`check_env.bat`**，会打印七项路径。正常长这样：

```
home             OK       D:\...\chordlite
models           OK       D:\...\chordlite\models
ismir19          OK       D:\...\chordlite\models\ismir19
chordmini        OK       D:\...\chordlite\models\chordmini
chordnet_ckpt    OK       D:\...\chordlite\models\chordnet
piano_ckpt       OK       D:\...\chordlite\models\piano\...
temp             OK       D:\...\chordlite\temp
```

**任何一项 `MISSING`** 就说明那个目录不在位，重新解压。

---

## 第 3 步：用 start.bat 看真实报错

`chordlite.exe` 是窗口程序，出错时不一定显示信息。`start.bat` 会保留黑窗口和完整报错。

### 常见报错对照

| 报错 | 原因 | 怎么办 |
|---|---|---|
| `venv not found` | venv 目录缺失 | 重新解压 |
| `ModuleNotFoundError: No module named 'torch'` | venv 被破坏 | 重新解压整个文件夹 |
| `ModuleNotFoundError: 'sklearn'` | venv 被手动精简过 | 重新解压（**sklearn 不能删**） |
| `ModuleNotFoundError: 'matplotlib'` | 同上 | 同上（**matplotlib 也不能删**） |
| `OSError: [WinError 10048]` | 端口被占 | 关掉其它实例 |
| `NoBackendError` | 音频解不开 | 换格式另存为 wav 再试 |
| `CUDA` 相关报错 | 装了 GPU 版 torch | 本软件只需 CPU 版 |

---

## 第 4 步：杀毒软件

未签名的 exe 常被误报。判断方法：

1. 打开杀毒软件的**隔离区**，看有没有 `chordlite.exe`
2. 如果有，恢复并加白名单
3. 或者直接用 `start.bat`（它是文本文件，不会被拦）

**这不是在劝你关杀软**。如果不信任这个软件，完全可以不用。源码和依赖清单都在仓库里，可以自己核对。

---

## 第 5 步：还不行

开 [Issue](https://github.com/Rduex/Chordlite/issues)，附上：

1. `check_env.bat` 的完整输出（**截图或复制文字**）
2. `start.bat` 的报错（如果有）
3. Windows 版本
4. 你用的是哪个板块、什么类型的音频

**不要附上音频文件本身**——版权问题，而且多数问题看报错就能定位。

---

## 附：想自己从源码跑

```bat
cd /d <解压目录>

python -m venv venv2
venv2\Scripts\activate

REM 关键：必须用 --extra-index-url，不能用 --index-url
pip install torch==2.5.1 --extra-index-url https://download.pytorch.org/whl/cpu
pip install -r requirements.txt

venv2\Scripts\python.exe app\paths.py     REM 先确认模型找得到
venv2\Scripts\python.exe app\serve.py     REM 然后启动
```

需要 Python **3.10**（3.11/3.12 部分依赖装不上）。

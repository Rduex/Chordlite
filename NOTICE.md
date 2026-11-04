# 第三方组件与素材声明

本项目使用了以下第三方软件和素材。此处按其许可证要求列出。

## 运行时依赖

| 组件 | 版本 | 许可证 | 用途 |
|---|---|---|---|
| [PyTorch](https://pytorch.org/) | 2.5.1+cpu | BSD-3-Clause | 推理框架 |
| [ChordNet](https://github.com/music-x-lab/ISMIR2019-Chord-Recognition) | ISMIR2019 | **MIT** | 和弦识别模型 |
| [ChordMini](https://github.com/ptnghia1102/ChordMini) | — | MIT | 和弦融合（ONNX） |
| [piano_transcription_inference](https://github.com/bytedance/piano_transcription) | 0.0.6 | **MIT** | 钢琴转谱 |
| [librosa](https://librosa.org/) | 0.10.2 | ISC | 音频特征 |
| [PyAV](https://pyav.org/) | 17.1.0 | BSD-3-Clause | 音频解码 |
| [soundfile](https://python-soundfile.readthedocs.io/) | 0.14.0 | BSD-3-Clause | 音频读写 |
| [onnxruntime](https://onnxruntime.ai/) | 1.23.2 | MIT | ONNX 推理 |
| [pretty_midi](https://github.com/craffel/pretty-midi) | 0.2.11 | MIT | MIDI 读写 |
| [NumPy](https://numpy.org/) | 1.26.4 | BSD-3-Clause | 数值计算 |
| [SciPy](https://scipy.org/) | 1.15.3 | BSD-3-Clause | 信号处理 |
| [scikit-learn](https://scikit-learn.org/) | 1.7.2 | BSD-3-Clause | 被 librosa.decompose 间接使用 |
| [Numba](https://numba.pydata.org/) / llvmlite | 0.61 / 0.44 | BSD-2-Clause | librosa JIT |
| [matplotlib](https://matplotlib.org/) | 3.10.9 | PSF-based | 被钢琴转谱模块导入 |

## 模型权重

| 权重 | 来源 | 许可证 |
|---|---|---|
| ChordNet 5 折 `.sdict` | Music X Lab ISMIR2019 | MIT |
| `chordnet.onnx` | ChordMini | MIT |
| `note_F1=0.9677_pedal_F1=0.9186.pth` | ByteDance piano_transcription | MIT |

## 界面素材

### 背景照片

来自 Wikimedia Commons，均为自由授权：

| 板块 | 文件 | 作者 | 许可证 |
|---|---|---|---|
| 流行 / 摇滚 | Roland Jazz Chorus-120 on the stage | Solomon203 | CC BY-SA 4.0 |
| 日系 J-Pop | Pink Cherry Blossom | pxhere | **CC0** |
| 爵士 | A Saxophone | Sally V | CC BY-SA 4.0 |
| 钢琴独奏 | PianoKeyboard2 | Raysonho @ Open Grid Scheduler | **CC0** |

CC BY-SA 要求署名。署名入口在界面右下角「背景图来源」，完整信息见 `assets/CREDITS.md`。

### 图标

`assets/chordlite.ico` 由本项目的 `app/make_icon.py` 用 Pillow 生成，无外部素材。

### 教学示例音频

`content/audio/*.wav` 由 `app/build_examples.py` **从和弦本身程序合成**，不含任何录音或采样素材。

## 参考文献

和弦识别的评测口径参考：

- Ni et al., *Revisiting the chord recognition problem: A deep learning approach*, ISMIR 2019
- Cho et al., *ChordMini* (2024)
- Kong et al., *High-resolution piano transcription with pedals by regressing onset and offset times*, TASLP 2021

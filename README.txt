# Multimodal Emotion-Aware AI Assistant

本專案是一套本地端多模態情緒感知 AI 互動系統。

系統會透過文字、語音與臉部表情分析使用者情緒，並依照情緒結果進行多模態融合，再動態調整互動人格，搭配前面的對話上下文產生回應，最後透過語音合成播放 AI 的回答。

---

## 功能

- 語音輸入與語音辨識
- 中文文字情緒辨識
- 英文文字情緒辨識
- 語音情緒辨識
- 臉部表情情緒辨識
- 多模態情緒融合
- 自動人格切換
- 手動人格切換
- 對話上下文記錄
- CosyVoice 2 語音合成
- 中文與英文互動支援

---

## 系統需求

建議使用環境：

- Windows 11
- Python 3.10
- NVIDIA GPU
- CUDA
- 麥克風
- 攝影機

本專案包含多個 AI 模型，因此實際硬體需求會依模型與執行方式有所不同。

---

## 安裝方式

### 1. 下載專案

```bash
git clone https://github.com/iffc1852/for-gca-2026.git
cd for-gca-2026
```

### 2. 建立 Python 虛擬環境

```bash
python -m venv .venv
```

啟用虛擬環境：

```bash
.venv\Scripts\activate
```

### 3. 安裝 Python 套件

GPU 版本：

```bash
pip install -r requirements-gpu.txt

---

## CosyVoice 2 設定

本專案使用 CosyVoice 2 進行語音合成。

CosyVoice 本身不直接包含於此 Repository 中，請另外下載官方 CosyVoice 專案，並放置於本專案根目錄。

建議資料夾結構：

```text
for-gca-2026/
├─ CosyVoice/
├─ audio/
├─ main.py
├─ gui_main.py
├─ config.py
├─ services.py
└─ ...
```

CosyVoice 2 模型預設放置位置：

```text
CosyVoice/pretrained_models/CosyVoice2-0.5B/
```

---

## 音訊檔案

本專案會使用部分語音與參考音訊檔案。

建議放置於：

```text
audio/
```

例如：

```text
audio/
├─ Cosyvoice_test1.wav
├─ ref_encouraging.wav
├─ ref_happy.wav
├─ ref_gentle.wav
├─ answer_yes_Zh.mp3
├─ answer_yes_En.mp3
├─ Switching_complete_Zh.mp3
└─ Switching_complete_En.mp3
```

---

## 模型設定

部分 AI 模型與模型權重因檔案大小或授權因素，不直接包含於本 Repository。

本專案會使用以下模型或元件：

- Whisper 語音辨識模型
- 中文文字情緒辨識模型
- 英文文字情緒辨識模型
- Emotion2Vec 語音情緒辨識模型
- Py-Feat 臉部表情辨識
- CosyVoice 2
- 本地端大型語言模型

請依照各模型官方來源下載並安裝。

---

## 本地端 LLM 設定

本專案目前使用本地端 LLM API。

預設 API 位址：

```text
http://127.0.0.1:5000/v1
```

設定內容可於：

```text
config.py
```

中修改。

啟動主程式之前，請先確認本地端 LLM API 已正常運作。

---

## 執行方式

完成環境、模型與 CosyVoice 設定後，執行：

```bash
python main.py
```

系統啟動後即可開始進行語音互動與多模態情緒辨識。

---

## 專案結構

```text
for-gca-2026/
├─ main.py
├─ gui_main.py
├─ config.py
├─ services.py
├─ utils.py
├─ model_loader.py
├─ hardware_setup.py
├─ body_emotion_detector.py
├─ facial_emotion_detector_pyfeat.py
│
├─ requirements-gpu.txt
│
├─ audio/
├─ assets/
├─ image/
│
└─ CosyVoice/
```

其中：

- `main.py`：系統主要執行程式
- `gui_main.py`：圖形介面
- `config.py`：系統參數與模型設定
- `services.py`：系統功能整合
- `model_loader.py`：模型載入相關功能
- `facial_emotion_detector_pyfeat.py`：臉部情緒辨識
- `body_emotion_detector.py`：身體情緒辨識相關程式
- `requirements-gpu.txt`：GPU 環境套件需求


---

## 多模態情緒融合

系統會將不同模態的情緒辨識結果進行融合。

目前主要使用：

```text
文字情緒
+
語音情緒
+
臉部表情情緒
```

再依照不同模態的權重與信心度，產生最後的情緒結果。

情緒融合與相關權重可於：

```text
config.py
```

中調整。

---

## 人格系統

系統會依照辨識到的情緒，自動切換不同互動人格。

包含：

- 安撫型
- 開朗型
- 幽默型
- 溫柔型
- 理性型
- 鼓勵型
- 共鳴型

除了自動切換外，也支援手動切換人格。

---

## Demo

實機操作影片：

```text
之後補上 YouTube 或其他公開影片連結
```

---

## 操作截圖

可於此區域放置實際系統操作畫面。

例如：

```markdown
![Main Interface](image/main_interface.png)

![Emotion Detection](image/emotion_detection.png)

![Conversation Demo](image/conversation_demo.png)
```

---

## 注意事項

- 本專案主要以本地端方式執行。
- 部分功能需要 NVIDIA GPU。
- 模型權重不直接包含於 Repository。
- CosyVoice 需另外下載與安裝。
- 執行前請先確認本地端 LLM API 已正常啟動。
- 不同硬體環境可能需要調整 CUDA、PyTorch 或其他相關套件版本。

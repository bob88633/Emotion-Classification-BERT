情緒分類實作筆記：BERT 與 DistilBERT 的微調練習
這個專案是我使用 Hugging Face 的 Transformers 庫來練習模型微調（Fine-tuning）的紀錄。我選用了 dair-ai/emotion 資料集，目標是讓模型能精準辨識文字背後隱藏的情緒類別。

實作重點
模型測試：同時跑了 BERT-base-uncased 和 DistilBERT-base-uncased 兩個模型來對比結果。

優化訓練速度：為了不浪費 GPU 資源，我使用了動態填充（Dynamic Padding）。透過 DataCollatorWithPadding，系統會根據每個 batch 的最長句子來調整長度，這讓訓練效率提升了不少。

完整的評估紀錄：除了準確率（Accuracy），還計算了 Precision、Recall 和 F1-score，確保模型在每一種情緒的判斷上都是均衡的。

訓練設定：使用了 Adam 優化器，學習率設為 2e-5，並跑了 5個 Epochs。

實驗結果
在測試集上的表現超乎預期，特別是 DistilBERT 在保持輕量的同時，準確率甚至比 BERT 還高一點點

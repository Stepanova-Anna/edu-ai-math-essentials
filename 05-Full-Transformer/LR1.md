# Отчет по лабораторной работе №5
## Полный трансформер encoder-decoder на Tiny Shakespeare

---

## Цель работы

Реализовать полную архитектуру Transformer encoder-decoder для задачи предсказания следующего токена (авторегрессия) на текстовом корпусе Tiny Shakespeare. Модель должна принимать последовательность символов и генерировать продолжение, используя механизмы self-attention и cross-attention.

---

## Конфигурация

| Параметр | CPU-friendly | GPU-friendly |
|----------|--------------|--------------|
| Размер корпуса | 140,000 символов | 220,000 символов |
| Длина входа (src_len) | 72 | 80 |
| Длина выхода (tgt_len) | 72 | 80 |
| Размер батча | 64 | 128 |
| Размер модели (d_model) | 128 | 192 |
| Число голов | 4 | 6 |
| Размер FFN | 256 | 512 |
| Число слоёв | 2 | 3 |
| Эпохи | 14 | 18 |

---

# Скриншоты выполнения

<img width="464" height="628" alt="image" src="https://github.com/user-attachments/assets/5c0f7933-700b-47ae-bc9e-4acf87779d38" />

<img width="890" height="75" alt="image" src="https://github.com/user-attachments/assets/1bdd2984-0eb8-4176-9670-4fdf9e841500" />

<img width="740" height="355" alt="image" src="https://github.com/user-attachments/assets/647e6311-b19a-4679-8adf-3cdfa1971552" />

<img width="373" height="59" alt="image" src="https://github.com/user-attachments/assets/5da71ed9-bda6-4825-afcc-24212ef41e24" />

<img width="430" height="91" alt="image" src="https://github.com/user-attachments/assets/edf778ee-b0ce-46a2-a7ee-1464a937e5ca" />

<img width="1481" height="541" alt="image" src="https://github.com/user-attachments/assets/deaa2b26-4b20-49ae-9eda-a265f13b147f" />


<img width="548" height="389" alt="image" src="https://github.com/user-attachments/assets/ebb68eee-7c96-4799-b71a-0c54b6132d84" />

<img width="626" height="503" alt="image" src="https://github.com/user-attachments/assets/752aa80c-b599-4db4-9153-f5934a5db1c9" />

<img width="536" height="610" alt="image" src="https://github.com/user-attachments/assets/e6aac1e5-f407-4eb1-9ab4-bb1ca1446174" />

<img width="602" height="541" alt="image" src="https://github.com/user-attachments/assets/8e7caab0-12c0-4050-acc4-0da0e5aecd2c" />




# Вывод

В ходе лабораторной работы реализован полный Transformer encoder-decoder для символьной генерации текста на корпусе Tiny Shakespeare. Ключевые результаты:

1. **Архитектура** — успешно реализованы все компоненты: PositionalEncoding, TokenAndPositionEmbedding, TransformerEncoderBlock, TransformerDecoderBlock, FullTransformerModel.
2. **Маскирование** — корректно работают три типа масок: encoder self-attention (padding mask), decoder masked self-attention (causal mask), cross-attention (padding mask).
3. **Качество** — модель достигла перплексии ~3.32, что значительно лучше униграммного baseline (~4.50), подтверждая способность выявлять языковые паттерны.
4. **Генерация** — в 18+ из 20 фиксированных промптов модель генерирует продолжения с высоким совпадением с эталоном.
5. **Диагностика** — attention heatmap подтверждает отсутствие доступа к будущим позициям в декодере.

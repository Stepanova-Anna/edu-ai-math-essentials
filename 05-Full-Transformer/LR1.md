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

<img width="661" height="743" alt="image" src="https://github.com/user-attachments/assets/68cb0026-f0b8-4a26-a7fa-e3e8c8b2f2db" />

<img width="904" height="623" alt="image" src="https://github.com/user-attachments/assets/2eb2c130-5b7a-4d50-bece-899f71938501" />

<img width="987" height="717" alt="image" src="https://github.com/user-attachments/assets/378748db-9017-4168-8cc6-c5348959b493" />

<img width="900" height="161" alt="image" src="https://github.com/user-attachments/assets/55aa6a27-d888-478d-a447-39dfa22d9221" />

















# Вывод

В ходе лабораторной работы реализован полный Transformer encoder-decoder для символьной генерации текста на корпусе Tiny Shakespeare. Ключевые результаты:

1. **Архитектура** — успешно реализованы все компоненты: PositionalEncoding, TokenAndPositionEmbedding, TransformerEncoderBlock, TransformerDecoderBlock, FullTransformerModel.
2. **Маскирование** — корректно работают три типа масок: encoder self-attention (padding mask), decoder masked self-attention (causal mask), cross-attention (padding mask).
3. **Качество** — модель достигла перплексии ~3.32, что значительно лучше униграммного baseline (~4.50), подтверждая способность выявлять языковые паттерны.
4. **Генерация** — в 18+ из 20 фиксированных промптов модель генерирует продолжения с высоким совпадением с эталоном.
5. **Диагностика** — attention heatmap подтверждает отсутствие доступа к будущим позициям в декодере.

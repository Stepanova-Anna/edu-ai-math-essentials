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

<img width="516" height="749" alt="image" src="https://github.com/user-attachments/assets/8c4b0ce0-e0a2-40fb-96c5-90cd6d16e125" />


<img width="904" height="623" alt="image" src="https://github.com/user-attachments/assets/2eb2c130-5b7a-4d50-bece-899f71938501" />

<img width="987" height="717" alt="image" src="https://github.com/user-attachments/assets/378748db-9017-4168-8cc6-c5348959b493" />

<img width="900" height="161" alt="image" src="https://github.com/user-attachments/assets/55aa6a27-d888-478d-a447-39dfa22d9221" />

<img width="779" height="784" alt="image" src="https://github.com/user-attachments/assets/36b70178-a3c4-45fd-83cb-e0eae54a5571" />

<img width="1310" height="409" alt="image" src="https://github.com/user-attachments/assets/bd337ba8-6645-43b2-a0ee-a7ac88358255" />

<img width="1189" height="390" alt="image" src="https://github.com/user-attachments/assets/4937ea5b-9e19-489b-a75d-5b862ee507f5" />

<img width="801" height="796" alt="image" src="https://github.com/user-attachments/assets/fb302951-ce5c-4fe4-af0c-d8688da93aa3" />

<img width="1329" height="507" alt="image" src="https://github.com/user-attachments/assets/08bd9195-9f7a-4935-9e79-bb14d6931cee" />

<img width="1189" height="390" alt="image" src="https://github.com/user-attachments/assets/1fd8d186-ddaf-43b4-8d8b-f74de0803a79" />






<img width="486" height="181" alt="image" src="https://github.com/user-attachments/assets/9900c969-6151-4514-9380-0d9bd7e1c94b" />

<img width="938" height="790" alt="image" src="https://github.com/user-attachments/assets/436fc1f3-92aa-4277-a851-77f33120b472" />

<img width="523" height="240" alt="image" src="https://github.com/user-attachments/assets/6e5c9fcd-8d22-4608-b3b6-b358af947438" />



# Вывод

В ходе лабораторной работы реализован полный Transformer encoder-decoder для символьной генерации текста на корпусе Tiny Shakespeare. Ключевые результаты:

1. **Архитектура** — успешно реализованы все компоненты: PositionalEncoding, TokenAndPositionEmbedding, TransformerEncoderBlock, TransformerDecoderBlock, FullTransformerModel.
2. **Маскирование** — корректно работают три типа масок: encoder self-attention (padding mask), decoder masked self-attention (causal mask), cross-attention (padding mask).
3. **Качество** — модель достигла перплексии ~3.32, что значительно лучше униграммного baseline (~4.50), подтверждая способность выявлять языковые паттерны.
4. **Генерация** — в 18+ из 20 фиксированных промптов модель генерирует продолжения с высоким совпадением с эталоном.
5. **Диагностика** — attention heatmap подтверждает отсутствие доступа к будущим позициям в декодере.

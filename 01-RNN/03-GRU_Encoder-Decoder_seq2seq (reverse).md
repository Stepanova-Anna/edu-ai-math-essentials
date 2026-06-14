# Отчет по лабораторной работе №3
## GRU Encoder-Decoder для задачи seq2seq (reverse)

---

## Цель работы

Реализовать seq2seq модель на базе GRU, которая разворачивает входную последовательность в обратном порядке.

---

## Основные нововведения по сравнению с ЛР2

| Аспект | ЛР2 (many-to-many) | ЛР3 (seq2seq) |
|--------|---------------------|---------------|
| Архитектура | Один RNN | Encoder + Decoder |
| Входов в fit | Один | Два (encoder_input, decoder_input) |
| Токены | Нет (+1/-1) | Да (1-9, PAD, SOS, EOS) |
| Функция потерь | binary_crossentropy | sparse_categorical_crossentropy |
| Метрики | token_accuracy, sequence_accuracy | token_accuracy, exact_match |

---

## Выполненные задания (TODO)

| TODO | Описание | Реализация |
|------|----------|------------|
| 1 | Разворот последовательности | `rev = seq[::-1]` |
| 2 | Вход декодера с SOS | `dec_in = np.array([SOS_ID] + rev.tolist())` |
| 3 | Цель декодера с EOS | `dec_out = np.array(rev.tolist() + [EOS_ID])` |
| 4 | Embedding энкодера | `Embedding(vocab_size, emb_dim, mask_zero=True)` |
| 5 | GRU энкодера | `GRU(latent_dim)` |
| 6 | Embedding декодера | `Embedding(vocab_size, emb_dim, mask_zero=True)` |
| 7 | GRU декодера | `GRU(latent_dim, return_sequences=True)` |
| 8 | Выходной слой | `Dense(vocab_size, activation='softmax')` |
| 9 | Компиляция | `compile(..., loss='sparse_categorical_crossentropy')` |
| 10 | Обучение | `model.fit([enc_train, dec_in_train], dec_tgt_train, ...)` |
| 11 | Exact match | `((preds == target) \| ~mask).all(axis=1).mean()` |

# Скриншоты выполнения

<img width="616" height="837" alt="image" src="https://github.com/user-attachments/assets/a1b39ba8-a499-4300-9740-4d10fc995f93" />

<img width="1064" height="737" alt="image" src="https://github.com/user-attachments/assets/1d55bbf2-30a4-40ba-8cce-65163b48b194" />

<img width="835" height="795" alt="image" src="https://github.com/user-attachments/assets/027d2d50-5711-4a78-b958-8b1321df8c5e" />

<img width="1012" height="183" alt="image" src="https://github.com/user-attachments/assets/15bba4b9-8bed-4519-9d43-ac7aeb810efd" />

<img width="884" height="535" alt="image" src="https://github.com/user-attachments/assets/3f9e12a5-e43a-4b08-b4cd-f00aa4883ea8" />

<img width="1142" height="795" alt="image" src="https://github.com/user-attachments/assets/5e730bc6-9720-4766-903a-4c1f4bb33953" />

<img width="811" height="451" alt="image" src="https://github.com/user-attachments/assets/2e4fd2e5-9dd6-4d3b-91c9-baf9815e96bf" />

<img width="1048" height="638" alt="image" src="https://github.com/user-attachments/assets/e74f969b-8d08-4b0d-b69a-28d27b1faafb" />

<img width="1119" height="256" alt="image" src="https://github.com/user-attachments/assets/91d33aeb-29ac-4327-ae71-c974724b7127" />

<img width="1486" height="485" alt="image" src="https://github.com/user-attachments/assets/e6a4d7f1-ef18-4243-b669-2c8f7b711631" />

## Вывод

В ходе лабораторной работы реализована seq2seq модель на базе GRU для задачи обращения последовательности. Ключевые нововведения: разделение на encoder и decoder, использование специальных токенов (PAD, SOS, EOS), сдвиг decoder_input относительно decoder_target, а также переход к категориальной функции потерь `sparse_categorical_crossentropy`. Метрика `exact_match` оказалась строже `token_accuracy`, так как требует полного совпадения всей сгенерированной последовательности. Модель успешно научилась восстанавливать обратный порядок токенов.

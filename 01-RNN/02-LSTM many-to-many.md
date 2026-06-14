# Отчет по лабораторной работе №2
## [LSTM для задачи many-to-many](https://github.com/Stepanova-Anna/edu-ai-math-essentials/blob/main/01-RNN/02_lstm_many_to_many_toy.ipynb)

---

## Цель работы

Построить LSTM-модель для классификации последовательностей в формате many-to-many: на каждом временном шаге выдается бинарный ответ (положительная или отрицательная кумулятивная сумма).

---

## Основные отличия от ЛР1

| Параметр | ЛР1 (many-to-one) | ЛР2 (many-to-many) |
|----------|-------------------|---------------------|
| Тип слоя | SimpleRNN | LSTM |
| return_sequences | False (по умолчанию) | **True** |
| Форма выходных меток y | (N,) | **(N, T, 1)** |
| Метрики | accuracy | token_accuracy + sequence_accuracy |

---

## Выполненные задания (TODO)

| TODO | Описание | Реализация |
|------|----------|------------|
| TODO 1 | Кумулятивная сумма по оси времени | `cumsum = np.cumsum(x[:, :, 0], axis=1)` |
| TODO 2 | Бинарные метки формы (N,T,1) | `y = (cumsum > 0).astype(np.float32).reshape(-1, seq_len, 1)` |
| TODO 3 | LSTM слой с return_sequences=True | `model.add(tf.keras.layers.LSTM(16, return_sequences=True))` |
| TODO 4 | Компиляция модели | `model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])` |
| TODO 5 | Обучение с валидацией | `model.fit(X_train, y_train, validation_split=0.2, batch_size=64, epochs=epochs)` |
| TODO 6 | Преобразование вероятностей в классы | `preds = (probs > 0.5).astype(int)` |
| TODO 7 | Вычисление sequence_accuracy | `seq_acc = (preds == y_test).all(axis=(1, 2)).mean()` |

---

# Скриншоты выполнения

<img width="959" height="848" alt="image" src="https://github.com/user-attachments/assets/b7d7a214-c820-4dfa-b261-46dffb5c1ea4" />

<img width="923" height="670" alt="image" src="https://github.com/user-attachments/assets/24c8a72a-fbd8-44de-a714-7e5c9083a57d" />

<img width="812" height="208" alt="image" src="https://github.com/user-attachments/assets/52952d73-f088-4653-a31c-0377e9bae6ae" />

<img width="920" height="848" alt="image" src="https://github.com/user-attachments/assets/68ede3b6-ffd2-4da9-abe6-0efa91118981" />

<img width="1016" height="668" alt="image" src="https://github.com/user-attachments/assets/c07471d6-8571-4f9a-84c2-89ded111fb1a" />

<img width="1007" height="450" alt="image" src="https://github.com/user-attachments/assets/5aa31774-9bea-46dd-bab5-45fad78e4b6c" />

<img width="1181" height="807" alt="image" src="https://github.com/user-attachments/assets/194687b9-006b-404e-b55f-74c440e94917" />

<img width="835" height="213" alt="image" src="https://github.com/user-attachments/assets/c772d0b7-ac9e-41e3-a1e9-a5a95f3341ff" />

<img width="1123" height="526" alt="image" src="https://github.com/user-attachments/assets/f0027a19-1d44-46d7-bb0a-14a2cc30394c" />

<img width="901" height="257" alt="image" src="https://github.com/user-attachments/assets/a356f098-9f18-4a2d-8e02-a159cdc357b8" />

<img width="1486" height="488" alt="image" src="https://github.com/user-attachments/assets/b85e7d75-5453-40a1-8f8c-edb4c1051237" />

# Вывод
В ходе лабораторной работы построена LSTM-модель для задачи `many-to-many`. Ключевое отличие от предыдущей работы — использование `return_sequences=True`, что позволило получать предсказания на каждом временном шаге. Метрика `sequence_accuracy` ожидаемо оказалась ниже `token_accuracy`, так как требует полного совпадения всех шагов последовательности. Модель успешно научилась определять знак кумулятивной суммы на каждом префиксе входной последовательности.

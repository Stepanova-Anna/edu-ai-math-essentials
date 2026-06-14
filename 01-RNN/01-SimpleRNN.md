# Отчет по лабораторной работе №1
## (SimpleRNN для задачи many-to-one)[https://github.com/Stepanova-Anna/edu-ai-math-essentials/blob/main/01-RNN/01_simple_rnn_many_to_one_toy.ipynb]

---

## Цель работы

Реализовать рекуррентную нейронную сеть (SimpleRNN) для задачи классификации последовательностей в формате many-to-one: на вход подается последовательность чисел, на выходе — один бинарный ответ (положительная или отрицательная сумма).

---

## Выполненные задания (TODO)

| TODO | Описание | Реализация |
|------|----------|------------|
| TODO 1 | Вычисление суммы по временной оси | `sums = x.sum(axis=1).reshape(-1)` |
| TODO 2 | Формирование бинарных меток | `y = (sums > 0).astype(np.float32)` |
| TODO 3 | Добавление слоя SimpleRNN | `model.add(tf.keras.layers.SimpleRNN(16))` |
| TODO 4 | Компиляция модели | `model.compile(optimizer='adam', loss='binary_crossentropy', metrics=['accuracy'])` |
| TODO 5 | Обучение модели | `history = model.fit(X_train, y_train, validation_split=0.2, batch_size=64, epochs=epochs)` |
| TODO 6 | Преобразование вероятностей в классы | `preds = (probs > 0.5).astype(int)` |

---

# Скриншоты выполнения
<img width="1620" height="690" alt="image" src="https://github.com/user-attachments/assets/b47ce593-8acb-461f-bdfc-5855a9b45b16" />

<img width="836" height="210" alt="image" src="https://github.com/user-attachments/assets/2471bf4f-c253-4943-b002-e4f48e6ea7f9" />


<img width="1617" height="820" alt="image" src="https://github.com/user-attachments/assets/08343cc0-aed8-4fb8-bb23-9053bba5d293" />

<img width="809" height="172" alt="image" src="https://github.com/user-attachments/assets/ced291ea-9a5d-43e2-b36f-a05a2ef6ea0b" />


<img width="1196" height="718" alt="image" src="https://github.com/user-attachments/assets/b72b9b8b-53d5-40c7-8854-c9693406ac5d" />

<img width="836" height="236" alt="image" src="https://github.com/user-attachments/assets/02cb4d65-20b1-453b-9a0b-b658ee16402d" />


<img width="961" height="507" alt="image" src="https://github.com/user-attachments/assets/f905eec3-34d6-4045-9ae9-debb64ea579b" />

<img width="955" height="261" alt="image" src="https://github.com/user-attachments/assets/4640e52c-3dad-4bb8-8aa9-08ecd338639a" />

# Вывод
В ходе лабораторной работы построена SimpleRNN-модель для задачи `many-to-one`. Модель успешно научилась определять знак суммы всей последовательности и выдавать один бинарный ответ на выходе. Достигнутая точность на тестовых данных превысила целевой порог в 90%, что подтверждает корректность реализации и понимание формата `many-to-one`.





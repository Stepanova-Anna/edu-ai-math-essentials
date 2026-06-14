# Отчет по лабораторной работе №2 (GPU-вариант)
## [Декодерный трансформер на Tiny Shakespeare (увеличенная модель)](https://github.com/Stepanova-Anna/edu-ai-math-essentials/blob/main/04-Autoregression/02_decoder_only_tiny_shakespeare_gpu.ipynb)

---

## Цель работы

Перенести авторегрессионную модель предсказания следующего токена на реальный текстовый корпус Tiny Shakespeare в режиме GPU-ускорения. Увеличить масштаб модели и добиться улучшения качества относительно CPU-варианта.

---

## Конфигурация GPU-варианта

| Параметр | CPU-вариант | GPU-вариант |
|----------|-------------|-------------|
| Размер корпуса | 250,000 символов | **900,000 символов** |
| Длина контекста | 64 | **128** |
| Размер эмбеддинга | 96 | **192** |
| Число голов внимания | 4 | **6** |
| Размер FFN | 192 | **384** |
| Бюджет обучения | 3 эпохи | **60 минут** |
| Размер батча | 64 | **128** |

---

# Скриншоты выполнения

<img width="1142" height="429" alt="image" src="https://github.com/user-attachments/assets/4d61a5f7-568f-4ecc-bc95-cdd90558de38" />

<img width="851" height="333" alt="image" src="https://github.com/user-attachments/assets/40b16c02-1e12-4d38-8599-784bfedfed40" />

<img width="892" height="697" alt="image" src="https://github.com/user-attachments/assets/1bcc282c-6172-4f14-b6ae-a63557b9388c" />

<img width="840" height="354" alt="image" src="https://github.com/user-attachments/assets/2a2f821b-6acc-486b-9930-412a216ccd04" />

<img width="1390" height="667" alt="image" src="https://github.com/user-attachments/assets/1a7d5a1b-c7c9-4c8a-8b50-ee99098623a7" />

<img width="448" height="167" alt="image" src="https://github.com/user-attachments/assets/2c7db38e-785c-4a70-bfdc-a9ee57a1e896" />

<img width="386" height="80" alt="image" src="https://github.com/user-attachments/assets/402705c9-1649-4d02-aa06-68ce7ea5486c" />

<img width="520" height="103" alt="image" src="https://github.com/user-attachments/assets/86404179-be92-4cf1-a136-d66949f28cbd" />

<img width="937" height="790" alt="image" src="https://github.com/user-attachments/assets/8c187118-bc1b-4635-bf0a-9f529cc1f531" />

# Вывод

В ходе лабораторной работы реализован масштабированный декодерный трансформер для символьной генерации текста на корпусе Tiny Shakespeare с использованием GPU-ускорения. Ключевые результаты:

1. **Масштабирование** — модель успешно обучена на увеличенном корпусе (900K символов) с большим контекстом (128 токенов).
2. **Качество** — модель превосходит частотный baseline по перплексии и демонстрирует высокое качество генерации (19/20 успешных продолжений).
3. **Причинная маска** — диагностика подтвердила отсутствие утечки будущей информации (future_ratio < 1e-4).
4. **Teacher forcing** — контролируемое продолжение показало значительное улучшение по сравнению с CPU-вариантом.


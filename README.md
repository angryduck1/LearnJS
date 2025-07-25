# Рукописный классификатор с ИИ на JS

## О проекте

Этот проект — простой пример системы классификации рукописных рисунков на JavaScript, использующей *перцептрон* с двумя скрытыми слоями. Пользователь рисует на холсте, и модель определяет, относится ли рисунок к категории GOOD или BAD (например, “хороший” или “плохой” символ).

## Использование

- **Рисование:** используйте мышь, чтобы рисовать на канвасе.
- **Добавление примеров:**
  - Нарисуйте пример нужной категории.
  - Нажмите `P` для переключения статуса между GOOD и BAD (текущее состояние переменной goodStatus).
  - Нажмите `V` для добавления текущего рисунка в выбранную категорию (GOOD или BAD).
- **Обучение:** когда есть хотя бы один пример GOOD и BAD, нажмите `T`. Модель обучится на ваших примерах (5000 эпох, со снижением learningWeight).
- **Классификация:** чтобы классифицировать новый рисунок, нажмите `R`. В зависимости от вывода нейросети отобразится сообщение “I think what you draw GOOD” или “I think what you draw BAD”.
- **Переобучение:** для проверки корректности ответа нейросети, нажмите `F`. Если нейросеть ответила не верно, она переобучится.
- **Сброс:** после добавления примера или классификации холст очищается автоматически. Можно также вручную очистить массив — для этого используйте соответствующий код.

## Кратко о реализации

- *Входные данные* — 28×28 пикселей (784 элемента), каждый пиксель либо 0, либо 1 (закрашен).
- Модель: полностью связная нейронная сеть с архитектурой `[784 → 128 → 64 → 2]`, функция активации — сигмоида.
- Слои:
  - **Вход**: 784
  - **Скрытый 1**: 128
  - **Скрытый 2**: 64
  - **Выход**: 2 (GOOD, BAD)
- **Обучение** реализовано методом обратного распространения ошибки (backpropagation).
- Обработка взаимодействий с мышью и клавиатурой через стандартные события DOM.

## Горячие клавиши

| Клавиша | Назначение                     |
|---------|--------------------------------|
| P       | Переключить GOOD/BAD           |
| V       | Добавить пример текущей категории |
| T       | Обучить сеть                   |
| R       | Классифицировать рисунок       |
| F       | Проверить ответ нейросети      |
| X       | Очистить холст                 |

# Chirp: Sound-based Data Transfer

This application allows you to transmit and receive data through sound. It uses a simple encoding scheme to convert text into audio frequencies, which can be played through your speakers and picked up by a microphone.

## Features

- Real-time frequency visualization of audio input
- Send messages by converting text to sound
- Receive messages by listening to sound and decoding it back to text
- Distinctive start and end signatures to mark transmissions

## How It Works

1. **Text Encoding**: Each character is mapped to a unique frequency
2. **Transmission**: The app plays a start signature, followed by the encoded text, and ends with an end signature
3. **Reception**: The app listens for frequencies, looks for the start signature, decodes the frequencies back to text, and stops at the end signature
4. **Visualization**: Real-time visualization of the frequency spectrum lets you see the data being transmitted and received

## Getting Started

### Prerequisites

- Node.js (version 14 or higher)
- npm or yarn


### Installation

#### Clone this repository  

First—assuming you have the GitHub CLI—use this command while in your end directory:

   ```bash
   gh repo clone solst-ice/chirp
   ```

Otherwise use this command while in your end directory:

   ```bash
   git clone https://github.com/solst-ice/chirp.git
   ```

#### Install dependencies

   ```bash
   npm install
   ```

   **or**

   ```bash
   yarn
   ```

### Running the Application

```bash
npm run dev
```
**or**
```bash
yarn dev
```

Then open your browser to the URL shown in the terminal (usually http://localhost:5173).

## Usage

1. Click "Start Listening" to begin capturing audio
2. Type a message in the text box at the bottom
3. Click "Transmit Message" to send the message as sound
4. The message will be played through your speakers and should be picked up by your microphone if it's enabled
5. Received messages will appear in the "Received Messages" section

## Notes

- Best results are achieved in a quiet environment
- You may need to adjust your microphone and speaker settings
- Browser security may require you to explicitly grant permission to use the microphone
- This is a proof of concept with a simplified encoding scheme

## Technologies Used

- React
- TypeScript
- Vite
- Web Audio API

16.03.26 Sync forc

Ось результати аналізу та стратегія трансформації для проекту **Chirp**, підготовлені у форматі для копіювання в Notion.

---

# 📑 Звіт AI-консультанта: Проект "Chirp"

**Chirp** — це інноваційний інструмент для передачі даних за допомогою звукових хвиль, що використовує веб-технології для перетворення тексту в унікальні аудіочастоти та навпаки.

---

## 🧬 Частина 1: "ДНК" Проекту

Логіку коду проекту **Chirp** можна розбити на такі **атомарні функції**:

*   **Кодування тексту (Text Encoding):** Кожен символ тексту зіставляється з унікальною звуковою частотою за спрощеною схемою кодування.
*   **Управління сигнатурами (Signaling):** Додавання чітких сигнатур початку та завершення передачі ("start and end signatures") для синхронізації пристроїв.
*   **Аудіо-синтез (Transmission):** Генерація та відтворення звукових тонів через Web Audio API на основі закодованих частот.
*   **Захоплення та обробка сигналу (Reception):** Прослуховування навколишнього середовища через мікрофон та виявлення частот-маркерів.
*   **Декодування частот (Frequency Decoding):** Зворотне перетворення виявлених звукових сигналів у текстові символи.
*   **Спектральна візуалізація (Visualization):** Візуалізація частотного спектру в реальному часі для моніторингу процесу передачі.

### 💎 Головна технічна цінність
Головна цінність проекту полягає у створенні **"повітряного мосту" (air-gapped communication)** для передачі даних без використання традиційних мереж (Wi-Fi, Bluetooth чи стільникового зв'язку). Завдяки використанню **Web Audio API**, проект працює безпосередньо в браузері, не потребуючи встановлення додаткового ПЗ, що робить його універсальним для будь-яких пристроїв з динаміками та мікрофоном.

---

## 🚀 Частина 2: "Трансформація" (Інтеграція з Gemini LLM)

Додавання мультимодальної моделі **Gemini** (через **GitHub Models**) перетворює Chirp з простої утиліти передачі тексту на **акустичний інтелектуальний шлюз**.

### Як зміниться функціонал?
1.  **Семантичне стиснення даних:** Замість передачі сирого тексту, Gemini може стискати складні інструкції в короткі тональні коди, які розкодовуються на іншому кінці назад у повні команди.
2.  **Акустичне керування ШІ-агентами:** Можливість "надиктувати" команду ШІ-системам через нечутні для людини ультразвукові частоти.
3.  **Інтелектуальна фільтрація шуму:** Використання ШІ для відокремлення корисного сигналу Chirp від фонового шуму в складних акустичних умовах.

### Сценарій сервісу "Offline AI Bridge" (Chirp + Gemini + ваші ID_{$})

Сценарій створення сервісу для керування пристроями в ізольованому середовищі:
1.  **Формування запиту (ID_{$1}):** Ваш Python-скрипт **ID_{$1}** генерує технічне завдання для локального сервера.
2.  **Обробка (Gemini):** Gemini аналізує завдання та перетворює його на максимально стислий JSON-промпт.
3.  **Передача (Chirp):** Проект Chirp кодує цей промпт у звук і транслює його.
4.  **Прийом та дія (ID_{$2}):** Приймаючий пристрій (наприклад, Raspberry Pi) через мікрофон декодує звук. Python-скрипт **ID_{$2}** отримує текст, розгортає його через локальну копію Gemini та виконує команду (наприклад, відкриває замок або вмикає світло).
5.  **Деплой (GitHub Spark):** Ви розгортаєте інтерфейс керування як інтелектуальний застосунок через **GitHub Spark**, що дозволяє миттєво оновлювати логіку взаємодії.

---

## 📋 План дій для Notion
| Крок | Дія | Результат |
| :--- | :--- | :--- |
| **1** | Встановлення залежностей: `npm install` | Підготовка React/TS середовища |
| **2** | Запуск: `npm run dev` | Активація Web Audio API інтерфейсу |
| **3** | Підключення Gemini через **MCP Registry** | Можливість генерації звукових команд через ШІ |
| **4** | Зв'язування з вашими скриптами `ID_{$}` | Автономний канал передачі даних |

---

### 💡 Резюме

**Суть:** **Передача даних через звукові частоти**.

**AI-Роль:** **Створення інтелектуальних застосунків через Spark**.

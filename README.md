# ⏳ Vue 3 + Vite + Tailwind CSS + Pinia Time Tracker

A simple time-tracking application built with **Vue 3**, **Vite**, **Tailwind CSS**, and **Pinia**. This app allows you to start, pause, resume, and stop tasks with automatic time logging stored in your browser's local storage — no backend required.

## 🖼️ Features

- ✅ Start/Pause/Resume/Stop task timers
- 📦 Task data is stored locally using `localStorage`
- 📊 Total time and task statistics
- 🔄 Auto-updating UI using Vue's reactivity
- 🎨 Styled with modern Tailwind CSS utility classes
- 🧠 Built using Composition API and Pinia for state management

## 🧱 Project Structure

```
src/
├── components/
│   └── Timer.vue        # Timer component with controls and display
├── store/
│   └── timeStore.js     # Pinia store managing tasks and timers
├── App.vue              # Root component listing tasks
├── main.js              # App entry point
└── assets/
    └── main.css         # Tailwind CSS
```

## 🚀 Getting Started

### Prerequisites

- Node.js (v16+ recommended)
- npm or yarn

### Install dependencies

```bash
npm install
# or
yarn install
```

### Run the app locally

```bash
npm run dev
# or
yarn dev
```

The app will be available at `http://localhost:5173` (or your Vite port).

## 🧪 Usage

1. Enter a task name and click **Start**
2. Use **Pause/Resume** to manage the timer
3. Click **Stop** to complete the task and log it
4. View task history and total time stats
5. Click **Clear All Tasks** to reset the tracker

## 📁 Local Storage

Tasks are stored under the key: `tasks`. Each task object contains:

```js
{
  name: String,
  startTime: Number,
  duration: Number, // in seconds
  endTime: Number | null,
  status: 'in-progress' | 'paused' | 'completed'
}
```

## 🛠️ Built With

- [Vue 3](https://vuejs.org/)
- [Pinia](https://pinia.vuejs.org/)
- [Tailwind CSS](https://tailwindcss.com/)
- [Vite](https://vitejs.dev/) (for development)

## 📃 License

This project is open-source and available under the [MIT License](LICENSE).

---

### 👨‍💻 Author

Built with ❤️ by Arjun V D  
[GitHub](https://github.com/ArjunvDevaraj) • [LinkedIn](https://www.linkedin.com/in/arjunvdevaraj)
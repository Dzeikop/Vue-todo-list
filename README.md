# Vue Todo

Prosta lista zadań w Vue 3 — dodawanie, usuwanie, oznaczanie jako zrobione, zapis w `localStorage`.

## Stack

- Vue 3 (`script setup`)
- Vite
- localStorage

## Funkcje

- dodawanie zadania
- usuwanie
- przełączanie statusu „zrobione”
- przekreślenie ukończonych
- persystencja po odświeżeniu strony (`localStorage` + `watch` / `onMounted`)

## Uruchomienie

```bash
npm install
npm run dev
```

Otwórz adres z terminala Vite (zwykle `http://localhost:5173`).

## Czego się nauczyłem

- `ref` i `.value` w Composition API
- `v-model`, `v-for`, `:class`, `@click`
- niemutacyjne aktualizacje tablic (`map` / `filter` / spread)
- `onMounted` + `watch` (w tym `{ deep: true }`) z localStorage

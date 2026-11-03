# Copilot instructions

## Project shape

- This is a standalone browser quiz. The interface, styles, quiz data, and interaction logic all live in the root `index.html`; there is no framework, module bundler, server, or external runtime dependency.
- The HTML contains three screen sections (welcome, quiz, results). The script switches between them and updates quiz state in place rather than navigating to other pages.
- Quiz content is the `questions` array. `renderQuestion()` builds answer buttons from each item, `selectAnswer()` handles scoring and feedback, and `showResults()` chooses the final message from the score. Keep question count and progress calculations tied to `questions.length`.

## Commands and verification

- There are no configured build, test, or lint commands or single-test runner in this repository.
- To run the app, open `index.html` directly in a browser (`file://`); it requires no server.
- For a browser smoke check, start and restart the quiz, answer all 10 questions with both correct and incorrect choices, and confirm the progress, score, feedback, and results update.

## Codebase conventions

- Keep changes self-contained in `index.html` unless the project is deliberately expanded. CSS is inline in `<style>` and JavaScript is inline in `<script>`.
- Use the existing screen/state flow: `currentQuestion`, `score`, and `hasAnswered` drive the quiz; dynamically created answer buttons use event listeners, and the `hasAnswered` guard prevents duplicate scoring.
- Preserve the existing accessibility patterns: semantic buttons, visible keyboard focus, live status announcements, labeled progress, focus movement between screens/questions, responsive layout, and reduced-motion handling.
- Keep quiz copy and per-question explanations in the question objects. Render user-facing question and answer text with `textContent` rather than interpolating it into HTML.

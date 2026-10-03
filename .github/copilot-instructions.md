# Copilot instructions

## Project shape

This is a no-build, no-dependency space quiz. The complete application is in the root `index.html`: semantic screen markup, CSS/theme tokens and animations, inline SVG hero artwork, and a plain JavaScript quiz state machine. Keep changes self-contained there unless the project gains a concrete need for additional files or tooling.

The page moves between three sections (`#intro`, `#quiz`, and `#results`) by toggling `.hidden`. The `questions` array is the source of truth for question text, answer choices, zero-based correct-answer indexes, categories, and feedback facts. `renderQuestion()` builds each question's controls; `chooseAnswer()` locks an answer, updates the score, and presents feedback; `finishQuiz()` derives the results reaction from the final score. Keep these responsibilities and the displayed progress/score in sync when changing quiz behavior.

## Build, test, and lint

There are no package manifest, build, test, or lint commands. No server or dependency installation is required: open `index.html` directly in a browser. For a focused manual smoke test, start the quiz, choose one correct answer and one incorrect answer, verify score and feedback, then complete the remaining questions and verify the results screen. The integrated browser can open the local file URL.

## Project conventions

- Keep presentation and functionality dependency-free. CSS, JavaScript, and the rocket illustration are inline; do not introduce a framework, remote asset, or server requirement for a UI change.
- Use the existing CSS custom properties for surfaces, text, accents, and feedback colors. Define light-mode defaults in `:root` and their dark-mode counterparts in `@media (prefers-color-scheme: dark)` so the two themes remain coordinated.
- Motion is part of the visual design, but honor `prefers-reduced-motion`; keep decorative artwork hidden from assistive technology and preserve visible keyboard focus.
- Use native buttons for answer and navigation actions. Preserve focus handoff as screens/questions change, and keep score, progress, and feedback exposed as readable text or appropriate ARIA status/progress semantics.
- Keep question-specific content in the `questions` array rather than embedding it in screen markup. Correct-answer values are zero-based indexes into each question's `answers`.

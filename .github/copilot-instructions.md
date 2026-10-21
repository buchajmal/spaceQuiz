# Copilot instructions

## Project shape

This is a dependency-free, single-page quiz. `index.html` contains all markup, theme styling, question data, and browser-side behavior; there is no framework, build pipeline, or server-side code. The question bank drives the quiz state (`current`, `score`, and `answered`): `renderQuestion()` updates the current view, `chooseAnswer()` handles and locks in an answer, `showResults()` replaces the quiz view at completion, and `restart()` restores the initial view.

## Build, test, and lint

There are no build, test, or lint commands configured. Open `index.html` directly in a browser to run the app; no server or dependency installation is needed. For browser-level checks, verify answer selection and feedback, score changes only for correct answers, progress through all ten questions, results and replay, keyboard focus, both system color schemes, and a narrow mobile viewport without horizontal overflow.

## Project-specific conventions

- Keep this app self-contained in `index.html`; it is intended to work from a local `file://` URL without external assets or packages.
- Treat each question's `answer` as a zero-based index into its `options` array. Keep the question count, progress display, and result scoring derived from the `questions` array rather than hard-coding a separate quiz length.
- The initial quiz markup and the template in `restart()` must stay in sync. Both `showResults()` and `restart()` replace `#quiz-content` with `innerHTML`; call `cacheElements()` after restoring the quiz markup so rendering uses the current DOM nodes.
- Use the CSS custom properties in `:root` and `@media (prefers-color-scheme: light)` for theme-sensitive colors. Keep interactive states legible in both schemes.
- Preserve the semantic buttons, heading association, progressbar values, live announcements, visible keyboard focus, and `prefers-reduced-motion` handling when changing UI behavior or styling.
- Keep the centered column usable on small screens: the page supports viewports down to 320px, and answer/primary action targets should retain their existing comfortable sizing.

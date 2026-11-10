# Repository instructions

## Project shape and architecture

This repository is a single-page space quiz implemented entirely in `index.html`. The document contains the markup, CSS, quiz data, and JavaScript; there is no framework, package manager, server, or build step. Open the file directly in a browser to run it.

The quiz's `questions` array is the source of truth for question text, answer options, the zero-based `correct` answer index, and feedback facts. `renderQuestion()` builds the answer buttons from that data; `selectAnswer()` handles scoring, feedback, and progress; `showResults()` and `restartQuiz()` manage the end and restart states.

Presentation is also self-contained. CSS custom properties define the shared palette and theme colors, with system-preference defaults and explicit light/dark overrides. The theme button sets `data-theme` on the root element. Keep decorative effects separate from content and controls, and preserve the narrow responsive quiz layout.

## Build, test, and lint

- **Run:** Open `index.html` directly in a browser. No server or build tool is required.
- **Automated tests / single-test command:** None are configured in this repository.
- **Lint:** No linter or lint command is configured.
- **Manual smoke check:** Open `index.html`, answer a question correctly and incorrectly, check that score and progress update once per answer, complete the quiz, restart it, and toggle both themes. Check a narrow viewport and keyboard focus on the answer and theme buttons when changing UI behavior.

## Codebase conventions

- Keep the app dependency-free and self-contained in `index.html` unless the project is deliberately expanded.
- Add or edit quiz content in the `questions` array. `correct` is a zero-based index into that question's `answers`; keep the question, answers, correct index, and fact together.
- Keep quiz state transitions in the existing functions (`renderQuestion`, `selectAnswer`, `showResults`, and `restartQuiz`) so score, progress, and feedback remain synchronized.
- Keep the implementation straightforward to follow: use the question data and named DOM/state functions as the main structure; avoid compressed logic or extra abstraction for one-off behavior.
- Use the existing CSS variables for colors so new UI follows both themes. The system preference selects the initial appearance; `data-theme="light"` and `data-theme="dark"` provide explicit overrides.
- Preserve the existing accessibility patterns: semantic buttons, visible keyboard focus, a labeled progress bar, live score and feedback announcements, hidden decorative elements, and reduced-motion support.
- Keep decorative background layers non-interactive and behind the quiz content; do not reduce text or control contrast to achieve visual effects.

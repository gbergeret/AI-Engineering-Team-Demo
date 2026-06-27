# 000 - Welcome wizard

A short, friendly first-run interview, tailored for an engineering team. The goal:
learn the basics about you and what you're building, then save them so the team
remembers from now on. It runs once: when it finishes, it
saves your answers and cleans up after itself (removing the wizard and its first-run
hook) in a single pull request.

## When to run
On the first session, if `context/PROFILE.md` still shows the placeholder name
("(not set yet)"). Once onboarding is done, this file is gone and it never runs
again.

## How to run
Ask one question at a time. Keep it warm and brief, and accept whatever the person
gives (there are no wrong answers). They can skip any question. When you are done,
write the answers to the files and show what you saved.

### Questions (keep it to these, do not add more)
1. **What should I call you?**
   Save to `context/PROFILE.md` (Name).
2. **What are you building?** One line about your product, project, or domain.
   Save to `context/PROFILE.md` (What you're building).
3. **Which languages should the engineers specialise in?** Backend and frontend
   (for example: "Python backend, TypeScript / React frontend").
   Save to `context/PROFILE.md` (Stack), and use to build up the standards (below).
4. **Do you work test-first (TDD)?** Strict TDD, tests alongside code, or light.
   Use to tune `standards/TESTING-STRATEGY.md` (below).
5. **What language should I reply in?**
   Save to `context/PROFILE.md` (Language).

## After the interview
- Write each answer into the right place in `context/PROFILE.md`, replacing the
  placeholders. Keep it tidy.
- **Build up the standards** from the language and TDD answers. The repo ships
  Python (`standards/BACKEND-STANDARDS.md`) and TypeScript
  (`standards/FRONTEND-STANDARDS.md`) defaults: keep each if it matches the chosen
  language, otherwise rewrite it for that language, same structure. Tune
  `standards/TESTING-STRATEGY.md` to match how strict the TDD answer was (test-first
  by default; soften to "tests alongside code" if they are not strict).
- Delete this playbook (`playbooks/000-welcome-wizard.md`): one-time setup, not
  needed once it has run.
- Clean up `CLAUDE.md`: remove the "## First run: the welcome wizard" section, so
  nothing points at the deleted playbook.
- Open a pull request with all of these changes together (the filled-in profile,
  the tailored standards, the removed wizard, and the cleaned-up `CLAUDE.md`). The
  PR is the record of your onboarding.
- Confirm in one line: "I have opened a PR with your details, set up your standards,
  and removed the setup wizard. Review and merge it and you are set. You can change
  any of this any time."

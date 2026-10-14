# Generative AI Disclosure

Using AI tools for this challenge is allowed. Be honest here — an accurate
"I used AI heavily" is worth more to us than an inaccurate "I did not".

**Did you use AI tools?** (yes / no):
yes

**Which ones?** (e.g. ChatGPT, Claude, Copilot, Cursor):
Gemini

> If you answered **no**, write "N/A" in sections 1 and 2 and skip to
> section 3. That is a perfectly good answer.

---

## 1. Key prompts

List the main prompts you used. Paraphrasing is fine.

1. `Why does the proxy Dockerfile fail to build and what is the issue with apt-get and COPY?`
2. `Why can't the proxy reach the backend container using 127.0.0.1 in Docker Compose?`
3. `Explain why the test-runner failed in app.py and what CONFIG_FETCH_SECONDS does.`
4. `What does 'line 1: ./scripts/run-tests.sh: Permission denied' and exit code 126 mean in CI?`

---

## 2. Where the AI got it wrong

Describe **one concrete case** where the AI's answer was wrong, outdated, or
sub-optimal. Cover: what it suggested, how you noticed it was wrong, and what
you did instead. 3–5 sentences.

> For Defect 3, the AI initially suggested a heavy solution adding full healthchecks and polling logic inside docker-compose.yml. I noticed this was unnecessary because the real issue was just an artificial delay inside backend/app.py. Instead of adding complex configuration, I added the line `CONFIG_FETCH_SECONDS=0` directly in docker-compose.yml, which solved the delay in one line.

---

## 3. Anything in your submission you could not fully explain?

We would rather know. Write "nothing" if that is the case.

> I don't have deep experience with Linux and Git yet. For example, in task 4, I know that adding "chmod +x" gave the file execution permissions, but I don't know why it was saved without those permissions in the first place.

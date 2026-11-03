# Lab 06 project rules

- `REQUIREMENTS.md` is the source of truth for the acceptance criteria. Keep it and the supplied `fees.py` unchanged: this lab evaluates the teammate's code rather than fixing it.
- Tests use Python's standard-library `unittest`, live in `tests/`, and import the function with `from fees import late_fee`.
- Run tests from `lab06/` with `python3 -m unittest discover -s tests`.
- Use only the standard library. Test only supported inputs: whole numbers of minutes, zero or more.
- Use separate custom-agent sessions for the independent checks. In the tester permission profile, spawn the `tester` custom agent; in the reviewer permission profile, spawn the `reviewer` custom agent. Do not pass the implementation or reviewer findings to the tester, or the tests/results to the reviewer.
- Keep each persona's starting permissions. Never request or use an unsandboxed command or broader permissions to complete its work.
- Tester: read `REQUIREMENTS.md` and write `tests/test_fees.py`; do not read the implementation and do not run tests. Stop once the test file exists.
- Reviewer: read `REQUIREMENTS.md` and `fees.py`; change nothing. Return only criterion violations with an input, actual fee and required fee, then stop.
- Record observed results honestly. A failing test is evidence; do not change it to match incorrect code. Do not commit session files or `tests/check.txt`.

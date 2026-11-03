# 📄 ATS Resume Checker

A Streamlit app that reads your resume (PDF or DOCX) and uses Google Gemini to give you:

- an estimated **ATS score** (0-100)
- an optional **job match score** if you paste a job description
- a breakdown: keywords, formatting, impact, readability, completeness
- strengths, weaknesses and **missing keywords**
- specific **improvement suggestions** and example bullet rewrites
- quick rule-based checks (email, phone, LinkedIn, sections, bullets, measurable results)
- a downloadable Markdown report

> The score is an AI estimate, not the output of a real ATS. Use it as guidance.

## Tech stack

Python, Streamlit, Google Gemini API (Google AI Studio key), pypdf, python-docx.

## Project structure

```
ats-resume-checker/
├── app.py
├── requirements.txt
└── README.md
```

## Run locally

1. Install Python 3.10 or newer.
2. Open a terminal in the project folder and create a virtual environment:
   ```bash
   python -m venv venv
   venv\Scripts\activate          # Mac/Linux: source venv/bin/activate
   pip install -r requirements.txt
   ```
3. Get a free API key from [Google AI Studio](https://aistudio.google.com/apikey).
4. Either paste the key into the app sidebar, or create `.streamlit/secrets.toml`:
   ```toml
   GOOGLE_API_KEY = "your-key-here"
   ```
5. Start the app:
   ```bash
   streamlit run app.py
   ```

## Push to GitHub using the website (no Git commands)

1. Sign in at [github.com](https://github.com).
2. Click the **+** icon (top right) → **New repository**.
3. Enter the name `ats-resume-checker`, choose **Public**, then click **Create repository**.
   (Streamlit's free hosting works best with a public repo.)
4. On the new repo page, click **uploading an existing file**
   (or **Add file → Upload files**).
5. Drag and drop `app.py`, `requirements.txt` and `README.md` into the page.
6. Scroll down, write a message like `Add ATS resume checker`, and click **Commit changes**.
7. Refresh the page. You should see all three files.

**Important:** never upload your API key or a `secrets.toml` file. You will add the key
inside Streamlit instead (see below).

To update the app later: open a file on GitHub → click the pencil icon → edit → **Commit changes**.
Streamlit redeploys automatically.

## Deploy on Streamlit Community Cloud

1. Go to [share.streamlit.io](https://share.streamlit.io) and click **Continue with GitHub**.
   Authorize Streamlit to access your repositories.
2. Click **Create app** → **Deploy a public app from GitHub**.
3. Fill in:
   - **Repository:** `your-username/ats-resume-checker`
   - **Branch:** `main`
   - **Main file path:** `app.py`
4. Click **Advanced settings**:
   - choose Python 3.11 or 3.12
   - in **Secrets**, paste:
     ```toml
     GOOGLE_API_KEY = "your-key-here"
     ```
   - click **Save**
5. Click **Deploy**. The first build takes a few minutes.
6. When it finishes you get a public link like `https://your-app-name.streamlit.app`.
   Add it to your GitHub repo description and your portfolio.

To change the key later: open your app on Streamlit → **Manage app** → **Settings → Secrets**.

## Troubleshooting

| Problem | Fix |
|---|---|
| "Very little text was found" | Your PDF is probably a scanned image. Export it as a text-based PDF or use DOCX. |
| "The analysis failed" | Check the API key, and check the model name in the sidebar against Google AI Studio. |
| Quota or rate-limit error | Free keys have limits. Wait a minute and retry. |
| Build fails on Streamlit | Make sure `requirements.txt` is in the repo root and spelled correctly. |

## Privacy

The resume text is sent to the Gemini API for analysis. The app does not save your file or text.

## Ideas for improvement

- Compare two resume versions side by side
- Export the report as PDF
- Generate a tailored cover letter from the resume and job description

## License

MIT

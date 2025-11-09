# KlassRoom — A companion for student life

**KlassRoom** helps students turn lecture audio into actionable study aids:
- **Transcript generation** from uploaded audio
- **Keyword/entity extraction** using Google Cloud Natural Language
- Curated **YouTube video suggestions** based on extracted topics
- Optional **email delivery** of the transcript, topics, and links

The app is a simple **Flask** web application with classic HTML/CSS/JS templates.

### Features
- Speech-to-text from WAV audio uploads using `SpeechRecognition`
- Entity extraction via `google-cloud-language`
- YouTube suggestions scraped from search results
- Email summaries via Gmail SMTP (optional)

### Project structure
- `app.py`: Flask app, routes, and server bootstrap
- `GoogleNLPAPI.py`: Google Cloud Language client and entity extraction
- `emailAnalysis.py`: Email composer/sender (SMTP)
- `emailer.py`: Minimal email sender (not used by default routes)
- `getYoutubeVideoLinks.py`: YouTube search scraping to build embed links
- `templates/`: HTML templates
- `static/`: CSS, JS, and assets

### Prerequisites
- Python 3.10+ (macOS recommended; tested locally)
- A Google Cloud project with the Natural Language API enabled
- A service account key JSON file downloaded from Google Cloud Console
  - Save the key file as `googleNLPAPIcodes.json` in the project root
  - The app sets `GOOGLE_APPLICATION_CREDENTIALS` to this filename at runtime
- Optional: Gmail account with an App Password (for email sending)
  - If you plan to use email, configure the sender and password before sending

### Quickstart
1) Create and activate a virtual environment
```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
```

2) Install dependencies
```bash
pip install Flask google-cloud-language SpeechRecognition
```

3) Put your Google Cloud key in place
- Copy your service account JSON into the project root as:
  - `googleNLPAPIcodes.json`

4) Run the app
```bash
python app.py
```
Then open `http://127.0.0.1:5000/`

### Email sending (optional)
The route that emails summaries uses Gmail SMTP. Before using it in production:
- In `emailAnalysis.py`, the SMTP sender email must be a valid Gmail address
- Use a Gmail App Password for the SMTP login
- Some routes in `app.py` currently pass placeholder credentials for demo purposes; you should wire your own secure values before using email in a real environment

### Notes and tips
- Audio uploads should be WAV/PCM for best results with `SpeechRecognition`
- If you see certificate/SSL issues on macOS when scraping YouTube, run Apple’s “Install Certificates.command” bundled with your Python or install certificates via Homebrew
- If you get Google credentials errors at runtime, ensure `googleNLPAPIcodes.json` exists in the project root and is a valid service account key with access to the Natural Language API
- YouTube search scraping is best-effort and may change if YouTube alters its markup

### Troubleshooting
- Google Cloud auth error:
  - Ensure `googleNLPAPIcodes.json` exists at the project root and is a valid key
- Flask server starts but analysis fails:
  - Confirm you installed: `Flask google-cloud-language SpeechRecognition`
- SSL / certificate errors on macOS:
  - Install/update system certificates or run the Python “Install Certificates.command”
- Email fails to send:
  - Use a Gmail App Password and correct sender/recipient addresses

### License
This project is provided as-is for educational purposes.

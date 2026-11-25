SkillSphere
SkillSphere is a web-based recruitment and assessment platform. It gives candidates a place to look for jobs and complete technical assessments, while recruiters can post openings and manage the questions used in those assessments.

Live project: https://skillsphere-i6hm.onrender.com/
What the project does
For candidates
- Create an account and log in.
- View available jobs and apply.
- Upload a resume.
- Take technical MCQ assessments.
- Complete assessments with the configured proctoring and recording features.
- Check application and assessment progress.
For recruiters
- Log in to a recruiter account.
- Add job openings and update existing ones.
- Close job postings when they are no longer available.
- Add and manage questions for a job's technical assessment.
- Review applications and assessment results.
Built with
- Backend: Python, FastAPI
- Frontend: HTML, CSS, JavaScript
- Database: SQLite
- Other tools: Docker, Cloudinary (optional), SMTP (optional)
PDF handling and OCR are also used for document-related features.
Folder structure
skillsphere-/
├── backend/
│   ├── main.py
│   └── tests/
│       └── test_api.py
├── frontend/
│   ├── index.html
│   ├── app.js
│   ├── styles.css
│   └── vendor/
├── .env.example
├── Dockerfile
├── docker-compose.yml
├── render.yaml
└── requirements.txt
Run the project locally
Requirements
- Python 3.11 or newer
- pip
- Git
If you want to use the PDF OCR features, install Tesseract OCR as well.
1. Clone the repository
git clone https://github.com/aditigoyal779/skillsphere-.git
cd skillsphere-
2. Create a virtual environment
Windows:
py -3.11 -m venv .venv
.\.venv\Scripts\Activate.ps1
macOS / Linux:
python3 -m venv .venv
source .venv/bin/activate
3. Install the packages
pip install -r requirements.txt
4. Set up environment variables
Copy .env.example and rename the copy to .env.

Windows PowerShell:
Copy-Item .env.example .env
macOS / Linux:
cp .env.example .env
Open .env and add the values needed for your setup. Keep this file private; do not upload passwords, API keys, or other secrets to GitHub.

For production, set a strong, unique value for SKILLSPHERE_SECRET_KEY. Cloudinary and SMTP details are only needed if you are using those services.
5. Start the server
Run this command from the project folder:
uvicorn backend.main:app --reload
Then open http://127.0.0.1:8000 in your browser.

You can check whether the server is running at http://127.0.0.1:8000/health.
Run with Docker
If Docker is installed, you can start the application with:
docker compose up --build
Then visit http://localhost:8000.
Run the tests
From the main project folder, run:
python -m unittest discover -s backend/tests -p "test_*.py"
Deployment
The repository includes a Dockerfile and a render.yaml file for deployment on Render. The Render setup uses a persistent disk for the SQLite database and application data.

Before deploying, set the production environment variables in Render. In particular, use a strong SKILLSPHERE_SECRET_KEY and set SKILLSPHERE_PUBLIC_BASE_URL to the public URL of the deployed app.

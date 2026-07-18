# FUTURE_ML_03 - AI Candidate Screening & Ranking Engine

This is my submission for Task 3 of the Future Interns Machine Learning track. I built an automated resume screening system in Python designed to act like an AI assistant for HR-tech startups and technical recruiters. Instead of reading through applications manually, this engine evaluates an applicant pool against a target job posting, ranks candidates by relevance, and performs a skill gap analysis automatically.

### How the scoring and ranking works
Most basic applicant tracking systems just count keywords, which makes them easy to cheat. For this project, I used a semantic similarity approach:
* **The Math:** I used Scikit-Learn's `TfidfVectorizer` (with two-word N-gram phrasing and English stopwords removed) to convert the text of both the job description and the candidate resumes into mathematical vectors.
* **The Scoring:** I calculated the Cosine Similarity between the target job posting vector and each candidate's resume vector. This measures the multi-dimensional alignment between the documents, ensuring candidates who actually share the right technical context score higher than someone just spamming buzzwords.
* **Why Candidates Rank Higher:** In my test run using a Software/Data Engineering job posting from a Monster.com dataset, experienced Full-Stack and Data AI candidates immediately shot to the top of the leaderboard, while non-technical candidates naturally ranked at the bottom.

### Skill Gap Analysis
A key feature I built into this engine is automated gap identification. The script checks each applicant against a core set of tech competencies (like Python, SQL, AWS, Java, and Machine Learning). If an HR manager is looking at a promising junior developer who ranked a bit lower, the output table explicitly lists exactly which core skills that candidate is missing so the team can decide if they are worth interviewing and upskilling.

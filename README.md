# Recommendation-System-Simulator
Teen Algorithmic Recommendation Simulator
1. Title
Teen Algorithmic Recommendation Simulator (TARS)

2. By
Author: Kuzayet

Contributors: Open‑source collaborators welcome—see CONTRIBUTING.md.

3. About
TARS is a research‑grade simulator that emulates TikTok‑/Instagram‑style “For You” feeds for teenagers.
It combines classical collaborative filtering (Surprise) with reinforcement learning (OpenAI Gym) to recreate the engagement‑optimization loop and measure how quickly niche content (e.g., body‑image videos) saturates a teen’s feed.

4. Time Spent
~40 hours across three weekends (June 2025).

5. Required Features & Optional Features
Category	Required	Optional
Data	✔️ Pre‑processed YouTube‑8M / open TikTok datasets	🔄 Plug‑in data loader for your own crawl
Core CF	✔️ Matrix Factorization (SVD) recommender	🔁 k‑NN baseline, neural CF
RL Loop	✔️ DQN agent that maximises watch‑time reward	🚀 PPO / SAC agents
Metrics	✔️ Feed‑similarity %, bubble‑intensity score	📊 Attention‑span decay, sentiment drift
CLI	✔️ python simulate.py --user teenA	🖥️ Streamlit dashboard
Docs / Tests	✔️ API docs with Sphinx, unit tests	🧪 Jupyter demo notebooks

6. Notes
Ethics first: The simulator never uses live teen data—only anonymised public sets.

Reproducibility: All random seeds fixed; results in /reports/.

Hardware: Runs on CPU; GPU optional for large RL agents.

7. Relevant Information
Full methodology paper → docs/methodology.pdf

TikTok “How our recommendation system works” white‑paper.

Surprise library → https://surpriselib.com

OpenAI Gym → https://github.com/openai/gym

8. License
MIT License—see LICENSE.

9. Inspiration
Project inspired by Mozilla Foundation’s “YouTube Regrets” study and TikTok’s transparency brief on recommender systems (https://newsroom.tiktok.com/en-us/how-tiktok-recommendation-system-works).

10. What It Does
Given a seed interaction (like, full‑watch, comment), TARS outputs a simulated feed sequence plus quantitative metrics such as:

sql
Copy
Edit
User teen_042
Seed: watched “quick ab workout”
→ 6/10 next videos are body‑image related within 25 min
Bubble‑Intensity: 0.78
Engagement gain Δ: +32 %
11. How We Built It
Dataset wrangling: Filtered teens‑relevant clips from YouTube‑8M.

Collaborative Filtering: Trained SVD model for initial relevance scores.

RL Environment: Wrapped CF scores into a Gym env (FeedSimEnv).

Agent: Implemented a DQN that rewards watch‑time + like probability.

Evaluation: Logged similarity trajectories & plotted bubble‑growth curves.

12. Challenges We Ran Into
Aligning CF outputs with RL state‑space without data leakage.

Preventing reward hacking (agent spamming extreme content).

Balancing simulation speed vs. interpretability of agent policy.

13. Accomplishments We’re Proud Of
Achieved ±3 % fidelity against a held‑out real engagement trace.

Modular design—swap in any RL algorithm with two config lines.

Clear ethical‑risk documentation adopted by two university labs.

14. What We Learnt
Subtle reward tweaks drastically shift algorithmic behavior.

CF alone is mild; the RL feedback loop is what amplifies bubbles.

Good logging & visualisation speed up “red‑team” style audits.

15. What’s Next
🪄 Add explainability layer (SHAP on CF + saliency on RL Q‑values).

🌐 Deploy a Streamlit demo so educators can watch the feed mutate live.

📚 Publish comparative study on bubble intensity across age cohorts.

🤝 Partner with digital‑wellbeing NGOs to propose safer default

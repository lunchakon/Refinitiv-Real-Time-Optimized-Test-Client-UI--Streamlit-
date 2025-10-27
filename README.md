# Refinitiv Real-Time Optimized Test Client UI
A Streamlit web dashboard that lets you test Refinitiv Real-Time Optimized (TestCL) connectivity directly from a browser — running inside Docker and powered by the Docker SDK (no manual CLI).


sudo docker exec -it infratools-docker-infratools-1 bash
./script KTBc1=


# Ideas
- Friendly web UI (No need for CLI access; run tests from browser):
- Input any RIC (record) from web UI
- Launch the Refinitiv Test bashscript(./script <ric>) inside a target container
- View and stream log output live
- Enforce automatic timeout (e.g., 10 seconds)

# Diagrame 
Streamlit App (Docker SDK)
   │
   │→ Docker Socket (/var/run/docker.sock)
   ▼
Infratools Container
   └── ./script <record> ("testing script for full command")


* The Idea is to have both containers share:
```The Docker socket (/var/run/docker.sock) → control access ```
```A shared ./logs folder → collect client logs ```


Security Notice

Mounting /var/run/docker.sock grants full control of the host Docker daemon.
Only use this setup in controlled internal environments or behind authentication.


Quick Start
git clone https://github.com/lunchakon/Refinitiv-Real-Time-Optimized-Test-Client-UI--Streamlit-.git
cd refinitiv-testclient-ui
docker compose up -d --build

Project Structure
├── app/
│   └── Refinitiv-Realtime-TestClient.py
├── script/                     # contains ./script script for TestCL
├── logs/                       # shared logs folder
├── Dockerfile
└── docker-compose.yml

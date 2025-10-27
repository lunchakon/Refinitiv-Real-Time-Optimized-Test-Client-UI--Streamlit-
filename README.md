# Refinitiv-Real-Time-Optimized-Test-Client-UI--Streamlit-
A Streamlit web dashboard for testing Refinitiv Real-Time Optimized (TestCL) connections directly inside a Docker environment — no manual CLI steps required.

*** This tool provides a friendly UI to:
*** Input any RIC (record) you want to test
*** Launch the Refinitiv Test Client (./client <ric>) inside a target container
*** View and stream log output live
*** Enforce automatic timeout (e.g., 10 seconds)


+-----------------------+
|  Streamlit App (UI)   |   → Runs in container A (scripttools-app)
|  (Docker SDK client)  |   → Uses docker.sock to talk to Docker Engine
+-----------+-----------+
            │
            │ Docker SDK API
            ▼
+---------------------------+
| infratools-docker-infratools-1 |
|  ./client <record>             |
|  Refinitiv Test Client Binary  |
+--------------------------------+


Both containers share:
The Docker socket (/var/run/docker.sock) → control access
A shared ./logs folder → collect client logs

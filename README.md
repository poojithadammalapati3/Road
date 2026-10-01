# 🚗 SafeDrive AI – Smart Road Safety & Emergency Response System

Streamlit + OpenCV + Folium hackathon prototype: driver-distraction detection, accident simulation,
emergency dashboard, map, SOS alert (Demo Mode built in) and response tracking.

## Setup
```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```
Python 3.9–3.12 recommended. Opens at http://localhost:8501

## Real SOS alerts (optional)
Demo Mode is ON by default – nothing is sent. To send real alerts:
1. `cp .env.example .env` (or use `.streamlit/secrets.toml.example`) and fill SMTP or Twilio values.
2. In the sidebar, switch **Demo Mode** off.
(Gmail needs an App Password. For Twilio, also run `pip install twilio`.)

## 3-minute demo script
1. **Home** – explain problem + workflow.
2. **Driver Monitoring** – Start camera; look away / close eyes → DISTRACTED → alert after 3 s.
   (No webcam? Use *Simulate distraction*.)
3. **Accident Detection** – *Simulate Accident* (or upload an image → Analyze).
4. **Emergency Dashboard** – metrics flip to ALERT / ACCIDENT DETECTED / SOS SENT; map shows markers.
5. Judge changes **Response Status** dropdown → tracker updates.
6. **Emergency Alert** – show SOS banner + alert history.

## Notes / limitations
- Detection uses OpenCV Haar cascades (fast, no downloads). Glasses, low light or camera angle affect
  eye detection – tune *Eyes-closed limit* in the sidebar.
- "Phone use" is a heuristic (head tilted down), not an object detector.
- Accident detection and image analysis are **simulated**; the emergency-unit marker is a demo position.
- Close other apps using the webcam; change *Camera index* if the wrong camera opens.

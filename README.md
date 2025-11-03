from gtts import gTTS
import os
from datetime import datetime
 
# ---- Step 1: Dynamic Summary Input ----
# You can replace this with text from a report, dashboard, or AI output
summary = """
This dashboard provides a comprehensive view of student performance and learning trends across key subjects.

As of August 2025, the overall pass rate stands at 61.11 percent, with an expected improvement to 64.17 
percent in September — reflecting a five percent increase in academic performance.

The top-performing subject is Science, with a pass rate of 82.1 percent, 
while English and Math show moderate performance levels that may need focused improvement.

The Needs Support indicator highlights English as the subject requiring additional attention, 
with a performance level of 46.95 percent.

Attendance continues to play a crucial role, with an overall attendance impact of minus 0.10 percent, 
emphasizing the need to maintain above 85 percent attendance to sustain academic growth.

The Student Progress table provides detailed trends, showing that most students are demonstrating steady performance improvement month over month, 
supported by positive attendance rates.

The Pass Rate Trend and Forecast chart indicates that while performance was at 61.7 percent in August, 
it may decline slightly to 60 percent if interventions are not introduced soon.

Overall, the Class Average Score is projected at 64.17 percent, with four high achievers expected to cross 85 percent, 
and six at-risk students forecasted to fall below 50 in Science without additional support.

Finally, the AI confidence level predicts a target pass rate of 68.48 percent, 
signaling a strong opportunity for improvement with focused mentoring and consistent attendance.

This dashboard enables educators to identify learning gaps, prioritize support for at-risk students, 
and reinforce high-performing areas to achieve class-wide academic success.
"""
 
# ---- Step 2: Convert Summary to Audio ----
# Use current timestamp for dynamic file name
timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
audio_filename = f"AI Student Academic Report Summary{timestamp}.mp3"
 
# Generate audio using gTTS (Google Text-to-Speech)
tts = gTTS(text=summary, lang='en')
tts.save(audio_filename)
 
print(f"✅ Audio summary saved as: {audio_filename}")
 
# ---- Optional: Play the Audio ----
try:
    from playsound import playsound
    playsound(audio_filename)
except:
    print("🔊 Audio playback skipped. Install 'playsound' if needed.")
 

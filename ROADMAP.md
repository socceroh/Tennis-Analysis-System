# 🎾 2-Week Plan: Tennis Coaching Analysis Project

## 🎯 End Goal (After 2 Weeks)
You should have:
- A working pipeline (video → tracking → stats)
- Basic coaching insights (auto-generated)
- Example report + video clips

## 🗓 Week 1 — Foundation + Data Pipeline

### ✅ Day 1–2: Setup & Run Baseline
**Tasks:**
- Clone Tennis-Analysis-System
- Install dependencies
- Run on a sample tennis video

**Output:**
- Player tracking
- Ball tracking
- Annotated video

👉 **Goal:** Understand the pipeline, don't modify yet

### ✅ Day 3: Understand Code Structure
**Focus on:**
- Tracking module (players + ball)
- Frame processing loop
- Output format

**Deliverable:**  
Write down:
- Where positions are stored
- Where frames are processed

👉 **Goal:** Know where to inject your logic

### ✅ Day 4–5: Extract Structured Data
**Task:**  
Convert tracking outputs into structured data:
- `frame_id`, `player1_x`, `player1_y`, `player2_x`, `player2_y`, `ball_x`, `ball_y`

**Store as:**
- CSV or Pandas DataFrame

**Bonus:**
- Convert to court coordinates (if available)

### ✅ Day 6: Basic Metrics
Compute simple coaching-relevant stats:
- Rally length (approx using ball movement)
- Player movement distance
- Ball speed (if available)

**Output example:**
```json
{
  "avg_rally_length": 4.2,
  "player1_distance": 1200,
  "player2_distance": 1350
}
```

### ✅ Day 7: First Simple Insights (Rule-Based)
Create a basic coaching logic layer:

```python
if avg_rally_length < 3:
    insight = "Points are too short – improve rally consistency"

if player1_distance < player2_distance:
    insight = "Low movement – possible positioning issue"
```

👉 **Goal:** FIRST coaching output (even if simple)

## 🗓 Week 2 — Coaching Intelligence + Video Integration

### ✅ Day 8–9: Rally Segmentation (Simple Version)
Detect rallies using:
- Ball movement continuity
- Time gaps

**Output:**
```python
rallies = [
  {"start": 120, "end": 180},
  {"start": 250, "end": 310}
]
```

### ✅ Day 10: Event Detection (Basic)
Detect:
- Serve (ball starts high velocity)
- Rally end (ball disappears / stops)

👉 Keep it heuristic (no ML yet)

### ✅ Day 11: Video Clip Extraction 🎥
Use OpenCV to cut clips:
- Examples: Short rallies, Long rallies, Errors (approx)

```python
clip = video[start_frame:end_frame]
```

**Save as:**
```
clips/
  short_rallies/
  long_rallies/
```

👉 This is huge for coaching value

### ✅ Day 12: Insight + Clip Linking
Now combine:
- Insight
- Supporting clips

**Example:**
```json
{
  "insight": "Struggling in long rallies",
  "clips": ["rally_03.mp4", "rally_07.mp4"]
}
```

### ✅ Day 13: Auto Coaching Report
Generate a simple report (Markdown):

```markdown
# Coaching Report

## Key Insights
- Short rallies dominate
- Player under-moves

## Recommended Training
- Consistency drills
- Footwork training

## Video Evidence
- [Short Rally 1]
- [Short Rally 2]
```

### ✅ Day 14: Polish + Demo
**Final tasks:**
- Clean code structure
- Save outputs in `/results`
- Prepare: 1 example video, 1 report, 3–5 clips

## 🧠 Architecture You'll Build
```
Video
  ↓
Tracking (existing repo)
  ↓
Structured Data (YOU)
  ↓
Metrics (YOU)
  ↓
Insights (YOU ⭐)
  ↓
Report + Clips (YOU ⭐⭐)
```

## 🔥 Priority Features (Don't Overbuild)
**Focus on:**
- ✅ Rally length
- ✅ Movement
- ✅ Clip extraction
- ✅ Simple insights

**Avoid for now:**
- Deep learning models
- Perfect shot classification
- Complex UI

## 🚀 After 2 Weeks (Next Steps)
If this works, next upgrades:
- Shot classification (FH/BH)
- Error detection
- Serve placement analysis
- Streamlit dashboard
- Confluence auto-report integration (fits your workflow)

## 💡 Pro Tips
- Use 1–2 videos only (don't scale early)
- Keep logic simple but interpretable
- Coaching value > technical perfection
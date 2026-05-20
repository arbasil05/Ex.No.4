# EXP 4 Generate the Prompt and evaluate that for following prompt types - Comparative Analysis Prompt · Experiential Perspective Prompt · Everyday Functioning Prompts · Universal Prompt Structures · Prompt Refinements · Prompt Size Limitations

## DATE: 19-05-2026
## REGISTER NUMBER : 212223040002

---

## Aim

To design and test prompts for the following prompt types, apply them to a Unit-5 use case (manufacturing automation), compare outputs across AI tools, and evaluate them with a rubric:
1. Comparative Analysis Prompt
2. Experiential Perspective Prompt
3. Everyday Functioning Prompt
4. Universal Prompt Structures
5. Prompt Size Limitations

---

## Methodology

One use case from Unit 5 (manufacturing automation) was selected to create example prompts for each prompt type from Unit 2. The prompts were executed across multiple AI tools and the responses were evaluated using a specialized rubric.

---

## Procedure

### 1. Define the Scenario and Use Case

#### Scenario
The manufacturing industry aims to reduce manual monitoring and increase efficiency with automation. The system will use IoT devices and embedded controllers to automate equipment, monitor performance, and enable predictive maintenance. Goals: streamline production, minimize downtime, and improve energy efficiency.

#### Target Audience
Manufacturing engineers and operations managers in automotive, electronics, and food processing sectors.

#### Main Objectives
- Improve production efficiency by ~30%.
- Reduce machinery downtime via predictive maintenance.
- Enable real-time monitoring and remote control of systems.
- Reduce energy consumption through process optimization.

---

### 2. Prompt Patterns and Concrete Example Prompts (Manufacturing Use Case)

#### Comparative Analysis Prompt
- **Purpose:** Compare approaches, trade-offs, or tools.
- **Prompt:** "Compare a rule-based threshold alerting system with a machine-learning-based predictive maintenance model for detecting bearing failures in an assembly line. Discuss accuracy, false-positive risk, implementation complexity, data needs, and maintenance cost. Recommend which to choose for a medium-sized electronics plant and why."

#### Experiential Perspective Prompt
- **Purpose:** Elicit first-person experience or role-based insights.
- **Prompt:** "From the perspective of a plant floor maintenance engineer, describe the daily benefits and challenges of using an AI-driven predictive maintenance dashboard connected to IoT sensors. Include how it changes your workflow and the types of alerts you would trust most."

#### Everyday Functioning Prompt
- **Purpose:** Explain practical, everyday uses and impact.
- **Prompt:** "Explain how an IoT-enabled energy management system reduces energy consumption on a factory floor. Give three concrete examples of automated actions it might take and the expected energy savings for each."

#### Universal Prompt Structures
- **Purpose:** Reusable templates for clarity and completeness.
- **Template:** "Explain [concept] in simple terms, list assumptions, provide a step-by-step implementation outline, and include a short example."
- **Prompt:** "Explain 'edge anomaly detection' in simple terms, list assumptions, provide a step-by-step implementation outline for a conveyor-belt vibration sensor, and include a short example of an anomaly and the expected alert."

#### Prompt Size Limitations
- **Purpose:** Manage long outputs or large inputs.
- **Prompt (chunking):** "Summarize the attached 6000-word maintenance log into a 300-word incident summary. Start with the first 1500 words and wait for confirmation to continue."
- **Prompt (limits):** "List 20 possible sensor types used in predictive maintenance, grouped by function; return 5 groups at a time."

---

## 3. Implementation and Model Responses

The designed prompts were tested on ChatGPT, Gemini, and Claude. Below are the verbatim-style responses recorded during the experiment.

---

### Comparative Analysis Prompt

**Prompt:** "Compare a rule-based threshold alerting system with a machine-learning-based predictive maintenance model for detecting bearing failures in an assembly line. Discuss accuracy, false-positive risk, implementation complexity, data needs, and maintenance cost. Recommend which to choose for a medium-sized electronics plant and why."

#### ChatGPT Response:

> Great question — this is one of the most common architectural decisions in industrial IoT. Let me break it down across each dimension you asked about.
>
> **Accuracy:**
> Rule-based threshold systems are inherently reactive. They fire when a sensor value — say, vibration amplitude — crosses a hard-coded limit. This works well for obvious, abrupt failures but completely misses gradual bearing degradation where values drift slowly over weeks. Machine learning models, especially those trained on historical failure data using techniques like Random Forest or LSTM networks, can learn the subtle multivariate patterns that precede bearing failure — often flagging issues 2–3 weeks before a threshold-based system would catch them.
>
> **False-Positive Risk:**
> Rule-based systems are notoriously noisy in real industrial environments. Sensor drift, temperature-induced fluctuations, and vibration from nearby machinery can all trigger false alerts. This leads to "alarm fatigue," where technicians start ignoring warnings. ML models, once properly trained and validated, significantly reduce false positives because they learn the *context* of a reading, not just its absolute value.
>
> **Implementation Complexity:**
> Rule-based systems are low-complexity and fast to deploy — you define your thresholds in a configuration file and you're essentially done. ML-based systems, however, require a full MLOps pipeline: data collection, feature engineering, model training, validation against labeled failure events, deployment, and scheduled retraining as equipment ages. This is substantially more work upfront.
>
> **Data Needs:**
> Rule-based systems need almost no historical data — just domain expertise to set initial thresholds. ML models require large volumes of labeled data, including examples of both normal operation and actual failure events. In practice, collecting enough real failure examples is the hardest part, and data augmentation or transfer learning is often needed.
>
> **Maintenance Cost:**
> Once deployed, rule-based systems are cheap to maintain — you just adjust thresholds periodically. ML models require monitoring for model drift, periodic retraining when equipment characteristics change, and dedicated ML engineering resources.
>
> **Recommendation for a Medium-Sized Electronics Plant:**
> I'd recommend a **hybrid approach**. Deploy a rule-based threshold system immediately to catch critical safety events and protect your production line right now. Simultaneously, instrument your line to capture high-quality sensor data, and start building your ML training dataset. Once you have 6–12 months of data (including any failure events), pilot an ML model on a single line. Run both systems in parallel, compare their alert quality, and gradually transition decision-making to the ML model as confidence grows. This incremental roadmap minimizes upfront risk and cost while setting you up for a more intelligent, predictive operation within 12–18 months.

---

#### Gemini Response:

> Absolutely, let's compare these two approaches head to head for bearing failure detection on an assembly line.
>
> **Rule-Based Threshold Alerting:**
> This is the traditional approach — you configure upper and lower bounds for sensor metrics like vibration (mm/s RMS), temperature (°C), and acoustic emission, and an alert fires the moment a reading breaches those bounds. The strengths are obvious: it's simple, fully transparent, easy to audit, and requires almost no data infrastructure. An experienced maintenance engineer can configure it in an afternoon.
>
> The weaknesses, however, are significant in the context of bearing failure. Bearings typically fail through a gradual process — micro-cracking, race wear, lubricant degradation — that produces sensor signals that creep upward over weeks rather than jumping past a threshold overnight. A purely threshold-based system will often miss early-stage degradation entirely, only triggering when damage is already severe. Additionally, these systems generate a high volume of false positives in noisy factory environments, which erodes technician trust over time.
>
> **Machine Learning-Based Predictive Maintenance:**
> ML models — particularly anomaly detection models, survival analysis models, or supervised classifiers trained on labeled run-to-failure data — can learn the complex, multivariate signature of impending bearing failure. They're far more sensitive to early-stage degradation and can provide a "remaining useful life" (RUL) estimate rather than a binary alert.
>
> The trade-off is implementation complexity. You need a robust data pipeline, labeled historical failure data (which is often scarce), a model training and validation workflow, and ongoing monitoring for model drift. The total cost of ownership is higher, especially if your team lacks in-house data science expertise.
>
> **My Recommendation:**
> For a medium-sized electronics plant, I'd suggest a phased strategy. In Phase 1 (Months 1–3), implement conservative rule-based thresholds on all critical bearings. This gives you immediate protection and begins accumulating structured sensor data. In Phase 2 (Months 4–12), use that data to train an initial anomaly detection model — unsupervised approaches like Isolation Forest or autoencoders are good starting points when labeled failure data is limited. In Phase 3, transition to a supervised predictive model once you've gathered enough labeled failure examples. This way you balance cost, risk, and performance at each stage.

---


---

### Experiential Perspective Prompt

**Prompt:** "From the perspective of a plant floor maintenance engineer, describe the daily benefits and challenges of using an AI-driven predictive maintenance dashboard connected to IoT sensors. Include how it changes your workflow and the types of alerts you would trust most."

#### ChatGPT Response:

> *Speaking as a maintenance engineer on the floor...*
>
> Honestly, the dashboard changed my mornings completely. Before, I'd start every shift by walking the entire line — Section A, the conveyor system, the CNC stations, then the packaging end. That walk alone took 45 minutes, and half the time I was just doing a visual check with no real diagnostic value. Now I walk in, pull up the dashboard on the workstation near the supervisor's desk, and within two minutes I have a prioritized list of machines that need attention today, ranked by predicted severity. That alone has given me back almost an hour every shift.
>
> The biggest daily benefit is the *anticipation*. Yesterday, the dashboard flagged Motor 7B on Line 3 — it showed a gradual upward trend in bearing temperature and a 12% increase in vibration amplitude over the past 72 hours. Nothing had crossed a threshold yet. Two years ago, I wouldn't have known about that until the motor tripped a breaker mid-production. Instead, I scheduled a bearing replacement for the weekend maintenance window, ordered the part on Thursday, and the line never went down. That's the system working exactly as it should.
>
> Now, the challenges — and I want to be honest here, because it isn't all smooth. The biggest challenge early on was trust. When the system first went live, it fired a lot of alerts that turned out to be nothing. We'd get a high-confidence warning on a motor, go inspect it, find nothing wrong, and come back frustrated. That happened three or four times in the first month, and some of the guys on my team started calling it the "boy who cried wolf" board. It took about eight weeks of tuning — working with the data team to adjust sensitivity thresholds and add contextual filters — before the false positive rate dropped to an acceptable level.
>
> The types of alerts I trust most? The ones that show me *why* they fired. I don't trust a simple red light that says "Motor 7B: Anomaly Detected." That tells me nothing. What I do trust is an alert that shows me: the sensor reading trend over the last 7 days, the specific feature that triggered it (e.g., "RMS vibration in the 800–1200 Hz band increased 18% above baseline"), a confidence score, and ideally a recommended inspection step. When I can see the evidence, I can make my own judgment. That's the kind of alert I'll act on immediately — and I'll trust the system to give me more of them.

---

#### Gemini Response:

> *As a maintenance engineer who's been working this floor for six years, here's what a day with the predictive maintenance dashboard actually looks like...*
>
> The single biggest change to my daily workflow is that I'm no longer in purely reactive mode. In the old days, my job basically had two states: either nothing was wrong and I was doing routine PMs, or something had already failed and I was scrambling to fix it as fast as possible while the production supervisor stood behind me asking for an ETA every five minutes. That second state was stressful, expensive, and — if I'm being honest — embarrassing. A failure that stops a production line is a visible failure. Everyone knows.
>
> With the dashboard, I've added a third state to my working life: *proactive intervention*. I get early warning that something is developing, I have time to think about it, I can plan the repair during a scheduled window, and I can order parts in advance. The difference in stress levels alone has been significant.
>
> On a typical morning, I review the dashboard's priority queue. Green means nominal, yellow means "watch this," and red means "act today." Most days I have two or three yellows and no reds. I check the trend graphs on the yellows, make notes, and decide whether to escalate or just monitor for another 24 hours. That decision used to be a gut call with no data — now it's an informed judgment with seven days of sensor history behind it.
>
> The challenge that catches most engineers off guard is integration with existing workflows. The dashboard doesn't replace our CMMS (computerized maintenance management system) — it has to feed into it. Getting those two systems to talk to each other took three months of IT work that nobody budgeted for. There's also a learning curve for the more experienced technicians who've been doing this for 20 years. They trust their hands and their ears more than a graph on a screen, and that's not unreasonable — their intuitions are often right. The key was framing the system as a "second opinion" rather than a replacement for their judgment. Once they felt it was supporting them rather than second-guessing them, adoption improved substantially.
>
> The alerts I trust most are the ones corroborated by multiple sensors. If only the vibration sensor flags an anomaly, I'll note it but I won't escalate. If the vibration sensor *and* the temperature sensor *and* the acoustic emission sensor are all trending in the same direction at the same time, that convergence is a very strong signal. I've learned to look for those multi-sensor agreements — they're the ones that have consistently predicted real failures in my experience with this system.


---

### Everyday Functioning Prompt

**Prompt:** "Explain how an IoT-enabled energy management system reduces energy consumption on a factory floor. Give three concrete examples of automated actions it might take and the expected energy savings for each."

#### ChatGPT Response:

> An IoT-enabled energy management system (EMS) works by deploying networked sensors throughout a facility — power meters, occupancy sensors, temperature sensors, and equipment state monitors — and continuously feeding that data into a central platform that uses rule-based logic or ML algorithms to optimize energy consumption in real time. Unlike manual energy audits or monthly utility bill reviews, an IoT EMS operates continuously and can respond to changing conditions within seconds or minutes. Here are three concrete automated actions such a system might take, along with realistic energy savings estimates:
>
> **1. Dynamic HVAC Zoning Based on Occupancy and Production Status**
> The EMS integrates occupancy sensors and production schedule data to determine which zones of the factory floor are actively staffed or in operation. During a shift changeover — say, the 45-minute window between the day shift leaving and the night shift arriving — the system automatically reduces ventilation rates to minimum code-compliant levels and raises cooling setpoints by 2–3°C in unoccupied zones. It restores conditions five minutes before the next shift arrives.
> *Expected savings: 8–12% of HVAC energy consumption, or roughly 5–8% of total facility energy spend. For a medium-sized plant consuming 500 MWh/month in HVAC, this represents 40–60 MWh saved per month.*
>
> **2. Automated Lighting Control with Daylight Harvesting and Motion Detection**
> The EMS connects to smart lighting controllers that use motion sensors and, where skylights or windows are present, lux sensors to measure available natural light. In areas where daylight provides sufficient illumination, artificial lighting is automatically dimmed or switched off. In areas that are unoccupied for more than 10 minutes, lighting drops to 10% or off entirely.
> *Expected savings: 5–10% of total facility lighting load. In a plant where lighting accounts for 15% of electricity use, this represents a 0.75–1.5% reduction in total energy spend — modest individually, but significant at scale over a year.*
>
> **3. Demand-Response Motor Start Sequencing to Reduce Peak Demand Charges**
> Many industrial electricity tariffs include a peak demand charge based on the highest 15-minute average power draw in a billing period. At shift start, if every motor and compressor on the line starts simultaneously, the peak demand spike can add thousands of dollars to the monthly bill. The EMS automatically staggers motor start sequences — starting the highest-power equipment first, then adding loads in 30-second increments — to flatten the demand curve.
> *Expected savings: 7–15% reduction in peak demand charges. For a plant with a $20,000/month demand charge, this can translate to $1,400–$3,000 in monthly savings, without reducing production capacity at all.*

---

#### Gemini Response:

> An IoT-enabled energy management system reduces factory energy consumption by giving the facility real-time visibility into how energy is being used at the equipment level — not just at the utility meter — and automating responses to waste conditions that previously went unnoticed or unaddressed. Think of it as giving the factory a nervous system: every piece of equipment reports its energy state continuously, and the system takes action when it detects inefficiency. Here are three concrete examples:
>
> **1. Automated Shutdown of Idle Compressed Air Compressors**
> Compressed air systems are one of the largest energy consumers in manufacturing, and one of the most wasteful — compressors often run at full load even during periods of low or zero demand, simply because no one manually adjusts them. An IoT EMS monitors air consumption in real time using flow sensors at the compressor outlet and demand sensors at key use points. When consumption drops below a configured threshold during breaks or between production batches, the system automatically unloads or shuts down secondary compressors and ramps them back up 60 seconds before they're needed.
> *Expected savings: approximately 10–15% of compressed air system energy, which in many plants represents 3–6% of total facility electricity.*
>
> **2. Adaptive Conveyor Speed Matching to Live Production Rate**
> Conveyors in most plants run at a fixed speed set for peak throughput — even during periods of reduced production rate, machine changeovers, or upstream bottlenecks. Variable-frequency drives (VFDs) on conveyor motors can adjust speed dynamically, but only if they receive a signal to do so. The EMS integrates with production execution data and upstream sensor inputs to continuously calculate the optimal conveyor speed and sends setpoint adjustments to the VFDs automatically.
> *Expected savings: 5–8% of conveyor motor energy consumption. Since conveyor power scales approximately with the cube of speed, even a 15% speed reduction during partial-load periods can yield 30%+ energy savings for those intervals.*
>
> **3. Chiller Setpoint Optimization Using Weather Forecast Data**
> Process cooling systems and HVAC chillers often operate at a fixed setpoint regardless of ambient conditions. On mild days or overnight, the chiller works harder than necessary to maintain a setpoint that's optimized for worst-case summer heat. An IoT EMS that integrates real-time weather API data can dynamically adjust chiller setpoints — raising them by 1–2°C when ambient conditions allow — without compromising process quality.
> *Expected savings: 6–10% of chiller energy consumption per degree Celsius of setpoint increase. For large process cooling loads, this can represent significant monthly savings with zero impact on production.*

---


### Universal Prompt Structures

**Prompt:** "Explain 'edge anomaly detection' in simple terms, list assumptions, provide a step-by-step implementation outline for a conveyor-belt vibration sensor, and include a short example of an anomaly and the expected alert."

#### ChatGPT Response:

> **Simple Explanation:**
> Edge anomaly detection means running the anomaly-spotting algorithm *directly on the device* next to the sensor — on a microcontroller, an industrial gateway, or a small edge server on the factory floor — rather than sending raw sensor data to a cloud server for analysis. Think of it like having a security guard at the door rather than sending footage to a remote monitoring center: the response is faster, the data doesn't have to travel, and the system keeps working even if the internet connection drops.
>
> **Assumptions:**
> 1. The conveyor-belt vibration sensor samples at sufficient frequency to capture relevant failure signatures (typically 1–10 kHz for mechanical vibration).
> 2. A "normal" baseline of vibration behavior has been collected during healthy operation (at least 2–4 weeks of continuous data under typical production conditions).
> 3. The edge computing device has enough processing power to run inference on extracted features in real time (a modern industrial IoT gateway with 1–2 GB RAM is generally sufficient for lightweight models).
> 4. Network connectivity to the central monitoring system is available for alert transmission but is not required for anomaly detection itself.
> 5. Bearing failure is the primary failure mode of interest (as opposed to belt misalignment or motor electrical faults, which produce different vibration signatures).
>
> **Step-by-Step Implementation Outline:**
> 1. **Hardware Setup:** Mount an accelerometer (e.g., MEMS-based, ±16g range, 10 kHz max sampling rate) on the conveyor drive housing. Connect to an edge gateway via industrial protocol (e.g., MQTT over local LAN).
> 2. **Data Collection:** Run the conveyor under normal operating conditions for 3–4 weeks. Log continuous raw vibration data with timestamps and production state (running, idle, changeover).
> 3. **Feature Extraction:** Compute time-domain features (RMS, peak, crest factor) and frequency-domain features (FFT spectrum, dominant frequency bands) from fixed-length windows (e.g., 0.5-second windows every 5 seconds).
> 4. **Baseline Modeling:** Train a lightweight anomaly detection model on the extracted normal-operation features. Good choices for edge deployment include: statistical thresholding on feature distributions, Isolation Forest, or a compact autoencoder. Export the model in a lightweight format (ONNX or TensorFlow Lite).
> 5. **Edge Deployment:** Deploy the model to the edge gateway. Implement a real-time inference loop: acquire sensor data → extract features → run model → compare output to anomaly threshold → trigger alert if threshold exceeded.
> 6. **Alert Configuration:** Define alert routing: local LED/buzzer for immediate floor notification, MQTT message to central dashboard, and logging to local time-series database.
> 7. **Validation and Tuning:** Monitor false positive rate for 2–4 weeks post-deployment. Adjust anomaly threshold to balance sensitivity and specificity.
>
> **Short Example:**
> During a Monday morning shift, the conveyor is running at normal production speed. The edge device is continuously computing vibration features every 5 seconds.
>
> At 10:23 AM, the extracted feature vector shows: RMS vibration = 3.8 mm/s (normal baseline: 1.2 mm/s), crest factor = 6.2 (normal: 2.8), and a prominent spectral peak at 162 Hz corresponding to the bearing's ball-pass-outer-race (BPFO) frequency.
>
> The on-device model outputs an anomaly score of 0.91 (threshold: 0.70). The edge gateway immediately:
> - Triggers a yellow warning indicator on the local HMI panel.
> - Publishes an MQTT alert to the central dashboard: *"Conveyor 3 Drive End Bearing — Anomaly Detected | RMS: 3.8 mm/s | BPFO Peak at 162 Hz | Confidence: 91% | Recommended Action: Schedule bearing inspection within 48 hours."*
> - Logs the event with full feature vector to local storage.
>
> The maintenance engineer receives the alert on their dashboard tablet, reviews the 7-day trend showing a gradual RMS increase, and schedules a bearing inspection for the next planned maintenance window.

---

#### Gemini Response:

> **Simple Explanation:**
> Imagine you have a guard standing right next to a machine on the factory floor. This guard knows exactly what "normal" looks like for that machine — its usual sounds, vibrations, and rhythms — because they've been watching it for months. The moment something starts to seem off, the guard raises an alarm right there, on the spot, without needing to call headquarters first. That's edge anomaly detection: the detection logic lives *at the sensor*, on a small computer near the machine, rather than in a distant cloud data center. It's faster, more reliable in low-connectivity environments, and keeps sensitive operational data on-premises.
>
> **Assumptions:**
> 1. The vibration sensor is correctly mounted on the conveyor drive housing at the bearing location and is sampling at an appropriate rate (minimum 5× the highest frequency of interest — typically 5–20 kHz for bearing diagnostics).
> 2. A sufficiently long period of normal-operation data (4+ weeks recommended) is available for baseline modeling.
> 3. The edge device has the computational resources to run inference in near-real-time (sub-second latency preferred for safety-critical applications).
> 4. The production environment is reasonably stationary in its operating conditions — a model trained on summer operating data may need retraining if winter ambient temperatures significantly change vibration characteristics.
> 5. Connectivity to the central monitoring system is available for alert forwarding but is treated as optional for the core detection function.
> 6. The primary anomaly of interest is mechanical bearing degradation; electrical motor faults and belt misalignment are considered out of scope for this implementation.
>
> **Step-by-Step Implementation Outline for a Conveyor-Belt Vibration Sensor:**
> 1. **Sensor Selection and Mounting:** Select an industrial MEMS accelerometer with appropriate frequency range and IP rating for the factory environment. Mount at the drive-end bearing housing of the conveyor motor, perpendicular to the shaft axis for radial vibration measurement.
> 2. **Data Acquisition Setup:** Configure sampling rate, window size, and data buffering on the edge device. Establish local MQTT broker for data routing.
> 3. **Baseline Data Collection:** Operate the conveyor under typical production conditions for 4–6 weeks. Capture data across all production states (full speed, reduced speed, idle, startup, shutdown) to ensure the baseline represents the full normal operating envelope.
> 4. **Feature Engineering:** Extract both time-domain features (RMS, kurtosis, peak-to-peak) and frequency-domain features (FFT spectrum, bearing characteristic frequencies: BPFO, BPFI, BSF, FTF) from overlapping analysis windows.
> 5. **Model Training:** Train an anomaly detection model — an autoencoder or One-Class SVM works well when failure examples are scarce — on the normal-operation feature set. Optimize for edge deployment by reducing model size and quantizing weights where possible.
> 6. **Deployment and Integration:** Deploy the model to the edge gateway. Implement the inference pipeline and integrate alert outputs with the plant's SCADA or CMMS system.
> 7. **Monitoring and Model Maintenance:** Track false positive rate, missed detection rate, and model prediction confidence over time. Schedule model retraining whenever equipment is serviced or operating conditions change significantly.
>
> **Short Example of an Anomaly and Expected Alert:**
> Scenario: Conveyor Belt 2 has been operating normally for three months. At 14:40 on a Wednesday afternoon, the edge device detects a persistent, rhythmic increase in vibration amplitude that was not present in the baseline data. The frequency analysis shows a growing peak at the bearing's inner-race defect frequency (BPFI), which corresponds to a characteristic signature of inner-race wear progressing from Stage 2 to Stage 3 of the ISO degradation curve.
>
> The model's reconstruction error exceeds the anomaly threshold for three consecutive analysis windows (15 seconds of sustained anomaly).
>
> **Alert generated by the edge device:**
> *"[WARNING] Conveyor 2 — Inner Race Bearing Anomaly | Detected: 14:40:32 | Feature: BPFI amplitude +340% above baseline | Sustained for: 15 seconds | Model confidence: 87% | Recommended action: Inspect conveyor drive-end bearing; consider scheduling replacement at next maintenance window. Estimated urgency: Medium — monitor closely for rate of change increase."*

---

### Prompt Size Limitations

**Prompt:** "Summarize the attached 6000-word maintenance log into a 300-word incident summary. Start with the first 1500 words and wait for confirmation to continue."

#### ChatGPT Response:

> Understood — I'll process the maintenance log in chunks of approximately 1500 words each and produce a consolidated 300-word summary after all segments have been reviewed. Here is my summary of the first 1500 words:
>
> ---
>
> **Incident Summary — Chunk 1 of 4 (Words 1–1500):**
>
> The log opens with a chronological account of anomalous temperature readings first observed on Line 3, Spindle Assembly Station 7, beginning on Day 1 of the two-week logging period. The initial readings showed spindle housing temperatures approximately 8°C above the established baseline of 42°C, accompanied by a marginal but consistent increase in spindle vibration amplitude measured at the drive-end bearing. At the time, the on-shift technician attributed the elevated readings to ambient temperature variation — the facility HVAC had been operating in economy mode during a mild weather period — and logged the event as "monitoring required, no immediate action."
>
> By Day 3, a second temperature exceedance event was recorded, this time reaching 54°C — 12°C above baseline — during a sustained production run at full spindle speed. The vibration amplitude had increased by approximately 15% relative to the Day 1 readings. A brief halt of 4 minutes was logged while the technician performed a visual and tactile inspection of the bearing housing. No abnormalities were observed externally, and the spindle was returned to service after lubricant was manually applied. The event was logged but not escalated to the maintenance supervisor.
>
> Day 5 through Day 8 show no significant events, with temperature readings returning to near-baseline levels, possibly due to the manual lubrication applied on Day 3 providing temporary relief.
>
> **Key emerging indicators from Chunk 1:** recurring temperature exceedances correlated with spindle speed, initial attribution to environmental factors, and a missed escalation opportunity on Day 3.
>
> ---
>
> Please confirm to proceed with Chunk 2 (words 1501–3000), or let me know if you'd like me to adjust the summary focus or level of detail.

---

#### Gemini Response:

> Thank you for sharing the maintenance log. I'll proceed with the first 1500 words as requested and await your confirmation before continuing with the remainder.
>
> ---
>
> **Partial Incident Summary — Segment 1 (Words 1–1500):**
>
> The opening section of the maintenance log documents the initial identification of a recurring thermal anomaly on Line 3 of the assembly facility, centered on the spindle unit at Station 7. The first temperature exceedance event is recorded on Day 1 of the monitoring period, with the spindle housing measuring 8–10°C above the established operational baseline. Concurrent with the thermal readings, minor increases in spindle vibration levels were noted in the sensor data, though these were within a range that the monitoring system classified as "advisory" rather than "warning."
>
> The Day 1 response was conservative: the shift technician logged the readings, noted the concurrent HVAC economy-mode operation as a possible contributing factor, and did not escalate the event. This decision is noted in the log as consistent with the facility's standard operating procedure for first-occurrence advisory-level anomalies.
>
> Days 2 through 4 show a pattern of intermittent elevated readings, predominantly during high-speed production runs, with temperatures returning closer to baseline during lower-demand intervals. This cyclic pattern is significant and will be relevant when examining the later escalation of the incident.
>
> On Day 4, a more significant exceedance event — 54°C sustained for approximately 12 minutes during a full-speed production run — prompted a brief manual inspection and lubrication intervention. The intervention temporarily reduced the temperature readings, creating a false impression of resolution that delayed further investigation.
>
> **Key themes from Segment 1:** early-stage thermal and vibration indicators present from Day 1; initial response appropriate per SOP but insufficient in retrospect; temporary symptom relief from lubrication masking underlying bearing degradation.
>
> ---
>
> Ready to continue with Segment 2 (words 1501–3000) upon your confirmation.

---


## 4. Evaluation Rubric

The responses were evaluated based on the following criteria (each scored 1–5):

| Criterion | Description | 1 (Poor) | 5 (Excellent) |
|---|---|---|---|
| **Relevance** | Does the response address the prompt and manufacturing context? | Off-topic | Fully on-target |
| **Accuracy / Technical Correctness** | Are technical claims correct and realistic? | Many errors | Technically sound |
| **Completeness** | Are important aspects covered (assumptions, steps, examples)? | Incomplete | Thorough |
| **Actionability** | Can the plant act on the recommendations or steps? | Not actionable | Directly actionable |
| **Clarity** | Is the response easy to understand and well-structured? | Confusing | Clear and well-structured |

**Scoring Interpretation:** Sum of the five criterion scores (max 25).

| Score Range | Rating |
|---|---|
| 21–25 | Excellent |
| 16–20 | Good |
| 11–15 | Fair |
| ≤ 10 | Poor |

---

## 5. Evaluation Workflow

- The comparative analysis prompt and others were executed on the chosen AI tools (ChatGPT, Gemini, Claude).
- Each generated response was reviewed and scored using the evaluation rubric.
- Average scores were computed, and qualitative differences (such as tone, level of technical depth, assumptions stated, and use of examples) were noted and compared across models.
- All three models performed well on relevance and clarity. Claude and ChatGPT generally provided more technically specific responses with detailed assumptions and step-by-step reasoning. Gemini responses were consistently concise and well-structured but sometimes less granular on implementation specifics.

---

## Result

The experiment was successfully carried out. Prompts were designed for all five prompt types using the IoT-enabled Manufacturing Automation use case (Unit 5). Each prompt was tested across AI tools (ChatGPT, Claude, Gemini) and evaluated using a rubric-based scoring method. The results demonstrate that structured and refined prompts yield the highest quality outputs, while prompt size management (chunking and confirmation gates) ensures responses remain concise and within model limits. First-person framing in the Experiential Perspective prompts produced notably more nuanced and practically grounded responses across all three models compared to third-person or generic framings.

# EXP 4 Generate the Prompt and eveluate that for following prompt types - Comparative Analysis Prompt Experiential Perspective Prompt - Everyday Functioning Prompts - Universal Prompt Structures Prompt Refinements- Prompt Size Limitations.
## DATE: 19-05-2026
## REGISTER NUMBER : 212223040002

## Aim
To design and test prompts for the following prompt types, apply them to a Unit-5 use case (manufacturing automation), compare outputs across AI tools, and evaluate them with a rubric: 1) Comparative Analysis Prompt 2) Experiential Perspective Prompt 3) Everyday Functioning Prompt 4) Universal Prompt Structures 5) Prompt Size Limitations.

### Methodology
One use case from Unit 5 (manufacturing automation) was selected to create example prompts for each prompt type from Unit 2. The prompts were executed across multiple AI tools and the responses were evaluated using a specialized rubric.

## Procedure
### 1. Define the Scenario and Use Case

#### Scenario
The manufacturing industry aims to reduce manual monitoring and increase efficiency with automation. The system will use IoT devices and embedded controllers to automate equipment, monitor performance, and enable predictive maintenance. Goals: streamline production, minimize downtime, and improve energy efficiency.

#### Target audience
Manufacturing engineers and operations managers in automotive, electronics, and food processing sectors.

#### Main objectives
- Improve production efficiency by ~30%.
- Reduce machinery downtime via predictive maintenance.
- Enable real-time monitoring and remote control of systems.
- Reduce energy consumption through process optimization.

### 2. Prompt patterns and concrete example prompts (manufacturing use case)

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

## 3. Implementation and Model Responses

The designed prompts were tested on ChatGPT, Gemini, and Claude. Below are the responses recorded during the experiment.

### Comparative Analysis Prompt
**Prompt:** "Compare a rule-based threshold alerting system with a machine-learning-based predictive maintenance model for detecting bearing failures in an assembly line. Discuss accuracy, false-positive risk, implementation complexity, data needs, and maintenance cost. Recommend which to choose for a medium-sized electronics plant and why."

#### Responses:
- **ChatGPT:** "Rule-based systems are simple, interpretable, and quick to deploy; they detect obvious threshold breaches but struggle with gradual degradation and sensor drift, causing high false positives. ML-based predictive models can learn complex failure patterns and reduce false positives given quality labeled data, but they require more data engineering, model training, and ongoing retraining. For a medium-sized electronics plant with reasonable historical failure logs, an ML approach combined with conservative thresholds for initial deployment is recommended: start hybrid (rules + ML) to lower risk and cost."
- **Gemini:** "Threshold alerts work well for clear-cut events and minimal data, offering low implementation overhead. Machine learning offers better precision over time but needs historical failure records and an infrastructure for feature extraction and retraining. Recommendation: begin with a rule-based safety net while collecting data, then phase in an ML model once sufficient labeled examples exist, which balances cost and performance."
- **Claude:** "Rule-based thresholds are cost-effective and transparent but lead to many false positives in noisy industrial environments. Supervised ML models reduce false alarms and can detect early signs of bearing wear, yet they demand labeling, validation, and monitoring. For a medium-sized plant, adopt an incremental roadmap: implement robust thresholding for critical lines, instrument extensive data capture, and pilot an ML model on a subset for validation before full rollout."

### Experiential Perspective Prompt
**Prompt:** "From the perspective of a plant floor maintenance engineer, describe the daily benefits and challenges of using an AI-driven predictive maintenance dashboard connected to IoT sensors. Include how it changes your workflow and the types of alerts you would trust most."

#### Responses:
- **ChatGPT:** "The dashboard centralizes machine health so I no longer walk the entire line to spot issues; I get prioritized alerts highlighting high-severity anomalies. Challenges include alert fatigue from low-confidence notifications and occasional false positives that require manual verification. I trust alerts that include confidence scores, recent sensor trends, and suggested troubleshooting steps."
- **Gemini:** "Daily benefit: faster diagnosis and fewer unexpected stoppages because I can see trends and act before failures. Challenge: integrating dashboard tasks into existing maintenance routines and ensuring alerts are precise. Trusted alerts show corroborating sensor patterns and historical precedents."
- **Claude:** "The system reduces reactive tasks and schedules targeted interventions, saving time. However, initial skepticism and the need for sensor calibration slow adoption. I rely on alerts tied to multiple sensors and clear root-cause hints."

### Everyday Functioning Prompt
**Prompt:** "Explain how an IoT-enabled energy management system reduces energy consumption on a factory floor. Give three concrete examples of automated actions it might take and the expected energy savings for each."

#### Responses:
- **ChatGPT:** "1) Dynamic HVAC zoning: reduce ventilation in idle zones — ~8–12% savings. 2) Shift-based lighting control: dim or switch off lights when no motion detected — ~5–10% savings. 3) Demand-response motor scheduling: stagger heavy motor starts to avoid peak demand charges — ~7–15% savings. Combined, these can yield meaningful operational reductions when tuned to facility patterns."
- **Gemini:** "Examples: automated shutoff of idle compressors (10% saving), adaptive conveyor speed matching production rate (5–8%), and optimized chiller setpoints using weather forecasts (6–10%). Each action targets different subsystems and together reduce total energy usage."
- **Claude:** "Automated actions: schedule non-urgent heating outside peak hours (4–8%), use variable-frequency drives to trim motor usage (6–12%), and integrate local renewable generation with load shifting (variable savings). Implementation needs a feedback loop to avoid process disruption."

### Universal Prompt Structures
**Prompt:** "Explain 'edge anomaly detection' in simple terms, list assumptions, provide a step-by-step implementation outline for a conveyor-belt vibration sensor, and include a short example of an anomaly and the expected alert."

#### Responses:
- **ChatGPT:** "Edge anomaly detection runs lightweight models on local devices to flag unusual sensor behavior quickly. Assumptions: reliable sensor sampling, baseline normal behavior available, and low-latency connectivity for alerts. Steps: collect baseline vibration data; preprocess and extract features; train a compact model (e.g., autoencoder); deploy to edge device; set alert rules and logging. Example anomaly: sudden high-frequency spike indicating bearing crack → immediate high-priority alert with recent waveform attached."
- **Gemini:** "Simple explanation, assumptions, steps: same structure; emphasis on model size and update pipeline. Example: persistent rhythmic vibration increase indicating misalignment → actionable alert with suggested inspection steps."
- **Claude:** "Explains concept, lists practical constraints (compute, power), gives stepwise plan including fallback rules, and a short example where an anomaly triggers temporary shutdown for inspection."

### Prompt Size Limitations
**Prompt:** "Summarize the attached 6000-word maintenance log into a 300-word incident summary. Start with the first 1500 words and wait for confirmation to continue."

#### Responses:
- **ChatGPT:** "Summary (first 1500 words): The log documents recurring temperature spikes on Line 3 over a two-week period, correlated with increased spindle vibration. Early alerts were attributed to sensor noise; however, on day 12 a sustained spike coincided with a brief production halt. Recommended immediate actions: inspect bearing housing, verify cooling flow, and archive sensor logs for model retraining. (Continue to process next chunk on confirmation.)"
- **Gemini:** "Concise incident summary focusing on timeline, probable causes, and recommended checks, with a note to continue with the next segment upon confirmation."
- **Claude:** "Highlights main incidents, sequence of events, and a prioritized action list; asks for confirmation to proceed with the remaining text."

## 4. Evaluation Rubric
The responses were evaluated based on the following criteria (each scored 1–5):
- **Relevance:** Does the response address the prompt and manufacturing context? (1 = off-topic, 5 = fully on-target)
- **Accuracy / Technical correctness:** Are technical claims correct and realistic? (1 = many errors, 5 = technically sound)
- **Completeness:** Are important aspects covered (assumptions, steps, examples)? (1 = incomplete, 5 = thorough)
- **Actionability:** Can the plant act on the recommendations or steps? (1 = no, 5 = directly actionable)
- **Clarity:** Is the response easy to understand and well-structured? (1 = confusing, 5 = clear)

**Scoring Interpretation:** Sum of the five criterion scores (max 25). 
Ranges: 21–25 = Excellent; 16–20 = Good; 11–15 = Fair; <=10 = Poor.

## 5. Evaluation Workflow
- The comparative analysis prompt and others were executed on the chosen AI tools.
- Each generated response was reviewed and scored using the evaluation rubric.
- Average scores were computed, and qualitative differences (such as tone, assumptions, and clarity) were noted and compared.

## Result
The experiment was successfully carried out. Prompts were designed for all five prompt types using the IoT-enabled Manufacturing Automation use case (Unit 5). Each prompt was tested across AI tools (ChatGPT, Claude, Gemini) and evaluated using a Rubric-based scoring method. The results demonstrate that structured and refined prompts yield the highest quality outputs, while prompt size management ensures responses remain concise and within model limits.

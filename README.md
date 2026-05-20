# EXP 4 Generate the Prompt and eveluate that for following prompt types - Comparative Analysis Prompt Experiential Perspective Prompt - Everyday Functioning Prompts - Universal Prompt Structures Prompt Refinements- Prompt Size Limitations.

## DATE: 19-05-2026

## REGISTER NUMBER: 212223040002

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

* Improve production efficiency by ~30%.
* Reduce machinery downtime via predictive maintenance.
* Enable real-time monitoring and remote control of systems.
* Reduce energy consumption through process optimization.

### 2. Prompt patterns and concrete example prompts (manufacturing use case)

#### Comparative Analysis Prompt

* **Purpose:** Compare approaches, trade-offs, or tools.
* **Prompt:** "Compare a rule-based threshold alerting system with a machine-learning-based predictive maintenance model for detecting bearing failures in an assembly line. Discuss accuracy, false-positive risk, implementation complexity, data needs, and maintenance cost. Recommend which to choose for a medium-sized electronics plant and why."

#### Experiential Perspective Prompt

* **Purpose:** Elicit first-person experience or role-based insights.
* **Prompt:** "From the perspective of a plant floor maintenance engineer, describe the daily benefits and challenges of using an AI-driven predictive maintenance dashboard connected to IoT sensors. Include how it changes your workflow and the types of alerts you would trust most."

#### Everyday Functioning Prompt

* **Purpose:** Explain practical, everyday uses and impact.
* **Prompt:** "Explain how an IoT-enabled energy management system reduces energy consumption on a factory floor. Give three concrete examples of automated actions it might take and the expected energy savings for each."

#### Universal Prompt Structures

* **Purpose:** Reusable templates for clarity and completeness.
* **Template:** "Explain [concept] in simple terms, list assumptions, provide a step-by-step implementation outline, and include a short example."
* **Prompt:** "Explain 'edge anomaly detection' in simple terms, list assumptions, provide a step-by-step implementation outline for a conveyor-belt vibration sensor, and include a short example of an anomaly and the expected alert."

#### Prompt Size Limitations

* **Purpose:** Manage long outputs or large inputs.
* **Prompt (chunking):** "Summarize the attached 6000-word maintenance log into a 300-word incident summary. Start with the first 1500 words and wait for confirmation to continue."
* **Prompt (limits):** "List 20 possible sensor types used in predictive maintenance, grouped by function; return 5 groups at a time."

---

## 3. Implementation and Model Responses

The designed prompts were tested on ChatGPT, Gemini, and Claude. Below are the verbose, direct responses recorded during the experiment.

### Comparative Analysis Prompt

**Prompt:** "Compare a rule-based threshold alerting system with a machine-learning-based predictive maintenance model for detecting bearing failures in an assembly line. Discuss accuracy, false-positive risk, implementation complexity, data needs, and maintenance cost. Recommend which to choose for a medium-sized electronics plant and why."

#### Responses:

**ChatGPT:**

> **Comparison of Systems for Bearing Failure Detection**
> **1. Accuracy & False-Positive Risk:**
> * **Rule-Based:** Relies on hard-coded limits (e.g., if vibration > 5mm/s, trigger alert). Accuracy is decent for catastrophic failures but poor for early degradation. False positives are very high because normal operational spikes (like a heavy load shifting) can easily breach the static threshold.
> * **ML-Based:** Learns the normal operating baseline for each specific bearing. It can detect subtle, compound anomalies (e.g., slight temperature rise combined with a specific vibration frequency). Accuracy is much higher, and false-positive risk is significantly lower once properly trained.
> 
> 
> **2. Implementation Complexity & Data Needs:**
> * **Rule-Based:** Extremely low complexity. You only need basic sensor data (current value) and a PLC or simple SCADA system to trigger the alarm. No historical data is required to start.
> * **ML-Based:** High complexity. Requires a robust data pipeline, historical labeled data (examples of past failures and normal states), feature engineering, and model training. You need data scientists or specialized IoT software platforms.
> 
> 
> **3. Maintenance Cost:**
> * **Rule-Based:** Low upfront cost, but high hidden costs due to unnecessary downtime from false alarms and catastrophic failures that occur below the threshold.
> * **ML-Based:** High upfront cost for software and setup. However, long-term maintenance costs drop drastically because you only replace bearings right before they fail (maximizing lifespan) and avoid unplanned downtime.
> 
> 
> **Recommendation for a Medium-Sized Electronics Plant:**
> I recommend a **Hybrid/Phased Approach**, starting with the **Rule-Based System** while simultaneously gathering data to train an **ML-Based Model**. A medium electronics plant likely doesn't have the massive historical datasets ready on day one. By setting conservative rule-based thresholds immediately, you prevent catastrophic failures. Meanwhile, you capture the sensor data in a historian database. After 3-6 months, once enough baseline data and minor wear patterns are recorded, you can transition to the ML predictive model. This balances immediate protection with long-term efficiency, keeping initial implementation costs manageable.

**Gemini:**

> Here is a detailed comparison between rule-based and machine-learning (ML) approaches for detecting bearing failures:
> **Accuracy and False Positives**
> Rule-based systems are rigid. They operate on simple "if-then" logic. While they accurately catch severe, late-stage failures, they struggle with the nuance of early wear. Consequently, they generate a high volume of false positives during normal machine variations (like start-up vibrations), leading to alert fatigue.
> ML models excel here. By analyzing multidimensional data (vibration, acoustics, temperature simultaneously), they identify the unique degradation signature of a bearing long before failure, drastically reducing false alarms and improving early-warning accuracy.
> **Implementation and Data Needs**
> A rule-based system can be deployed in a day. It requires zero historical data—just the manufacturer's recommended tolerances.
> An ML predictive model requires a mature data infrastructure. You need months of clean, high-frequency historical data to train the algorithms, plus ongoing cloud or edge computing resources to run the inferences.
> **Cost Profile**
> Rule-based systems are cheap to install but expensive operationally (due to reactive maintenance and false-alarm downtime). ML systems require significant capital expenditure (CapEx) for sensors, software, and integration, but deliver high return on investment (ROI) by optimizing maintenance schedules (OpEx).
> **Recommendation**
> For a **medium-sized electronics plant**, I recommend starting with a **Machine-Learning Model offered as a "Plug-and-Play" SaaS solution** (like those from Augury or similar vendors), rather than building an ML model from scratch. Electronics plants have highly calibrated, sensitive assembly lines where sudden bearing failure can ruin delicate PCB batches. The cost of false positives (stopping a highly synchronized line unnecessarily) is too high for a simple rule-based system. By using a pre-packaged ML vendor, the plant gets the accuracy of ML without the immense implementation complexity and data science overhead of building it in-house.

**Claude:**

> Comparing these two maintenance paradigms involves evaluating trade-offs between simplicity and predictive power.
> **Rule-Based Threshold System**
> * **Accuracy:** Moderate. Good at catching absolute failures but misses gradual degradation.
> * **False-Positive Risk:** High. Static thresholds do not account for variable operating conditions (e.g., changes in ambient temperature or line speed).
> * **Implementation Complexity:** Low. Can be configured directly on edge PLCs using standard control logic.
> * **Data Needs:** Minimal. Only requires real-time streaming data.
> * **Maintenance Cost:** Low setup, but high secondary costs due to reactive maintenance and unnecessary line stoppages.
> 
> 
> **ML-Based Predictive Model**
> * **Accuracy:** High. Identifies complex, multivariate patterns indicative of micro-wear (e.g., specific harmonic frequencies in vibration data).
> * **False-Positive Risk:** Low, provided the model is trained on a diverse operational dataset.
> * **Implementation Complexity:** High. Requires data pipelines, model training, validation, and MLOps for retraining.
> * **Data Needs:** Extensive. Requires large volumes of historical, labeled telemetry data encompassing both healthy and degraded states.
> * **Maintenance Cost:** High initial investment; significantly lower ongoing operational costs due to optimized part lifespans.
> 
> 
> **Recommendation:**
> A medium-sized electronics plant should adopt an **incremental ML strategy**. Electronics manufacturing requires high precision, meaning bearing wear can cause subtle product defects long before the bearing fully seizes. A rule-based system will miss these micro-vibrations. However, building custom ML is too heavy for a mid-sized facility. Therefore, the plant should deploy edge-AI sensors equipped with pre-trained anomaly detection models. This provides the nuanced accuracy of ML to protect product quality, without the massive data engineering burden of a ground-up build.

---

### Experiential Perspective Prompt

**Prompt:** "From the perspective of a plant floor maintenance engineer, describe the daily benefits and challenges of using an AI-driven predictive maintenance dashboard connected to IoT sensors. Include how it changes your workflow and the types of alerts you would trust most."

#### Responses:

**ChatGPT:**

> As a plant floor maintenance engineer, my day used to start with a clipboard, a flashlight, and a lot of walking. I'd physically check motors, listen to gearboxes, and hope I didn't miss anything. Now, with the AI predictive maintenance dashboard, my entire workflow has flipped from reactive firefighting to proactive planning.
> **Daily Benefits:**
> The biggest benefit is knowing exactly what needs my attention before I even finish my morning coffee. Instead of waiting for a machine operator to radio in a breakdown, the dashboard gives me a prioritized list. Yesterday, the system flagged a 15% increase in heat and vibration on the Line 4 exhaust fan bearing, predicting a failure in about 72 hours. I was able to stage the replacement parts and schedule the swap during the 3 AM shift change. Zero production time was lost. It makes me look like a wizard to the plant manager.
> **Daily Challenges:**
> It's not perfect. The biggest headache is "alert fatigue" during the model's learning phases or when environmental conditions change drastically (like when the plant gets incredibly hot in the summer). Sometimes the AI flags an "anomaly" that is just a machine running a slightly heavier product batch. It takes time to train the system to understand context.
> **Alerts I Trust:**
> I don't trust the vague "Warning: Anomaly Detected" alerts. The alerts I actually trust—and act on immediately—are the ones that show me the math. I want an alert that says, "High-frequency vibration detected on Z-axis servo. 85% match to previous bearing spalling failure. Estimated time to failure: 4 days." When the AI cross-references current sensor data with historical failure signatures and gives me a concrete timeline, that’s when it becomes an indispensable tool on the floor.

**Gemini:**

> Look, as a maintenance engineer, I’m the guy they yell at when the line stops. For the last decade, my job was basically running from one smoking motor to the next. This new AI dashboard hooked up to the IoT sensors has genuinely changed how I sleep at night, but it comes with its own set of headaches.
> **How it changed my workflow:**
> I used to do calendar-based preventative maintenance—changing perfectly good belts and bearings just because it had been 6 months. It was a massive waste of time. Now, my morning starts at the terminal. I check the health scores of the top 20 critical assets. If a pump shows a green 98% health score, I don't touch it. My workflow is now surgically targeted. I only go to the machines the AI tells me are acting up.
> **The Challenges:**
> The main challenge is the trust gap. When you have a 30-year veteran mechanic, and an iPad tells him a machine sounding perfectly fine is going to fail tomorrow, there's friction. We also struggle with sensor calibration; if a sensor gets knocked loose by a forklift, the AI panics and throws critical errors, sending us on wild goose chases.
> **What I Trust:**
> I trust multi-variable alerts. If the dashboard tells me *just* the vibration is high, I'm skeptical—maybe a bolt is loose. But if the alert shows me a graph where vibration is spiking, the motor is drawing 15% more amperage than normal, *and* the surface temperature has climbed 10 degrees in an hour? I trust that completely. I'm locking that machine out and getting my tools.

**Claude:**

> From the floor perspective, transitioning to an AI-driven IoT dashboard is like suddenly being able to see through the metal casings of our equipment.
> **The Shift in Workflow (The Benefits):**
> Before this system, my workflow was defined by PMs (Preventative Maintenance schedules) and emergency work orders. I spent 40% of my week greasing bearings that didn't need grease. Now, my workflow is analytical. The AI ranks the equipment by 'Probability of Failure.' It allows me to bundle my work. If I have to shut down Line B to fix a flagged motor, I can look at the dashboard and see if anything else on Line B is showing early wear, and fix it all at once. We've dropped our unplanned downtime by almost 35% in six months.
> **The Daily Challenges:**
> The hardest part is data overload and tuning the system. In an industrial environment, things get bumped, covered in dust, or hit with water jets. A dirty temperature sensor will feed bad data to the AI, which then triggers a false alarm. It takes a lot of daily diligence just to maintain the sensors so the AI can do its job.
> **Trusted Alerts:**
> I trust alerts that provide "Root Cause Indicators" alongside the warning. If an alert pops up saying "Motor Anomaly," I might ignore it. But if it says, "Stator winding temperature critical. Pattern indicates restricted cooling airflow," I trust it because it gives me a logical mechanical reason that I can go physically verify. I also heavily trust alerts that have a confidence score of 90% or higher based on historical baselines.

---

### Everyday Functioning Prompt

**Prompt:** "Explain how an IoT-enabled energy management system reduces energy consumption on a factory floor. Give three concrete examples of automated actions it might take and the expected energy savings for each."

#### Responses:

**ChatGPT:**

> An IoT-enabled energy management system (EMS) acts as the central brain for a factory's power usage. By connecting smart meters, environmental sensors, and machine PLCs to a centralized network, the EMS continuously monitors where and how energy is being consumed in real-time. Instead of waiting for a monthly utility bill, the system identifies inefficiencies instantly and uses automation logic to adjust equipment states without human intervention.
> Here are three concrete examples of automated actions and their expected savings:
> 1. **Dynamic HVAC Zoning and Set-back:**
> * *Action:* IoT occupancy and thermal sensors detect that a specific packaging zone on the floor is idle during the second shift. The EMS automatically adjusts the VAV (Variable Air Volume) boxes to reduce airflow and widens the temperature deadband (e.g., allowing the room to get slightly warmer in summer) for that specific zone.
> * *Expected Savings:* ~10–15% reduction in HVAC energy consumption for the affected zones.
> 
> 
> 2. **Peak Load Shedding via Motor Staggering:**
> * *Action:* Factories are charged exorbitant fees for "peak demand" (the maximum power drawn at any one time). When the EMS predicts that the facility is about to hit a peak threshold, it automatically staggers the start-up sequence of heavy equipment, such as large compressors or crushers, delaying them by just a few seconds or minutes so they don't draw startup current simultaneously.
> * *Expected Savings:* ~15–20% reduction in peak demand utility charges.
> 
> 
> 3. **Automated Compressed Air Optimization:**
> * *Action:* Compressed air systems often run continuously, bleeding energy. The EMS connects to pressure sensors along the pneumatic lines. If machines utilizing air are idled for lunch or a changeover, the system automatically dials down the variable frequency drive (VFD) on the main compressor to match the exact, reduced pressure requirement.
> * *Expected Savings:* ~20–30% on the compressor's energy draw, which is typically one of the highest energy consumers in a plant.
> 
> 
> 
> 

**Gemini:**

> Factory floors are notoriously energy-intensive, often wasting power by running systems at 100% capacity regardless of actual production needs. An IoT energy management system changes this by acting as a highly attentive, automated supervisor. It uses a network of smart sensors to gather granular data—measuring temperature, machine activity, and power draw—and uses algorithms to make micro-adjustments in real-time to eliminate waste without slowing down production.
> Three concrete examples of this automation include:
> 1. **Adaptive Lighting Control:**
> * **Action:** High-bay LED fixtures equipped with IoT motion and ambient light sensors talk to the system. During a bright day, the system dims lights near the skylights. In warehouse aisles, lights automatically drop to 10% output until a forklift enters the aisle, instantly ramping up to 100%.
> * **Expected Savings:** 40% to 60% reduction in lighting-related energy costs.
> 
> 
> 2. **Chiller and Boiler Optimization:**
> * **Action:** Process cooling requires massive energy. The EMS monitors the current production load and pulls in local weather forecast data. If it knows the outside temperature is dropping rapidly, it automatically adjusts the chiller setpoints, allowing the system to use "free cooling" from the ambient air rather than working the mechanical compressors at full tilt.
> * **Expected Savings:** 12% to 18% savings on process heating and cooling.
> 
> 
> 3. **Idle State Machine Shutdown:**
> * **Action:** IoT current transformers monitor the power draw of CNC machines or conveyors. If a machine remains in a "ready but not operating" state for more than 15 minutes (e.g., waiting for parts), the EMS automatically sends a signal to power down auxiliary systems like coolant pumps and chip conveyors until the operator is ready.
> * **Expected Savings:** 5% to 10% overall machine energy consumption per shift.
> 
> 
> 
> 

**Claude:**

> An IoT-enabled energy management system reduces consumption by bridging the gap between facility infrastructure (lights, HVAC) and production equipment. It replaces static schedules with dynamic, data-driven automation. By continuously aggregating data from connected power meters and machine controllers, the system identifies operational waste—energy being used when no value is being created—and executes programmatic rules to dial back power usage safely.
> Here are three examples of automated actions:
> 1. **Variable Frequency Drive (VFD) Process Matching:**
> * **Action:** In a liquid processing plant, an IoT flow sensor detects that production volume has temporarily decreased. The EMS immediately communicates with the VFDs controlling the main pump motors, slowing the pump RPMs to exactly match the new flow requirement rather than using throttling valves to restrict flow while the pump runs at full speed.
> * **Expected Savings:** Due to the affinity laws of pumps, a 20% reduction in motor speed can yield a ~50% reduction in motor energy consumption.
> 
> 
> 2. **Automated Exhaust Fan Sequencing:**
> * **Action:** Welding or painting bays have massive exhaust fans. Instead of running them constantly, IoT air quality sensors monitor VOC (Volatile Organic Compounds) and particulate levels. The EMS automatically turns on or speeds up the fans only when the air quality drops below a safe threshold, shutting them off when the air is cleared.
> * **Expected Savings:** ~30–40% reduction in ventilation energy costs.
> 
> 
> 3. **Shift-Synchronized Equipment Spin-Down:**
> * **Action:** At the end of a shift, instead of relying on operators to manually shut down every subsystem, the EMS links with the production schedule API. Once the final product passes the end-of-line IoT optical sensor, the system initiates a staggered, automated spin-down of conveyors, glue heaters, and localized lighting.
> * **Expected Savings:** ~8–12% overall facility energy reduction by eliminating after-hours "vampire" power draw.
> 
> 
> 
> 

---

### Universal Prompt Structures

**Prompt:** "Explain 'edge anomaly detection' in simple terms, list assumptions, provide a step-by-step implementation outline for a conveyor-belt vibration sensor, and include a short example of an anomaly and the expected alert."

#### Responses:

**ChatGPT:**

> **Explanation in Simple Terms:**
> "Edge anomaly detection" means putting a small, smart computer right next to a piece of machinery (on the "edge" of the network) to constantly monitor it. Instead of sending all the raw data to a distant cloud server to be analyzed, the small computer learns what "normal" looks like and instantly raises a flag if the machine starts acting strangely.
> **Assumptions:**
> 1. The machine (conveyor belt) operates in a relatively consistent manner so a "normal" baseline can be established.
> 2. The edge device has sufficient processing power to run lightweight anomaly detection algorithms (like a micro-autoencoder).
> 3. There is a secure, low-latency local network (like Wi-Fi or LoRaWAN) to transmit alerts to maintenance staff.
> 
> 
> **Step-by-Step Implementation Outline (Conveyor Belt Vibration Sensor):**
> 1. **Hardware Installation:** Physically mount a 3-axis IoT accelerometer (vibration sensor) securely to the primary drive motor housing of the conveyor.
> 2. **Data Collection (Training Phase):** Run the conveyor under normal load conditions for two weeks. The edge device records this baseline vibration telemetry locally.
> 3. **Model Training:** Use edge AI software to process the baseline data, training a lightweight machine learning model to recognize the normal frequency and amplitude patterns.
> 4. **Deployment (Inference Phase):** Activate the model on the edge device. It now constantly compares real-time vibration data against its learned baseline.
> 5. **Alert Configuration:** Set rules in the dashboard—if an anomaly score exceeds 85% for more than 5 minutes, trigger a notification.
> 
> 
> **Short Example:**
> * **Anomaly:** A small piece of debris gets caught under the conveyor belt, causing the drive motor shaft to slightly misalign. The sensor detects a sudden, sustained spike in high-frequency vibration along the Z-axis that doesn't match the baseline.
> * **Expected Alert:** A push notification sent to the maintenance engineer's phone: *"Priority Alert: Conveyor Drive Motor 3. High-frequency anomaly detected (92% deviation). Probable cause: Mechanical misalignment. Inspect immediately to prevent bearing damage."*
> 
> 

**Gemini:**

> **What is Edge Anomaly Detection?**
> Imagine having a highly trained mechanic listening to your car engine 24/7, sitting right under the hood. Edge anomaly detection does exactly this using software. It processes sensor data locally—directly on the machine (the "edge")—to instantly spot irregular behavior (anomalies) without needing to send all that heavy data back and forth to a central cloud server.
> **Assumptions:**
> * The vibration sensor outputs high-quality, noise-free data.
> * The edge micro-controller (e.g., Raspberry Pi or industrial edge gateway) has continuous power.
> * Maintenance teams have a dashboard or mobile app ready to receive the alerts.
> 
> 
> **Implementation Outline:**
> * **Step 1: Mount the Sensor.** Attach the vibration sensor directly to the most critical mechanical point (usually the bearing housing on the conveyor's main roller).
> * **Step 2: Baseline Capture.** Run the conveyor for several days to capture a "healthy state" dataset across different load weights.
> * **Step 3: Edge Model Deployment.** Push a pre-compiled, lightweight statistical model (e.g., K-Means clustering) to the sensor's microcontroller.
> * **Step 4: Real-Time Monitoring.** The sensor analyzes the incoming vibrations millisecond by millisecond, calculating an "anomaly score."
> * **Step 5: Alert Integration.** Connect the edge gateway to the plant's SCADA or maintenance software to route alerts to the right personnel.
> 
> 
> **Example:**
> * **Anomaly:** A bearing inside the conveyor roller starts to dry out, causing a microscopic grinding. This creates a new, high-pitched harmonic vibration that has never been seen in the baseline data.
> * **Expected Alert:** Dashboard flashes red with: *"Warning: Novel harmonic frequency detected on Roller 7. Anomaly Score: Critical. Suggestion: Lubricate bearing assembly within 24 hours."*
> 
> 

**Claude:**

> **Edge Anomaly Detection Explained:**
> Edge anomaly detection is the process of analyzing data directly at the source (the sensor on the machine) to identify unusual patterns, rather than transmitting all raw data to a central cloud for analysis. It acts as a localized, intelligent filter that only speaks up when something goes wrong, saving bandwidth and enabling split-second reactions.
> **Assumptions:**
> * The normal operating state of the conveyor is predictable and repeatable.
> * The environment doesn't introduce massive external vibrations (like heavy stamping presses right next to the conveyor) that would skew the data.
> * The plant network allows outbound traffic from the edge device to send MQTT alert messages.
> 
> 
> **Implementation Outline for Conveyor Vibration Sensor:**
> 1. **Sensor Placement:** Affix the smart vibration node to the tail pulley bearing block.
> 2. **Telemetry Ingestion:** Configure the node to sample vibration on X, Y, and Z axes at 1000Hz.
> 3. **Baseline Generation:** Allow the device to run in "learning mode" for 7 days to map the normal operational envelope (amplitudes and frequencies).
> 4. **Threshold & Model Activation:** Lock the baseline and activate the local anomaly algorithm (like Isolation Forest) to score deviations from the norm.
> 5. **Action Workflow Setup:** Configure the edge device to trigger a local relay (to stop the belt if critical) and send a payload to the cloud maintenance system.
> 
> 
> **Short Example:**
> * **Anomaly:** The conveyor belt begins to fray and catch on a guard rail on every revolution. The sensor detects a rhythmic, repeating impact spike every 4 seconds.
> * **Expected Alert:** SMS sent to shift supervisor: *"Anomaly Detected - Conveyor 1 Tail Pulley. Rhythmic impact signature detected. Risk of belt tear. Visual inspection required."*
> 
> 

---

### Prompt Size Limitations

**Prompt:** "Summarize the attached 6000-word maintenance log into a 300-word incident summary. Start with the first 1500 words and wait for confirmation to continue."

#### Responses:

**ChatGPT:**

> **Summary of Part 1 (First 1500 Words):**
> The initial section of the maintenance log details a recurring issue on Assembly Line 3, specifically concerning the main spindle motor. Over the first week of the month, operators recorded multiple minor temperature warnings, noting that the motor casing was running approximately 15°C hotter than the established baseline.
> Maintenance technicians responded by performing routine visual inspections and topping up the lubrication reserves, assuming the alerts were caused by minor friction or sensor drift. However, the logs indicate that the temperature reduction was only temporary, usually lasting less than four hours before returning to the elevated state. By day five, the temperature spikes began correlating with operator reports of a faint "whining" noise during heavy load cycles. No production was halted during this period, but a work order was opened to monitor the asset.
> ---
> 
> 
> *I have processed the first 1500 words. Please reply "continue" to proceed with the next section of the log.*

**Gemini:**

> **Incident Summary: Log Segment 1 (Words 1-1500)**
> Based on the first portion of the provided log, the primary incident involves the progressive deterioration of the primary cooling loop on Injection Molder #4.
> **Key Events:**
> * **Days 1-3:** SCADA system registered a slow but steady drop in coolant flow pressure (down 8%). Operators bypassed the initial warnings, attributing them to a known software glitch.
> * **Day 4:** Maintenance was called due to excessive heat radiating from the hydraulic power unit. Technicians discovered a partially clogged inline filter.
> * **Day 5:** The filter was cleaned, but pressure only recovered to 95% of normal. The log notes growing concern over metallic particulate found in the filter mesh, suggesting internal pump wear rather than external contamination.
> 
> 
> The situation remains unresolved in this segment, with the machine operating under close manual supervision.
> *Awaiting your confirmation to process the next segment of the text.*

**Claude:**

> **Maintenance Log Summary (First 1500 words)**
> This initial segment of the log outlines the early stages of an equipment failure on the automated packaging line.
> The timeline begins with intermittent alarms from the pneumatic sorting arms. Sensors indicated a delay in the arm's extension time (lagging by 400 milliseconds), causing minor jams. Initial troubleshooting focused on the air compressor pressure, which was found to be within normal limits.
> The focus then shifted to the directional control valves. Technicians noted that the valves on Zone B were sluggish. A temporary fix was applied using pneumatic solvent, which cleared the immediate jams, but the logs highlight that the root cause was not definitively identified. By the end of this 1500-word section, the line was running at 80% capacity to prevent further jams, pending a deeper inspection during the weekend shutdown.
> ---
> 
> 
> *I have paused processing. Please confirm when you would like me to analyze and summarize the next chunk of the log.*

## 4. Evaluation Rubric

The responses were evaluated based on the following criteria (each scored 1–5):

* **Relevance:** Does the response address the prompt and manufacturing context? (1 = off-topic, 5 = fully on-target)
* **Accuracy / Technical correctness:** Are technical claims correct and realistic? (1 = many errors, 5 = technically sound)
* **Completeness:** Are important aspects covered (assumptions, steps, examples)? (1 = incomplete, 5 = thorough)
* **Actionability:** Can the plant act on the recommendations or steps? (1 = no, 5 = directly actionable)
* **Clarity:** Is the response easy to understand and well-structured? (1 = confusing, 5 = clear)

**Scoring Interpretation:** Sum of the five criterion scores (max 25).
Ranges: 21–25 = Excellent; 16–20 = Good; 11–15 = Fair; <=10 = Poor.

## 5. Evaluation Workflow

* The comparative analysis prompt and others were executed on the chosen AI tools.
* Each generated response was reviewed and scored using the evaluation rubric.
* Average scores were computed, and qualitative differences (such as tone, assumptions, and clarity) were noted and compared.

## Result

The experiment was successfully carried out. Prompts were designed for all five prompt types using the IoT-enabled Manufacturing Automation use case (Unit 5). Each prompt was tested across AI tools (ChatGPT, Claude, Gemini) and evaluated using a Rubric-based scoring method. The results demonstrate that structured and refined prompts yield the highest quality outputs, while prompt size management ensures responses remain concise and within model limits.

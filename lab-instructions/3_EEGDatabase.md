# 3-EEG Database

## Table of Contents

1. [3.1 Behavioral Tasks](#31-behavioral-tasks)
   - [Experimental Paradigms](#experimental-paradigms)
2. [3.2 EEG Structure](#32-eeg-structure)
   - [3.2.1 Description of Free Recall `events.mat` Fields](#321-description-of-free-recall-eventsmat-fields)
   - [3.2.2 Subject Example Behavioral Results](#322-subject-example-behavioral-results)
3. [3.3 Behavioral Analyses (Exercises)](#33-behavioral-analyses)
   - [3.3.1 Calculating Recall Probability](#331-calculating-recall-probability)
   - [3.3.2 Generating Serial Position Curve](#332-generating-serial-position-curve)
   - [3.3.3 Generating a Lag-Conditional Response Probability (CRP) Curve](#333-generating-a-lag-conditional-response-probability-crp-curve)
   - [3.3.4 Electrophysiological Analyses](#334-electrophysiological-analyses)
     - [3.3.4.1 Plotting Raw Voltage](#3341-plotting-raw-voltage)
     - [3.3.4.2 Plotting Event-Related Potential (ERP)](#3342-plotting-event-related-potential-erp)
   - [3.3.5 Analyzing AR Data](#335-analyzing-ar-data)
   - [3.3.6 Filtering SR Data](#336-filtering-sr-data)

---

## 3.1 Behavioral Tasks

### General Task Descriptions

- **FR Task**:  
  In a free-recall task, participants study a list of words for later recall. Words are presented one at a time, and participants attempt to recall them in any order after presentation. This task allows the analysis of memory search mechanisms, examining factors like the order of recall and total recall count.

- **AR Task**:  
  Associative memory tasks explore the ability to encode relationships between items and retrieve one item using another as a cue. These tasks focus on association and recall dimensions, often involving encoding pairs of words and later identifying them as "new," "rearranged," or "same."

- **SR Task**:  
  Serial recall tasks test memory for sequentially ordered materials. Participants study an ordered list and are tasked with recalling items in the same sequence. This task examines encoding and retrieval of ordered sequences.

[Kahana, M. J. (2012). *Foundations of human memory*. Oxford University Press.]

---

### Experimental Paradigms

- **FR1**: Verbal free recall paradigm for the RAM project.
- **FR2**: Similar to FR1 but includes stimulation on random words within each list.
- **pyFR**: A Python-based free recall paradigm with minor differences in list length, recall duration, and number of lists.
- **pyFR stim**: Similar to pyFR but with stimulation during the entire encoding or recall period.
- **AccRew**: A reward processing task.
- **PS2/PS3**: Stimulation tasks with varying parameters like amplitude and frequency, not tied to behavioral tasks.
- **catFR1**: FR1 with category groupings (e.g., Animals, Fruits, Tools).
- **catFR2**: Similar to catFR1 but with added stimulation.
- **YC1**: Spatial navigation task.
- **YC2**: Similar to YC1 but with stimulation.
- **PAL1**: Paired-associate task requiring recall of one word from a pair.
- **PAL2**: Similar to PAL1 but with added stimulation.
- **AR1**: Associative recognition task (see AR Task).
- **AR stim**: Associative recognition with stimulation.
- **SR**: Verbal serial recall paradigm.

---

## 3.2 EEG Structure

### BehData Folder

The `BehData` folder contains subject-specific data. Each folder corresponds to a unique subject ID.

#### Example Subjects in `BehData` Folder

1. **UT014**
   - Participated in: `acc reward`, `FR1`, `PS`, `pyFR stim`, and `YC1`.
   - Relevant folders:
     - **behavioral**: Contains all behavioral data. For example:
       - `events.mat`: Contains all events for `FR1`. Each row represents a specific event (e.g., word presentation, vocal response).
       - Session-specific folders (e.g., `session 0`, `session 1`) contain session-wise `events.mat` files.
     - **eeg.noreref**: Raw, non-referenced EEG files.
     - **eeg.reref**: EEG files re-referenced to the weighted average of all other electrodes.

2. **UT104**
   - Data structured similarly to UT014.

3. **UT340**
   - Data structured similarly to UT014.

---

### 3.2.1 Description of Free Recall `events.mat` Fields

The `events.mat` files include structured data for Free Recall tasks. Key fields:

- **`subject`**: Unique subject identifier (e.g., `UT014`).
- **`session`**: Session number.
- **`list`**: List number within the session.
- **`serialpos`**: Position of the word in the list.
- **`type`**: Type of event (e.g., "WORD", "REC WORD").
- **`item`**: Word presented or recalled.
- **`itemno`**: Word ID from the word pool.
- **`recalled`**: Recall status (1: recalled, 0: not recalled).
- **`intrusion`**: Intrusion type (0: correct, >0: PLI, -1: ELI).
- **`eegfile`**: Corresponding EEG file.
- **`set`**: EEG time offset in milliseconds.

---

### 3.2.2 Subject Example Behavioral Results

1. **Successfully Recalled Word**:  
   Example for UT014:
   ```plaintext
   subject: 'UT014'
   session: 0
   list: 1
   serialpos: 4
   type: 'WORD'
   item: 'HORSE'
   itemno: 128
   recalled: 1
   rectime: 14318
   intrusion: 0

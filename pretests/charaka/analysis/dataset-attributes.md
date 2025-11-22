# Dataset Attributes

This document lists all attributes/features provided by each of the four datasets.

---

## 1. UCI Student Performance Dataset

**Files**: `student-mat.csv`, `student-por.csv`  
**Total Attributes**: 33

### Demographics
- `school` - student's school (binary: "GP" or "MS")
- `sex` - student's sex (binary: "F" - female or "M" - male)
- `age` - student's age (numeric: from 15 to 22)
- `address` - student's home address type (binary: "U" - urban or "R" - rural)

### Family Background
- `famsize` - family size (binary: "LE3" - less or equal to 3 or "GT3" - greater than 3)
- `Pstatus` - parent's cohabitation status (binary: "T" - living together or "A" - apart)
- `Medu` - mother's education (numeric: 0 - none, 1 - primary education, 2 - 5th to 9th grade, 3 - secondary education, 4 - higher education)
- `Fedu` - father's education (numeric: 0 - none, 1 - primary education, 2 - 5th to 9th grade, 3 - secondary education, 4 - higher education)
- `Mjob` - mother's job (nominal: "teacher", "health", "services", "at_home", "other")
- `Fjob` - father's job (nominal: "teacher", "health", "services", "at_home", "other")
- `guardian` - student's guardian (nominal: "mother", "father", "other")

### Academic Factors
- `reason` - reason to choose this school (nominal: "home", "reputation", "course", "other")
- `traveltime` - home to school travel time (numeric: 1 - <15 min., 2 - 15 to 30 min., 3 - 30 min. to 1 hour, 4 - >1 hour)
- `studytime` - weekly study time (numeric: 1 - <2 hours, 2 - 2 to 5 hours, 3 - 5 to 10 hours, 4 - >10 hours)
- `failures` - number of past class failures (numeric: n if 1<=n<3, else 4)
- `schoolsup` - extra educational support (binary: yes or no)
- `famsup` - family educational support (binary: yes or no)
- `paid` - extra paid classes within the course subject (binary: yes or no)
- `activities` - extra-curricular activities (binary: yes or no)
- `nursery` - attended nursery school (binary: yes or no)
- `higher` - wants to take higher education (binary: yes or no)
- `internet` - Internet access at home (binary: yes or no)

### Lifestyle & Behavior
- `romantic` - with a romantic relationship (binary: yes or no)
- `famrel` - quality of family relationships (numeric: from 1 - very bad to 5 - excellent)
- `freetime` - free time after school (numeric: from 1 - very low to 5 - very high)
- `goout` - going out with friends (numeric: from 1 - very low to 5 - very high)
- `Dalc` - workday alcohol consumption (numeric: from 1 - very low to 5 - very high)
- `Walc` - weekend alcohol consumption (numeric: from 1 - very low to 5 - very high)
- `health` - current health status (numeric: from 1 - very bad to 5 - very good)
- `absences` - number of school absences (numeric: from 0 to 93)

### Target Variables (Grades)
- `G1` - first period grade (numeric: from 0 to 20)
- `G2` - second period grade (numeric: from 0 to 20)
- `G3` - final grade (numeric: from 0 to 20, output target)

---

## 2. xAPI-Edu-Data Dataset

**File**: `xAPI-Edu-Data.csv`  
**Total Attributes**: 17

### Demographics
- `gender` - student's gender
- `NationalITy` (Nationality) - student's nationality
- `PlaceofBirth` - place of birth

### Academic Context
- `StageID` - educational stage ID
- `GradeID` - grade level ID
- `SectionID` - section ID
- `Topic` - course topic
- `Semester` - semester information
- `Relation` - relationship/guardian type

### Behavioral Metrics
- `raisedhands` - number of times student raised hands
- `VisITedResources` (VisitedResources) - number of resources visited
- `AnnouncementsView` - number of announcements viewed
- `Discussion` - participation in discussions

### Parental Involvement
- `ParentAnsweringSurvey` - whether parent answered survey (yes/no)
- `ParentschoolSatisfaction` - parent's satisfaction with school

### Other
- `StudentAbsenceDays` - student absence days (categorical: "Under-7", "Above-7")

### Target Variable
- `Class` - performance class (nominal: "L" - Low, "M" - Medium, "H" - High)

---

## 3. Open University Learning Analytics Dataset (OULAD)

**Files**: Multiple CSV files  
**Total Attributes**: 43 (across multiple tables)

### courses.csv
- `code_module` - code name of the module (identifier)
- `code_presentation` - code name of the presentation (year + "B" for February or "J" for October)
- `length` - length of the module-presentation in days

### assessments.csv
- `code_module` - identification code of the module
- `code_presentation` - identification code of the presentation
- `id_assessment` - identification number of the assessment
- `assessment_type` - type of assessment
- `date` - final submission date (days since start of module-presentation)
- `weight` - weight of the assessment in %

### vle.csv
- `id_site` - identification number of the material
- `code_module` - identification code for module
- `code_presentation` - identification code of presentation
- `activity_type` - role associated with the module material
- `week_from` - week from which the material is planned to be used
- `week_to` - week until which the material is planned to be used

### studentInfo.csv
- `code_module` - identification code for a module
- `code_presentation` - identification code of the presentation
- `id_student` - unique identification number for the student
- `gender` - student's gender
- `region` - geographic region where the student lived
- `highest_education` - highest student education level on entry
- `imd_band` - Index of Multiple Deprivation band
- `age_band` - band of the student's age
- `num_of_prev_attempts` - number of times the student has attempted this module
- `studied_credits` - total number of credits for modules the student is currently studying
- `disability` - indicates whether the student has declared a disability
- `final_result` - student's final result in the module-presentation (Distinction, Pass, Fail, Withdrawn)

### studentRegistration.csv
- `code_module` - identification code for a module
- `code_presentation` - identification code of the presentation
- `id_student` - unique identification number for the student
- `date_registration` - date of student's registration (days relative to start, negative values indicate early registration)
- `date_unregistration` - date of student unregistration (days relative to start, empty for completed students)

### studentAssessment.csv
- `id_assessment` - identification number of the assessment
- `id_student` - unique identification number for the student
- `date_submitted` - date of student submission (days since start of module presentation)
- `is_banked` - status flag indicating assessment result transferred from previous presentation
- `score` - student's score in the assessment (0 to 100)

### studentVle.csv
- `code_module` - identification code for a module
- `code_presentation` - identification code of the module presentation
- `id_student` - unique identification number for the student
- `id_site` - identification number for the VLE material
- `date` - date of student's interaction with the material (days since start of module-presentation)
- `sum_click` - number of times a student interacts with the material in that day

---

## 4. Educational Process Mining (EPM) Dataset

**Files**: Multiple CSV files (one per student per session)  
**Total Attributes**: 13

### Session & Student Information
- `session` - number of laboratory session (1 to 6)
- `student_Id` - ID of student (1 to 115)
- `exercise` - ID of the exercise the student is working on (format: Es_#session_#exercise)

### Activity Information
- `activity` - activity label based on web page title (anonymized activity names)
- `start_time` - start date and time of activity (format: dd.mm.yyyy hh:mm:ss)
- `end_time` - end date and time of activity (format: dd.mm.yyyy hh:mm:ss)
- `idle_time` - duration of idle time between start and end time of activity (milliseconds)

### Interaction Metrics
- `mouse_wheel` - amount of mouse wheel during an activity
- `mouse_wheel_click` - number of mouse wheel clicks during an activity
- `mouse_click_left` - number of mouse left clicks during an activity
- `mouse_click_right` - number of mouse right clicks during an activity
- `mouse_movement` - distance covered by mouse movements during an activity
- `keystroke` - number of keystrokes during an activity

---

## Summary

| Dataset | Total Attributes | Key Characteristics |
|---------|-----------------|---------------------|
| **UCI Student Performance** | 33 | Demographics, family background, academic factors, lifestyle, grades (0-20 scale) |
| **xAPI-Edu-Data** | 17 | Demographics, behavioral metrics, parental involvement, performance class (L/M/H) |
| **OULAD** | 43 (across 7 tables) | Multi-table relational data, VLE interactions, assessments, student demographics |
| **EPM** | 13 | Time-series event logs, mouse/keyboard interactions, activity sequences |

---

## Prediction Task Suitability

This section identifies which datasets can be used for specific prediction tasks.

### 1. Predicting Pass/Fail

**Available datasets:**

- **UCI Student Performance Dataset** ✅
  - **Target Variable**: `G3` (final grade, 0-20 scale)
  - **Usage**: Derive pass/fail from G3 (e.g., G3 ≥ 10 = Pass, G3 < 10 = Fail)
  - **Note**: Requires threshold definition for pass/fail classification

- **xAPI-Edu-Data Dataset** ✅
  - **Target Variable**: `Class` (L=Low, M=Medium, H=High)
  - **Usage**: Derive pass/fail from Class (L = Fail, M/H = Pass)
  - **Note**: Categorical performance class, not direct pass/fail labels

- **OULAD (Open University Learning Analytics Dataset)** ✅
  - **Target Variable**: `final_result` in `studentInfo.csv` (Pass, Fail, Distinction, Withdrawn)
  - **Usage**: Direct pass/fail labels available
  - **Note**: Best option as it provides explicit pass/fail outcomes

- **EPM (Educational Process Mining) Dataset** ✅
  - **Target Variable**: Final exam grades in `final_grades.xlsx`
  - **Usage**: Derive pass/fail from final exam scores
  - **Note**: Requires threshold definition and grade file processing

---

### 2. Predicting Dropouts

**Available datasets:**

- **OULAD (Open University Learning Analytics Dataset)** ✅
  - **Target Variable**: `final_result` = "Withdrawn" in `studentInfo.csv`
  - **Additional Indicator**: `date_unregistration` in `studentRegistration.csv` (non-empty value indicates dropout)
  - **Usage**: Direct dropout tracking with explicit withdrawal status
  - **Note**: Only dataset with explicit dropout information

**Not suitable:**
- **UCI Student Performance**: No dropout information available
- **xAPI-Edu-Data**: No dropout information available
- **EPM**: Some students didn't take final exam, but no explicit dropout tracking

---

### 3. Predicting Final Grade

**Available datasets:**

- **UCI Student Performance Dataset** ✅
  - **Target Variable**: `G3` (final grade, 0-20 scale)
  - **Usage**: Direct numeric final grade for regression
  - **Note**: Simple and straightforward numeric target variable

- **OULAD (Open University Learning Analytics Dataset)** ✅
  - **Target Variable**: Aggregate assessment scores from `studentAssessment.csv` (0-100 scale)
  - **Usage**: Can compute final grade from weighted assessments
  - **Additional**: Also has `final_result` (categorical: Distinction, Pass, Fail, Withdrawn)
  - **Note**: Requires aggregation of assessment scores with weights

- **EPM (Educational Process Mining) Dataset** ✅
  - **Target Variable**: Final exam grades in `final_grades.xlsx`
  - **Usage**: Direct final exam scores available
  - **Note**: Requires processing Excel file with final exam grades

**Not suitable:**
- **xAPI-Edu-Data**: Only has `Class` (L/M/H), no numeric final grade available

---

### Summary Table

| Prediction Task | UCI | xAPI | OULAD | EPM |
|----------------|-----|------|-------|-----|
| **Pass/Fail** | ✅ (derive from G3) | ✅ (derive from Class) | ✅ (direct) | ✅ (derive from final grades) |
| **Dropouts** | ❌ | ❌ | ✅ (Withdrawn) | ❌ |
| **Final Grade** | ✅ (G3, 0-20) | ❌ | ✅ (assessment scores, 0-100) | ✅ (final exam grades) |

**Best Choices:**
- **Pass/Fail**: OULAD (direct labels) or UCI (numeric grade with threshold)
- **Dropouts**: OULAD (only dataset with dropout information)
- **Final Grade**: UCI (simple numeric target) or OULAD (rich assessment data for aggregation)

---

## Dataset Recommendations by Task

This section provides specific recommendations for the best and second-best datasets for each prediction task.

### 1. Predicting Pass/Fail

**🥇 Best Choice: OULAD (Open University Learning Analytics Dataset)**
- **Why**: Provides direct `final_result` labels (Pass, Fail, Distinction, Withdrawn)
- **Advantages**:
  - No threshold definition needed
  - Large sample size (32,953 students)
  - Includes additional categories (Distinction, Withdrawn) for more nuanced analysis
  - Ready-to-use labels without derivation

**🥈 Second Best: UCI Student Performance Dataset**
- **Why**: Simple numeric target (`G3`) that can be easily converted to pass/fail
- **Advantages**:
  - Clean, straightforward structure (single CSV per course)
  - Clear threshold definition (typically G3 ≥ 10 = Pass)
  - Smaller dataset (1,044 students) but well-structured and easy to work with
  - No complex data processing required

---

### 2. Predicting Dropouts

**🥇 Best Choice: OULAD (Open University Learning Analytics Dataset)**
- **Why**: Only dataset with explicit dropout information
- **Advantages**:
  - Direct indicator: `final_result` = "Withdrawn" in `studentInfo.csv`
  - Additional signal: `date_unregistration` in `studentRegistration.csv` (non-empty value indicates dropout)
  - Large sample size provides sufficient dropout cases for modeling
  - Temporal data allows for early dropout prediction
  - Multiple indicators for robust dropout detection

**🥈 Second Best: None**
- **Why**: Other datasets do not track dropout information
- **Note**: UCI, xAPI, and EPM datasets do not contain explicit dropout indicators

---

### 3. Predicting Final Grade

**🥇 Best Choice: UCI Student Performance Dataset**
- **Why**: Simple, direct numeric target variable
- **Advantages**:
  - Direct numeric target: `G3` (0-20 scale) - no aggregation needed
  - Simple structure: single CSV file per course
  - Clean, ready-to-use format
  - Ideal for regression models
  - No complex data processing required

**🥈 Second Best: OULAD (Open University Learning Analytics Dataset)**
- **Why**: Rich assessment data that can be aggregated into final grades
- **Advantages**:
  - Multiple assessment scores (0-100 scale) in `studentAssessment.csv`
  - Can compute weighted final grades using assessment weights
  - Larger dataset (32,953 students) provides more training data
  - Temporal features enable early grade prediction
  - More comprehensive assessment history
- **Note**: Requires joining multiple tables and aggregating scores with weights

---

### Quick Reference Table

| Task | Best Choice | Second Best | Key Reason |
|------|-------------|-------------|------------|
| **Pass/Fail** | OULAD | UCI | Direct labels vs. easy derivation |
| **Dropouts** | OULAD | None | Only dataset with dropout information |
| **Final Grade** | UCI | OULAD | Simple numeric vs. rich aggregated data |

---

## Cross-Validation Dataset Pairs

This section identifies dataset pairs that can be used for cross-validation, where a model trained on one dataset can be evaluated on another dataset with aligned features and targets.

### 1. Predicting Pass/Fail

#### ✅ **Best Pair: UCI ↔ xAPI** (High Feasibility)

**Common Feature Set (with derivation):**

**Demographics:**
- `gender`/`sex` - Direct match (binary: M/F)

**Absences:**
- UCI: `absences` (numeric: 0-93)
- xAPI: `StudentAbsenceDays` (categorical: "Under-7", "Above-7")
- **Derivation**: Convert xAPI to numeric (Under-7 → 3.5, Above-7 → 10), then normalize both to 0-1 scale

**Engagement/Study Time:**
- UCI: `studytime` (numeric: 1-4 scale)
- xAPI: `engagement_score` (derived from behavioral metrics)
- **Derivation**: Create composite score from xAPI features:
  - `raisedhands` (normalized)
  - `VisitedResources` (normalized)
  - `AnnouncementsView` (normalized)
  - `Discussion` (normalized)
  - Formula: `engagement_score = 0.3×raisedhands + 0.3×VisitedResources + 0.2×AnnouncementsView + 0.2×Discussion`

**Parental Support:**
- UCI: `famsup` (binary: yes/no)
- xAPI: `parental_support` (derived from surveys)
- **Derivation**: Create binary indicator from xAPI:
  - `parental_support = (ParentAnsweringSurvey == 'Yes') AND (ParentschoolSatisfaction == 'Good')`

**Academic Level/History:**
- UCI: `failures` (numeric: number of past failures)
- xAPI: `academic_level` (derived from GradeID/StageID)
- **Derivation**: Map GradeID/StageID to numeric scale approximating academic progression

**Target Alignment:**
- **UCI**: Pass/Fail derived from `G3` (threshold: G3 ≥ 10 = Pass, G3 < 10 = Fail)
- **xAPI**: Pass/Fail derived from `Class` (L = Fail, M/H = Pass)

**Feasibility**: ✅ **High** - Well-documented feature mapping strategy (see `cross-dataset-regression-plan.md`)

**Key Advantages:**
- Good feature overlap with clear derivation paths
- Both datasets have similar sizes (UCI: 1,044, xAPI: 480)
- Complementary contexts (Portugal vs. Middle East) for testing generalization

---

#### ⚠️ **Alternative Pair: UCI ↔ OULAD** (Moderate Feasibility)

**Common Feature Set (with derivation):**

**Demographics:**
- `gender` - Direct match
- `age` - UCI (numeric: 15-22) ↔ OULAD `age_band` (categorical, convert to numeric)

**Engagement:**
- UCI: `studytime` (numeric: 1-4)
- OULAD: `vle_engagement` (aggregate `sum_click` from `studentVle.csv`)

**Absences:**
- UCI: `absences` (numeric: 0-93)
- OULAD: `absence_indicator` (derive from low VLE activity patterns)

**Academic History:**
- UCI: `failures` (numeric)
- OULAD: `num_of_prev_attempts` (direct match)

**Education Background:**
- UCI: `Medu`/`Fedu` (numeric: 0-4)
- OULAD: `highest_education` (categorical, map to numeric scale)

**Target Alignment:**
- **UCI**: Pass/Fail from `G3` (threshold: G3 ≥ 10 = Pass)
- **OULAD**: Pass/Fail from `final_result` (Pass/Fail categories)

**Feasibility**: ⚠️ **Moderate** - Requires feature engineering and aggregation of VLE data

---

### 2. Predicting Final Grade

#### ✅ **Best Pair: UCI ↔ OULAD** (High Feasibility)

**Common Feature Set (with derivation):**

**Demographics:**
- `gender` - Direct match
- `age` - UCI (numeric: 15-22) ↔ OULAD `age_band` (categorical, normalize to numeric)

**Engagement/Study Time:**
- UCI: `studytime` (numeric: 1-4 scale)
- OULAD: `vle_engagement` (aggregate `sum_click` from `studentVle.csv` per student)
- **Derivation**: Sum all clicks per student, normalize to 0-1 scale

**Academic History:**
- UCI: `failures` (numeric: number of past failures)
- OULAD: `num_of_prev_attempts` (direct match, numeric)

**Education Background:**
- UCI: `Medu`/`Fedu` (numeric: 0-4, parent education)
- OULAD: `highest_education` (categorical, map to numeric: 0-4 scale)

**Absences:**
- UCI: `absences` (numeric: 0-93)
- OULAD: `absence_indicator` (derive from VLE activity: low activity = high absence)

**Support Indicators:**
- UCI: `famsup`, `schoolsup` (binary support indicators)
- OULAD: `imd_band` (socioeconomic indicator, can proxy for support)

**Target Alignment:**
- **UCI**: `G3` (final grade, 0-20 scale)
- **OULAD**: Aggregated assessment scores (0-100 scale)
- **Normalization**: Normalize OULAD scores to 0-20 scale OR normalize both to 0-1 scale
  - Option 1: `OULAD_normalized = (aggregated_score / 100) * 20`
  - Option 2: `UCI_normalized = G3 / 20`, `OULAD_normalized = aggregated_score / 100`

**Feasibility**: ✅ **High** - Good feature overlap, both have numeric targets, requires normalization

**Key Advantages:**
- Both datasets have numeric final grade targets
- Rich feature overlap in demographics, engagement, and academic history
- Large OULAD dataset (32,953 students) provides robust evaluation
- Different educational contexts (secondary school vs. university) test generalization

**Implementation Notes:**
- Aggregate OULAD assessment scores: Weight by `weight` from `assessments.csv`
- Calculate weighted average: `final_grade = Σ(score × weight) / Σ(weight)` for each student
- Handle missing assessments appropriately

---

#### ⚠️ **Alternative Pair: OULAD ↔ EPM** (Moderate Feasibility)

**Common Feature Set (with derivation):**

**Engagement Metrics:**
- OULAD: `vle_engagement` (aggregate `sum_click` from `studentVle.csv`)
- EPM: `interaction_engagement` (aggregate mouse/keyboard interactions)
- **Derivation**: Sum mouse clicks, keystrokes, and movements per student, normalize

**Activity Patterns:**
- OULAD: `activity_frequency` (from `studentVle.csv` activity counts)
- EPM: `activity_frequency` (from activity logs per session)

**Time Metrics:**
- EPM: `idle_time` (can be aggregated to engagement indicators)
- OULAD: Time-based features from VLE interaction dates

**Target Alignment:**
- **OULAD**: Aggregated assessment scores (0-100 scale)
- **EPM**: Final exam grades from `final_grades.xlsx`
- **Normalization**: Both to 0-1 or 0-100 scale

**Feasibility**: ⚠️ **Moderate** - Both have interaction data but different types; requires significant aggregation

**Limitations:**
- Limited demographic overlap (EPM lacks demographics)
- Different interaction contexts (online VLE vs. lab software)
- EPM dataset is smaller (115 students)

---

### Cross-Validation Summary Table

| Task | Best Pair | Feasibility | Key Common Features |
|------|----------|-------------|---------------------|
| **Pass/Fail** | UCI ↔ xAPI | ✅ High | gender, absences, engagement, parental support |
| **Pass/Fail** | UCI ↔ OULAD | ⚠️ Moderate | gender, age, engagement, academic history |
| **Final Grade** | UCI ↔ OULAD | ✅ High | gender, age, engagement, academic history, education |
| **Final Grade** | OULAD ↔ EPM | ⚠️ Moderate | engagement metrics, activity patterns |

**Recommendations:**
- **Pass/Fail Cross-Validation**: Use **UCI ↔ xAPI** (best documented and most feasible)
- **Final Grade Cross-Validation**: Use **UCI ↔ OULAD** (best feature overlap and both have numeric targets)


# Data Folder Structure Index

## Dataset Overview

| Dataset | Folder | Description | Link |
|---------|--------|-------------|------|
| OULAD (Open University Learning Analytics Dataset) | `open-university-learning-analytics-dataset` | 32K+ students, demographics, VLE engagement, and results | https://archive.ics.uci.edu/dataset/349/open+university+learning+analytics+dataset |
| xAPI-Edu-Data (Kaggle) | `xapi-edu-data` | Behavioral data (raised hands, discussion participation, etc.) | https://www.kaggle.com/datasets/aljarah/xAPI-Edu-Data |
| UCI Student Performance Dataset | `uci-student-performance` | Grades, demographic, and social data | https://archive.ics.uci.edu/ml/datasets/Student+Performance |
| Educational Process Mining Dataset | `epm-dataset` | Sequential event logs of student interactions | https://archive.ics.uci.edu/dataset/346/educational+process+mining+epm+a+learning+analytics+data+set |

---

This file provides links and references to all folders and files within the data directory.

## Dataset Folders

### 1. Open University Learning Analytics Dataset (OULAD)
**Path:** [./open-university-learning-analytics-dataset/](./open-university-learning-analytics-dataset/)

#### Files
- [assessments.csv](./open-university-learning-analytics-dataset/assessments.csv)
- [courses.csv](./open-university-learning-analytics-dataset/courses.csv)
- [OULAD.names](./open-university-learning-analytics-dataset/OULAD.names)
- [studentAssessment.csv](./open-university-learning-analytics-dataset/studentAssessment.csv)
- [studentInfo.csv](./open-university-learning-analytics-dataset/studentInfo.csv)
- [studentRegistration.csv](./open-university-learning-analytics-dataset/studentRegistration.csv)
- [vle.csv](./open-university-learning-analytics-dataset/vle.csv)

#### studentVle Split Files
**Path:** [./open-university-learning-analytics-dataset/studentVle_split/](./open-university-learning-analytics-dataset/studentVle_split/)

**Note:** The original `studentVle.csv` file had been split into smaller files due to its large size (>200MB, containing over 10.6 million rows).

##### Files
- [README.md](./open-university-learning-analytics-dataset/studentVle_split/README.md) - Documentation about the split files
- [studentVle_part1.csv](./open-university-learning-analytics-dataset/studentVle_split/studentVle_part1.csv) - 2,000,000 data rows
- [studentVle_part2.csv](./open-university-learning-analytics-dataset/studentVle_split/studentVle_part2.csv) - 2,000,000 data rows
- [studentVle_part3.csv](./open-university-learning-analytics-dataset/studentVle_split/studentVle_part3.csv) - 2,000,000 data rows
- [studentVle_part4.csv](./open-university-learning-analytics-dataset/studentVle_split/studentVle_part4.csv) - 2,000,000 data rows
- [studentVle_part5.csv](./open-university-learning-analytics-dataset/studentVle_split/studentVle_part5.csv) - 2,000,000 data rows
- [studentVle_part6.csv](./open-university-learning-analytics-dataset/studentVle_split/studentVle_part6.csv) - 655,280 data rows (remainder)

**Total:** 10,655,280 data rows across all split files

### 2. xAPI-Edu-Data
**Path:** [./xapi-edu-data/](./xapi-edu-data/)

#### Files
- [xAPI-Edu-Data.csv](./xapi-edu-data/xAPI-Edu-Data.csv) - xAPI Educational Data CSV file

### 3. UCI Student Performance Dataset
**Path:** [./uci-student-performance/](./uci-student-performance/)

#### Files
- [student-mat.csv](./uci-student-performance/student-mat.csv)
- [student-merge.R](./uci-student-performance/student-merge.R)
- [student-por.csv](./uci-student-performance/student-por.csv)
- [student.txt](./uci-student-performance/student.txt)

### 4. EPM Dataset
**Path:** [./epm-dataset/](./epm-dataset/)

#### Root Files
- [activities_info.txt](./epm-dataset/activities_info.txt)
- [activities.txt](./epm-dataset/activities.txt)
- [exercises_info.txt](./epm-dataset/exercises_info.txt)
- [features_info.txt](./epm-dataset/features_info.txt)
- [features.txt](./epm-dataset/features.txt)
- [grades_info.txt](./epm-dataset/grades_info.txt)
- [README.txt](./epm-dataset/README.txt)

#### Data Subfolder
**Path:** [./epm-dataset/Data/](./epm-dataset/Data/)

##### Files
- [final_exam_ ENG.pdf](./epm-dataset/Data/final_exam_%20ENG.pdf)
- [final_exam.pdf](./epm-dataset/Data/final_exam.pdf)
- [final_grades.xlsx](./epm-dataset/Data/final_grades.xlsx)
- [intermediate_grades.xlsx](./epm-dataset/Data/intermediate_grades.xlsx)
- [logs.txt](./epm-dataset/Data/logs.txt)

##### Processes Subfolder
**Path:** [./epm-dataset/Data/Processes/](./epm-dataset/Data/Processes/)

###### Session Folders
- [Session 1/](./epm-dataset/Data/Processes/Session%201/) - Contains numbered process files (1, 2, 4, 5, 7, 9, 10, 11, 12, 14, 15, 17, 19, 20, 21, 22, 28, 30, 32, 34, 36, 37, 38, 39, 42, 43, 44, 46, 47, 49, 51, 52, 53, 54, 55, 56, 59, 62, 63, 66, 67, 68, 70, 71, 73, 74, 76, 78, 79, 80, 81, 82, 85, 86, 87, 88, 90, 91, 92, 93, 94, 96, 97, 98, 100, 101, 102, 104, 105, 108, 109, 110, 111, 112, 113, 114, 115)
- [Session 2/](./epm-dataset/Data/Processes/Session%202/) - Contains numbered process files (1, 2, 3, 4, 5, 6, 7, 8, 10, 11, 12, 14, 15, 16, 17, 18, 19, 20, 21, 22, 24, 27, 28, 29, 30, 32, 34, 36, 38, 39, 41, 42, 43, 44, 46, 47, 48, 49, 50, 51, 52, 53, 54, 56, 59, 61, 63, 66, 67, 70, 71, 72, 73, 74, 76, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 100, 101, 102, 103, 104, 107)
- [Session 3/](./epm-dataset/Data/Processes/Session%203/) - Contains numbered process files (2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 14, 15, 16, 17, 18, 19, 20, 23, 24, 25, 27, 28, 29, 30, 31, 32, 34, 35, 36, 38, 39, 41, 42, 43, 44, 45, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 59, 61, 63, 66, 67, 68, 69, 70, 72, 73, 74, 75, 76, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 97, 98, 99, 100, 101, 102, 105, 106, 107)
- [Session 4/](./epm-dataset/Data/Processes/Session%204/) - Contains numbered process files (1-99, complete sequence)
- [Session 5/](./epm-dataset/Data/Processes/Session%205/) - Contains numbered process files (1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 22, 23, 24, 27, 28, 29, 30, 31, 32, 34, 35, 36, 37, 38, 39, 40, 41, 42, 44, 45, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 59, 60, 61, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 74, 75, 76, 78, 79, 80, 81, 82, 83, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 98, 99, 100, 101, 102, 103, 104)
- [Session 6/](./epm-dataset/Data/Processes/Session%206/) - Contains numbered process files (1, 2, 4, 5, 6, 7, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 24, 25, 27, 28, 29, 30, 32, 34, 35, 36, 37, 38, 39, 41, 42, 44, 46, 47, 48, 49, 50, 51, 52, 53, 54, 56, 57, 59, 60, 61, 63, 64, 65, 66, 67, 68, 69, 70, 72, 73, 74, 75, 76, 78, 79, 80, 81, 82, 83, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99, 102, 104)

---

## Files by Type
- **CSV Files**: assessments.csv, courses.csv, studentAssessment.csv, studentInfo.csv, studentRegistration.csv, vle.csv, studentVle_split/studentVle_part1.csv through studentVle_part6.csv (original studentVle.csv split due to size), xapi-edu-data/xAPI-Edu-Data.csv, student-mat.csv, student-por.csv
- **Excel Files**: final_grades.xlsx, intermediate_grades.xlsx
- **PDF Files**: final_exam.pdf, final_exam_ ENG.pdf
- **Text Files**: activities_info.txt, activities.txt, exercises_info.txt, features_info.txt, features.txt, grades_info.txt, logs.txt, OULAD.names, README.txt, student.txt
- **R Scripts**: student-merge.R
- **Process Files**: Numbered files in Session 1-6 folders (student process logs)

---

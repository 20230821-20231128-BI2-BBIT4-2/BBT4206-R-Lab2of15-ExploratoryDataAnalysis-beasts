Business Intelligence Lab Submission Markdown
================
<Specify your name here>
<Specify the date when you submitted the lab>

- [Student Details](#student-details)
- [Setup Chunk](#setup-chunk)
- [Loading Dataset](#loading-dataset)
- [Dimensions](#dimensions)
- [Data Types](#data-types)
- [Descriptive Statistics](#descriptive-statistics)
  - [Measures of Frequency](#measures-of-frequency)
  - [Measures of Central Tendency](#measures-of-central-tendency)
  - [Measures of
    Distribution/Dispersion/Spread/Scatter/Variability](#measures-of-distributiondispersionspreadscattervariability)
    - [Measure the variance](#measure-the-variance)
    - [Measure the standard deviation](#measure-the-standard-deviation)
- [Inferential Statistics](#inferential-statistics)
  - [Perform ANOVA](#perform-anova)
- [Qualitative Data Analysis](#qualitative-data-analysis)
  - [Univariate Plots](#univariate-plots)
    - [Create Histograms](#create-histograms)
    - [Missingness Map](#missingness-map)
  - [Multivariate Plots](#multivariate-plots)
    - [Create a Scatter Plot](#create-a-scatter-plot)

# Student Details

<table>
<colgroup>
<col style="width: 53%" />
<col style="width: 46%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Student ID Numbers and Names of Group Members</strong></td>
<td><p>131038 Doreen Muema</p>
<p>19630 Venus Karanja</p>
<p>135844 Mercy Macharia</p>
<p>Ryan Shuma</p>
<p>Bill Akide</p></td>
</tr>
<tr class="even">
<td><strong>BBIT 4.2 Group</strong></td>
<td>A,A,A,B,C</td>
</tr>
<tr class="odd">
<td><strong>Course Code</strong></td>
<td>BBT4206</td>
</tr>
<tr class="even">
<td><strong>Course Name</strong></td>
<td>Business Intelligence II</td>
</tr>
<tr class="odd">
<td><strong>Program</strong></td>
<td>Bachelor of Business Information Technology</td>
</tr>
<tr class="even">
<td><strong>Semester Duration</strong></td>
<td>21<sup>st</sup> August 2023 to 28<sup>th</sup> November 2023</td>
</tr>
</tbody>
</table>

# Setup Chunk

**Note:** the following KnitR options have been set as the global
defaults:  
`knitr::opts_chunk$set(echo = TRUE, warning = FALSE, eval = TRUE,                        collapse = FALSE, tidy = TRUE)`.

> output:  
>   
> github_document:  
> toc: yes  
> toc_depth: 4  
> fig_width: 6  
> fig_height: 4  
> df_print: default  
>   
> editor_options:  
> chunk_output_type: console

More KnitR options are documented here
<https://bookdown.org/yihui/rmarkdown-cookbook/chunk-options.html> and
here <https://yihui.org/knitr/options/>.

# Loading Dataset

***Describe the code chunk here:*** Commands to loading Dataset

``` r
student_performance_dataset <- readr::read_csv("data/StudentPerformance.csv", col_types = readr::cols(class_group = readr::col_factor(levels = c("A",
    "B", "C")), gender = readr::col_factor(levels = c("1", "0")), YOB = readr::col_date(format = "%Y"),
    regret_choosing_bi = readr::col_factor(levels = c("1", "0")), drop_bi_now = readr::col_factor(levels = c("1",
        "0")), motivator = readr::col_factor(levels = c("1", "0")), read_content_before_lecture = readr::col_factor(levels = c("1",
        "2", "3", "4", "5")), anticipate_test_questions = readr::col_factor(levels = c("1",
        "2", "3", "4", "5")), answer_rhetorical_questions = readr::col_factor(levels = c("1",
        "2", "3", "4", "5")), find_terms_I_do_not_know = readr::col_factor(levels = c("1",
        "2", "3", "4", "5")), copy_new_terms_in_reading_notebook = readr::col_factor(levels = c("1",
        "2", "3", "4", "5")), take_quizzes_and_use_results = readr::col_factor(levels = c("1",
        "2", "3", "4", "5")), reorganise_course_outline = readr::col_factor(levels = c("1",
        "2", "3", "4", "5")), write_down_important_points = readr::col_factor(levels = c("1",
        "2", "3", "4", "5")), space_out_revision = readr::col_factor(levels = c("1",
        "2", "3", "4", "5")), studying_in_study_group = readr::col_factor(levels = c("1",
        "2", "3", "4", "5")), schedule_appointments = readr::col_factor(levels = c("1",
        "2", "3", "4", "5")), goal_oriented = readr::col_factor(levels = c("1", "0")),
    spaced_repetition = readr::col_factor(levels = c("1", "2", "3", "4")), testing_and_active_recall = readr::col_factor(levels = c("1",
        "2", "3", "4")), interleaving = readr::col_factor(levels = c("1", "2", "3",
        "4")), categorizing = readr::col_factor(levels = c("1", "2", "3", "4")),
    retrospective_timetable = readr::col_factor(levels = c("1", "2", "3", "4")),
    cornell_notes = readr::col_factor(levels = c("1", "2", "3", "4")), sq3r = readr::col_factor(levels = c("1",
        "2", "3", "4")), commute = readr::col_factor(levels = c("1", "2", "3", "4")),
    study_time = readr::col_factor(levels = c("1", "2", "3", "4")), repeats_since_Y1 = readr::col_integer(),
    paid_tuition = readr::col_factor(levels = c("0", "1")), free_tuition = readr::col_factor(levels = c("0",
        "1")), extra_curricular = readr::col_factor(levels = c("0", "1")), sports_extra_curricular = readr::col_factor(levels = c("0",
        "1")), exercise_per_week = readr::col_factor(levels = c("0", "1", "2", "3")),
    meditate = readr::col_factor(levels = c("0", "1", "2", "3")), pray = readr::col_factor(levels = c("0",
        "1", "2", "3")), internet = readr::col_factor(levels = c("0", "1")), laptop = readr::col_factor(levels = c("0",
        "1")), family_relationships = readr::col_factor(levels = c("1", "2", "3",
        "4", "5")), friendships = readr::col_factor(levels = c("1", "2", "3", "4",
        "5")), romantic_relationships = readr::col_factor(levels = c("0", "1", "2",
        "3", "4")), spiritual_wellnes = readr::col_factor(levels = c("1", "2", "3",
        "4", "5")), financial_wellness = readr::col_factor(levels = c("1", "2", "3",
        "4", "5")), health = readr::col_factor(levels = c("1", "2", "3", "4", "5")),
    day_out = readr::col_factor(levels = c("0", "1", "2", "3")), night_out = readr::col_factor(levels = c("0",
        "1", "2", "3")), alcohol_or_narcotics = readr::col_factor(levels = c("0",
        "1", "2", "3")), mentor = readr::col_factor(levels = c("0", "1")), mentor_meetings = readr::col_factor(levels = c("0",
        "1", "2", "3")), `Attendance Waiver Granted: 1 = Yes, 0 = No` = readr::col_factor(levels = c("0",
        "1")), GRADE = readr::col_factor(levels = c("A", "B", "C", "D", "E"))), locale = readr::locale())
```

# Dimensions

***Describe the next code chunk here:*** Commands to display the
dimensions of the datasets

``` r
dim(student_performance_dataset)
```

    ## [1] 100 100

# Data Types

***Describe the next code chunk here:*** Command to identify the data
types

``` r
result <- sapply(student_performance_dataset, class)
for (i in seq_along(result)) {
    cat(sprintf("%-50s %s\n", names(result)[i], result[[i]]))
}
```

    ## class_group                                        factor
    ## gender                                             factor
    ## YOB                                                Date
    ## regret_choosing_bi                                 factor
    ## drop_bi_now                                        factor
    ## motivator                                          factor
    ## read_content_before_lecture                        factor
    ## anticipate_test_questions                          factor
    ## answer_rhetorical_questions                        factor
    ## find_terms_I_do_not_know                           factor
    ## copy_new_terms_in_reading_notebook                 factor
    ## take_quizzes_and_use_results                       factor
    ## reorganise_course_outline                          factor
    ## write_down_important_points                        factor
    ## space_out_revision                                 factor
    ## studying_in_study_group                            factor
    ## schedule_appointments                              factor
    ## goal_oriented                                      factor
    ## spaced_repetition                                  factor
    ## testing_and_active_recall                          factor
    ## interleaving                                       factor
    ## categorizing                                       factor
    ## retrospective_timetable                            factor
    ## cornell_notes                                      factor
    ## sq3r                                               factor
    ## commute                                            factor
    ## study_time                                         factor
    ## repeats_since_Y1                                   integer
    ## paid_tuition                                       factor
    ## free_tuition                                       factor
    ## extra_curricular                                   factor
    ## sports_extra_curricular                            factor
    ## exercise_per_week                                  factor
    ## meditate                                           factor
    ## pray                                               factor
    ## internet                                           factor
    ## laptop                                             factor
    ## family_relationships                               factor
    ## friendships                                        factor
    ## romantic_relationships                             factor
    ## spiritual_wellnes                                  factor
    ## financial_wellness                                 factor
    ## health                                             factor
    ## day_out                                            factor
    ## night_out                                          factor
    ## alcohol_or_narcotics                               factor
    ## mentor                                             factor
    ## mentor_meetings                                    factor
    ## A - 1. I am enjoying the subject                   numeric
    ## A - 2. Classes start and end on time               numeric
    ## A - 3. The learning environment is participative, involves learning by doing and is group-based numeric
    ## A - 4. The subject content is delivered according to the course outline and meets my expectations numeric
    ## A - 5. The topics are clear and logically developed numeric
    ## A - 6. I am developing my oral and writing skills  numeric
    ## A - 7. I am developing my reflective and critical reasoning skills numeric
    ## A - 8. The assessment methods are assisting me to learn numeric
    ## A - 9. I receive relevant feedback                 numeric
    ## A - 10. I read the recommended readings and notes  numeric
    ## A - 11. I use the eLearning material posted        numeric
    ## B - 1. Concept 1 of 6: Principles of Business Intelligence and the DataOps Philosophy numeric
    ## B - 2. Concept 3 of 6: Linear Algorithms for Predictive Analytics numeric
    ## C - 2. Quizzes at the end of each concept          numeric
    ## C - 3. Lab manuals that outline the steps to follow during the labs numeric
    ## C - 4. Required lab work submissions at the end of each lab manual that outline the activity to be done on your own numeric
    ## C - 5. Supplementary videos to watch               numeric
    ## C - 6. Supplementary podcasts to listen to         numeric
    ## C - 7. Supplementary content to read               numeric
    ## C - 8. Lectures slides                             numeric
    ## C - 9. Lecture notes on some of the lecture slides numeric
    ## C - 10. The quality of the lectures given (quality measured by the breadth (the full span of knowledge of a subject) and depth (the extent to which specific topics are focused upon, amplified, and explored) of learning - NOT quality measured by how fun/comical/lively the lectures are) numeric
    ## C - 11. The division of theory and practice such that most of the theory is done during the recorded online classes and most of the practice is done during the physical classes numeric
    ## C - 12. The recordings of online classes           numeric
    ## D - 1. 
    ## Write two things you like about the teaching and learning in this unit so far. character
    ## D - 2. Write at least one recommendation to improve the teaching and learning in this unit (for the remaining weeks in the semester) character
    ## Average Course Evaluation Rating                   numeric
    ## Average Level of Learning Attained Rating          numeric
    ## Average Pedagogical Strategy Effectiveness Rating  numeric
    ## Project: Section 1-4: (20%) x/10                   numeric
    ## Project: Section 5-11: (50%) x/10                  numeric
    ## Project: Section 12: (30%) x/5                     numeric
    ## Project: (10%): x/30 x 100 TOTAL                   numeric
    ## Quiz 1 on Concept 1 (Introduction) x/32            numeric
    ## Quiz 3 on Concept 3 (Linear) x/15                  numeric
    ## Quiz 4 on Concept 4 (Non-Linear) x/22              numeric
    ## Quiz 5 on Concept 5 (Dashboarding) x/10            numeric
    ## Quizzes and  Bonus Marks (7%): x/79 x 100 TOTAL    numeric
    ## Lab 1 - 2.c. - (Simple Linear Regression) x/5      numeric
    ## Lab 2 - 2.e. -  (Linear Regression using Gradient Descent) x/5 numeric
    ## Lab 3 - 2.g. - (Logistic Regression using Gradient Descent) x/5 numeric
    ## Lab 4 - 2.h. - (Linear Discriminant Analysis) x/5  numeric
    ## Lab 5 - Chart JS Dashboard Setup x/5               numeric
    ## Lab Work (7%) x/25 x 100                           numeric
    ## CAT 1 (8%): x/38 x 100                             numeric
    ## CAT 2 (8%): x/100 x 100                            numeric
    ## Attendance Waiver Granted: 1 = Yes, 0 = No         factor
    ## Absenteeism Percentage                             numeric
    ## Coursework TOTAL: x/40 (40%)                       numeric
    ## EXAM: x/60 (60%)                                   numeric
    ## TOTAL = Coursework TOTAL + EXAM (100%)             numeric
    ## GRADE                                              factor

# Descriptive Statistics

## Measures of Frequency

***Describe the next code chunk here:*** is used to calculate and
display the frequency and percentage distribution of the “gender”
variable in the “student_performance_dataset.”

``` r
gender_freq <- student_performance_dataset$gender
cbind(frequency = table(gender_freq), percentage = prop.table(table(gender_freq)) *
    100)
```

    ##   frequency percentage
    ## 1        58         58
    ## 0        42         42

## Measures of Central Tendency

***Describe the next code chunk here:*** calculates the mode (most
frequent value) of the “EXAM: x/60 (60%)” column in the
“student_performance_dataset” and prints the result.

``` r
student_performance_dataset_mode <- names(table(student_performance_dataset$`EXAM: x/60 (60%)`))[which(table(student_performance_dataset$`EXAM: x/60 (60%)`) ==
    max(table(student_performance_dataset$`EXAM: x/60 (60%)`)))]
print(student_performance_dataset_mode)
```

    ## [1] "42"

## Measures of Distribution/Dispersion/Spread/Scatter/Variability

``` r
summary(student_performance_dataset)
```

    ##  class_group gender      YOB             regret_choosing_bi drop_bi_now
    ##  A:23        1:58   Min.   :1998-01-01   1: 2               1: 2       
    ##  B:37        0:42   1st Qu.:2000-01-01   0:98               0:98       
    ##  C:40               Median :2001-01-01                                 
    ##                     Mean   :2000-11-25                                 
    ##                     3rd Qu.:2002-01-01                                 
    ##                     Max.   :2003-01-01                                 
    ##                                                                        
    ##  motivator read_content_before_lecture anticipate_test_questions
    ##  1:75      1:11                        1: 5                     
    ##  0:25      2:25                        2: 6                     
    ##            3:46                        3:31                     
    ##            4:14                        4:42                     
    ##            5: 4                        5:16                     
    ##                                                                 
    ##                                                                 
    ##  answer_rhetorical_questions find_terms_I_do_not_know
    ##  1: 3                        1: 6                    
    ##  2:14                        2: 2                    
    ##  3:32                        3:30                    
    ##  4:38                        4:36                    
    ##  5:13                        5:26                    
    ##                                                      
    ##                                                      
    ##  copy_new_terms_in_reading_notebook take_quizzes_and_use_results
    ##  1: 5                               1: 4                        
    ##  2:10                               2: 5                        
    ##  3:24                               3:22                        
    ##  4:36                               4:31                        
    ##  5:25                               5:38                        
    ##                                                                 
    ##                                                                 
    ##  reorganise_course_outline write_down_important_points space_out_revision
    ##  1: 7                      1: 4                        1: 8              
    ##  2:16                      2: 8                        2:16              
    ##  3:28                      3:20                        3:34              
    ##  4:31                      4:38                        4:28              
    ##  5:18                      5:30                        5:14              
    ##                                                                          
    ##                                                                          
    ##  studying_in_study_group schedule_appointments goal_oriented spaced_repetition
    ##  1:34                    1:41                  1:20          1:12             
    ##  2:21                    2:35                  0:80          2:30             
    ##  3:20                    3:16                                3:48             
    ##  4:16                    4: 5                                4:10             
    ##  5: 9                    5: 3                                                 
    ##                                                                               
    ##                                                                               
    ##  testing_and_active_recall interleaving categorizing retrospective_timetable
    ##  1: 2                      1:13         1: 6         1:16                   
    ##  2:17                      2:51         2:27         2:36                   
    ##  3:55                      3:32         3:56         3:38                   
    ##  4:26                      4: 4         4:11         4:10                   
    ##                                                                             
    ##                                                                             
    ##                                                                             
    ##  cornell_notes sq3r   commute study_time repeats_since_Y1 paid_tuition
    ##  1:19          1:18   1:16    1:45       Min.   : 0.00    0:89        
    ##  2:26          2:27   2:23    2:39       1st Qu.: 0.00    1:11        
    ##  3:37          3:30   3:33    3:12       Median : 2.00                
    ##  4:18          4:25   4:28    4: 4       Mean   : 2.05                
    ##                                          3rd Qu.: 3.00                
    ##                                          Max.   :10.00                
    ##                                                                       
    ##  free_tuition extra_curricular sports_extra_curricular exercise_per_week
    ##  0:73         0:47             0:64                    0:23             
    ##  1:27         1:53             1:36                    1:49             
    ##                                                        2:23             
    ##                                                        3: 5             
    ##                                                                         
    ##                                                                         
    ##                                                                         
    ##  meditate pray   internet laptop  family_relationships friendships
    ##  0:49     0: 8   0:13     0:  0   1: 0                 1: 0       
    ##  1:35     1:24   1:87     1:100   2: 2                 2: 3       
    ##  2: 7     2:19                    3:18                 3:17       
    ##  3: 9     3:49                    4:39                 4:56       
    ##                                   5:41                 5:24       
    ##                                                                   
    ##                                                                   
    ##  romantic_relationships spiritual_wellnes financial_wellness health day_out
    ##  0:56                   1: 1              1:10               1: 2   0:27   
    ##  1: 0                   2: 8              2:18               2: 3   1:67   
    ##  2: 6                   3:37              3:41               3:22   2: 5   
    ##  3:27                   4:33              4:21               4:35   3: 1   
    ##  4:11                   5:21              5:10               5:38          
    ##                                                                            
    ##                                                                            
    ##  night_out alcohol_or_narcotics mentor mentor_meetings
    ##  0:55      0:68                 0:59   0:53           
    ##  1:41      1:30                 1:41   1:29           
    ##  2: 2      2: 1                        2:15           
    ##  3: 2      3: 1                        3: 3           
    ##                                                       
    ##                                                       
    ##                                                       
    ##  A - 1. I am enjoying the subject A - 2. Classes start and end on time
    ##  Min.   :3.000                    Min.   :3.000                       
    ##  1st Qu.:4.000                    1st Qu.:4.000                       
    ##  Median :5.000                    Median :5.000                       
    ##  Mean   :4.495                    Mean   :4.677                       
    ##  3rd Qu.:5.000                    3rd Qu.:5.000                       
    ##  Max.   :5.000                    Max.   :5.000                       
    ##  NA's   :1                        NA's   :1                           
    ##  A - 3. The learning environment is participative, involves learning by doing and is group-based
    ##  Min.   :3.000                                                                                  
    ##  1st Qu.:4.000                                                                                  
    ##  Median :4.000                                                                                  
    ##  Mean   :4.354                                                                                  
    ##  3rd Qu.:5.000                                                                                  
    ##  Max.   :5.000                                                                                  
    ##  NA's   :1                                                                                      
    ##  A - 4. The subject content is delivered according to the course outline and meets my expectations
    ##  Min.   :3.000                                                                                    
    ##  1st Qu.:4.500                                                                                    
    ##  Median :5.000                                                                                    
    ##  Mean   :4.737                                                                                    
    ##  3rd Qu.:5.000                                                                                    
    ##  Max.   :5.000                                                                                    
    ##  NA's   :1                                                                                        
    ##  A - 5. The topics are clear and logically developed
    ##  Min.   :2.000                                      
    ##  1st Qu.:4.000                                      
    ##  Median :5.000                                      
    ##  Mean   :4.657                                      
    ##  3rd Qu.:5.000                                      
    ##  Max.   :5.000                                      
    ##  NA's   :1                                          
    ##  A - 6. I am developing my oral and writing skills
    ##  Min.   :1.000                                    
    ##  1st Qu.:4.000                                    
    ##  Median :4.000                                    
    ##  Mean   :4.131                                    
    ##  3rd Qu.:5.000                                    
    ##  Max.   :5.000                                    
    ##  NA's   :1                                        
    ##  A - 7. I am developing my reflective and critical reasoning skills
    ##  Min.   :2.000                                                     
    ##  1st Qu.:4.000                                                     
    ##  Median :4.000                                                     
    ##  Mean   :4.384                                                     
    ##  3rd Qu.:5.000                                                     
    ##  Max.   :5.000                                                     
    ##  NA's   :1                                                         
    ##  A - 8. The assessment methods are assisting me to learn
    ##  Min.   :1.000                                          
    ##  1st Qu.:4.000                                          
    ##  Median :5.000                                          
    ##  Mean   :4.606                                          
    ##  3rd Qu.:5.000                                          
    ##  Max.   :5.000                                          
    ##  NA's   :1                                              
    ##  A - 9. I receive relevant feedback
    ##  Min.   :3.000                     
    ##  1st Qu.:4.000                     
    ##  Median :5.000                     
    ##  Mean   :4.586                     
    ##  3rd Qu.:5.000                     
    ##  Max.   :5.000                     
    ##  NA's   :1                         
    ##  A - 10. I read the recommended readings and notes
    ##  Min.   :3.000                                    
    ##  1st Qu.:4.000                                    
    ##  Median :5.000                                    
    ##  Mean   :4.545                                    
    ##  3rd Qu.:5.000                                    
    ##  Max.   :5.000                                    
    ##  NA's   :1                                        
    ##  A - 11. I use the eLearning material posted
    ##  Min.   :3.000                              
    ##  1st Qu.:4.000                              
    ##  Median :5.000                              
    ##  Mean   :4.707                              
    ##  3rd Qu.:5.000                              
    ##  Max.   :5.000                              
    ##  NA's   :1                                  
    ##  B - 1. Concept 1 of 6: Principles of Business Intelligence and the DataOps Philosophy
    ##  Min.   :1.000                                                                        
    ##  1st Qu.:4.000                                                                        
    ##  Median :4.000                                                                        
    ##  Mean   :4.242                                                                        
    ##  3rd Qu.:5.000                                                                        
    ##  Max.   :5.000                                                                        
    ##  NA's   :1                                                                            
    ##  B - 2. Concept 3 of 6: Linear Algorithms for Predictive Analytics
    ##  Min.   :2.000                                                    
    ##  1st Qu.:3.000                                                    
    ##  Median :4.000                                                    
    ##  Mean   :3.949                                                    
    ##  3rd Qu.:5.000                                                    
    ##  Max.   :5.000                                                    
    ##  NA's   :1                                                        
    ##  C - 2. Quizzes at the end of each concept
    ##  Min.   :2.000                            
    ##  1st Qu.:4.000                            
    ##  Median :5.000                            
    ##  Mean   :4.586                            
    ##  3rd Qu.:5.000                            
    ##  Max.   :5.000                            
    ##  NA's   :1                                
    ##  C - 3. Lab manuals that outline the steps to follow during the labs
    ##  Min.   :3.000                                                      
    ##  1st Qu.:4.000                                                      
    ##  Median :5.000                                                      
    ##  Mean   :4.616                                                      
    ##  3rd Qu.:5.000                                                      
    ##  Max.   :5.000                                                      
    ##  NA's   :1                                                          
    ##  C - 4. Required lab work submissions at the end of each lab manual that outline the activity to be done on your own
    ##  Min.   :3.000                                                                                                      
    ##  1st Qu.:4.000                                                                                                      
    ##  Median :5.000                                                                                                      
    ##  Mean   :4.556                                                                                                      
    ##  3rd Qu.:5.000                                                                                                      
    ##  Max.   :5.000                                                                                                      
    ##  NA's   :1                                                                                                          
    ##  C - 5. Supplementary videos to watch
    ##  Min.   :1.000                       
    ##  1st Qu.:4.000                       
    ##  Median :4.000                       
    ##  Mean   :4.202                       
    ##  3rd Qu.:5.000                       
    ##  Max.   :5.000                       
    ##  NA's   :1                           
    ##  C - 6. Supplementary podcasts to listen to
    ##  Min.   :1.000                             
    ##  1st Qu.:4.000                             
    ##  Median :4.000                             
    ##  Mean   :4.101                             
    ##  3rd Qu.:5.000                             
    ##  Max.   :5.000                             
    ##  NA's   :1                                 
    ##  C - 7. Supplementary content to read C - 8. Lectures slides
    ##  Min.   :1.000                        Min.   :2.000         
    ##  1st Qu.:4.000                        1st Qu.:4.000         
    ##  Median :4.000                        Median :5.000         
    ##  Mean   :4.202                        Mean   :4.596         
    ##  3rd Qu.:5.000                        3rd Qu.:5.000         
    ##  Max.   :5.000                        Max.   :5.000         
    ##  NA's   :1                            NA's   :1             
    ##  C - 9. Lecture notes on some of the lecture slides
    ##  Min.   :2.000                                     
    ##  1st Qu.:4.000                                     
    ##  Median :5.000                                     
    ##  Mean   :4.596                                     
    ##  3rd Qu.:5.000                                     
    ##  Max.   :5.000                                     
    ##  NA's   :1                                         
    ##  C - 10. The quality of the lectures given (quality measured by the breadth (the full span of knowledge of a subject) and depth (the extent to which specific topics are focused upon, amplified, and explored) of learning - NOT quality measured by how fun/comical/lively the lectures are)
    ##  Min.   :2.000                                                                                                                                                                                                                                                                                
    ##  1st Qu.:4.000                                                                                                                                                                                                                                                                                
    ##  Median :5.000                                                                                                                                                                                                                                                                                
    ##  Mean   :4.545                                                                                                                                                                                                                                                                                
    ##  3rd Qu.:5.000                                                                                                                                                                                                                                                                                
    ##  Max.   :5.000                                                                                                                                                                                                                                                                                
    ##  NA's   :1                                                                                                                                                                                                                                                                                    
    ##  C - 11. The division of theory and practice such that most of the theory is done during the recorded online classes and most of the practice is done during the physical classes
    ##  Min.   :2.000                                                                                                                                                                   
    ##  1st Qu.:4.000                                                                                                                                                                   
    ##  Median :5.000                                                                                                                                                                   
    ##  Mean   :4.495                                                                                                                                                                   
    ##  3rd Qu.:5.000                                                                                                                                                                   
    ##  Max.   :5.000                                                                                                                                                                   
    ##  NA's   :1                                                                                                                                                                       
    ##  C - 12. The recordings of online classes
    ##  Min.   :2.000                           
    ##  1st Qu.:4.000                           
    ##  Median :5.000                           
    ##  Mean   :4.354                           
    ##  3rd Qu.:5.000                           
    ##  Max.   :5.000                           
    ##  NA's   :1                               
    ##  D - 1. \r\nWrite two things you like about the teaching and learning in this unit so far.
    ##  Length:100                                                                               
    ##  Class :character                                                                         
    ##  Mode  :character                                                                         
    ##                                                                                           
    ##                                                                                           
    ##                                                                                           
    ##                                                                                           
    ##  D - 2. Write at least one recommendation to improve the teaching and learning in this unit (for the remaining weeks in the semester)
    ##  Length:100                                                                                                                          
    ##  Class :character                                                                                                                    
    ##  Mode  :character                                                                                                                    
    ##                                                                                                                                      
    ##                                                                                                                                      
    ##                                                                                                                                      
    ##                                                                                                                                      
    ##  Average Course Evaluation Rating Average Level of Learning Attained Rating
    ##  Min.   :2.909                    Min.   :2.000                            
    ##  1st Qu.:4.273                    1st Qu.:3.500                            
    ##  Median :4.545                    Median :4.000                            
    ##  Mean   :4.534                    Mean   :4.096                            
    ##  3rd Qu.:4.909                    3rd Qu.:4.500                            
    ##  Max.   :5.000                    Max.   :5.000                            
    ##  NA's   :1                        NA's   :1                                
    ##  Average Pedagogical Strategy Effectiveness Rating
    ##  Min.   :3.182                                    
    ##  1st Qu.:4.091                                    
    ##  Median :4.545                                    
    ##  Mean   :4.441                                    
    ##  3rd Qu.:4.909                                    
    ##  Max.   :5.000                                    
    ##  NA's   :1                                        
    ##  Project: Section 1-4: (20%) x/10 Project: Section 5-11: (50%) x/10
    ##  Min.   : 0.000                   Min.   : 0.000                   
    ##  1st Qu.: 7.400                   1st Qu.: 6.000                   
    ##  Median : 8.500                   Median : 7.900                   
    ##  Mean   : 8.031                   Mean   : 6.587                   
    ##  3rd Qu.: 9.000                   3rd Qu.: 8.300                   
    ##  Max.   :10.000                   Max.   :10.000                   
    ##                                                                    
    ##  Project: Section 12: (30%) x/5 Project: (10%): x/30 x 100 TOTAL
    ##  Min.   :0.000                  Min.   :  0.00                  
    ##  1st Qu.:0.000                  1st Qu.: 58.70                  
    ##  Median :0.000                  Median : 66.40                  
    ##  Mean   :1.025                  Mean   : 62.53                  
    ##  3rd Qu.:1.500                  3rd Qu.: 71.60                  
    ##  Max.   :5.000                  Max.   :100.00                  
    ##  NA's   :1                                                      
    ##  Quiz 1 on Concept 1 (Introduction) x/32 Quiz 3 on Concept 3 (Linear) x/15
    ##  Min.   : 4.75                           Min.   : 3.000                   
    ##  1st Qu.:11.51                           1st Qu.: 7.000                   
    ##  Median :15.22                           Median : 9.000                   
    ##  Mean   :16.29                           Mean   : 9.485                   
    ##  3rd Qu.:19.50                           3rd Qu.:11.750                   
    ##  Max.   :31.25                           Max.   :15.000                   
    ##                                          NA's   :2                        
    ##  Quiz 4 on Concept 4 (Non-Linear) x/22 Quiz 5 on Concept 5 (Dashboarding) x/10
    ##  Min.   : 3.00                         Min.   : 0.000                         
    ##  1st Qu.:10.83                         1st Qu.: 5.000                         
    ##  Median :13.41                         Median : 6.330                         
    ##  Mean   :13.90                         Mean   : 6.334                         
    ##  3rd Qu.:17.50                         3rd Qu.: 7.753                         
    ##  Max.   :22.00                         Max.   :12.670                         
    ##  NA's   :6                             NA's   :12                             
    ##  Quizzes and  Bonus Marks (7%): x/79 x 100 TOTAL
    ##  Min.   :26.26                                  
    ##  1st Qu.:43.67                                  
    ##  Median :55.29                                  
    ##  Mean   :55.97                                  
    ##  3rd Qu.:64.94                                  
    ##  Max.   :95.25                                  
    ##                                                 
    ##  Lab 1 - 2.c. - (Simple Linear Regression) x/5
    ##  Min.   :3.000                                
    ##  1st Qu.:5.000                                
    ##  Median :5.000                                
    ##  Mean   :4.897                                
    ##  3rd Qu.:5.000                                
    ##  Max.   :5.000                                
    ##  NA's   :3                                    
    ##  Lab 2 - 2.e. -  (Linear Regression using Gradient Descent) x/5
    ##  Min.   :2.150                                                 
    ##  1st Qu.:3.175                                                 
    ##  Median :4.850                                                 
    ##  Mean   :4.188                                                 
    ##  3rd Qu.:5.000                                                 
    ##  Max.   :5.000                                                 
    ##  NA's   :6                                                     
    ##  Lab 3 - 2.g. - (Logistic Regression using Gradient Descent) x/5
    ##  Min.   :2.850                                                  
    ##  1st Qu.:4.850                                                  
    ##  Median :4.850                                                  
    ##  Mean   :4.628                                                  
    ##  3rd Qu.:4.850                                                  
    ##  Max.   :5.000                                                  
    ##  NA's   :9                                                      
    ##  Lab 4 - 2.h. - (Linear Discriminant Analysis) x/5
    ##  Min.   :1.850                                    
    ##  1st Qu.:4.100                                    
    ##  Median :4.850                                    
    ##  Mean   :4.425                                    
    ##  3rd Qu.:5.000                                    
    ##  Max.   :5.000                                    
    ##  NA's   :17                                       
    ##  Lab 5 - Chart JS Dashboard Setup x/5 Lab Work (7%) x/25 x 100
    ##  Min.   :0.000                        Min.   : 17.80          
    ##  1st Qu.:0.000                        1st Qu.: 71.25          
    ##  Median :5.000                        Median : 81.00          
    ##  Mean   :3.388                        Mean   : 79.83          
    ##  3rd Qu.:5.000                        3rd Qu.: 97.35          
    ##  Max.   :5.000                        Max.   :100.00          
    ##                                                               
    ##  CAT 1 (8%): x/38 x 100 CAT 2 (8%): x/100 x 100
    ##  Min.   :32.89          Min.   :  0.00         
    ##  1st Qu.:59.21          1st Qu.: 51.00         
    ##  Median :69.08          Median : 63.50         
    ##  Mean   :69.21          Mean   : 62.13         
    ##  3rd Qu.:82.89          3rd Qu.: 81.75         
    ##  Max.   :97.36          Max.   :100.00         
    ##  NA's   :4              NA's   :30             
    ##  Attendance Waiver Granted: 1 = Yes, 0 = No Absenteeism Percentage
    ##  0:95                                       Min.   : 0.00         
    ##  1: 5                                       1st Qu.: 7.41         
    ##                                             Median :14.81         
    ##                                             Mean   :15.35         
    ##                                             3rd Qu.:22.22         
    ##                                             Max.   :51.85         
    ##                                                                   
    ##  Coursework TOTAL: x/40 (40%) EXAM: x/60 (60%)
    ##  Min.   : 7.47                Min.   : 5.00   
    ##  1st Qu.:20.38                1st Qu.:26.00   
    ##  Median :24.58                Median :34.00   
    ##  Mean   :24.55                Mean   :33.96   
    ##  3rd Qu.:29.35                3rd Qu.:42.00   
    ##  Max.   :35.08                Max.   :56.00   
    ##                               NA's   :4       
    ##  TOTAL = Coursework TOTAL + EXAM (100%) GRADE 
    ##  Min.   : 7.47                          A:23  
    ##  1st Qu.:45.48                          B:25  
    ##  Median :58.94                          C:21  
    ##  Mean   :57.15                          D:25  
    ##  3rd Qu.:69.01                          E: 6  
    ##  Max.   :87.72                                
    ## 

### Measure the variance

***Describe the next code chunk here:*** calculates the variance of each
numeric column, disregarding missing values (NAs), and t

``` r
library(dplyr)
```

    ## 
    ## Attaching package: 'dplyr'

    ## The following objects are masked from 'package:stats':
    ## 
    ##     filter, lag

    ## The following objects are masked from 'package:base':
    ## 
    ##     intersect, setdiff, setequal, union

``` r
library(tidyr)

numeric_columns <- student_performance_dataset %>%
    select_if(is.numeric)

variance_df <- numeric_columns %>%
    summarise_all(~var(., na.rm = TRUE)) %>%
    pivot_longer(everything(), names_to = "Column", values_to = "Variance")

print(variance_df, n = Inf)
```

    ## # A tibble: 49 × 2
    ##    Column                                                               Variance
    ##    <chr>                                                                   <dbl>
    ##  1 repeats_since_Y1                                                        4.45 
    ##  2 A - 1. I am enjoying the subject                                        0.355
    ##  3 A - 2. Classes start and end on time                                    0.241
    ##  4 A - 3. The learning environment is participative, involves learning…    0.435
    ##  5 A - 4. The subject content is delivered according to the course out…    0.216
    ##  6 A - 5. The topics are clear and logically developed                     0.330
    ##  7 A - 6. I am developing my oral and writing skills                       0.727
    ##  8 A - 7. I am developing my reflective and critical reasoning skills      0.484
    ##  9 A - 8. The assessment methods are assisting me to learn                 0.425
    ## 10 A - 9. I receive relevant feedback                                      0.306
    ## 11 A - 10. I read the recommended readings and notes                       0.393
    ## 12 A - 11. I use the eLearning material posted                             0.270
    ## 13 B - 1. Concept 1 of 6: Principles of Business Intelligence and the …    0.614
    ## 14 B - 2. Concept 3 of 6: Linear Algorithms for Predictive Analytics       0.742
    ## 15 C - 2. Quizzes at the end of each concept                               0.388
    ## 16 C - 3. Lab manuals that outline the steps to follow during the labs     0.361
    ## 17 C - 4. Required lab work submissions at the end of each lab manual …    0.372
    ## 18 C - 5. Supplementary videos to watch                                    0.775
    ## 19 C - 6. Supplementary podcasts to listen to                              0.949
    ## 20 C - 7. Supplementary content to read                                    0.836
    ## 21 C - 8. Lectures slides                                                  0.529
    ## 22 C - 9. Lecture notes on some of the lecture slides                      0.407
    ## 23 C - 10. The quality of the lectures given (quality measured by the …    0.434
    ## 24 C - 11. The division of theory and practice such that most of the t…    0.477
    ## 25 C - 12. The recordings of online classes                                0.680
    ## 26 Average Course Evaluation Rating                                        0.161
    ## 27 Average Level of Learning Attained Rating                               0.503
    ## 28 Average Pedagogical Strategy Effectiveness Rating                       0.250
    ## 29 Project: Section 1-4: (20%) x/10                                        4.42 
    ## 30 Project: Section 5-11: (50%) x/10                                       7.85 
    ## 31 Project: Section 12: (30%) x/5                                          3.21 
    ## 32 Project: (10%): x/30 x 100 TOTAL                                      408.   
    ## 33 Quiz 1 on Concept 1 (Introduction) x/32                                42.3  
    ## 34 Quiz 3 on Concept 3 (Linear) x/15                                       9.53 
    ## 35 Quiz 4 on Concept 4 (Non-Linear) x/22                                  19.7  
    ## 36 Quiz 5 on Concept 5 (Dashboarding) x/10                                 4.36 
    ## 37 Quizzes and  Bonus Marks (7%): x/79 x 100 TOTAL                       268.   
    ## 38 Lab 1 - 2.c. - (Simple Linear Regression) x/5                           0.156
    ## 39 Lab 2 - 2.e. -  (Linear Regression using Gradient Descent) x/5          1.04 
    ## 40 Lab 3 - 2.g. - (Logistic Regression using Gradient Descent) x/5         0.414
    ## 41 Lab 4 - 2.h. - (Linear Discriminant Analysis) x/5                       0.811
    ## 42 Lab 5 - Chart JS Dashboard Setup x/5                                    5.47 
    ## 43 Lab Work (7%) x/25 x 100                                              375.   
    ## 44 CAT 1 (8%): x/38 x 100                                                228.   
    ## 45 CAT 2 (8%): x/100 x 100                                               609.   
    ## 46 Absenteeism Percentage                                                 83.0  
    ## 47 Coursework TOTAL: x/40 (40%)                                           39.1  
    ## 48 EXAM: x/60 (60%)                                                      128.   
    ## 49 TOTAL = Coursework TOTAL + EXAM (100%)                                250.

### Measure the standard deviation

***Describe the next code chunk here:*** calculates the standard
deviation for “EXAM: x/60 (60%)” column

``` r
standard_deviation <- sd(student_performance_dataset$`EXAM: x/60 (60%)`, na.rm = TRUE)

print(standard_deviation)
```

    ## [1] 11.31549

# Inferential Statistics

## Perform ANOVA

***Describe the next code chunk here:***code is conducting a two-way
Analysis of Variance (ANOVA) to analyze the effects of two categorical
independent variables, class_group and gender, on the dependent variable
Average Course Evaluation Rating.

``` r
student_performance_dataset_anova <- aov(`Average Course Evaluation Rating` ~ class_group +
    gender, data = student_performance_dataset)

summary(student_performance_dataset_anova)
```

    ##             Df Sum Sq Mean Sq F value Pr(>F)  
    ## class_group  2  0.302  0.1508   0.968 0.3834  
    ## gender       1  0.648  0.6482   4.163 0.0441 *
    ## Residuals   95 14.791  0.1557                 
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 1 observation deleted due to missingness

# Qualitative Data Analysis

## Univariate Plots

### Create Histograms

***Describe the next code chunk here:*** code generates histograms for
three different variables (“project_score,” “exam_score,” and
“course_score”)

``` r
project_score <- as.numeric(student_performance_dataset$`Project: (10%): x/30 x 100 TOTAL`)
exam_score <- as.numeric(student_performance_dataset$`EXAM: x/60 (60%)`)
course_score <- as.numeric(student_performance_dataset$`Coursework TOTAL: x/40 (40%)`)

course_score <- course_score[!is.na(course_score)]

par(mfrow = c(2, 2))

# Create a histogram for study time
hist(project_score, main = "Histogram of Project Scores", xlab = "Project Scores",
    ylab = "Frequency", col = "skyblue", border = "black", breaks = 10)

# Create a histogram for exam scores
hist(exam_score, main = "Histogram of Exam Scores", xlab = "Exam Scores", ylab = "Frequency",
    col = "green", border = "black", breaks = 10)

# Create a histogram for quiz scores (after removing missing values)
hist(course_score, main = "Histogram of Quiz Scores", xlab = "Quiz Scores", ylab = "Frequency",
    col = "orange", border = "black", breaks = 10)
```

![](Lab-Submission-Markdown_files/figure-gfm/Your%2011th%20Code%20Chunk-1.png)<!-- -->

### Missingness Map

***Describe the next code chunk here:***checks for missing data patterns
in the “student_performance_dataset”

``` r
if (!is.element("Amelia", installed.packages()[, 1])) {
    install.packages("Amelia", dependencies = TRUE)
}
require("Amelia")
```

    ## Loading required package: Amelia

    ## Loading required package: Rcpp

    ## ## 
    ## ## Amelia II: Multiple Imputation
    ## ## (Version 1.8.1, built: 2022-11-18)
    ## ## Copyright (C) 2005-2023 James Honaker, Gary King and Matthew Blackwell
    ## ## Refer to http://gking.harvard.edu/amelia/ for more information
    ## ##

``` r
# Create a missing data pattern plot for student_performance_dataset
missmap(student_performance_dataset, col = c("red", "green"), legend = TRUE)
```

![](Lab-Submission-Markdown_files/figure-gfm/Your%2012th%20Code%20Chunk-1.png)<!-- -->

## Multivariate Plots

### Create a Scatter Plot

***Describe the next code chunk here:*** creates a scatter plot that
visualizes the relationship between “Study Time” and “Average Course
Evaluation Rating” for the dataset

``` r
library(ggplot2)

ggplot(student_performance_dataset, aes(x = study_time, y = `Average Course Evaluation Rating`)) +
    geom_point() + labs(x = "Study Time", y = "Average Course Evaluation Rating") +
    ggtitle("Scatter Plot: Study Time vs. Average Course Evaluation Rating")
```

![](Lab-Submission-Markdown_files/figure-gfm/Your%2013th%20Code%20Chunk-1.png)<!-- -->

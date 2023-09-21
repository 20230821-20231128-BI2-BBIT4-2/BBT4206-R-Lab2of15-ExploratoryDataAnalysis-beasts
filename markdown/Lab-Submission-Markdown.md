Business Intelligence Lab Submission Markdown
================
<Specify your name here>
<Specify the date when you submitted the lab>

- [Student Details](#student-details)
- [Setup Chunk](#setup-chunk)
- [Loading Dataset](#loading-dataset)

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
student_performance_dataset <- readr::read_csv("data/StudentPerformance.CSV", col_types = readr::cols(class_group = readr::col_factor(levels = c("A",
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

**etc.** as per the lab submission requirements.

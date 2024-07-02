# AI essay grading
 A project examining the consistency between AI writing tools and human graders

 ### Introduction
This was a project for the Lede Program. 

The goal was to explore how Grammarly and Writable, two AI-powered writing tools that are marketed to schools, perform compared to each other and to human graders. I found that the AI scores broadly corresponeded to human scores, with essays that received a score of 5 from humans, for example, receiving better Grammarly and Writable scores, on average, than essays that received a 4 from humans. But within any given human score bucket, both AI mdoels returned a wide range of different scores. The two AI tools also often disagreed with each other on the quality of a particular essay.

I used pandas for the data analysis, Vega-Altair for the charts, and Adobe Illustrator for the essay graphics.

### Data

The data for this project comes from the [PERSUADE 2.0 corpus](https://github.com/scrosseye/persuade_corpus_2.0). The corpus contains more than 25,000 argumentative essays written by students in middle and high school that have been graded on a scale of 1 to 6. Each essay is also annotated with details about the student, including their race/ethnicity, gender, English Language Learner status, and grade level.

### Methodology
Grammarly and Writable both offer free versions or trials of their AI grading systems. While it's possible to upload files in bulk to these systems, doing so with more than 25,000 essays presented a number of problems so I decided to conduct this experiment with a sample of 100 essays from the Persuade 2.0 corpus. The corpus contains essays responding to several different prompts and to ensure the most consistency in my analysis I chose to focus on just one, which asked 10th grade students to argue whether emotion detection technology called the facial action coding system (FACS) would be valuable in classrooms. I wanted to examine how the grading tools performed for students of different races, so using pandas I extracted five random samples of 20 essays responding to the FACS prompt, one each for students who identified as White, Black, Hispanic, Asian or Pacific Islander, or two-or-more races. 

I joined those sampled datasets together into a file called "facial_graded.csv" then looped through the new data set extracting the essay text for each essay and saving it into a .txt file with a filename that matched the unique ID assigned to that essay in the PERSUADE 2.0 corpus. I then created 100 different student accounts in Writablewith the name of an essay's unique ID, uploaded the corresponding essay, and ran it through Writable's grading system. I gave writable the FACS prompt, told it that these essays were persuasive written by high school students, and selected from one of its pre-populated writing rubrics that closely matched the rubric used by the PERSUADE 2.0 graders. Once all 100 essays were graded, I was able to download the results as a .csv file that contained the name of the student (the unique ID) and the Writable score. Using the unique ID field, I joined this data to the "facial_graded.csv" file.

I followed a similar process for Grammarly. I didn't need to create individual student accounts for each essay but I did have to manually enter the Grammarly score for each essay into the "facial_graded.csv" file. Creating student accounts in Writable and manually entering the Grammarly scores were time-consuming steps that limited how many essays I chose to include in my analysis.

Once the "facial_graded.csv" dataset was populated with the scores assigned by human graders (the column 'holistic_essay_score'), Writable score (the column 'Teacher'), and Grammarly scores (the column 'grammarly score'), I was able to preform several different analyses. Using Vega-Altair, I charted the relationship between each essay's Grammaarly and Writable scores and the relationship between the human-assigned scores and the Grammarly and Writable scores. I also examined how students of different races/ethnicities fared under the three grading systems.

### Challenges/Learnings

Through this project I learned a number of new techniques in pandas and how to use Vega-Altair. Particularly challenging but ultimately enlightening steps included:

- Taking a random sample of a dataset with paramaters about how students of different ethnicities were represented in the sample
- Extracting the essay text from the dataset and saving it to a .txt file with a filename that corresponded to the essay's unique ID
- Creating Vega-Altair charts that highlighted specific data points that I used as examples in the story
 

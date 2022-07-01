Install the following packages:
    . numpy:
        . 1st:
            In a terminal window run ' pip install numpy '

        . 2nd:
            Go to 'File' --> 'Settings' --> 'project_name' --> 'Python Interpreter' --> ' numpy '
            see 'https://www.youtube.com/watch?v=pVLmWlRT55E'

    . pandas:
        . 1st:
            In a terminal window run ' pip install pandas '

        . 2nd:
            Go to 'File' --> 'Settings' --> 'project_name' --> 'Python Interpreter' --> ' pandas '

    . seaborn:
        . 1st:
            In a terminal window run ' pip install seaborn '

        . 2nd:
            Go to 'File' --> 'Settings' --> 'project_name' --> 'Python Interpreter' --> ' seaborn '

    . pytest: ' pip install -U pytest '

    . NOTE: if it returns an error try to check if pip, setuptools, and wheel are up to date:
            ' py -m pip install --upgrade pip setuptools wheel '


Program Description:
Visualize and make calculations from medical examination data using matplotlib, seaborn, and pandas.
The dataset values were collected during medical examinations.

This program creates a chart where it shows the counts of good and bad outcomes for the cholesterol, gluc,
alco, active, and smoke variables for patients with cardio=1 and cardio=0 in different panels.

Using the available data, the following tasks in medical_data_visualizer.py will be executed:

. Add an overweight column to the data.
  To determine if a person is overweight, first calculate their BMI by dividing their weight in kilograms
  by the square of their height in meters.
  If that value is > 25 then the person is overweight. Value 0 represents NOT overweight and value 1 for
  overweight.

. Normalize the data by making 0 always good and 1 always bad.
  If the value of cholesterol or gluc is 1, make the value 0.
  If the value is more than 1, make the value 1.

. Convert the data into long format and create a chart that shows the value counts of the categorical
  features using seaborn's catplot().
  The dataset will be split by 'Cardio' so there is one chart for each cardio value.

. Clean the data.
  Filter out the following patient segments that represent incorrect data:
        . diastolic pressure is higher than systolic
          (Keep the correct data with (df['ap_lo'] <= df['ap_hi']))
        . height is less than the 2.5th percentile
          (Keep the correct data with (df['height'] >= df['height'].quantile(0.025)))
        . height is more than the 97.5th percentile
        . weight is less than the 2.5th percentile
        . weight is more than the 97.5th percentile

. Create a correlation matrix using the dataset.
  Plot the correlation matrix using seaborn's heatmap().
  Mask the upper triangle.

Any time a variable is set to None, the program makes sure to set it to the correct code.

Note: see examples figures of the expected output charts.

Data Description:
The rows in the dataset represent patients and the columns represent information like body measurements,
results from various blood tests, and lifestyle choices.
Dataset will be used to explore the relationship between cardiac disease, body measurements, blood markers,
and lifestyle choices.

File name: medical_examination.csv

         Feature	    |     Variable Type     |	Variable	|   Value Type
--------------------------------------------------------------------------------------
          Age           |   Objective Feature	|      age      |   int (days)
--------------------------------------------------------------------------------------
         Height	        |   Objective Feature	|    height	    |    int (cm)
--------------------------------------------------------------------------------------
         Weight	        |   Objective Feature	|    weight     |   float (kg)
--------------------------------------------------------------------------------------
         Gender         |   Objective Feature	|    gender	    | categorical code
--------------------------------------------------------------------------------------
Systolic blood pressure |  Examination Feature	|    ap_hi	    |       int
--------------------------------------------------------------------------------------
Diastolic blood pressure|  Examination Feature	|    ap_lo	    |       int
--------------------------------------------------------------------------------------
         	            |                       |	            |    1: normal,
      Cholesterol       |  Examination Feature	|  cholesterol  | 2: above normal,
                        |                       |               |3: well above normal
--------------------------------------------------------------------------------------
               	        |                   	|       	    |    1: normal,
        Glucose         |  Examination Feature  |      gluc     |  2: above normal,
                        |                       |               |3: well above normal
--------------------------------------------------------------------------------------
        Smoking	        |  Subjective Feature	|      smoke	|       binary
--------------------------------------------------------------------------------------
     Alcohol intake	    |  Subjective Feature	|       alco	|       binary
--------------------------------------------------------------------------------------
    Physical activity	|  Subjective Feature	|      active	|       binary
--------------------------------------------------------------------------------------
   Presence or absence  |                       |               |
    of cardiovascular	|    Target Variable	|      cardio	|       binary
        disease         |                       |               |
--------------------------------------------------------------------------------------


The file test_module.py is a unit test.

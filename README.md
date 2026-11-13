The contents of the file includes a screenshot of the power bi dashboard with several self descriptive charts 
The DAX code used in the course of this visualization are as follows:  
Age Group =
SWITCH(
    TRUE(),
    'Hospital Encounters Data'[Age] < 30, "18–29",
    'Hospital Encounters Data'[Age] < 50, "30–49",
    'Hospital Encounters Data'[Age] < 65, "50–64",
    "65+"
)
Total Encounters = COUNTROWS('Hospital Encounters Data')

Total Billed Revenue = SUM('Hospital Encounters Data'[TreatmentCost])

ALOS = ROUND(AVERAGE('Hospital Encounters Data'[LengthOfStay]), 1)

Readmission Rate % =
DIVIDE(
    CALCULATE(COUNTROWS('Hospital Encounters Data'), 'Hospital Encounters Data'[Readmitted] = "Yes"),
    [Total Encounters]
)

Emergency Admission Rate % =
DIVIDE(
    CALCULATE(COUNTROWS('Hospital Encounters Data'), 'Hospital Encounters Data'[AdmissionType] = "Emergency"),
    [Total Encounters]
)

Avg Patient Satisfaction = AVERAGE('Hospital Encounters Data'[SatisfactionScore])

Avg Treatment Cost = AVERAGE('Hospital Encounters Data'[TreatmentCost])

# NDSS Scoring Framework

Calculate the scores automatically after completing each evaluation.

## Rating Scale

- **2** = Fully Met
- **1** = Partially Met / Opportunity Exists
- **0** = Improvement Required
- **N/A** = Not Applicable

## Criterion Weights

EARNT Score



If(
 Compliance   "No" ||
 Behaviour = "No" ||
 System Usage = "No",
 0,
If(
    Opening = "N/A",
    0,
    Value(Opening) * 3
)
+
If(
    Empathy = "N/A",
    0,
    Value(Empathy) * 6
)
+
If(
    Customer Recognition = "N/A",
    0,
    Value(Customer Recognition) * 2
)
+
If(
    Active Listening = "N/A",
    0,
    Value(Active Listening) * 3
)
+
If(
    Efficient Messaging & Writing Style = "N/A",
    0,
    Value(Efficient Messaging & Writing Style) * 3
)
+
If(
    Closing = "N/A",
    0,
    Value(Closing) * 3
)
+
If(
    Relevant Information = "N/A",
    0,
    Value(Relevant Information) * 5
)
+
If(
    Completeness = "N/A",
    0,
    Value(Completeness) * 4
)
+
If(
    Transfer Process = "N/A",
    0,
    Value(Transfer Process) * 2
)
+
If(
    Reasoning / Ownership = "N/A",
    0,
    Value(Reasoning / Ownership) * 4
)
+
If(
    Promoting Emirates Features = "N/A",
    0,
    Value(Promoting Emirates Features) * 7
)
+
If(
    Strategic Sales Opportunities = "N/A",
    0,
    Value(Strategic Sales Opportunities) * 8
))


Applicable MAX Score



If(Opening<>"N/A",6,0)+
If(Empathy<>"N/A",12,0)+
If(Customer Recognition<>"N/A",4,0)+
If(Active Listening<>"N/A",6,0)+
If(Efficient Messaging & Writing Style<>"N/A",6,0)+
If(Closing<>"N/A",6,0)+
If(Relevant Information<>"N/A",10,0)+
If(Completeness<>"N/A",8,0)+
If(Transfer Process<>"N/A",4,0)+
If(Reasoning / Ownership<>"N/A",8,0)+
If(Promoting Emirates Features<>"N/A",14,0)+
If(Strategic Sales Opportunities<>"N/A",16,0)




Score %



Round(
    (
        Value(EarntScore_DataCard1.Update) /
        (
            If(Opening<>"N/A",6,0)+
            If(Empathy<>"N/A",12,0)+
            If(Customer Recognition<>"N/A",4,0)+
            If(Active Listening<>"N/A",6,0)+
            If(Efficient Messaging & Writing Style<>"N/A",6,0)+
            If(Closing<>"N/A",6,0)+
            If(Relevant Information<>"N/A",10,0)+
            If(Completeness<>"N/A",8,0)+
            If(Transfer Process<>"N/A",4,0)+
            If(Reasoning / Ownership<>"N/A",8,0)+
            If(Promoting Emirates Features<>"N/A",14,0)+
            If(Strategic Sales Opportunities<>"N/A",16,0)
        )
    ) * 100,
    0
)


Healthy Range




With(
{
    ScorePct:
    Round(
        (
            Value(EarntScore_DataCard1.Update) /
            (
                If(Opening<>"N/A",6,0)+
                If(Empathy<>"N/A",12,0)+
                If(Customer Recognition<>"N/A",4,0)+
                If(Active Listening<>"N/A",6,0)+
                If(Efficient Messaging & Writing Style<>"N/A",6,0)+
                If(Closing<>"N/A",6,0)+
                If(Relevant Information<>"N/A",10,0)+
                If(Completeness<>"N/A",8,0)+
                If(Transfer Process<>"N/A",4,0)+
                If(Reasoning / Ownership<>"N/A",8,0)+
                If(Promoting Emirates Features<>"N/A",14,0)+
                If(Strategic Sales Opportunities<>"N/A",16,0)
            )
        ) * 100,
        2
    )
},
If(
    ScorePct >= 90,
    "Thriving",
    If(
        ScorePct >= 75,
        "Healthy",
        If(
            ScorePct >= 60,
            "Getting There",
            "Critical"
        )
    )
)
)

README: shared data for the TADS adversity and learning-trajectory analyses
====================================================================================================

File: CTQ_RL_data.csv

This is the analysis-ready dataset used for the main analyses: long format, one row per participant
per study wave, containing the learning measures from the PoP-ORL computational model (after model
fitting), the traditional task scores, the Childhood Trauma Questionnaire (CTQ) scores, and the
covariates used in the models.

Rows: 528 participant-waves from 166 participants (T1 n = 166, T2 n = 130, T3 n = 107, T4 n = 71, T5 n = 54).
Columns: 56 (listed below). Missing values are coded NA.

Sample notes: Only participants with complete data on age, sex, nonverbal IQ and all CTQ scales
(except Minimization/Denial) were retained. 

====================================================================================================
VARIABLE DICTIONARY
====================================================================================================
For each variable: description, then the observed range in this file and the number of NA rows.

Identifiers and study design
----------------------------


id
    Participant ID (4-digit study ID beginning with 5). Rows with the same id belong to the same
    participant.
    Observed: 5000 to 5347; NA: 0

time
    Study wave of the task session: T1 (baseline), T2, T3, T4, T5. Roughly 9 months apart.
    Observed: values: T1, T2, T3, T4, T5; NA: 0

T
    Numeric wave index: 0 for T1, 1 for T2, 2 for T3, 3 for T4, 4 for T5.
    Observed: 0 to 4; NA: 0


Demographics / covariates
-------------------------------------------------

age
    Age (years, decimal) at the PoP-IGT session for that wave, read from the lab's demographics file
    (variables T1_IGT_Age_Child ... T5_IGT_Age_Child; recorded to one decimal place). 
    Observed: 9 to 17.1; NA: 0

baseline_age
    Participant's age at T1 (age at the baseline session), repeated on every row for that
    participant.
    Observed: 9 to 14; NA: 0

age_centered
    age minus the mean baseline (T1) age of the analysis sample (10.99 years, SD 1.48, n = 166).
    Used as the age term in the growth models.
    Observed: -1.992 to 6.108; NA: 0

age_squared
    age_centered squared. Used as the quadratic age term.
    Observed: 0 to 37.306; NA: 0

child_sex
    Sex assigned at birth: 0 = male, 1 = female.
    Observed: 0 to 1; NA: 0

race_T1
    Child race reported at baseline (T1), repeated on every row of the participant: 1 = White/Caucasian,
    2 = Black/African American, 3 = Asian, 4 = Pacific Islander, 5 = Native American/Alaskan Native,
    6 = Multiracial, 7 = Not listed (other). NA = did not report race (prefer not to answer or missing).
    Observed: 1 to 7 (codes present: 1, 2, 3, 6, 7); NA: 70 rows (26 participants at baseline)

NonVerbal_Std
    Nonverbal IQ: K-BIT standard score (child), collected at baseline and repeated on every row for
    that participant.
    Observed: 57 to 147; NA: 0

NonVerbal_Std_centered
    NonVerbal_Std minus the mean NonVerbal_Std among T1 rows. Used as a covariate in the models.
    Observed: -44.319 to 45.681; NA: 0

eprime
    Task administration mode for that session: 1 = in the lab with E-Prime; 0 = remote with
    PsychoPy/Pavlovia. Included as a covariate in all longitudinal models.
    Observed: 0 to 1; NA: 0




Computational model (PoP-ORL) parameters, individual posterior means from the PoP-ORL, fit separately to each wave's data.
--------------------------------------------------------------------

Arew
    Reward Learning Rate (A_rew) from the PoP-ORL model: each participant-wave's posterior mean on
    the 0-1 learning-rate scale. 
    Observed: 0.008 to 0.375; NA: 0

Apun
    Punishment Learning Rate (A_pun) from the PoP-ORL model: posterior mean on the 0-1 learning-rate
    scale.
    Observed: 0.01 to 0.426; NA: 0

betaF
    Win/Loss Frequency Sensitivity (beta_f) from the PoP-ORL model: posterior mean.
    Observed: -8.389 to 19.167; NA: 0

betaB
    Go Bias (beta_b) from the PoP-ORL model: posterior mean. Higher = greater general tendency to
    play (rather than pass).
    Observed: -0.605 to 2.819; NA: 0

Arew_qnormed
    Reward Learning Rate on the probit (normal-quantile, qnorm) scale. This is the version of the learning rate
    used in the growth models.
    Observed: -2.585 to -0.374; NA: 0

Apun_qnormed
    Punishment Learning Rate on the probit (normal-quantile, qnorm) scale. This is the version of the learning rate used in the growth models.
    Observed: -2.42 to -0.192; NA: 0

Overall_A
    Overall learning rate (the Averaged Single Learning Rate in the paper): the mean of Arew_qnormed
    and Apun_qnormed, (Arew_qnormed + Apun_qnormed) / 2.
    Observed: -2.102 to -0.793; NA: 0





Traditional (model-free) task scores. Note: the paper's primary traditional scores are computed from the last block of the task. Secondary analyses use traditional task scores computed from the full task data. 
------------------------------------------------------------------------

good_proportion
    Good Deck Proportion, full task: proportion of trials with a 'play' choice among the trials on
    good decks (Decks C and D), across all 120 trials. Used in the secondary full-task analyses.  
    Observed: 0.15 to 1; NA: 0

bad_proportion
    Bad Deck Proportion, full task: proportion of 'play' choices among trials on bad decks (Decks A
    and B), across all 120 trials.
    Observed: 0.117 to 0.983; NA: 0

net_good_bad
    Net Performance, full task: good_proportion - bad_proportion.
    Observed: -0.417 to 0.65; NA: 0

good_proportion_LastBlock
    Good Deck Proportion, last block (trials 81-120): proportion of 'play' choices among trials on
    good decks (Decks C and D). Primary traditional learning metric in the paper.
    Observed: 0 to 1; NA: 0

bad_proportion_LastBlock
    Bad Deck Proportion, last block (trials 81-120): proportion of 'play' choices among trials on
    bad decks (Decks A and B).
    Observed: 0 to 1; NA: 0

net_good_bad_LastBlock
    Net Performance, last block: good_proportion_LastBlock - bad_proportion_LastBlock. In the paper
    this is expressed in percentage points (x 100).
    Observed: -0.55 to 1; NA: 0





The individual deck variables below were used as the outcomes of the unconditional growth models for the proportion of cards played from each deck (Supplemental Table 8). 
------------------------------------------------------------------------

deckA_proportion
    Proportion of Deck A cards (a bad deck) that the participant played rather than passed, across
    all 120 trials.
    Observed: 0.133 to 1; NA: 0

deckB_proportion
    Proportion of Deck B cards (a bad deck) that the participant played, across all 120 trials.
    Observed: 0.067 to 1; NA: 0

deckC_proportion
    Proportion of Deck C cards (a good deck) that the participant played, across all 120 trials.
    Observed: 0.1 to 1; NA: 0

deckD_proportion
    Proportion of Deck D cards (a good deck) that the participant played, across all 120 trials.
    Observed: 0.133 to 1; NA: 0






Childhood Trauma Questionnaire (CTQ), baseline, uncentered
----------------------------------------------------------

ctq_EA_T1_avg
    CTQ Emotional Abuse subscale score at baseline (T1). Scored on the 5-25 scale: mean of the
    5 items x 5, coded NA if 25% or more of the items are missing. Same value on every row for a
    participant.
    Observed: 5 to 18; NA: 0

ctq_PA_T1_avg
    CTQ Physical Abuse subscale score at baseline (T1). Scored on the 5-25 scale: mean of the
    5 items x 5, coded NA if 25% or more of the items are missing. Same value on every row for a
    participant.
    Observed: 5 to 25; NA: 0

ctq_SA_T1_avg
    CTQ Sexual Abuse subscale score at baseline (T1). Scored on the 5-25 scale: mean of the 5
    items x 5, coded NA if 25% or more of the items are missing. Same value on every row for a
    participant.
    Observed: 5 to 13; NA: 0

ctq_EN_T1_avg
    CTQ Emotional Neglect subscale score at baseline (T1). Scored on the 5-25 scale: mean of
    the 5 items x 5, coded NA if 25% or more of the items are missing. Reverse-coded items are used
    where applicable. Same value on every row for a participant.
    Observed: 5 to 24; NA: 0

ctq_PN_T1_avg
    CTQ Physical Neglect subscale score at baseline (T1). Scored on the 5-25 scale: mean of
    the 5 items x 5, coded NA if 25% or more of the items are missing. Reverse-coded items are used
    where applicable. Same value on every row for a participant.
    Observed: 5 to 19; NA: 0

ctq_A_T1_avg
    Abuse composite (dimensional) at baseline: ctq_EA_T1_avg + ctq_PA_T1_avg + ctq_SA_T1_avg (NA if
    any is NA).
    Observed: 15 to 45; NA: 0

ctq_N_T1_avg
    Neglect composite (dimensional) at baseline: ctq_PN_T1_avg + ctq_EN_T1_avg (NA if either is NA).
    Observed: 10 to 39; NA: 0

ctq_tot_avg
    CTQ total score at baseline: mean of the 25 clinical items (the five subscales; excludes the
    Minimization/Denial items) x 25; NA if 25% or more of the items are missing.
    Observed: 25 to 79; NA: 0

ctq_mdr_T1
    CTQ Minimization/Denial score at baseline: number (0-3) of the three validity items (CTQ items
    10, 16, 22) answered 5 (the highest response) = the item is scored 1, otherwise 0; summed. NA if
    any of the 3 items is missing.
    Observed: 0 to 3; NA: 11




CTQ variables, mean-centered across all rows (suffix _c)
--------------------------------------------------------

ctq_EA_T1_c
    ctq_EA_T1_avg, mean-centered (the mean of all rows in this file subtracted).
    Observed: -1.76 to 11.24; NA: 0

ctq_PA_T1_c
    ctq_PA_T1_avg, mean-centered (the mean of all rows in this file subtracted).
    Observed: -0.902 to 19.098; NA: 0

ctq_SA_T1_c
    ctq_SA_T1_avg, mean-centered (the mean of all rows in this file subtracted).
    Observed: -0.152 to 7.848; NA: 0

ctq_EN_T1_c
    ctq_EN_T1_avg, mean-centered (the mean of all rows in this file subtracted).
    Observed: -2.343 to 16.657; NA: 0

ctq_PN_T1_c
    ctq_PN_T1_avg, mean-centered (the mean of all rows in this file subtracted).
    Observed: -1.828 to 12.172; NA: 0

ctq_A_T1_c
    ctq_A_T1_avg (Abuse composite), mean-centered (the mean of all rows in this file subtracted).
    Observed: -2.813 to 27.187; NA: 0

ctq_N_T1_c
    ctq_N_T1_avg (Neglect composite), mean-centered (the mean of all rows in this file subtracted).
    Observed: -4.171 to 24.829; NA: 0

ctq_tot_c
    ctq_tot_avg, mean-centered (the mean of all rows in this file subtracted).
    Observed: -6.968 to 47.032; NA: 0





CTQ variables, centered among rows with a Minimization/Denial score (suffix _mdr_c)
Note: since the Minimization/Denial sub-scale was only available for a sub-set of participants, the CTQ variables were centered in this sub-set of the data, specifically for analyses that used the Minimization/Denial sub-scale
-----------------------------------------------------------------------------------

ctq_EA_T1_mdr_c
    ctq_EA_T1_avg centered at its mean among rows that have a Minimization/Denial score. For the
    Minimization/Denial-adjusted analyses.
    Observed: -1.763 to 11.237; NA: 0

ctq_PA_T1_mdr_c
    ctq_PA_T1_avg centered at its mean among rows that have a Minimization/Denial score. For the
    Minimization/Denial-adjusted analyses.
    Observed: -0.897 to 19.103; NA: 0

ctq_SA_T1_mdr_c
    ctq_SA_T1_avg centered at its mean among rows that have a Minimization/Denial score. For the
    Minimization/Denial-adjusted analyses.
    Observed: -0.155 to 7.845; NA: 0

ctq_EN_T1_mdr_c
    ctq_EN_T1_avg centered at its mean among rows that have a Minimization/Denial score. For the
    Minimization/Denial-adjusted analyses.
    Observed: -2.377 to 16.623; NA: 0

ctq_PN_T1_mdr_c
    ctq_PN_T1_avg centered at its mean among rows that have a Minimization/Denial score (ctq_mdr_T1
    not NA). For the analyses that adjust for Minimization/Denial.
    Observed: -1.844 to 12.156; NA: 0

ctq_A_T1_mdr_c
    ctq_A_T1_avg (Abuse composite) centered at its mean among rows that have a Minimization/Denial
    score.
    Observed: -2.815 to 27.185; NA: 0

ctq_N_T1_mdr_c
    ctq_N_T1_avg (Neglect composite) centered at its mean among rows that have a Minimization/Denial
    score.
    Observed: -4.221 to 24.779; NA: 0

ctq_tot_mdr_c
    ctq_tot_avg centered at its mean among rows that have a Minimization/Denial score.
    Observed: -7.019 to 46.981; NA: 0

ctq_mdr_T1_mdr_c
    ctq_mdr_T1 (Minimization/Denial score) centered at its mean among rows that have a
    Minimization/Denial score.
    Observed: -1.219 to 1.781; NA: 11





====================================================================================================
ABBREVIATIONS
====================================================================================================
  CTQ            Childhood Trauma Questionnaire (Short Form)
  EA / PA / SA   Emotional / Physical / Sexual Abuse subscales
  EN / PN        Emotional / Physical Neglect subscales
  PoP-IGT        Play-or-Pass version of the Iowa Gambling Task
  PoP-ORL        Play-or-Pass Outcome-Representation Learning computational model
  K-BIT          Kaufman Brief Intelligence Test
  T1-T5          Study waves (T1 = baseline)

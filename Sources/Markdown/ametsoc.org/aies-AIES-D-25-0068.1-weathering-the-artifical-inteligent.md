---
type: source
created: '2026-09-30'
tags: []
status: seed
source_type: pdf
origin: Sources/Research Paper/ametsoc.org/aies-AIES-D-25-0068.1-weathering-the-artifical-inteligent.pdf
author: 'Pope, Dale, Steele, Graham'
published: 2026
retrieved: '2026-09-30'
immutable: true
---

# Weathering the Artificial Intelligence revolution: public attitudes to potential adoption of Machine Learning-based forecasts

<!-- Verbatim content only. Never edit the material below this line. -->

---

<!-- SHEET 1 of 24 -->

Manuscript (non-LaTeX)
Weathering the Artificial Intelligence revolution: public attitudes to
potential adoption of Machine Learning-based forecasts.
a, a, a, a
Edward C. D. Pope Kirstine I. Dale Edward C. C. Steele Philippa H. R. Graham
a
Met Office, Fitzroy Road, Exeter, United Kingdom
.
Pope,
Corresponding authors: Edward C. D. Edward.pope@metoffice.gov.uk; Kirstine I.
Dale, kirstine.dale@metoffice.gov.uk
File generated with AMS Word template 2.0
1
Early Online Release: This preliminary version has been accepted for publication in Artificial
Intelligence for the Earth Systems, may be fully cited, and has been assigned DOI 10.1175/AIES-
D-25-0068.1. The final typeset copyedited article will replace the EOR at the above DOI when it is published.
the default AMS reuse license. For information regarding reuse and general copyright information, consult the
AMS Copyright Policy (www.ametsoc.org/PUBSReuseLicenses).
Unauthenticated | Downloaded 09/27/26 04:12 PM UTC

---

<!-- SHEET 2 of 24 -->

ABSTRACT
We present the results from a survey of over 6,000 members of the UK public to understand
how they view the potential accuracy of Machine Learning Weather Prediction (MLWP)
forecasts, how confident they would feel using this information to make decisions, and how
these views compare to their opinions of physics-based Numerical Weather Prediction
(NWP) forecasts. Most respondents (~78%) perceive current NWP forecasts as accurate, with
only a very small proportion (~1%) indicating that they “Don’t know” the accuracy of these
forecasts. This perception is consistent across age, gender, social grade, and geographic
regions across the UK. In contrast, there is much less agreement across groups about the
potential accuracy of MLWP forecasts: only around 47% of respondents believe these
forecasts would be accurate, with roughly a fifth of respondents indicating they “Don’t
know” what the accuracy of ML-based forecasts would be. These findings highlight a
contrast between current perceptions of NWP, shaped through direct experience, and current
perceptions of MLWP, shaped largely by prior beliefs. However, the high agreement for
perceived accuracy of physics-based NWP forecasts suggests that users may be willing to
update their beliefs about MLWP capabilities, and that direct experience of using the
information is likely to be important. The diverse perceptions across demographic,
socioeconomic, and regional groups, together with emerging research on AI’s role in weather
forecasting and risk communication, underscore the need for broader public engagement.
This engagement should not only identify potential concerns, but also inform user-centred
solutions that can be embedded within forecast systems to strengthen trust and confidence.
1. Introduction
As the Artificial Intelligence (AI) Revolution (Clark et al., 2019; UKRI, 2021) continues
to gain pace, its impact is rippling across all aspects of society - rewriting the rules of entire
industries (HM Government, 2021) and fundamentally changing the way we work and live.
This is as true in meteorology as it is for any other sector, with recent years bearing witness
to a step-change in the performance of machine learning (ML) models for predicting the
weather (Keisler 2022, Lam et al. 2022, Pathak et al. 2022, Bi et al. 2023, Chen et al. 2023a,
Ben Bouallègue et al. 2024). Machine Learning Weather Prediction (MLWP) offers the
promise of increased accuracy and timeliness (de Burgh-Day and Leeuwenburg 2023) and,
2
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 3 of 24 -->

while model training costs remain significant, the computational cost of running the trained
model, referred to as ‘inference’, is several orders of magnitude less than Numerical Weather
Prediction (NWP) (Nipen et al. 2024). With increasing sophistication and improving
performance, MLWP models are rapidly approaching the point when they may be used
alongside physics-based NWP in operational systems to deliver forecasts for the public.
At the same time, the broader landscape of AI governance is evolving rapidly:
governments and regulatory bodies are introducing transparency requirements about AI use,
such as the EU AI Act, alongside national policies and standards that seek to define and
refine requirements around accountability and the responsible use of AI. Complementary
initiatives such as the UK’s Algorithmic Transparency Recording Standard (ATRS) illustrate
a broader movement towards documenting and communicating the use of algorithmic tools in
within the public sector. In this context, the term “algorithmic tools” is used as a broad
descriptor that covers applications of AI, statistical modelling and advanced computational
methods. These considerations are also increasingly important for the weather and climate
community, as AI capabilities continue to advance, alongside growing expectations for
transparency.
Building and maintaining trust in weather forecasts are especially critical for National
Meteorological Services, where a lack of user trust could have serious implications for lives
and livelihoods, particularly if it undermines the effectiveness of public weather warnings.
More broadly, there is growing recognition of the need for equitable weather and climate
services that ensure all communities, especially vulnerable groups, can benefit from timely
and actionable information. While equity has been more widely explored in climate services
(e.g. Doblas-Reyes, et al, 2024), there are strong reasons to incorporate similar thinking into
weather forecast services.
Addressing the challenges of trust and equity makes it increasingly important to
understand how users, including the public, perceive and respond to MLWP-based forecasts,
particularly as such systems are becoming more operationally relevant. However, research on
perceptions of MLWP remains limited, with most studies focusing on differences among
professional user groups, including forecasters and domain experts. Within these groups,
evidence suggests cautious optimism about the potential of AI to enhance weather warnings,
tempered by concerns about over-reliance (Kox et al. 2025). Expert users also differ in their
priorities, with some preferring data timeliness and availability, and others valuing clarity on
3
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 4 of 24 -->

system limitations (Harrison et al. 2025). Interestingly, one study found that labeling products
as AI or ML did not reduce trust and, in some cases, increased enthusiasm (Wirz et al. 2024).
We note that some of the concerns about MLWP among expert users are reminiscent of
scepticism that marked the early development of NWP (Martin-Nielsen, 2017), reinforcing
the gradual nature of trust-development, and the importance of aligning system design with
user needs (Cain et al. 2024).
A small but growing body of research has also examined the role of AI in weather
forecasting and risk communication across diverse user groups. Such work underscores two
key points: (i) trust is not a fixed property of technology, but an evolving judgment shaped by
user experience and context, even when systems adhere to formal standards (Wirz et al.
2025); and (ii) realising the potential of AI to help mitigate compounding weather-related
risks without introducing new ones requires a nuanced understanding of trustworthiness. This
includes consideration of decision-making needs, the intrinsic and contextual quality of
information, model development processes, and transparency (McGovern et al. 2024).
With the growing ambition to embed AI and ML into public services (HM Government,
2025), there is a clear need to systematically collate and explore public perceptions of these
technologies. These efforts should build on the expanding body of research outlined above,
ensuring that insights are translated into effective and practical engagement strategies. Doing
so will not only support the development of transparency and trust, but will also advance our
understanding of public acceptance, and the conditions under which emerging technologies
can be responsibly deployed.
To this end, several UK public surveys have benchmarked general attitudes and concerns
regarding the use of AI, including the annual ‘Public attitudes to data and AI: Tracker survey’
run by the Centre for Data Ethics and Innovation since 2022. However, to date, no surveys
have specifically focused on public perceptions of AI in the context of operational weather
forecasting. This study addresses that gap, with the aim of informing further anticipated
integration of AI-based methods within public service weather forecasts. In particular, the
findings could contribute to an emerging evidence base to inform approaches for the
adoption, and effective integration of MLWP alongside NWP.
Achieving these objectives requires the use of clear and consistent terminology to build a
shared understanding between the scientific community and the public. However, the
4
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 5 of 24 -->

increasing prevalence of technical language in this domain can introduce ambiguity,
particularly in public-facing contexts. In public surveys, the term “AI” is more commonly
used than “ML,” reflecting its broader and more intuitive framing. To maintain clarity, we
use “ML” when referring to the scientific forecasting capability and “AI” in survey questions
posed to the public, ensuring technical accuracy and accessibility, while minimising the risk
of misinterpretation.
2. Public Survey of accuracy and confidence
Every year, the UK Met Office commissions research to understand consumers’
perceptions of its Public Weather Service (PWS). To assess current public perceptions about
MLWP forecast accuracy, and confidence using forecast information for decision-making, we
incorporated the following targeted questions in recent PWS surveys, with responses given
on a Likert scale:
1) Have you ever heard of the term Artificial Intelligence (AI)?
2) How accurate, if at all, do you think most weather forecasts are for the following
types of weather?
a. Daily weather – e.g. sunshine, light rain showers
b. Severe weather – e.g. thunderstorms, very strong winds
3) Artificial Intelligence (AI) involves using computers and machines to do things that
have traditionally been done by humans. This includes creating ways to categorise, analyse,
and make predictions from data. AI is currently used in a variety of everyday situations from
facial recognition to medical diagnostics tools. Traditional weather forecasts are physics-
based, but AI shows significant potential for use in weather forecasting. How accurate, if at
all, do you think AI-generated forecasts would be for the following types of weather?
a. Daily weather – e.g. sunshine, light rain showers
b. Severe weather – e.g. thunderstorms, very strong winds
4) How confident, if at all, are you using weather forecasts when making the following
types of decisions?
5
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 6 of 24 -->

a. Typical daily decisions – those concerning daily tasks such as commuting to work,
household chores, also leisure activities such as having a barbecue or taking part in
sport/exercise
b. Important decisions – those concerning the impacts of severe weather on you, your
property or vulnerable people you care for, your plans for important events such as a
wedding, or decisions impacting livelihood (industries such as farming or construction)
5) How confident, if at all, do you think you would be when making these decisions
using AI-generated weather forecasts?
a. Typical daily decisions – those concerning daily tasks such as commuting to work,
household chores, also leisure activities such as having a barbecue or taking part in
sport/exercise
b. Important decisions – those concerning the impacts of severe weather on you, your
property or vulnerable people you care for, your plans for important events such as a
wedding, or decisions impacting livelihood (industries such as farming or construction)
The surveys were conducted using an online interview administered to members of the
YouGov Plc UK panel of 2.5 million+ individuals who have agreed to take part in surveys.
E-mails are sent to panelists selected at random from the base sample inviting them to take
part in a survey and via a generic survey link. Once a panel member clicks on the link they
are directed to the survey that they are most required for, according to the sample definition
and quotas which ensure the responses reflect the UK adult population by age, gender,
region, and social grade. Invitations to surveys do not expire and respondents can be sent to
any available survey.
Following the protocol outlined above, a total of 6,022 UK adults aged 18+ were
surveyed in three waves - October 2024 (2,043 people), January 2025 (2,011 people) and
April 2025 (1,968 people). Summary statistics show that differences between the sample and
national population are minimal, being typically less than 1% for most groups and never
exceeding 6%. While the sample is largely representative of the UK population, we want to
avoid over-generalising and, therefore, use the raw data, i.e. we did not apply weights which
are sometimes used to make the survey data fully representative of the UK adult population.
Clearly, the public are not currently using a machine learning weather forecast, so the
public perceptions contrast direct experience of current forecasts (based on NWP), with prior
6
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 7 of 24 -->

beliefs about MLWP forecasts based on their knowledge about AI and other factors described
above. The survey responses, therefore, provide a baseline against which we can compare
changing perceptions as the public becomes more familiar with MLWP. To some extent, the
survey questions represent a false dichotomy in that many weather forecasting capabilities of
the future will involve a blend of physics-based and machine learning components (Shipway
et al., 2026). However, asking separate questions about NWP and MLWP is necessary for
understanding prior beliefs, and enables us to explore with more clarity how labelling a
forecast as MLWP could influence public perceptions of its accuracy, and their confidence
using the information for making decisions. Caution is, therefore, needed when interpreting
absolute differences between the public perceptions of NWP and MLWP forecasts, because
responses based on personal experience (potentially associated with a human forecaster) may
not be directly comparable to perceptions about something that is largely unknown. Perhaps
more important are the differing perceptions of NWP and MLWP within each demographic,
socioeconomic and regional group, which will be important considerations when engaging
with the public about evolving weather forecasting capabilities.
3. Perceptions of accuracy and confidence
The responses to Question 1 (Figure 1) show that more than 95% (5,751/6,022) of
respondents had previously heard of AI, comparable with other recent surveys (Public
attitudes to data and AI: Tracker survey (Wave 4) report - GOV.UK). Just over 20%
(1,291/6,022) reported that they could explain AI in detail, with nearly 60% able to give a
partial explanation. In our full dataset (not presented here), self-reported AI knowledge shows
differences between demographic, socioeconomic and regional groups, which may affect how
MLWP forecasts are perceived and used by different parts of the population (discussed later).
Further research is needed to understand specific concerns and how to build trust across these
different groups so that everyone can benefit from new capabilities, potentially involving
tailored engagement strategies, including further surveys, workshops, and focus groups.
7
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 8 of 24 -->

Fig. 1: Self-reported AI knowledge (Question 1: have you ever heard of the term Artificial
Intelligence (AI)?).
Public perceptions of NWP and MLWP forecast accuracy are shown in Figure 2. Roughly
~78% of respondents rated NWP forecasts as either “Very accurate” or “Slightly accurate”,
compared to 45-48% for MWLP forecasts, both for daily and severe weather. In addition,
~20% of respondents “Don’t know” how accurate MLWP forecasts would be, compared to
only 0.5-1% for NWP forecasts. We see a similar pattern in responses about confidence using
forecast information for daily and important decisions (Figure 3), with 80-88% of
respondents confident using NWP information, compared to 40-44% for MWLP forecasts.
Roughly 17% of respondents “Don’t know” how confident they would be using MLWP
forecasts, compared to 2-4% for NWP. In each case, the more even spread in responses about
MLWP forecast accuracy and confidence using the information suggests a degree of rational
scepticism, i.e. in the absence of direct experience, the public is yet to reach a consensus
about potential AI forecasting capabilities and how to use them.
8
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 9 of 24 -->

Fig. 2: Perceptions of forecast accuracy for NWP (Question 2; blue) and MLWP (Question 3; red)
for typical daily weather (a; upper panel) and severe weather (b; lower panel).
9
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 10 of 24 -->

Fig. 3: Confidence using NWP weather forecasts (Question 4; blue) and MLWP (Question 5; red)
for typical daily decisions (a; upper panel) and important decisions (b; lower panel).
10
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 11 of 24 -->

The processed survey data provided to the Met Office are organised into blocks that
represent demographic, socioeconomic and regional groups, as well as self-reported AI
knowledge. As shown in the top-row of Table 1, each block contains between 2 groups (e.g.
gender) and 13 groups (e.g. region), enabling us to explore how perceptions vary between
groups within a block (for example, their dependence on age). However, because the
processed survey data provided by YouGov are aggregated at the group level, individual
responses are not available, and it is not possible to explore how perceptions vary
simultaneously across multiple characteristics. For this reason, the analysis is limited to
summarising the top-level findings for each block, noting that there will be latent factors that
influence perceptions which this survey does not capture.
To illustrate these patterns, Table 1 summarises the groups with the highest and lowest
fraction of respondents who perceive forecasts as accurate and who would be confident using
them for both NWP and MLWP. The corresponding numerical values are presented in Figure
4, where they are represented by the endpoints of the connected dots (often referred to as
“dumbbells”). For example, in response to Question 2a, the South East regional group had the
highest fraction of respondents who perceived NWP forecasts as accurate, while Wales had
the lowest fraction. Similarly, the 25–34-year-old age group had the highest fraction of
respondents who perceived both NWP and MLWP forecasts as accurate, whereas the 35-44
age group had the lowest fraction.
Blocks Gender Region Urban/ Social Age AI knowledge
Rural Grade (years)
Groups Male; North East; Urban; ABC1, 18-24; 25- Heard of AI, could
C2DE1
Female North West; Town and 34; 35-44; explain in detail;
Yorkshire and Heard of AI, could
1
https://www.ons.gov.uk/census/aboutcensus/censusproducts/approximatedsocialgradedata
11
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 12 of 24 -->

Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
the Humber; East Fringe;
Midlands; West Rural
Midlands; East of
England;
London; South
East; South
West; England;
Wales; Scotland;
Northern Ireland
Q2a. Max = Max = South Max =
Female; East; Min = Town and
NWP
Min = Wales Fringe;
accuracy
Male Min =
(daily)
Rural
Q3a. Max = Max = London; Max =
Male; Min Min = North East Urban;
MLWP
= Female Min =
accuracy
Rural
(daily)
Q2b. Max = Max = Northern Max =
Female; Ireland; Min = Urban;
NWP
Min = North East Min =
accuracy
Male Rural
(severe)
Q3b. Max = Max = London; Max =
Male; Min Min = Scotland Urban;
MLWP
= Female Min =
accuracy
Town and
(severe)
Fringe
Q4a. Max = Max = East of Max =
Female; England; Min = Rural;
NWP
Min = North East Min =
confidenc
Male Urban
e (typical)
Q5a. Max = Max = London; Max =
Male; Min Min = Scotland Urban;
MLWP
= Female Min =
File generated with AMS Word template 2.0
45-54; 55- explain partially;
64; 65+ Heard of AI, could
not explain; Not
heard of AI
Max = Max = 25- Max = Heard of
ABC1; 34; Min = AI, could explain;
Min = 35-44 Min = Heard of AI,
C2DE could not explain
Max = Max = 25- Max = Heard of
ABC1; 34; Min = AI, could explain;
Min = 65+ Min = Heard of AI,
C2DE could not explain
Max = Max = Max = Heard of
ABC1; 65+; Min = AI, could explain;
Min = 55-64 Min = Heard of AI,
C2DE could not explain
Max = Max = 25- Max = Heard of
ABC1; 34; Min = AI, could explain;
Min = 55-64 Min = Heard of AI,
C2DE could not explain
Max = Max = 25- Max = Heard of
ABC1; 34; Min = AI, could explain;
Min = 18-24 Min = Heard of AI,
C2DE could not explain
Max = Max = 25- Max = Heard of
ABC1; 34; Min = AI, could explain;
Min = 45-54 Min = Heard of AI,
C2DE could not explain
12
04:12 PM UTC

---

<!-- SHEET 13 of 24 -->

confidenc Town and
Fringe
e (typical)
Q4b. Max = Max = North Max = Max = Max = 45- Max = Heard of
Male; Min West; Min = Town and ABC1; 54; Min = AI, could explain;
NWP
= Female Yorkshire and Fringe; Min = 18-24 Min = Heard of AI,
confidenc
the Humber Min = C2DE could not explain
e
Rural
(importan
t)
Q5b. Max = Max = London; Max = Max = Max = 25- Max = Heard of
Male; Min Min = Scotland Urban; ABC1; 34; Min = AI, could explain;
MLWP
= Female Min = Min = 45-54 Min = Heard of AI,
confidenc
Town and C2DE could not explain
e
Fringe
(importan
t)
Table 1: Summary of survey responses for questions 2-5, by group within each block. For both
NWP and MLWP forecasts, the table highlights the groups with the highest (max) and lowest (min)
fraction of respondents who perceive the forecasts as accurate and who would be confident using
them. The top row lists the groups within each block. Figure 4 shows the numerical values
corresponding to these groups, where they are represented by the endpoints of the connected dots
(“dumbbells”).
To demonstrate how perceptions vary within and between each block, Figure 4 shows a
subset of the quantitative responses about perceived accuracy and confidence for each group
within the demographic, socioeconomic, regional and AI knowledge blocks. For clarity, we
simplify the Likert-scale responses using the following rules:
• Accuracy: for each block and group, respondents are categorised into those who rated
the forecast as “Accurate” (“Very” or “Slightly accurate”), (ii) rated it as “Inaccurate”
(“Slightly” or “Very inaccurate”), and (iii) selected “Don’t know”.
• Confidence: for each block and group, respondents are categorised into those who
were “Confident” (“Very” or “Slightly confident”), (ii) “Not confident” (“Slightly” or “Very
unconfident”), and (iii) those who selected “Don’t know”.
13
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 14 of 24 -->

Figure 4: Connected dot (“dumbbell”) plots showing fraction of respondents to perceive the
forecast as accurate (upper panel) and the fraction who are confident using forecast information for
decision-making (lower panel) within each response block. Each “dumbbell” represents the range of
responses by showing the lowest (min) and highest (max) fraction for each block, with the median
fraction shown in grey. Blue colours show results for NWP, red for MLWP. The darker shades show
14
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 15 of 24 -->

the responses for daily weather and typical decisions, and the lighter shades show the responses for
severe weather and important decisions, respectively. The ends of each dumbbell correspond to the
groups summarised in Table 1.
The fraction of respondents for each block and group who perceive the forecast as
accurate (upper panel), and who would be confident using forecast information for decision-
making (lower panel) are shown in Figure 4. Each dumbbell represents the range of responses
within the group, showing the minimum and maximum fraction (corresponding to the groups
listed in Table 1), with the median response shown in grey. Blue represents NWP, and red
represents MLWP, with darker shades showing the responses for daily weather and typical
daily decisions, while the lighter shades show the responses for severe weather and important
decisions.
There is remarkable agreement across demographic, socioeconomic and regional groups
in their perceptions of NWP forecast accuracy. This is probably because NWP is a well-
established approach, and users have had many years of direct experience using the
information for decision-making, i.e. they understand what it does well, what it does not, and
how to use it. In contrast, AI is an emerging technology and, in the absence of direct
experience, a smaller fraction of each block perceives it to be accurate, when compared to
traditional NWP forecasts.
In addition to systematic differences in blockwise perceptions of forecast accuracy, there
is a much wider spread in responses about MLWP forecasts across demographic,
socioeconomic and regional groups about its potential accuracy. However, given the small
number of groups within each block, formal statistical inference and significance tests are not
robust. For that reason, we do not calculate the statistical significance of differences in the
perceptions of accuracy between MLWP and NWP. Instead, we adopt a consistency-based
approach. Across all blocks, the median fraction who perceive the forecast as accurate is
always lower for MLWP than for NWP. Under the null hypothesis, there is no systematic
difference in perceived accuracy between MLWP and NWP forecasts. It follows that, for any
given block, the probability that the median perceived accuracy for MLWP is lower than that
for NWP is 0.5, reflecting random variation with no directional bias. In the observed data,
this occurs in all six blocks. Assuming independence across blocks, the probability of this
0.56
outcome arising by chance is ≈ 0.016. This low probability provides evidence of a
15
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 16 of 24 -->

systematic difference in perceptions about the two forecast types, with respondents currently
rating MLWP forecasts as less accurate than NWP forecasts. The same pattern is observed in
the range of responses: the difference between the maximum and minimum fractions is
always greater for MLWP than NWP, indicating greater variability in perceptions of MLWP
accuracy.
The results are broadly similar to the above for responses about confidence in using
forecast information for decision-making. A slightly higher fraction of people report being
confident using NWP forecasts to inform daily decisions than perceiving them as accurate. If
meaningful, this could suggest that some individuals who think the forecast is inaccurate are
still confident using it. However, it is also possible that this difference arises from variations
in the response categories between accuracy and confidence questions; as such, this
interpretation should be treated with caution.
Consistently, the median fraction of respondents who would be confident using the
forecast is always lower for MLWP than for NWP. In addition, the range of responses
(difference between the maximum and minimum fractions) is greater for MLWP than NWP
in five out of six blocks. Under the null hypothesis of no systematic variability between
forecast types, MLWP would be expected to exhibit a larger spread than NWP in any given
block with probability 0.5. Assuming independence across blocks, the probability of
0.55≈0.03.
observing this pattern in five out of six blocks by chance is The low probability
suggests that the pattern is unlikely to arise from random variation alone, providing some
evidence that perceived accuracy and confidence vary more for MLWP than for NWP. More
generally, the distribution of responses for NWP provides a useful baseline against which
changes in perceptions of MLWP can be assessed in future surveys.
As described above, Table 1 summarises the groups within each block that exhibit the
highest and lowest fractions of respondents who perceive forecasts as accurate and who
report confidence using them. This highlights several consistent patterns across both NWP
and MLWP, alongside some notable differences:
 AI knowledge – respondents who report having heard of AI and being able to
explain it show the highest fractions perceiving both NWP and MLWP forecasts
as accurate and who would be confident using them. In contrast, those who have
heard of AI and cannot explain it consistently show the lowest fractions
perceiving NWP and MLWP forecasts as accurate, and confidence in using them.
16
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 17 of 24 -->

 Social grade – respondents in the ABC1 group have higher fractions than those in
the C2DE group who perceive both NWP and MLWP forecasts as accurate, and
would be confident using them.
 Gender – a higher fraction of women than men perceive NWP forecasts as
accurate, whereas a higher fraction of men than women perceive MLWP forecasts
as accurate. The responses for confidence are less consistent.
 Region – in general, but not uniformly, respondents in the South, East, and
London show higher fractions perceiving NWP and MLWP forecasts as accurate
and who would be confident using them. Those in the North East, Scotland, and
Wales groups tend to have the lowest fractions perceiving NWP and MLWP
forecasts as accurate and who would be confident using them.
 Age – the 25-34 group most frequently exhibits the highest fraction of respondents
who perceive both NWP and MLWP forecasts as accurate and who would be
confident using them.
 Urban/Rural – there is limited evidence of a systematic pattern across these
groups; however, within this block, the rural respondents most frequently exhibit
the lowest fractions perceiving the NWP and MLWP forecast as accurate, and
who would be confident using them.
These patterns are largely consistent with established findings on the UK’s digital divide
(ONS, 2019), despite differences in survey design. While caution is warranted in interpreting
the findings, they suggest a risk of reinforcing existing disparities in engagement with
emerging technologies. This further highlights the importance of carefully considering the
needs of different user groups to ensure equitable access and build understanding of new
forecasting approaches. Addressing these factors may help align public perceptions of
MLWP with those currently associated with NWP, both in terms of perceived accuracy and
confidence using the information.
4. Bridging the gap
The observed gap between perceptions of NWP and MLWP seems to highlight the need
to build wider public trust in weather forecasting approaches that include machine learning.
17
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 18 of 24 -->

However, the results also highlight the limits of what we can learn from surveys alone. In
particular, the substantial minority of respondents (approximately 17-20%) who indicated
that they “Don’t know” how accurate MLWP forecasts would be, or how confident they
would be using them for decision-making, warrants close attention. This group may reflect
uncertainty, unfamiliarity or ambivalence rather than a neutral evaluation, and, therefore,
represents an important target for further research and engagement.
Understanding the basis for these views and the reasons behind them will be important
because many, if not most, public users are unlikely to interrogate formal forecast
performance metrics that are familiar to model developers. Indeed, previous work exploring
trust in AI system (e.g. McGovern et al 2024; Wirtz et al 2025) suggests that users will want
to evaluate themselves whether, when, and to what extent AI outputs can be trusted, even
when they have been developed according to formal technical standards. In this context,
transparency, particularly in how forecasts are generated, communicated and interpreted, will
be central to supporting understanding and trust, and aligns with broader regulatory
developments and emerging best practice.
Taken together, these findings point to the need for complementary research that extends
beyond structured surveys. Qualitative methods, including focus groups, interviews and
workshops, could help identify the reasons underpinning both negative and uncertain
perceptions of MLWP, and clarify what aspects raise concern, confusion, or scepticism. Such
mixed-method approaches would provide valuable context for interpreting survey responses,
and for informing effective communication strategies, public engagement, and building trust.
How quickly perceptions will change is unclear, with service providers having a vital role
to play. In a general description of this problem, Pope et al. (2017) proposed a Bayesian
decision-theoretic model in which perceived forecast value depended on both the user’s prior
beliefs about forecast accuracy, and evidence of forecast performance from direct experience.
In that model, perceptions of accuracy generally changed more slowly for users who were
sceptical, i.e. those who either under-estimated or were very uncertain about the forecast
accuracy - as is the case for MLWP. There could be many reasons for different prior beliefs,
including trust in institutions that produce forecasts, previous experience, as well as perceived
risks and benefits of new technologies. Given this framework, our survey findings suggest
prior beliefs vary considerably across demographic, socioeconomic, and regional groups.
This, in turn, suggests the need for both early and extensive engagement with the public,
18
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 19 of 24 -->

including partnerships with experts in other disciplines (e.g. social sciences), to elicit deeper
insights about attitudes towards emerging technologies, and priorities across different groups.
Once armed with this information, we encourage the weather forecasting community to work
together in ensuring these considerations are adequately represented in the development of
MLWP forecast products and services, and ensure both that the digital divide is not
reinforced or widened, and that trust in NWP (the backbone of most weather forecast
systems) is not undermined. This approach has the potential to pave the way for more rapid
realisation of anticipated benefits of integrating NWP and MLWP capabilities (e.g.
improving forecast accuracy, timeliness and resolution) to help people make better weather-
related decisions.
The public journey towards increasing AI integration in public services, such as weather
forecasts, must also extend beyond a requirement for simple audience engagement, and
explore a deeper embedding of user insights within technical developments. We are therefore
motivated to interpret the survey responses within the context of key science/strategy
implications that are relevant to weather forecast providers (including National
Meteorological Services), for example:
1. Approach. While the public survey treated NWP and MLWP as entirely separate
approaches, the choice does not have to be as stark; indeed, data science techniques have long
been used within the weather forecast value chain (albeit not necessarily acknowledged under
the ML label). However, the gap in perceptions of accuracy and confidence between NWP
and MLWP supports the need for continued efforts to combine their respective strengths (e.g.
Shipway et al., 2026). Products and services delivered using an integrated approach to NWP
and MLWP (which can be very carefully curated and controlled) may help support a
responsible approach to AI adoption.
2. Experience. As in any community, there are inevitably early-adopters with an
appetite for exploiting emerging technologies that both champion the new capability and
contribute informed feedback. Releasing experimental code and data to these early-adopters
can be highly beneficial. Examples of related initiatives include the advance publication of
early modelling work undertaken by Google regarding the GraphCast model (Lam et al 2023)
and the exposure of a set of basic data from five MLWP models (AIFS; Aurora;
FourCastNet; GraphCast and Pangu-Weather) by the European Centre for Medium-Range
Weather Forecast (ECMWF) to enable comparison against its equivalent operational NWP
19
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 20 of 24 -->

output (with the UK Met Office doing similarly for the experimental global Artificial
Intelligence-based weather forecast system that it co-developed with The Alan Turing
Institute, FastNet, e.g. Daub et al., 2025; Dunstan et al., 2025). Additionally, experiments
with consenting participants that compare NWP and MLWP, ideally in a context-based
decision-making scenario, could yield important insights. Other context-based approaches
could include industry-focused collaborative prototyping developments to better understand
forecast utility and encourage innovation (e.g. Chen et al., 2023b; Steele et al. 2024; Steele et
al., 2025).
3. Evaluation. Subjective measures such as perceived ‘accuracy’ and ‘confidence’ have
a natural analogy with standard weather forecast validation/verification measures of ‘skill’
and ‘value’. As such, impartial demonstrations of skill, representation of physical
phenomena, and value for decision-making can inform subjective perceptions of accuracy
and confidence. Incorporating user-relevant metrics within ML training loss functions and/or
forecast performance statistics would help strengthen the design of models and assess their
quality in a more-timely manner. There are further opportunities to bring together service
developer and user perspectives using argument-based assurance methods, e.g. using the
framework proposed by Burr & Leslie (2022). Such assurance frameworks are anticipated to
become increasingly important tools for breaking down silos and connecting research and
user communities.
Ultimately, even with a deeper embedding of user insights within technical developments,
regular public surveys will be required to track progress in the perceptions of NWP and
MLWP as the latter becomes more widely used and integrated with NWP.
In benchmarking perceptions of MLWP against NWP it is possible, and indeed probable,
that many of the learnings about approaches for building trust could transfer between the two,
in much the same way as perceptions of accuracy for forecasting daily weather inform
perceptions of severe weather. However, we suspect that this transfer is unlikely to hold
across very different timescales and with increasing uncertainty, with users of climate
information limited by much slower feedback about how to use it effectively, than for
weather forecasts. Thus, while trust in weather forecasts can be strongly influenced by
evidence gained through regular, direct experience, building trust in climate information
probably requires a stronger emphasis on evidence that informs the user’s prior beliefs, which
may include causal explanations described using established mechanistic principles (e.g.
20
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 21 of 24 -->

Newton’s laws, thermodynamics, etc.). This, of course, is yet to be tested, particularly in the
context of AI climate modelling.
Similarly, it is important to recognise that the results presented here are drawn from
representative surveys of the UK public. We encourage other service providers to undertake
similar surveys, which may reveal contrasting results, particularly in countries where training,
skills and experience of AI are very different to the UK – the analysis of which may, in turn,
stimulate further ideas for increasing appropriate adoption more generally.
This early foray into public perceptions of AI weather forecasting scratches the surface.
The authors hope that it stimulates the work and analysis needed to ensure a smooth
transition as MLWP capabilities are integrated alongside NWP. Together MLWP and NWP
have the potential to offer the public better, faster, more accurate forecasts, but these will
only deliver their true value if they are trusted and used to improve weather-related decision-
making.
Acknowledgments.
This article was supported by the Public Weather Service (PWS) overseen by the
Department for Science, Innovation and Technology (DSIT) of the UK Government.
The authors thank Jenny Wells and Tom Wigley at the Met Office and Sylvie Hobden at
the Responsible Technology Adoption Unit, Department for Science, Innovation and
Technology who provided guidance on survey questions and data. We also thank YouGov for
conducting the fieldwork with the public and providing the data for analysis.
Data Availability Statement.
Data sharing not applicable.
REFERENCES
Ben Bouallègue, Z., Clare, M.C., Magnusson, L., Gascón, E., Maier-Gerber, M.,
Janoušek, M., Rodwell, M., Pinault, F., Dramsch, J.S., Lang, S.T. and Raoult, B., 2024. The
rise of data-driven weather forecasting: A first statistical assessment of machine learning–
21
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 22 of 24 -->

based weather forecasts in an operational-like context. Bulletin of the American
Meteorological Society, 105(6), pp.E864-E883.
Cains, M. G., Wirz, C.D., Demuth, J.L, Bostrom, A., Gagne, J.D., McGovern, A., Sobash,
R.A., and Madlambayan, D., 2024. Exploring NWS forecasters' assessment of AI guidance
trustworthiness. Weather and Forecasting, 39(8), 1219-1241.
Chen, K., Han, T., Gong, J., Bai, L., Ling, F., Luo, J.J., Chen, X., Ma, L., Zhang, T., Su,
R. and Ci, Y., 2023a. Fengwu: Pushing the skillful global medium-range weather forecast
beyond 10 days lead. arXiv preprint arXiv:2304.02948.
Chen J., Ashton, I.G.C., Steele, E.C.C., and Pillai, A.C., 2023b. A real-time
spatiotemporal machine learning framework for the prediction of nearshore wave conditions.
Artificial Intelligence for the Earth Systems, 2, e220033. doi: https://doi.org/10.1175/AIES-
D-22-0033.1.
Clark, G., Hancock, M., Hall, W., and Pesenti, J., 2019. AI Sector Deal. Department for
Business, Energy & Industrial Strategy. Department for Digital, Culture, Media & Sport.
Available at: https://www.gov.uk/government/publications/artificial-intelligence-sector-
deal/ai-sector-deal
Daub, E.G., et al., 2025. Technical overview and architecture of the FastNet Machine
Learning weather prediction model, version 1.0. arXiv preprint arXiv:2509.17658.
de Burgh-Day, C.O. and Leeuwenburg, T., 2023. Machine learning for numerical weather
and climate modelling: a review. Geoscientific Model Development, 16(22), pp.6433-6477.
Dunstan, T., et al., 2025. FastNet: Improving the physical consistency of machine-
learning weather prediction models through loss function design. arXiv preprint
arXiv:2509.17601.
Harrison, D.R., McGovern, A., Karstens, C.D., Bostrom, A., Demuth, J.L, Jirak, I.L., and
Marsh, P.T., 2025. An assessment of how domain experts evaluate machine learning in
operational meteorology. Weather and Forecasting, 40(3), 393-410.
HM Government, 2021. National AI strategy. Command Paper 525. Office for Artificial
Intelligence. Available at: https://www.gov.uk/government/publications/national-ai-strategy.
22
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 23 of 24 -->

HM Government, 2025. AI Opportunities Action Plan. Available at:
https://www.gov.uk/government/publications/ai-opportunities-action-plan/ai-opportunities-
action-plan
Keisler, R., 2022. Forecasting global weather with graph neural networks. arXiv preprint
arXiv:2202.07575.
Kox, T., Harrison, S., Ziegler, F., and Gerhold, G., 2025. Perceptions, hopes, and
concerns regarding the possibilities of artificial intelligence in weather warning contexts.
International Journal of Disaster Risk Reduction, 105817.
Lam, R., Sanchez-Gonzalez, A., Willson, M., Wirnsberger, P., Fortunato, M., Alet, F.,
Ravuri, S., Ewalds, T., Eaton-Rosen, Z., Hu, W. and Merose, A., 2023. Learning skillful
medium-range global weather forecasting. Science, 382(6677), pp.1416-1421.
Lazanyuk, I.V., Eyeberdiyeva, M.M., Diaz, M.H.A.Z., 2025. AI and the Digital Divide:
Challenges and Opportunities. In: Popkova, E.G. (eds) Management of Digital Technologies
in the Innovative Economy. Advances in Science, Technology & Innovation. Springer,
Cham. https://doi.org/10.1007/978-3-031-83331-1_46
Martin-Nielsen, J., 2017. Scientific forecasting? Performing objectivity at the UK’s
Meteorological Office, 1960s–1970s. History of Meteorology, 8, 202–221.
McGovern, A., Demuth, J., Wirz, C.D., Tissot, P. E., Cains, M.G., and Musgrave, K.D.,
2024. The value of convergence research for developing trustworthy AI for weather, climate,
and ocean hazards. npj Natural Hazards, 1(1), 13.
Nipen, T.N., Haugen, H.H., Ingstad, M.S., Nordhagen, E.M., Salihi, A.F.S., Tedesco, P.,
Seierstad, I.A., Kristiansen, J., Lang, S., Alexe, M. and Dramsch, J., 2024. Regional data-
driven weather modeling with a global stretched-grid. arXiv preprint arXiv:2409.02891.
ONS, 2019. Exploring the UK’s digital divide, available at:
https://www.ons.gov.uk/peoplepopulationandcommunity/householdcharacteristics/homeinter
netandsocialmediausage/articles/exploringtheuksdigitaldivide/2019-03-04
Pathak, J., Subramanian, S., Harrington, P., Raja, S., Chattopadhyay, A., Mardani, M.,
Kurth, T., Hall, D., Li, Z., Azizzadenesheli, K. and Hassanzadeh, P., 2022. Fourcastnet: A
global data-driven high-resolution weather model using adaptive fourier neural operators.
arXiv preprint arXiv:2202.11214.
23
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

---

<!-- SHEET 24 of 24 -->

Pope, E.C.D., Buontempo, C. and Economou, T., 2017. Quantifying how user-interaction
can modify the perception of the value of climate information: A Bayesian approach. Climate
Services, 6, pp.41-47.
Shipway, B.J., Bain, C., Walters, D., Booth, B.B., Boutle, I., Clark, R.T., Hill, K.L.,
Kendon, E. and Vosper, S.B., 2026. Blending machine learning and physics-based
approaches for weather and climate: a typology. arXiv preprint arXiv:2605.20925.
Steele, E.C.C., Chen, J., Ashton, I.A.G., Pillai, A.C., Jaramillo, S., Leung, P., and Zarate,
L., 2024. A spatiotemporal machine learning framework for the prediction of metocean
conditions in the Gulf of Mexico. Offshore Technology Conference, Houston, TX, USA, 6-9
May 2024. doi: https://doi.org/10.4043/35104-MS.
Steele, E.C.C., Juniper, M.C.R., Pillai, A.C., Ashton, I.A.G., Chen, J., Jaramillo, S., and
Zarate, L., 2025. A spatiotemporal machine learning framework for the prediction of
metocean conditions in the Gulf of Mexico: application to Loop Current and Loop Current
Eddy forecasting. Offshore Technology Conference, Houston, TX, USA, 5-8 May 2025. doi:
https://doi.org/10.4043/35733-MS.
UKRI, 2021. Transforming our world with AI. UKRI’s role in embracing the opportunity.
Available at: https://www.ukri.org/wp-content/uploads/2021/02/UKRI-120221-
TransformingOurWorldWithAI.pdf.
Wirz, C.D., Demuth, J.L., Cains, M., G., White, M., Radford, J., and Bostrom, A., 2024.
National Weather Service (NWS) forecasters' perceptions of AI/ML and its use in operational
forecasting. Bulletin of the American Meteorological Society, 105(11), E2194-E2215.
Wirz, C.D., Demuth, J.L, Bostrom, A., Cains, M.G., Ebert-Uphoff, I., Gagne, D.J.,
Schumacher, A., McGovern, A., and Madlambayan, D., 2025. (Re)Conceptualizing
trustworthy AI: A foundation for change. Artificial Intelligence, 104309.
24
File generated with AMS Word template 2.0
Accepted for publication in Artificial Intelligence for the Earth Systems. DOI 10.11Un7a5ut/hAenItiEcaSted- D| D-o2wn5lo-a0d0ed6 089/2.17/2.6
04:12 PM UTC

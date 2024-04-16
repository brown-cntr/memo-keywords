
---
geometry:
    - margin=0.5in
output: pdf_document
colorlinks: true
fontsize: 9pt
toc: false
urlcolor: "violet"
header-includes:
    - \usepackage{titling}
    - \setlength{\droptitle}{-7em}
    - \pagenumbering{gobble}
    - \setlength{\parindent}{0em}
    - \usepackage{sansmathfonts}
    - \usepackage[T1]{fontenc}
    - \usepackage{graphicx}
    - \renewcommand*\familydefault{\sfdefault} 
    - \usepackage{wrapfig}
    - \usepackage{booktabs}
    - \usepackage[export]{adjustbox}
    - \newcommand{\forceindent}{\leavevmode{\parindent=1em\indent}}
    - \usepackage{fvextra}
    - \DefineVerbatimEnvironment{Highlighting}{Verbatim}{breaklines,commandchars=\\\{\}}
---

# State bills with found keywords from Memo 2024

\begin{figure}[h]
    \centering
    \includegraphics[width=\textwidth, angle=0]{docs/bill_count.pdf}
    \caption{\textbf{Preliminary government-scoped} bill counts per ``categories'' across states}
\end{figure}



## Methods

### OpenAI extraction

Below is the main prompt (there is also a refinement prompt when the text is long not shown here):

```text

You are a helpful assistant for legislators, researchers and lawyers.
You are given a task to read a bill and extract necessary information from them.
Below are the variables and instructions:

1. `has_government_scope`: Indicates whether the bill has government scope: a bill has government scope if it governs the government's use of artificial intelligence (AI) or automated decision systems (ADS) in its operations. This scope specifically focuses on the **government**'s use and procurement of these technologies.

Instruction: 
- First, answer only "Yes" or "No".
- If "Yes", also include 1-2 sentence excerpts from the text to support the government scope, label variable as `excerpt_government_scope`.

2. `has_ai_governance_body`: Indicates whether the bill designates, indicates or establishes an AI governance body: an AI governance body is a group of people in the within a government entity or organization that has the authority to manage and oversee the use of AI or ADS by that entity or organization.

Instruction: 
- First, answer only "Yes" or "No".
- If "Yes", also include the name(s) of the governance body, label variable as `ai_governance_body_names`.

3. `has_harmonization`: Indicates whether the bill outlines intent or strategy to harmonize legislation between state and federal government. Harmonization is defined as cooperation between different state and federal jurisdictions \ 
to make laws identical or at least more similar.

Instruction: 
- First, answer only "Yes" or "No".
- If "Yes", also include 1-2 sentence excerpts from the text to support existence of hamornization, label variable as `excerpt_harmonization`.
 

Use only the definitions and follow instructions here.
Only use the existing text as reference. Do not make things up.
If you know an answer is empty, just use an empty string "". 
If you do not know an answer for a variable, just answer as "unknown".

Please output as a JSON format.

Here is the text:

{text}

JSON_OUTPUT:

```



### Keyword detection categories


### *ImpactAssess*


This is detecting impact-related terms:

- `impact`
- `use`
- `risk`

then the assessment-related verbs:

- `assess`
- `evaluate`
- `manage`

This also allows the other way around: assessment- then AI-related terms.

For impact-related then verbs, no flexible wording in between is considered.

However, for the other way around, verb then impact, some words in between are allowed.





### *Inventory*


This is detecting either:

- AI-related terms:
    - `AI`
    - `artificial intelligence`
    - `automated decision (making) system`
    - `frontier model`
    - `face/facial/iris/gait recog/match`
- or impact related terms:
    - `impact`
    - `use`
    - `risk`
    
then the word `inventory`.

This also detects the other way around: `inventory`, then AI/impact-related terms.

Note that this also allows for some words in between of AI/impact-related terms and `inventory`
to allow more flexible capturing of such pairing.





### *GovBody*


This is detecting AI-related terms:

- `AI`
- `artificial intelligence`
- `automated decision (making) system`
- `frontier model`
- `face/facial/iris/gait recog/match`

then board-related terms:

- `governance body`
- `cabinet`
- `board`
- `council`
- `division`
- `office` (but not `officer`)
- `department`
- `agency`
- `branch`
- `(ethics) commission`

This detects both:

- AI-related terms, then board-related terms;
- as well as: board-related terms, followed by `of|on|for` then AI-related terms.

This is a difficult category to capture correctly with just word detection and will need manual verification.





### *PotentialHarmonize*


This is detecting board-related terms:

- `governance body`
- `cabinet`
- `board`
- `council`
- `division`
- `office` (but not `officer`)
- `department`
- `agency`
- `branch`
- `(ethics) commission`  

then possible harmonization verbs:

- `harmonize`
- `collaborate`
- `coordinate`

This detects also the other way around and also allows for flexible wordings between.

This is a very difficult category to operationalize, highly prone to false positives. This really needs manual verification.





### *Procurement*


This is detecting AI-related terms:

- `AI`
- `artificial intelligence`
- `automated decision (making) system`
- `frontier model`
- `face/facial/iris/gait recog/match`
    
then the procurement-related terms:

- `procure`
- `purchase`
- `acquire` (or `acquis` for `acquisition`)

This also allows the other way around: procurement- then AI-related terms.

Note that this also allows for some words in between of AI-related terms 
and procurement-related terms to allow more flexible capturing of such pairing.




### *AIOfficer*


This is detecting `chief`, then a few potential AI-related terms:

- `AI`
- `artificial intelligence`
- `automated decision (making) system`
- `frontier model`
- `face/facial/iris/gait recog/match`

then `officer`.




## Bill details

### 1. `AK_[33]_HB-306`

- Title: *An Act relating to artificial intelligence; requiring disclosure of deepfakes in campaign communications; relating to cybersecurity; and relating to data privacy.*
- From: Alaska, session `33`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *article 7. use by state agencies of artificial intelligence and data about individuals.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *impact assessments*
		- *impact assessment*

    - *Inventory*
		- *inventory of all systems used by state agencies that employ artificial intelligence*

### 2. `AK_[33]_SB-177`

- Title: *An Act relating to artificial intelligence; requiring disclosure of deepfakes in campaign communications; relating to cybersecurity; and relating to data privacy.*
- From: Alaska, session `33`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *article 7. use by state agencies of artificial intelligence and data about individuals.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *impact assessments*
		- *impact assessment*

    - *Inventory*
		- *inventory of all systems used by state agencies that employ artificial intelligence*

### 3. `CA_[20232024]_AB-2930`

- Title: *Automated decision tools.*
- From: California, session `20232024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *this bill would authorize certain public attorneys, including the attorney general, to bring a civil action against a deployer or developer for a violation of the bill and would authorize a court to award, only in an action for a violation involving algorithmic discrimination, a civil penalty of $25,000 per violation.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *manages the reasonably foreseeable risk*
		- *impact assessment*
		- *manage, and govern the reasonably foreseeable risks of algorithmic discrimination associated with the use*
		- *risk assessments*
		- *manage, and govern the risk*
		- *impact assessments*

### 4. `CA_[20232024]_AB-302`

- Title: *Department of Technology: high-risk automated decision systems: inventory.*
- From: California, session `20232024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *This bill would require the department, in coordination with other interagency bodies, to conduct, on or before september 1, 2024, a comprehensive inventory of all high-risk automated decision systems, as defined, that have been proposed for use, development, or procurement by, or are being used, developed, or procured by, state agencies, as defined.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *risk assessments*
		- *assessing the efficacy and relative benefits of the use*

    - *Inventory*
		- *inventory of all high-risk*

### 5. `CA_[20232024]_AB-331`

- Title: *Automated decision tools.*
- From: California, session `20232024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *this bill would define 'deployer' and 'developer' to include a local government agency and would thereby impose a state-mandated local program.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *manages the reasonably foreseeable risk*
		- *impact assessment*
		- *manage, and govern the reasonably foreseeable risks of algorithmic discrimination associated with the use*
		- *risk assessments*
		- *manage, and govern the risk*
		- *impact assessments*

### 6. `CA_[20232024]_SB-1047`

- Title: *Safe and Secure Innovation for Frontier Artificial Intelligence Systems Act.*
- From: California, session `20232024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *This bill would enact the safe and secure innovation for frontier artificial intelligence systems act to, among other things, require a developer of a covered model, as defined, to determine whether it can make a positive safety determination with respect to a covered model before initiating training of that covered model, as specified.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *evaluating appropriate uses of the public cloud resources and their potential downstream impact*
		- *through risk assessment*
		- *evaluation for use*
		- *best risk management*
		- *manage the risk*
		- *assess, and prioritize high-risk*
		- *assessment of the risk*

    - *GovBody*
		- *frontier model division*

### 7. `CA_[20232024]_SB-1120`

- Title: *Health care coverage: utilization review.*
- From: California, session `20232024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *this bill would require a health care service plan or health insurer to ensure that a licensed physician supervises the use of artificial intelligence decisionmaking tools when those tools are used to inform decisions to approve, modify, or deny requests by providers for authorization prior to, or concurrent with, the provision of health care services to enrollees or insureds.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *managed care administrative fines and penalties fund and shall be use*

### 8. `CA_[20232024]_SB-398`

- Title: *Department of Technology: advanced technology: research.*
- From: California, session `20232024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *this bill, the artificial intelligence for california research act, would require the department of technology, upon appropriation by the legislature, to develop and implement a comprehensive research plan to study the feasibility of using advanced technology to improve state and local government services.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *risk management*

### 9. `CA_[20232024]_SB-896`

- Title: *Artificial Intelligence Accountability Act.*
- From: California, session `20232024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *this bill, the artificial intelligence accountability act, would, among other things, require the government operations agency, the department of technology, and the office of data and innovation to produce a state of california benefits and risk of generative artificial intelligence report that includes certain items, including an examination of the most significant, potentially beneficial uses for deployment of generative artificial intelligence tools by the state*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *and risk management*
		- *evaluate the impact*
		- *evaluate equitable outcomes in deployment and implementation of high-risk*
		- *evaluated for risk*
		- *evaluate and revise guidelines for state agencies and departments to analyze the impact*
		- *al risk management*

    - *Inventory*
		- *inventory of all current high-risk*

    - *Procurement*
		- *procurement and enterprise use opportunities in which generative artificial intelligence*

### 10. `CT_[2023]_SB-1103`

- Title: *AN ACT CONCERNING ARTIFICIAL INTELLIGENCE, AUTOMATED DECISION-MAKING AND PERSONAL DATA PRIVACY.*
- From: Connecticut, session `2023`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the department of administrative services shall conduct an inventory of all systems that employ artificial intelligence and are in use by any state agency.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assess the likely impact*
		- *assessment of systems that employ artificial intelligence and are in use*
		- *assessments of systems that employ artificial intelligence and are in use*
		- *impact assessment*

    - *Inventory*
		- *inventory of all systems that employ artificial intelligence*

### 11. `CT_[2024]_SB-2`

- Title: *AN ACT CONCERNING ARTIFICIAL INTELLIGENCE.*
- From: Connecticut, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *each state agency shall study how generative artificial intelligence may be incorporated in its processes to improve efficiencies. each state agency shall solicit input from its employees concerning such incorporation, including, but not limited to, any applicable collective bargaining unit that represents its employees and appropriate experts from civil society organizations, academia and industry.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *evaluated for performance and relevant information related to explainability before such high-risk*
		- *a risk management*
		- *evaluate such risk*
		- *evaluate such impact*
		- *impact assessment*
		- *manages any known or reasonably foreseeable risk*
		- *each risk management*
		- *assessments of systems that employ artificial intelligence and are in use*
		- *the risk management*
		- *such risk management*
		- *any risk management*
		- *evaluate the performance and known limitations of the high-risk*
		- *intelligence risk management*
		- *recognized risk management*
		- *impact assessments*
		- *manages known or reasonably foreseeable risk*

    - *Inventory*
		- *inventory of all systems that employ artificial intelligence*

### 12. `FL_[2024]_SB-972`

- Title: *Artificial Intelligence*
- From: Florida, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *requiring each state agency to prepare and submit, by a specified date and using money appropriated by the legislature, an inventory report for all automated decision systems that are being developed, used, or procured by the agency; prohibiting a county or a municipality or a political subdivision thereof from regulating the private and public use of artificial intelligence systems*
    - `has_ai_governance_body`: True
        - governance bodies: *Artificial Intelligence Advisory Council*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessment of the impact*
		- *“risk assessment*

    - *Inventory*
		- *inventory report for all automated decision systems*
		- *automated decision systems inventory*
		- *inventory report of all automated decision systems*

### 13. `GA_[2023_24]_HB-988`

- Title: *Georgia Technology Authority; annual inventory of artificial intelligence usage by state agencies; provide*
- From: Georgia, session `2023_24`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the authority shall:
(1) not later than december 31, 2024, and annually thereafter, conduct an inventory of
all systems that employ artificial intelligence and are in use by any agency.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessment of systems that employ artificial intelligence and are in use*
		- *impact assessment*

    - *Inventory*
		- *inventory of artificial intelligence*
		- *inventory of all systems that employ artificial intelligence*

### 14. `GA_[2023_24]_SR-476`

- Title: *Senate Study Committee on Artificial Intelligence; create*
- From: Georgia, session `2023_24`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *it is important that this state establish policies and procedures concerning the development, procurement, implementation, utilization, and ongoing assessment of systems that employ ai and are in use by state agencies*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessment of systems that employ ai and are in use*

### 15. `HI_[2024]_HB-2152`

- Title: *RELATING TO ARTIFICIAL INTELLIGENCE.*
- From: Hawaii, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *establishes a plan for the use of generative artificial intelligence in state agencies, departments, and government branches.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessing impact*
		- *initial risk assessment*
		- *assessing the impact*
		- *evaluating the impact*
		- *use assessment*
		- *risk assessments*
		- *al risk management*
		- *joint risk assessments*
		- *evaluate equitable outcomes when considering a high-risk*
		- *out risk assessments*
		- *impact assessments*
		- *3 risk assessment*

    - *Inventory*
		- *inventory of all current high-risk*
		- *inventory of high-risk*

    - *PotentialHarmonize*
		- *coordination with the department*
		- *coordinate each executive branch department and agency*
		- *coordination with the state procurement office*

    - *Procurement*
		- *procurement of artificial intelligence*

### 16. `HI_[2024]_SB-2572`

- Title: *RELATING TO ARTIFICIAL INTELLIGENCE.*
- From: Hawaii, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *establishes the office of artificial intelligence safety and regulation within the department of commerce and consumer affairs to regulate the development, deployment, and use of artificial intelligence technologies in the state.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *regarding risk assessment*
		- *management of risk*
		- *assess existing and potential risk*
		- *its risk assessment*
		- *assessing and categorizing artificial intelligence systems based on risk*
		- *periodic risk assessments*

    - *GovBody*
		- *office of artificial intelligence*

### 17. `ID_[2024]_H-568`

- Title: *STATE AFFAIRS – Adds to existing law to establish the Artificial Intelligence Advisory Council.*
- From: Idaho, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *to require inventory reports regarding automated decision systems employed by state agencies*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessment of the impact*

    - *Inventory*
		- *automated decision systems inventory*
		- *inventory reports regarding automated decision systems*
		- *inventory report of all automated decision systems*

    - *GovBody*
		- *artificial intelligence council*

### 18. `IL_[103rd]_HB-3563`

- Title: *DOIT-AI TASK FORCE*
- From: Illinois, session `103rd`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the department of innovation and technology shall establish the generative ai and natural language processing task force investigate and provide a report on generative artificial intelligence software and natural language processing software.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessing the use*

### 19. `IL_[103rd]_HB-4836`

- Title: *STATE AGENCIES-AI SYSTEMS*
- From: Illinois, session `103rd`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *all state agency artificial intelligence systems or state-funded artificial intelligence systems must follow the trustworthiness, equity, and transparency standards framework established by the national institute for standards and technology's ai risk management framework.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *use evaluation*
		- *impact assessments*
		- *ai risk management*
		- *impact assessment*

    - *AIOfficer*
		- *chief artificial intelligence officer*

### 20. `IN_[2024]_SB-150`

- Title: *Artificial intelligence and cybersecurity.*
- From: Indiana, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *provides that political subdivisions, state agencies, school corporations, and state educational institutions (public entities) may adopt a: (1) technology resources policy; and (2) cybersecurity policy; subject to specified guidelines. specifies requirements for: (1) public entities; and (2) entities other than public entities; that connect to the state technology infrastructure of indiana.*
    - `has_ai_governance_body`: True
        - governance bodies: *Artificial Intelligence Task Force*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessment of the benefits and risk*

    - *Inventory*
		- *inventory of artificial intelligence*
		- *inventory of all artificial intelligence*

    - *PotentialHarmonize*
		- *collaboration with the department*

### 21. `MA_[193rd]_H-4024`

- Title: *An Act establishing a commission on automated decision-making by government in the Commonwealth*
- From: Massachusetts, session `193rd`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *establishing a commission on automated decision-making by government in the commonwealth*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *evaluate evidence based best practices for the use*

    - *Procurement*
		- *procurement or acquisition process whether a proposed agency automated decision system*

### 22. `MA_[193rd]_H-64`

- Title: *An Act establishing a commission on automated decision-making by government in the Commonwealth*
- From: Massachusetts, session `193rd`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *a bill has government scope if it governs the government's use of artificial intelligence (AI) or automated decision systems (ADS) in its operations.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *evaluate government use*
		- *assess how such system functions and is use*

    - *Procurement*
		- *procurement or acquisition process whether a proposed agency automated decision system*

### 23. `MA_[193rd]_HD-2261`

- Title: *An Act establishing a commission on automated decision-making by government in the Commonwealth*
- From: Massachusetts, session `193rd`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *there shall be a commission within the executive office of technology services and security for the purpose of studying and making recommendations relative to the use by the commonwealth of automated decision systems that may affect human welfare, including but not limited to the legal rights and privileges of individuals.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *evaluate government use*
		- *assess how such system functions and is use*

    - *Procurement*
		- *procurement or acquisition process whether a proposed agency automated decision system*

### 24. `MA_[193rd]_HD-4265`

- Title: *Special report of the Special Commission to Evaluate Government Use of Facial Recognition Technology (under Section 105 of Chapter 253 of the Acts of 2020 and most recently revived and continued by Section70 of Chapter 2 of the Acts of 2023) submitting its final report and appendices*
- From: Massachusetts, session `193rd`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *The bill contains provisions regarding the use of facial recognition technology by government entities, specifically focusing on law enforcement use and regulations.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assess privacy and other risk*
		- *evaluate government use*

    - *Procurement*
		- *purchase or otherwise utilize facial recognition*
		- *acquirement of facial recognition*

### 25. `MA_[193rd]_S-2539`

- Title: *An Act relative to cybersecurity and artificial intelligence*
- From: Massachusetts, session `193rd`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *an act relative to cybersecurity and artificial intelligence*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *evaluate the use*
		- *assess how such system functions and is use*

    - *Procurement*
		- *procurement or acquisition process whether a proposed governmental unit automated decision system*

### 26. `MA_[193rd]_S-33`

- Title: *An Act establishing a commission on automated decision-making by government in the commonwealth*
- From: Massachusetts, session `193rd`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *there shall be a commission within the executive office of technology services and security for the purpose of studying and making recommendations relative to the use by the commonwealth of automated decision systems that may affect human welfare, including but not limited to the legal rights and privileges of individuals.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *evaluate government use*
		- *assess how such system functions and is use*

    - *Procurement*
		- *procurement or acquisition process whether a proposed agency automated decision system*

### 27. `MD_[2024]_HB-1271`

- Title: *Information Technology - Artificial Intelligence - Policies and Procedures (Artificial Intelligence Governance Act of 2024)*
- From: Maryland, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *requiring the department of information technology to adopt policies and procedures concerning the development, procurement, implementation, use, and assessment of systems that employ artificial intelligence by units of state government; prohibiting a unit of state government from implementing or using a system that employs artificial intelligence under certain circumstances beginning on a certain date*
    - `has_ai_governance_body`: True
        - governance bodies: *Governor’S Artificial Intelligence Subcabinet*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *impact assessment*
		- *assess the likely impact*
		- *manage the risks of opportunities of artificial intelligence and determine appropriate permitted use*
		- *incorporate risk management*
		- *assessments of systems that employ artificial intelligence that are use*
		- *impact assessments*

    - *Inventory*
		- *inventories and ongoing assessments of systems that employ artificial intelligence*
		- *inventory of systems that employ artificial intelligence*
		- *inventory, a certain annual inventory of systems that employ artificial intelligence*

    - *GovBody*
		- *artificial intelligence subcabinet*

    - *PotentialHarmonize*
		- *coordinating council*
		- *collaboration with the state department*
		- *collaboration with the maryland department*

    - *Procurement*
		- *procurements; and generally relating to the use of artificial intelligence*
		- *procurement of a system that employs artificial intelligence*
		- *procurement of systems that employ artificial intelligence*
		- *procure or implement a system that employs artificial intelligence*
		- *procuring artificial intelligence*

### 28. `MD_[2024]_HB-883`

- Title: *Department of Information Technology - Evaluation of Emerging Technologies (Maryland Artificial Intelligence in Governmental Services Act)*
- From: Maryland, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *a bill has government scope if it governs the government's use of artificial intelligence (AI) or automated decision systems (ADS) in its operations.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *evaluation of the use*
		- *assessment of the use*

### 29. `MD_[2024]_SB-818`

- Title: *Information Technology - Artificial Intelligence - Policies and Procedures (Artificial Intelligence Governance Act of 2024)*
- From: Maryland, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *requiring each unit of state government to conduct a certain annual data inventory, a certain annual inventory of systems that employ artificial intelligence, and a certain impact assessment on or before a certain date; requiring the department of information technology to adopt policies and procedures concerning the development, procurement, implementation, use, and assessment of systems that employ artificial intelligence by units of state government; prohibiting a unit of state government from implementing or using a system that employs artificial intelligence under certain circumstances beginning on a certain date*
    - `has_ai_governance_body`: True
        - governance bodies: *Governor’S Artificial Intelligence Subcabinet Of The Governor’S Executive Council*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *impact assessment*
		- *assess the likely impact*
		- *manage the risks of opportunities of artificial intelligence and determine appropriate permitted use*
		- *incorporate risk management*
		- *assessments of systems that employ artificial intelligence that are use*
		- *impact assessments*

    - *Inventory*
		- *inventories and ongoing assessments of systems that employ artificial intelligence*
		- *inventory of systems that employ artificial intelligence*
		- *inventory, a certain annual inventory of systems that employ artificial intelligence*

    - *GovBody*
		- *artificial intelligence subcabinet*

    - *PotentialHarmonize*
		- *coordinating council*
		- *collaboration with the state department*
		- *collaboration with the maryland department*

    - *Procurement*
		- *procurements; and generally relating to the use of artificial intelligence*
		- *procurement of a system that employs artificial intelligence*
		- *procurement of systems that employ artificial intelligence*
		- *procure or implement a system that employs artificial intelligence*
		- *procuring artificial intelligence*

### 30. `NM_[2024]_HB-184`

- Title: *USE OF ARTIFICIAL INTELLIGENCE TRANSPARENCY*
- From: New Mexico, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *requiring inventories and assessments of artificial intelligence system use; requiring reports; amending the procurement code; requiring vendor transparency for purchases of artificial intelligence products and services*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessment of each artificial intelligence system use*
		- *assessment pursuant to the government use*
		- *assessed using local data and the source of other data use*
		- *assessments of artificial intelligence system use*

    - *Inventory*
		- *inventory or assessment pursuant to the government use of artificial intelligence*
		- *inventory shall include the following information for each artificial intelligence*
		- *inventories and assessments of artificial intelligence*

    - *Procurement*
		- *purchases of artificial intelligence*

### 31. `NY_[2023-2024]_A-3308`

- Title: *Enacts the "digital fairness act"*
- From: New York, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the legislature also finds that it has had a decades long interest in protecting new yorkers' privacy. for example, since 1996, section 79-l of the new york civil rights law has protected the privacy of genetic information, requiring an individual's informed, written consent prior to genetic testing and restricting the disclosure and retention of genetic information.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *impact assessments*
		- *assessment of the risk*
		- *evaluating the use of proxies and the types of data use*
		- *impact assessment*

    - *Procurement*
		- *acquiring agency has complied with the automated decision system impact assessment and automated decision system*
		- *automated decision systems prior to acquisition*
		- *acquisition, or deployment of new automated decision systems*
		- *acquiring or borrowing an automated decision system*

### 32. `NY_[2023-2024]_A-8195`

- Title: *Relates to enacting the "advanced artificial intelligence licensing act"*
- From: New York, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *The legislature hereby finds and declares that certain applications of artificial intelligence harbor such an immense capacity for causing significant harm to the security, integrity, and moral wellbeing of the state and such a risk of becoming uncontainable that the state has a compelling interest in preventing their creation.*
    - `has_ai_governance_body`: True
        - governance bodies: *Advisory Council For Artificial Intelligence*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *and risk management*
		- *assessment of new risks or risk*
		- *evaluations of the source code and outcomes associated with each high-risk*
		- *evaluation of known use cases of the system by use*
		- *thorough risk assessment*
		- *assess the ethical implications of all possible use*

    - *GovBody*
		- *council for artificial intelligence*

    - *PotentialHarmonize*
		- *coordinate across state agencies and department*

### 33. `NY_[2023-2024]_A-9430`

- Title: *Enacts the legislative oversight of automated decision-making in government act (LOADinG Act)*
- From: New York, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *enacts the legislative oversight of automated decision-making in government act (loading act) to regulate the use of automated decision-making systems and artificial intelligence techniques by state agencies.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessment of whether the use*
		- *impact assessments*
		- *impact assessment*

### 34. `NY_[2023-2024]_R-1952`

- Title: *Senate budget resolution in response to the 2024-2025 Executive Budget submission*
- From: New York, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the senate advances language to require statutory authorization and impact assessments for state agencies using automated decision-making systems (s.7543-b) and to create the position of chief artificial intelligence officer within the office of information technology services.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *impact assessments*

    - *PotentialHarmonize*
		- *coordinating office*

    - *AIOfficer*
		- *chief artificial intelligence officer*

### 35. `NY_[2023-2024]_S-2277`

- Title: *Enacts the "digital fairness act"*
- From: New York, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the legislature also finds that it has had a decades long interest in protecting new yorkers' privacy. for example, since 1996, section 79-l of the new york civil rights law has protected the privacy of genetic information, requiring an individual's informed, written consent prior to genetic testing and restricting the disclosure and retention of genetic information.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *impact assessments*
		- *assessment of the risk*
		- *evaluating the use of proxies and the types of data use*
		- *impact assessment*

    - *Procurement*
		- *acquiring agency has complied with the automated decision system impact assessment and automated decision system*
		- *automated decision systems prior to acquisition*
		- *acquisition, or deployment of new automated decision systems*
		- *acquiring or borrowing an automated decision system*

### 36. `NY_[2023-2024]_S-7543`

- Title: *Enacts the legislative oversight of automated decision-making in government act (LOADinG Act)*
- From: New York, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *enacts the legislative oversight of automated decision-making in government act (loading act) to regulate the use of automated decision-making systems and artificial intelligence techniques by state agencies.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessment of whether the use*
		- *impact assessments*
		- *impact assessment*

### 37. `OK_[2024]_HB-3828`

- Title: *State government; Office of Management and Enterprise Services; artificial intelligence; Administrative Office of the Courts; inventory; procedures; effective date.*
- From: Oklahoma, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *This bill directs the office of management and enterprise services to conduct inventory of artificial intelligence systems used by state agencies and establishes policies and procedures for the development, procurement, and ongoing assessment of these systems.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessment of systems that employ artificial intelligence and are in use*
		- *impact assessment*
		- *assess the likely impact*
		- *assessments of systems that employ artificial intelligence and are in use*
		- *management and enterprise services or agencies that do not use*
		- *management and enterprise services or any agency that does not use*

    - *Inventory*
		- *inventory of all systems that employ artificial intelligence*

### 38. `PA_[2023-2024]_HR-170`

- Title: *A Resolution directing the Joint State Government Commission to establish an advisory committee to conduct a study on the field of artificial intelligence and its impact and potential future impact in Pennsylvania.*
- From: Pennsylvania, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *resolved, that the house of representatives direct the joint state government commission to investigate the field of artificial intelligence and make recommendations on the responsible growth of this commonwealth's emerging technology markets and the use of artificial intelligence in state government and study how other states regulate the artificial intelligence field*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessment of the development and use*
		- *assessment of how ai has been use*

### 39. `PA_[2023-2024]_SR-143`

- Title: *A Resolution directing the Joint State Government Commission to establish an advisory committee to conduct a study on the field of artificial intelligence and its impact and potential future impact in Pennsylvania.*
- From: Pennsylvania, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *resolved, that the senate direct the joint state government commission to conduct a study on the field of artificial intelligence and make recommendations on the responsible growth of pennsylvania's emerging technology markets and the use of artificial intelligence in state government and to analyze how other states regulate the artificial intelligence field*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessment of the development and use*
		- *assessment of how artificial intelligence has been use*

### 40. `RI_[2023]_HB-6423`

- Title: *AN ACT RESPECTFULLY REQUESTING THE DEPARTMENT OF ADMINISTRATION AND THE OFFICE OF INFORMATION TECHNOLOGY TO REVIEW AND EVALUATE THE USE AND DEVELOPMENT OF ARTIFICIAL INTELLIGENCE (AI) AND AUTOMATED DECISION SYSTEMS AND PROVIDE RECOMMENDATIONS REGARDING ONGOING AND UPCOMING PLANS TO EXPAND THEIR USE AND CURRENT SECURITY AND IMPLEMENTATION PROCEDURES*
- From: Rhode Island, session `2023`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *an act respectfully requesting the department of administration and the office of information technology to review and evaluate the use and development of artificial intelligence (ai) and automated decision systems and provide recommendations regarding ongoing and upcoming plans to expand their use and current security and implementation procedures*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *evaluate the use*

### 41. `RI_[2023]_HR-6423`

- Title: *HOUSE RESOLUTION RESPECTFULLY REQUESTING THE DEPARTMENT OF ADMINISTRATION AND THE OFFICE OF INFORMATION TECHNOLOGY TO REVIEW AND EVALUATE THE USE AND DEVELOPMENT OF ARTIFICIAL INTELLIGENCE (AI) AND AUTOMATED DECISION SYSTEMS AND PROVIDE RECOMMENDATIONS REGARDING ONGOING AND UPCOMING PLANS TO EXPAND THEIR USE AND CURRENT SECURITY AND IMPLEMENTATION PROCEDURES*
- From: Rhode Island, session `2023`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *requests the department of administration and the ri division of information technology report the extent of algorithmic decision-making used by the state of rhode island and the progress made toward implementing any recommendations previously issued; how automated decision systems are validated, tested, and evaluated including for the effects of racial, gender, and other biases that are unknown to be perpetuated by ai technology; and all matters related to data sources, data sharing agreements, and data security provisions;*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *evaluate the use*

### 42. `RI_[2024]_HB-7158`

- Title: *AN ACT RELATING TO STATE AFFAIRS AND GOVERNMENT -- ARTIFICIAL INTELLIGENCE ACCOUNTABILITY ACT*
- From: Rhode Island, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *establishes a permanent commission to monitor the use of ai in state government and makes recommendations for state government policy and other decisions.*
    - `has_ai_governance_body`: True
        - governance bodies: *Rhode Island Artificial Intelligence Commission*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assess the likely impact*
		- *assessment of systems that employ artificial intelligence and are in use*
		- *assessments of systems that employ artificial intelligence and are in use*
		- *impact assessment*

    - *Inventory*
		- *inventory of all state agencies using artificial intelligence*
		- *inventory of all systems that employ artificial intelligence*

### 43. `TN_[113]_HB-2747`

- Title: *Finance and Administration, Dept. of - As introduced, enacts the "Tennessee Artificial Intelligence Advisory Council Act." - Amends TCA Title 4.*
- From: Tennessee, session `113`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the advisory council is attached to the department of finance and administration for administrative purposes.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *evaluation of potentially beneficial use*

### 44. `TN_[113]_SB-2678`

- Title: *Finance and Administration, Dept. of - As introduced, enacts the "Tennessee Artificial Intelligence Advisory Council Act." - Amends TCA Title 4.*
- From: Tennessee, session `113`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the advisory council is attached to the department of finance and administration for administrative purposes.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *evaluation of potentially beneficial use*

### 45. `TX_[88]_HB-2060`

- Title: *Relating to the creation of the artificial intelligence advisory council.*
- From: Texas, session `88`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *a bill has government scope if it governs the government's use of artificial intelligence (AI) or automated decision systems (ADS) in its operations.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessment of the impact*

    - *Inventory*
		- *inventoryreport of all automated decision systems*
		- *automated decisionsystems inventory*
		- *automated decision systems inventory*

### 46. `UT_[2024]_HB-3`

- Title: *Appropriations Adjustments*
- From: Utah, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *to implement the provisions of artificial intelligence amendments (senate bill 149, 2024 general session).*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *600 risk management*

### 47. `VA_[2024]_SB-487`

- Title: *Artificial intelligence by public bodies; prohibitions.*
- From: Virginia, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *prohibits any public body from implementing any system that employs artificial intelligence, defined in the bill, unless such public body (i) performs an initial impact assessment and ongoing impact assessments of such system to ensure its use will not result in any unlawful discrimination against any individual or group of individuals or have any disparate impact on any individual or group of individuals and (ii) does not implement or ceases to use such system if such effects occur.*
    - `has_ai_governance_body`: True
        - governance bodies: *Commission On Artificial Intelligence*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessment of systems that employ artificial intelligence and are in use*
		- *assessments and provide an inventory of all such systems use*
		- *impact assessment*
		- *assess the likely impact*
		- *assess potential options for an ai bill of rights concerning the regulation and use*
		- *impact assessments*
		- *assessments and provide an inventory of such systems use*

    - *Inventory*
		- *inventory of all such systems use*
		- *inventory of such systems use*

### 48. `VA_[2024]_SB-621`

- Title: *Artificial Intelligence, Commission on; established, report, sunset provision.*
- From: Virginia, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the purpose of the commission is to advise the governor on issues related to artificial intelligence and make advisory recommendations based on its findings.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assess potential options for an ai bill of rights concerning the regulation and use*

### 49. `WA_[2023-2024]_HB-1934`

- Title: *Establishing an artificial intelligence task force.*
- From: Washington, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the legislature finds that artificial intelligence is a fast-evolving technology that holds extraordinary potential and has a myriad of uses for both the public and private sectors. advances in artificial intelligence technology have led to programs that are capable of creating text, audio, and media that are difficult to distinguish from media created by a human. this technology has the potential to provide great benefits to people if used well and to cause great harm if used irresponsibly.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assess current use*
		- *impact assessment*

### 50. `WA_[2023-2024]_SB-5356`

- Title: *Establishing guidelines for government procurement and use of automated decision systems in order to protect consumers, improve transparency, and create more market predictability.*
- From: Washington, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *establishing guidelines for government procurement and use of automated decision systems in order to protect consumers, improve transparency, and create more market predictability.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessment should include evaluation of the potential impact*
		- *management policy prior to the use*
		- *assessment should include the existence or risk*

    - *Inventory*
		- *inventory of all algorithmic accountability reports on automated decision systems*

    - *Procurement*
		- *procure automated decision systems*
		- *procurement contract for an automated decision system*
		- *procurement, and development of automated decision systems*
		- *procurement, and use of automated decision systems*
		- *automated decision systems procured*
		- *procures an automated decision system*
		- *acquired automated decision systems*
		- *procurement and use of automated decision systems*
		- *procures, or uses an automated decision system*
		- *procure an automated decision system*
		- *procurement, or use of an automated decision system*

### 51. `WA_[2023-2024]_SB-5838`

- Title: *Establishing an artificial intelligence task force.*
- From: Washington, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *washington technology solutions (watech) developed guiding principles for artificial intelligence use by state agencies.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assess current use*
		- *impact assessment*

### 52. `WA_[2023-2024]_SB-5957`

- Title: *Requiring the office of privacy and data protection to develop guidelines for the use of artificial intelligence.*
- From: Washington, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *requiring the office of privacy and data protection to develop guidelines for the use of artificial intelligence.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *management designed to ensure optimum use*

    - *PotentialHarmonize*
		- *coordinate data protection in cooperation with the agency*

### 53. `WI_[2023]_AB-1068`

- Title: *Relating to: use of artificial intelligence by state agencies and staff reduction goals. (FE)*
- From: Wisconsin, session `2023`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *this bill requires, beginning in 2030, each submission to include a proposal to reduce the total number of the agency's position authorizations for each fiscal year of the succeeding fiscal biennium using as a base the agency's total number of position authorizations in the 2023-24 fiscal year.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *evaluate the data collected and use*

    - *Inventory*
		- *inventory of each artificial intelligence*

### 54. `WI_[2023]_SB-1010`

- Title: *Relating to: use of artificial intelligence by state agencies and staff reduction goals. (FE)*
- From: Wisconsin, session `2023`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *this bill requires, beginning in 2030, each submission to include a proposal to reduce the total number of the agency's position authorizations for each fiscal year of the succeeding fiscal biennium using as a base the agency's total number of position authorizations in the 2023-24 fiscal year.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *evaluate the data collected and use*

    - *Inventory*
		- *inventory of each artificial intelligence*

### 55. `WV_[2024]_HB-5690`

- Title: *Creating a West Virginia Task Force on Artificial Intelligence*
- From: West Virginia, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the west virginia task force on artificial intelligence is created and shall be organized within the office of the governor.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *ImpactAssess*
		- *assessing the use*

    - *Inventory*
		- *inventory of the current or proposed use of artificial intelligence*

### 56. `IL_[103rd]_HB-4705`

- Title: *ARTIFICIAL INTELLIGENCE REPORT*
- From: Illinois, session `103rd`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *This act may be cited as the artificial intelligence reporting act. State agency shall prepare an annual report concerning the state agency's use of covered algorithms in its operations.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *Inventory*
		- *inventory of all covered algorithms use*

    - *AIOfficer*
		- *chief artificial intelligence officer*

### 57. `NJ_[220]_S-3876`

- Title: *Concerns regulation of automated systems and artificial intelligence used by State agencies.*
- From: New Jersey, session `220`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the bill establishes the position of the artificial intelligence officer, who would be appointed by the chief technology officer, and is required to have extensive knowledge on automated systems and artificial intelligence. under the bill, the artificial intelligence officer is required to develop, and update every two years, procedures regulating the use of automated systems by state agency making critical decisions, which procedures would distributed to all state agencies and posted on the office of information technology’s internet website.*
    - `has_ai_governance_body`: True
        - governance bodies: *New Jersey Artificial Intelligence Advisory Board*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *Inventory*
		- *inventory all automated systems that are use*
		- *inventory of the automated systems that are use*
		- *inventory shall be in a form prescribed by the artificial intelligence*
		- *inventory to the artificial intelligence officer and the new jersey artificial intelligence*

    - *GovBody*
		- *artificial intelligence office*
		- *department of artificial intelligence*

    - *Procurement*
		- *procure, or utilize any automated system shall provide to the artificial intelligence*

    - *AIOfficer*
		- *artificial intelligence officer*
		- *“artificial intelligence officer*

### 58. `NJ_[221]_S-1438`

- Title: *Concerns regulation of automated systems and artificial intelligence used by State agencies.*
- From: New Jersey, session `221`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *This bill concerns the regulation of automated systems and artificial intelligence used by state agencies.*
    - `has_ai_governance_body`: True
        - governance bodies: *New Jersey Artificial Intelligence Advisory Board*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *Inventory*
		- *inventory all automated systems that are use*
		- *inventory of the automated systems that are use*
		- *inventory shall be in a form prescribed by the artificial intelligence*
		- *inventory to the artificial intelligence officer and the new jersey artificial intelligence*

    - *GovBody*
		- *artificial intelligence office*
		- *department of artificial intelligence*

    - *Procurement*
		- *procure, or utilize any automated system shall provide to the artificial intelligence*

    - *AIOfficer*
		- *artificial intelligence officer*
		- *“artificial intelligence officer*

### 59. `CA_[20232024]_SB-313`

- Title: *Department of Technology: Office of Artificial Intelligence: state agency public interface: use of AI.*
- From: California, session `20232024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *this bill would enact the california ai-ware act, which would establish, within the department of technology, the office of artificial intelligence, and would grant the office the power and authority necessary to guide the design, use, and deployment of automated systems by a state agency to ensure that all ai systems are designed and deployed in a manner that is consistent with state and federal laws and regulations regarding privacy and civil liberties and that minimizes bias and promotes equitable outcomes for all californians.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *GovBody*
		- *office of artificial intelligence*

### 60. `MD_[2023]_HB-1068`

- Title: *Commission on Responsible Artificial Intelligence in Maryland*
- From: Maryland, session `2023`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *establishing the commission on responsible artificial intelligence in Maryland to study certain issues related to the use and regulation of artificial intelligence*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *GovBody*
		- *department of artificial intelligence*

### 61. `NY_[2023-2024]_S-8755`

- Title: *Enacts the New York artificial intelligence ethics commission act*
- From: New York, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the commission shall consist of nine members: three appointed by the governor; two appointed by the temporary president of the senate; one appointed by the minority leader of the senate; two appointed by the speaker of the assembly; one appointed by the minority leader of the assembly, reflective of diverse expertise in ai technology, ethics, law, and public policy.*
    - `has_ai_governance_body`: True
        - governance bodies: *New York Artificial Intelligence Ethics Commission*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *GovBody*
		- *artificial intelligence ethics commission*

### 62. `CA_[20232024]_SB-893`

- Title: *California Artificial Intelligence Research Hub.*
- From: California, session `20232024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the bill would require the government operations agency, the governor's office of business and economic development, and the department of technology to collaborate to establish the california artificial intelligence research hub (hub) in the government operations agency.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *PotentialHarmonize*
		- *collaborate to establish the california artificial intelligence research hub in the government operations agency*

### 63. `MA_[193rd]_H-4459`

- Title: *An Act relative to strengthening Massachusetts' economic leadership*
- From: Massachusetts, session `193rd`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the bill will reauthorize the massworks infrastructure program to continue making investments in local infrastructure to unlock critical development projects in our communities; codify a rural community program and reauthorize the rural development fund; and establish a new tax credit to promote internships for young adults who attend our many colleges and universities so they are more likely to stay in massachusetts after completing their studies. we are again proposing a new tax credit for live theater productions to bolster our creative economy, as well as new reforms to the economic development incentive program (edip), both to make the edip tax credit a more effective tool to attract and retain jobs and to give local municipalities more autonomy to provide local tax incentives to spur capital investment and job creation. finally, we are proposing capital authorizations that will allow our quasi-public agencies to support other key sectors such as artificial intelligence, robotics and advanced manufacturing.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *PotentialHarmonize*
		- *collaboration with the department*

### 64. `TN_[113]_HB-2341`

- Title: *State Government - As introduced, requires each department of the executive branch to develop a plan to prevent the malicious and unlawful use of artificial intelligence for the purpose of interfering with the operation of the department, its agencies and divisions, and persons and entities regulated by the respective department; requires each department to report its plan, findings, and recommendations to each member of the general assembly no later than January 1, 2025.  - Amends TCA Title 2; Title 4; Title 8; Title 38; Title 39 and Title 47, Chapter 18.*
- From: Tennessee, session `113`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *requires each department of the executive branch to develop a plan to prevent the malicious and unlawful use of artificial intelligence for the purpose of interfering with the operation of the department, its agencies and divisions, and persons and entities regulated by the respective department*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *PotentialHarmonize*
		- *collaborate with other department*

### 65. `TN_[113]_SB-2461`

- Title: *State Government - As introduced, requires each department of the executive branch to develop a plan to prevent the malicious and unlawful use of artificial intelligence for the purpose of interfering with the operation of the department, its agencies and divisions, and persons and entities regulated by the respective department; requires each department to report its plan, findings, and recommendations to each member of the general assembly no later than January 1, 2025.  - Amends TCA Title 2; Title 4; Title 8; Title 38; Title 39 and Title 47, Chapter 18.*
- From: Tennessee, session `113`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *requires each department of the executive branch to develop a plan to prevent the malicious and unlawful use of artificial intelligence for the purpose of interfering with the operation of the department, its agencies and divisions, and persons and entities regulated by the respective department*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *PotentialHarmonize*
		- *collaborate with other department*

### 66. `WA_[2023-2024]_HB-1140`

- Title: *Making 2023-2025 fiscal biennium operating appropriations.*
- From: Washington, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the office of the chief information officer who must convene a work group to examine how automated decision making systems can best be reviewed before adoption and while in operation and be periodically audited to ensure that such systems are fair, transparent, accountable and do not improperly advantage or disadvantage washington residents.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *PotentialHarmonize*
		- *coordinate with the state emergency management division*
		- *collaborate with the department*

    - *Procurement*
		- *procurement of automated decision systems*
		- *procurement, and use of automated decision systems*
		- *procurement and use of automated decision systems*

### 67. `WA_[2023-2024]_HB-1141`

- Title: *Making 2021-2023 fiscal biennium second supplemental operating appropriations.*
- From: Washington, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the office of the chief information officer who must convene a work group to examine how automated decision making systems can best be reviewed before adoption and while in operation and be periodically audited to ensure that such systems are fair, transparent, accountable and do not improperly advantage or disadvantage washington residents.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *PotentialHarmonize*
		- *coordinate with the state emergency management division*
		- *collaborate with the department*

    - *Procurement*
		- *procurement of automated decision systems*
		- *procurement, and use of automated decision systems*
		- *procurement and use of automated decision systems*

### 68. `WA_[2023-2024]_SB-5187`

- Title: *Making 2023-2025 fiscal biennium operating appropriations.*
- From: Washington, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the office of the chief information officer who must convene a work group to examine how automated decision making systems can best be reviewed before adoption and while in operation and be periodically audited to ensure that such systems are fair, transparent, accountable and do not improperly advantage or disadvantage washington residents.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *PotentialHarmonize*
		- *coordinate with the state emergency management division*
		- *collaborate with the department*

    - *Procurement*
		- *procurement of automated decision systems*
		- *procurement, and use of automated decision systems*
		- *procurement and use of automated decision systems*

### 69. `WA_[2023-2024]_SB-5188`

- Title: *Making 2021-2023 fiscal biennium second supplemental operating appropriations.*
- From: Washington, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the office of the chief information officer who must convene a work group to examine how automated decision making systems can best be reviewed before adoption and while in operation and be periodically audited to ensure that such systems are fair, transparent, accountable and do not improperly advantage or disadvantage washington residents.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *PotentialHarmonize*
		- *coordinate with the state emergency management division*
		- *collaborate with the department*

    - *Procurement*
		- *procurement of automated decision systems*
		- *procurement, and use of automated decision systems*
		- *procurement and use of automated decision systems*

### 70. `IL_[103rd]_HB-5099`

- Title: *AI USE IN GOVT CONTRACTS*
- From: Illinois, session `103rd`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *requires a vendor who contracts for government services, grants, or leases or purchases of software or hardware to disclose if artificial intelligence technology is, has been, or will be used in the course of fulfilling the contract or in the goods, technology, or services being purchased.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *Procurement*
		- *purchases of software or hardware must disclose if artificial intelligence*
		- *purchases of software or hardware to disclose if artificial intelligence*

### 71. `IL_[103rd]_HB-5228`

- Title: *AI USE IN GOVT CONTRACTS*
- From: Illinois, session `103rd`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *requires a vendor who contracts for government services, grants, or leases or purchases of software or hardware to disclose if artificial intelligence technology is, has been, or will be used in the course of fulfilling the contract or in the goods, technology, or services being purchased.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *Procurement*
		- *purchases of software or hardware must disclose if artificial intelligence*
		- *purchases of software or hardware to disclose if artificial intelligence*

### 72. `KY_[2024RS]_HCR-38`

- Title: *A CONCURRENT RESOLUTION relating to the establishment of the Artificial Intelligence Task Force to study the impact of artificial intelligence on operation and procurement policies of Kentucky government agencies and consumer protection needed in private and public sectors.*
- From: Kentucky, session `2024RS`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *a bill has government scope if it governs the government's use of artificial intelligence (AI) or automated decision systems (ADS) in its operations.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *Procurement*
		- *procurement policies and provide recommendations on artificial intelligence*

### 73. `MN_[2023-2024]_HF-2048`

- Title: *Acquisition and use of facial recognition technology by government entities prohibited.*
- From: Minnesota, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *prohibiting the acquisition and use of facial recognition technology by government entities*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *Procurement*
		- *acquisition and use of facial recognition*

### 74. `MN_[2023-2024]_SF-129`

- Title: *Acquisition and use prohibition of facial recognition technology by government entities*
- From: Minnesota, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *prohibiting the acquisition and use of facial recognition technology by government entities*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *Procurement*
		- *acquisition and use of facial recognition*
		- *acquisition and use prohibition of facial recognition*

### 75. `NM_[2024]_SB-130`

- Title: *ARTIFICIAL INTELLIGENCE WORK GROUP*
- From: New Mexico, session `2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *the security officer shall convene a work group to develop legislative proposals and recommendations for policies for state use and procurement of artificial intelligence systems.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *Procurement*
		- *procurement of artificial intelligence*

### 76. `NY_[2023-2024]_A-5309`

- Title: *Requires state units to purchase a product or service that is or contains an algorithmic decision system that adheres to responsible artificial intelligence standards*
- From: New York, session `2023-2024`
- OpenAI extraction results:
    - `has_government_scope`: True
        - relevant excerpt: *a bill has government scope if it governs the government's use of artificial intelligence (AI) or automated decision systems (ADS) in its operations.*
    - `has_ai_governance_body`: False
        - governance bodies: *NA*
    - `has_harmonization`: False
        - relevant excerpt: *NA*


    
- Keyword category detection results:


    - *Procurement*
		- *purchase a product or service that adheres to responsible artificial intelligence*

Pharmacology-LLM-test-set: A test set for a large language model focused on pharmacology tasks

1 Inroduction

  Large language models (LLM), including ChatGPT, have fundamentally transformed the knowledge query schemes and methods in pharmacology for pharmacologists, drug researchers, clinical drug researchers, and artificial intelligence researchers in pharmacology. They can conduct multi-round consultations and query pharmacological issues in a question-and-answer format. However, pharmacology is a particularly complex field of application. To better apply large language models to pharmacological practice, we propose a pharmacology test set composed of three types of pharmacological tasks: drug attribute queries, lead compound structure optimization, and summarization of trends and limitations. This test set serves as a benchmark for general or pharmacology-specific large models, covering a variety of application scenarios in pharmacology (Figure 1).
 
  ![image](https://github.com/zyb1984/Pharmacology-LLM-test-set/blob/master/%E5%9B%BE010203.tiff)
  
  Figure 1 Pharmacology-LLM-TestSet Construction and ChatGPT Benchmark Evaluation Process

2 Test set Construction
   
   Pharmacology-LLM-test-set: Includes three basic components:
  
  （1）Pharmacological Attribute Query instructions: Encompassing chemical identifiers, drug molecular weight, drug isotopic molecular weight, bioavailability, specific surface area, pharmacokinetics, drug-drug interactions, etc., pharmacological attribute queries are fundamental needs and tasks in pharmacological research. To systematically explore and compare the performance of general large language models and specialized pharmacology large language models in pharmacological tasks, we use the DrugBank database as a data resource and employ a quartile method to categorize drugs into large, medium, and small molecules. Specifically, we selected Apremilast, Dequalinium, Irbesartan, Montelukast, and Silodosin as representatives of large molecules (molecular weight > 412.64, in the top 25% percentile), Camostat, Dimetacrine, Naltrexone, Pefloxacin, and Ropivacaine as medium molecules (412.64 > molecular weight > 255.24), and Amobarbital, Benzphetamine, Butobarbital, Chlorzoxazone, and Dezocine as small molecules (molecular weight < 255.24, in the bottom 25% percentile). For the pharmacological attribute query tasks, we examined five categories: chemical identifiers, basic physicochemical properties, pharmacological properties, target proteins, and drug-drug interactions. Furthermore, for chemical identifiers, we chose IUPAC International Chemical Identifier (InChI), Standard InChI hashes (InChIKey), International Union of Pure and Applied Chemistry (IUPAC) Name, Simplified Molecular Input Line Entry System (SMILES) Name, and Molecular Formula as standards for testing. For basic pharmacological properties, we selected Molecular Weight (MW), Monoisotopic Weight, Logarithm of the Partition Coefficient (logP), Bioavailability, and Polar Surface Area (PSA) as standards. For pharmacological properties, we chose indications of pharmacological properties, pharmacodynamics, mechanism of action, and toxicity as standards. For drug targets, we selected agonist, antagonist, blocker, inhibitor, and modulator as target protein properties. For drug-drug side effects, we identified ten drug-drug side effect risks, such as cross-tissue risk, therapeutic efficacy, nervous system disease, as potential risk indicators (Figure S2).
  
  （2）Lead Compound Structure Optimization instructions: This instruction aimed to ascertain ChatGPT's potential in exploring drug structure optimization. Referring to the series of articles on "Lead compound structure optimization strategies" published by Professor Hong Liu's team at the Shanghai Institute of Materia Medica, Chinese Academy of Sciences, from 2013 to 2021, we explored the application potential of ChatGPT in compound structure optimization schemes. Specifically, we focused on optimizing compounds with goals such as "Metabolic stability", "Enhanced water solubility", "Reduced cardiac toxicity", and "Minimized adverse effects". Details include optimizing metabolic stability with compounds like buspirone, paroxetine, and 8-chloro-4-(4-methylpiperazin-1-yl)benzofuro[3,2-d]pyrimidine; reducing liver toxicity with compounds like amodiaquine and ibufenac; reducing cardiac toxicity with compounds like 2-[[(2R)-4-(4-fluorophenyl)-2-methylpiperazin-1-yl]methyl]-7-methoxy-[1,2,4]triazolo[1,5-c]quinazolin-5-amine and N-(2,3-dihydro-[1,4]dioxino[2,3-c]pyridin-7-ylmethyl)-1-[2-(3-fluoro-6-methoxy-1,5-naphthyridin-4-yl)ethyl]piperidin-4-amine; and enhancing water solubility with compounds like rilpivirine, 8-hydroxyquinoline, and paclitaxel (Taxol).
  
  （3）Systematic Summary of Pharmacological Texts instructions: The main purpose of this instructions are to explore the large language model's performance in summarizing pharmacological texts. For this task, which involves summarizing and logically inferring the "Current limitations of research and future trends", we selected questions related to the "Problems and limitations of current pharmacology research" and the "future directions and trends of pharmacology research" as query questions."

2.2 Data Release 
  
   We also release the testset on Hugging Face at zhangyingbo1984/Pharmacology-LLM-test-set.

3 Large Language Model (LLM) Performance Evaluation
    
    To assess the capabilities of large language models in a pharmacology test dataset, we evaluated the performance of OpenAI's ChatGPT and GPT-4 on the Pharmacology-LLM-TestSet. The reason for choosing ChatGPT and GPT-4 as representatives of large language models is that they are among the earliest and most widely used general-purpose large language models. Furthermore, evaluations based on several pharmacology and biology datasets have also found that ChatGPT and GPT-4 are the best-performing general-purpose large language models.

3.1 Key prompt
   
   To evaluate the performance of large language models on the pharmacology test set in a balanced and unbiased manner, we used the prompt, “Imagine you are a pharmacologist, answer with fairness, justice, and a scientific attitude.” Additionally, to ensure consistent results, all questions for the three types of tasks mentioned above were administered in triplicate to ChatGPT.

3.2 Pharmacological Attribute Query Instructions
  
  For the pharmacological attribute query instructions, we adopted the inquiry method, “Imagine you are a pharmacologist, could you list the InChI Identifier of ropivacaine, chlorzoxazone, ...?” Specifically, (1) we included “Imagine you are a pharmacologist” as the Key prompt in each inquiry. (2) For the queried drugs, we would clearly list their standard names, which are sourced from DrugBank. (3) For the query targets, we would specify InChI Identifier, InChIKey Identifier, targets (including agonist, antagonist, blocker, inhibitor, and modulator as the five types of targets).

3.3 Lead Compound Structure Optimization Instructions
  
  For the lead compound structure optimization instructions, we consistently used the inquiry, "Buspirone is a 5-HT1A receptor agonist with anxiolytic effects. In terms of its in vivo metabolism kinetics, the pyrimidine ring at the 5-position of the molecule can undergo hydroxylation by CYP3A4, leading to a relatively short half-life. Imagine you are a pharmacologist, how can its in vivo half-life be prolonged through chemical structure optimization?" Specifically, (1) in each inquiry, "Imagine you are a pharmacologist" is included as the Key prompt. (2) For the drug query, we explicitly list the standard drug name and provide a brief background of these drugs, all of which are validated in Drugbank. (3) Regarding the optimization background and goals, we clearly state the objectives that need optimization, such as "increase metabolic stability," "reduce liver toxicity," "reduce cardiac toxicity," and "increase water solubility." At the same time, we also briefly describe background knowledge and information, such as the metabolism kinetics of the compound and how the pyrimidine ring at the 5-position can undergo hydroxylation by CYP3A4, leading to a relatively short half-life.

3.4 Systematic Summary of Pharmacological Texts Instructions
  
  For the systematic summary of pharmacological texts instructions, we consistently used the inquiry, "Imagine you are a pharmacologist, try to list the current limitations of pharmacological research and explain the basis." Not only do we clearly indicate the Key prompt, such as "Imagine you are a pharmacologist." but we also clearly specify the features that need systematic summarization, such as "current limitations" and "future trends."

3.5 Large Language Model Evaluation and Scoring for Answers

For different tasks, we adopted various evaluation methods. Specifically, for the first and second types of instructions, the scoring system used data records from the DrugBank database or records from Hong Liu's paper as the gold standard. It includes the characteristics of the tasks and uses both a correct/incorrect (100%/0) scoring method and a percentage scoring method. For the third type of question, a percentage scoring method is employed, combining frequency and importance. The scores, evaluated by three independent reviewers, are the basis for assessing the importance and exploring the potential application of ChatGPT in summarizing and inferring events.

After completing the task queries and task scoring, we used the Cronbach's Alpha index to assess the scoring agreement between different versions of ChatGPT (versions 3.5 and 4) and between repeated assessments. We then analyzed and compared the accuracy and repeatability of the results provided by ChatGPT and GPT-4 using direct comparison methods (Figure S1).

Furthermore, to compare the strengths and weaknesses of ChatGPT and GPT-4 across pharmacology tasks, we used different comparison methods for different tasks. For the first type of task, basic drug attribute queries, we assessed the performance of different versions of ChatGPT using the accuracy rate, true positive rate, false positive rate, and paired t-tests. Specifically, for predictive tasks with a single correct answer, such as Chemical Formula, molecular weight, isotopic molecular weight, logP, etc., we used the accuracy rate as the test metric and compared the predictive effectiveness of ChatGPT and GPT-4 using paired t-tests.

For predictive tasks with two or more correct answers, such as drug-drug interaction information and drug target information, we used the true positive rate and false positive rate as test metrics, comparing the predictive effectiveness of ChatGPT and GPT-4 using paired t-tests.

For tasks evaluated on a percentage scale for basic pharmacological properties, pharmacokinetics, drug mechanism of action, drug toxicity, etc., the tasks were assessed based on scoring quality, and paired t-tests were used to test the significance of the scores. For the second and third types of tasks, 'Lead Compound Structure Optimization' and 'Systematic Summary of Pharmacology Research Limitations/Trends,' we similarly directly tested the significance of the performance differences between different versions of GPT using paired t-tests.

4. About

4.1 References

  If you use our repository, please cite the following related paper:
 @article{Pharmacology-LLM-test-set,
  title={ Pharmacology-LLM-test-set: A test set for a large language model focused on pharmacology tasks },
  author={Yingbo Zhang, Jiao Wang, Dan Du, Zhajun Zhan, Rajeev K. Singla, and Bairong Shen},
  url={ https://github.com/zyb1984/Pharmacology-LLM-test-set },
  year={2024}
}

4.2 Acknowledgements
  
  Firstly, we express our gratitude to the Drugbank database for its collection and organization of existing pharmaceutical resources. We also acknowledge the systematic summary of the article on lead compound optimization strategies by Liu Hong and others. It is the presence of these datasets or data resources that enables us to construct a shared pharmacological large language model test dataset for the testing and evaluation of both general and specialized large language models.

   We extend our thanks again to the pharmacological large model collaboration team composed of Bairong S., Zhajun Z., Dan D., and Rajeev K. S., who proposed the framework for the pharmacology large language model test set.

   Lastly, we are grateful to Huggingface and Github for providing the data platforms, which allow us the opportunity to share this dataset and facilitate further improvements.


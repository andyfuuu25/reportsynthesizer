# reportsynthesizer
### **Synopsis:** 

**System Overview**  
This is a universal three-stage research pipeline that automates financial data parsing, extraction, and auditing. Instead of asking one AI to read, extract, verify, and write all at once, the workflow breaks the task into specialized steps to eliminate mistakes.  
This pipeline utilizes a modular design. Rather than relying on a rigid, linear template, analysts can treat the skill library as discrete blocks. The skills library dynamically calls upon specific skills, parameterizes them on the fly, and stacks them into a presentation layer. 

**Modular Skill Library** 

* Skill 1 (Textual Synthesis): Condenses multi-page reports into 5–6 high-density, quantitative bullet points detailing the core structural thesis.  
* Skill 2 (Figure Interpretation): Specifically interprets graphs and/or tables, providing summaries along with institutional implications.  
* Skill 3 (User-Directed Summary): A single-turn directed engine that ingests analyst-specified key topics from the meta-prompt, pulling out verbatim parameters to map asset-class implications and macro transmission paths.  
* Skill 4 (External Intelligence Sync): Executes targeted online sweeps across verified financial media outlets for specified time horizons, clustering findings into clean structural market themes.

**The Prompting Principles**

* EEDP Framework (Expose, Extract, Determine, Present): Forces the AI to use an internal "scratchpad" to locate the paragraph (Expose), copy the exact text (Extract), and normalize the metrics (Determine) before it starts writing the report (**Srivastava et al., 2024).**  
* Decentralized Markdown Schema Prompting: References the Markdown schema by nesting completely rigid, empty target output templates directly inside individual skill blocks using fenced Markdown code blocks. This leverages the model's natural pattern-completion traits to enforce an identical, predictable layout every week while providing the flexibility to dynamically stack or re-order skills (**Shin et al., 2024**). 


**Prompting Instructions/Template:**  
Skill 1 Template: 

| Apply \*\*Skill 1: "summarize\_text"\*\* to the attached source document, \`insert document name\`, but only (specify section if necessary) |
| :---- |

Skill 2 Template: 

| Apply \*\*Skill 2: "figure\_interpretations"\*\* to the attached source document, \`insert document name' for “graph titles”  |
| :---- |

Skill 3 Template: 

| Apply \*\*Skill 3: "humaninput\_summary"\*\* to the attached source document \`insert document name\`, \-the key points are (insert self-determined key focal points to emphasize summary) |
| :---- |

Skill 4 Template:

| Apply \*\*Skill 4: "external\_research"\*\* according to the parameters specified below. \- \*\*Specified Topic:\*\* "insert topic" \- \*\*Given Period of Time:\*\* "Insert time period, if any." |
| :---- |

**Example from Case Study:** (Green highlight: Fixed instruction prompt; Blue highlight: Modular area can be added & changed depending on skill needed/number of papers used in report).

|  To complete this task, you must always  import and strictly adhere to the persona, EEDP processing workflows, modular skill instructions, and target output schemas defined in your core utility library, "[skills.md](http://skills.md)".  \#\#\# CRITICAL FORMATTING RULE: You MUST execute the full EEDP workflow (Expose, Extract, Determine) internally to guarantee mathematical and verbatim accuracy. However, you are STRICTLY FORBIDDEN from printing the \`\<reasoning\_scratchpad\>\` block or any XML code in your response. Suppress the scratchpad entirely and ONLY output the clean, final Markdown presentation schemas in the sequence requested below. 1\) Apply \*\*Skill 1: "summarize\_text"\*\* using ONLY the attached source document, \`inputa.md\`. 2\) Apply \*\*Skill 1: "summarize\_text"\*\* using ONLY  the attached source document, \`inputb.md\`, restricting your scope exclusively to the chapter  titled ‘US Economics’ 3\) Apply \*\*Skill 1: "summarize\_text"\*\* using ONLY the attached source document, \`inputc.md\`. 4\) Apply \*\*Skill 2: "figure\_interpretations"\*\*  using ONLY  the attached source document, \`[inputc.md](http://inputb.md)\` for ‘Exhibit 10: Relative Value Views’ 5\) Apply \*\*Skill 2: "figure\_interpretations"\*\*  using ONLY  the attached source document, \`[inputc.md](http://inputb.md)\` for "Exhibit 15: Performance of USD and EUR Markets" 6\) Apply \*\*Skill 2: "figure\_interpretations"\*\* using ONLY  the attached source document, \`[inputc.md](http://inputb.md)\` for ‘exhibit 43: CLO Spread percentile rank’  and ‘Exhibit 44: CLO Equity vs. CLO BB Yield ’ 7\) Apply \*\*Skill 3: "humaninput\_summary"\*\* using ONLY  the attached source document \`inputd.md\`.    \- \*\*\[user specified key topics\]:\*\* "Fund-Flow Regime Shift, Asset-Liability Gap, Execution friction, Management Fee & Growth Incentives" 8\) Apply \*\*Skill 4: "external\_research"\*\* according to the parameters specified below:    \- \*\*\[specified topic\]:\*\* "US private credit mega-deals, volume scaling, and regulatory capital updates"    \- \*\*\[given period of time\]:\*\* "1st week of May 2026"  \#\# Final Compilation Directive Execute all 6 modules dynamically on the fly using the presentation layout framework from "skills.md". Ensure that each respective module only references the specified document. Remember: No scratchpad output allowed. |
| :---- |

**General Procedure**

1) Use Markitdown to convert PDF files into .md formatting  
2) Upload ‘skill.md’, all parsed files, and the customized prompt into the LLM  
3) Copy output into a Google Doc for manual formatting

**Cross-validation (DeepSeek)**

1) Insert “data\_audit” into the chat window along with the generated report, source files & charts & prompt (e.g., Read data\_audit.md for instructions; follow exactly what is listed there. Ignore the open source section for the data audit.)  
2) If the audit returns an issue, either manually fix the identified issue or copy the diagnosis to Gemini to debug/verify  
3) Manually adjust any suggestions/corrections

**\*Note:** skills.md file is included in the email submission  
**Works Cited:** 

- Shin, Donghun & Li, Xigui & Li, Hui & Shi, Shaojie & Chen, Kaitao & Fu, Daocheng. (2024). Prompt Engineering and Format on LLMs in the Financial Domain. 10.13140/RG.2.2.17057.11365.   
- Srivastava, P., Malik, M., Gupta, V., Ganu, T., & Roth, D. (2024). Evaluating LLMs’ Mathematical Reasoning in Financial Document Question Answering \[Conference paper\]. *Findings of the Association for Computational Linguistics ACL 2024*, 3853–3878. https://www.microsoft.com/en-us/research/publication/evaluating-llms-mathematical-reasoning-in-financial-document-question-answering/   
  

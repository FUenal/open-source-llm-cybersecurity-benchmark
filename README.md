# MORE COMING SOON
---

## 🧠 Introduction – Why I Built This

A few months ago, I found myself staring at yet another phishing incident report in our SOC queue. The team was overloaded, the indicators weren’t clear, and someone asked, half-jokingly, *“Can’t GPT just figure this out for us?”*

That comment stuck with me.

As a cybersecurity analyst with a background in computer science, data science, and engineering, I’ve spent the last few years navigating the growing intersection of AI and cyber defense. We’ve all seen the demos—LLMs summarizing threats, translating logs, generating YARA rules. But in the field, the reality is murkier. Some models hallucinate. Some are too slow. Some just don’t get it.

There’s no shortage of hype. But there is a shortage of **reliable, actionable benchmarks** that tell security professionals:
➡️ *Which open-source LLMs can you trust for which cyber tasks?*
➡️ *What works locally without sending sensitive data to the cloud?*
➡️ *Which model actually helps—not hinders—your SOC workflow?*

And so I built the **Open LLM Benchmark for Cyber Security**.

This isn’t just another AI benchmark. It’s a practical, task-driven evaluation designed for the trenches—where incident responders, red teamers, threat analysts, and vulnerability managers operate daily. Our goal: identify the strengths and limits of today’s open LLMs in solving real cybersecurity problems, so organizations can adopt them confidently and responsibly.

Because while LLMs may not replace humans in cybersecurity, the right ones can dramatically increase how fast and well we work.

---

## ⚠️ The Challenge – Not All LLMs Are Created Equal

When ChatGPT exploded onto the scene, many security teams—including mine—began experimenting:
"Can it summarize alerts?"
"Can it generate a quick incident report?"
"Can it help reverse engineer this suspicious script?"

Sometimes, the results were magical. Other times, they were dangerously wrong.

Here’s the thing: **Large Language Models are not interchangeable tools.** Each one has strengths and weaknesses. Some excel at structured reasoning; others are great at translation or summarization. Some are blazing fast but brittle under pressure. Some never hallucinate—until they do, and then they do it confidently.

Yet if you look at the public benchmarks—MMLU, ARC, TruthfulQA, even LMSYS’s leaderboard—you’ll notice something: **none of them test real-world cybersecurity tasks.**
No threat intel parsing.
No phishing detection.
No exploit reasoning.
No malware log analysis.

Cybersecurity has a unique language and logic. It's noisy. It's ambiguous. It requires context-switching between natural language, code, and IoCs. And we’re dealing with high stakes—getting it wrong could mean ignoring a breach or deleting a critical account.

So the current state of affairs leaves organizations with tough questions:

* Can we rely on open-source LLMs for high-sensitivity environments?
* Which ones are best for summarizing versus classifying?
* What tradeoffs do we make in performance, hallucination risk, latency, and cost?

Unfortunately, there’s no clear answer—because until now, **no one had tested open LLMs across a representative set of cybersecurity tasks**.

That’s the gap we aim to fill with the Open LLM Benchmark for Cyber Security.


---

## 🚀 Meet the Project – Open LLM Benchmark for Cyber Security

The **Open LLM Benchmark for Cyber Security** was born out of necessity—and built for practicality.

This isn’t an academic exercise or a leaderboard for leaderboard’s sake. It’s a hands-on, task-specific benchmarking framework designed to answer a simple but powerful question:

> ❓ *Which open-source LLM performs best for the cybersecurity tasks that actually matter?*

### 🎯 Core Objectives

We set out to evaluate large language models the way real security teams use them—under time pressure, with messy inputs, and mission-critical consequences. The benchmark focuses on six high-impact categories:

* **🔍 Incident Response:** Can the model summarize a multi-step intrusion timeline from EDR logs or analyst notes?
* **🌐 Threat Intelligence:** Can it extract relevant IoCs from a narrative threat report or generate STIX data?
* **🛡️ Vulnerability Management:** Can it read a CVE description and propose a practical remediation plan?
* **📨 Phishing Email Detection:** Can it classify emails as malicious or safe using headers, content, and embedded links?
* **🧬 Malware Analysis:** Can it interpret obfuscated code or explain dynamic sandbox behavior?
* **🛠️ Offensive Security Use Cases:** Can it assist with payload generation, explain an exploit chain, or simulate red-team tactics?

Each category includes real-world examples, carefully crafted prompts, and task-specific evaluation rubrics. We test models in:

* **Zero-shot mode** (no examples provided),
* **Few-shot mode** (primed with a few samples),
* And where possible, **fine-tuned versions** trained on domain-specific data.

### 🧱 Open, Modular, and Extensible

The entire framework is open-source, hosted on GitHub, and designed for easy collaboration. You can run the benchmarks locally, plug in your own models, add new tasks, or contribute additional evaluation metrics.

We also plan to include:

* A **GitHub Pages site** with visual dashboards and results.
* A **future leaderboard** for community-submitted models and prompts.
* **Synthetic prompt datasets** (coming soon) to support reproducible and fair comparisons.

📊 **Placeholder Visual:**
Diagram showing the flow:
Prompt → Model → Output → Evaluation → Dashboard Score
![](<./images/model.png>)
> This project is meant to be a compass, not a gatekeeper. The goal isn’t to crown a winner—it’s to give teams the **data and tools** they need to choose the right LLM for their mission.

---

## 🔬 Testing Strategy – How We Evaluate the Models

Evaluating LLMs for cybersecurity isn’t about asking trivia questions or measuring token accuracy. It’s about understanding how models perform under realistic conditions—where context is messy, inputs are mixed (text, code, logs), and answers need to be not just correct, but useful.

So we designed our testing strategy with a few key principles:

### 🎯 1. **Task-Relevant Prompts**

Each category in the benchmark is built around actual use cases from security operations, red teaming, threat intel, or vulnerability analysis. For example:

* **Incident response** prompts may include fragments of EDR logs, analyst notes, or event timelines.
* **Phishing detection** tasks include real (or well-crafted synthetic) email headers and bodies, sometimes in multiple languages.
* **Exploit analysis** prompts might involve deobfuscating PowerShell or analyzing a suspicious URL chain.

We’re not interested in whether the model “knows” a CVE ID—we care if it can **reason** through the implications and recommend a fix.

---

### 🧪 2. **Zero-Shot, Few-Shot, and Fine-Tuned**

We assess each model under three conditions:

* **Zero-Shot**: Can it generalize out of the box with no examples?
* **Few-Shot**: Does performance improve with a couple of good examples?
* **Fine-Tuned**: What happens when we train the model on domain-specific data?

This allows teams to make informed decisions about:

* Whether general-purpose LLMs are “good enough” for their needs.
* When investing in fine-tuning is worth the return.
* Which base models make the best foundation for cyber-specific instruction tuning.

---

### 📏 3. **Multi-Dimensional Evaluation**

Each model’s output is evaluated across a range of criteria:

* ✅ **Correctness**: Is the output factually accurate or misleading?
* 🧠 **Relevance**: Does the response directly address the task?
* 🔁 **Hallucination Rate**: How often does it invent plausible-sounding nonsense?
* 🚀 **Latency**: How fast is the model in generating responses?
* 💸 **Efficiency**: What compute/cost trade-offs are involved?

In some cases, we also score **readability**, **explainability**, or **SOC analyst usability** based on real-world expectations.

📈 **Visual Placeholder:**
Radar chart comparing three LLMs across six metrics.
![](<./images/spider.png>)
---

### 🧩 4. **What Makes This Different?**

* **Task-first**: This isn’t a benchmark of LLMs in general—it’s a benchmark of how they help solve security tasks.
* **Open-source**: Everything can be run locally, modified, or extended.
* **Human+AI evaluation**: We combine automated scoring with manual expert reviews in critical categories.

---

In short, we treat each LLM not as a novelty, but as a tool. And we ask the same question we would of any new tool in security:

> *“Does it actually help me get the job done—better, faster, or safer?”*


---

## 📊 Key Findings So Far

After hundreds of runs across six task categories, multiple open-source LLMs, and different configurations, one insight became clear:

> **There is no single best model.**
> Instead, *each model is a specialist*—with its own sweet spots and blind spots.

Here are some of the most interesting trends we’ve observed so far:

---

### ⚡ 1. **Size Isn’t Everything**

Some smaller models, like **Gemma 2 (27B)** and **Mistral**, outperformed larger ones like **LLaMA 3 (70B)** in specific tasks—especially when fine-tuned on targeted cybersecurity prompts. They were faster, lighter to deploy, and delivered **sharper results** for phishing detection or log summarization.

Meanwhile, LLaMA 3 excelled in **long-context reasoning**, like reconstructing a kill chain from mixed evidence, or explaining malware behaviors across multiple steps.

📉 *Lesson:* Don’t default to the biggest model—opt for the best fit.

---

### 🧠 2. **Fine-Tuning Unlocks Huge Gains**

When we fine-tuned base models on even modest, curated cybersecurity datasets (e.g., anonymized phishing emails or CVE analysis pairs), the improvement was **dramatic**—especially in hallucination reduction and terminology accuracy.

This made a big difference for red-team tasks, where precise syntax and intent matter.

---

### 🔄 3. **Hybrid Workflows Often Win**

One of the most promising approaches wasn’t picking a single model—it was combining them.

For example:

* Use a **small model** for fast triage and classification.
* Send edge cases to a **larger model** for reasoning or explanation.
* Use both in a **human-in-the-loop SOC assistant** with fallback strategies.

These workflows reduced latency, improved confidence, and made LLMs feel more like teammates than black boxes.

📐 **Visual Placeholder:**
Dashboard-style table:

| Task         | Top Zero-Shot | Top Fine-Tuned   | Best for Hybrid Use |
| ------------ | ------------- | ---------------- | ------------------- |
| Threat Intel | LLaMA 3       | Gemma 2          | Mistral + Gemma     |
| Phishing     | Mistral       | Fine-tuned Gemma | Gemma + Rules       |
| IR Logs      | LLaMA 3       | LLaMA 3 FT       | LLaMA + Mistral     |

---

### 🔍 4. **LLMs Struggle With Cross-Modality Reasoning**

Tasks that mix structured logs, URLs, and text (like phishing links embedded in narrative emails or sandbox output + description) revealed a **major limitation**:
LLMs often failed to connect the dots across formats—especially in zero-shot mode.

While fine-tuning helped, we believe future systems will benefit from **modular, multi-modal architectures** rather than brute-forcing everything through a single prompt.

---

### 🚨 5. **Hallucinations Are Still a Risk—Especially in Security**

This was perhaps the most concerning finding.

Some models gave **confident but wrong** answers when faced with ambiguous logs or partially obfuscated code. This risk increases when users rely on LLMs in automated pipelines (e.g., for alert triage or response generation).

That’s why we recommend:

* Keeping a human in the loop.
* Logging all model inputs/outputs.
* Tracking hallucination rates per task.

---

In short, while LLMs offer incredible promise, **blind trust is a security risk**. The Open LLM Benchmark gives teams the visibility to make smarter, safer, and more effective decisions.


---

## 🏢 Why This Matters for Organizations

It’s no secret that security teams today are under immense pressure—more alerts, more zero-days, more phishing, and fewer hands on deck. Every SOC, every red team, every risk office is asking the same question:

> *Can we safely adopt AI to increase our cybersecurity capacity—without increasing our risk?*

The answer isn’t a blanket “yes” or “no.” It’s:
**“It depends on the model. It depends on the task. And it depends on how you use it.”**

That’s where the Open LLM Benchmark for Cyber Security becomes a practical asset.

---

### 🧰 1. **Choose the Right Tool for the Right Task**

A one-size-fits-all LLM strategy doesn’t work. The model that explains malware behaviors well may not be great at extracting IoCs. A fast, lightweight model that classifies emails with high precision may not be able to explain a kill chain across 20 EDR logs.

With this benchmark:

* CISOs can make data-backed decisions about which models are deployable.
* SOC leads can test which models are helpful without creating noise or risk.
* Red teams can identify LLMs useful for emulation, not just defense.

---

### 🔐 2. **Retain Control Over Data and Privacy**

Most enterprise AI tools require sending sensitive data—emails, alerts, logs—to a third-party cloud.

With open LLMs:

* You can run models fully **on-premises or air-gapped**.
* You retain full control over prompts, outputs, and telemetry.
* You reduce the risk of leakage, compliance issues, or vendor lock-in.

For organizations in regulated industries or national infrastructure, this is more than a preference—it’s a requirement.

🛡️ **Sidebar Placeholder:**
*“Why Open LLMs Are the Right Choice for High-Security Environments”*

---

### 💡 3. **Enable Teams Without Overwhelming Them**

With the right guardrails, LLMs become **force multipliers**:

* Summarize tickets before they hit the queue.
* Generate remediation steps based on logs.
* Provide multilingual threat intel briefings.

This saves time, reduces analyst fatigue, and helps junior staff operate at a higher level.

But this only works if you trust the model. The benchmark helps ensure that **trust is earned—not assumed.**

---

### 🛠️ 4. **Avoid the “LLM Snake Oil” Trap**

We’ve all seen it—tools that slap “AI-powered” on the label but can’t back it up. That leads to wasted budget, workflow disruption, and disillusionment.

This benchmark is designed to help you:

* Cut through the hype.
* Validate claims.
* Build **LLM adoption plans** based on evidence, not demos.

---

By benchmarking open LLMs for real cybersecurity tasks, we’re enabling organizations to ask smarter questions, choose better tools, and deploy AI **on their terms**—not on a vendor’s timeline.

---

## 🔮 Beyond the Benchmark – Future Plans

The Open LLM Benchmark for Cyber Security isn’t a one-off experiment—it’s the foundation for a long-term, open, and evolving effort to make AI in cybersecurity transparent, trustworthy, and effective.

Here’s what’s coming next.

---

### 🧠 1. **Release of Synthetic Prompt Datasets**

We’re preparing a growing set of high-quality, synthetic prompt datasets that reflect real-world cyber tasks. These will include:

* Phishing emails in multiple languages (anonymized + synthetic)
* Threat reports with embedded IoCs
* CVE write-ups and patch advisories
* Reverse engineering examples and obfuscated scripts

The goal: make it easier for teams and researchers to replicate, fine-tune, and extend the benchmark.

📂 *These datasets will be free to use, modify, and contribute to—hosted on the benchmark’s GitHub repository.*

---

### 🌐 2. **Dedicated GitHub Pages Site + Dashboards**

We’re building a clean, interactive GitHub Pages site that will:

* Display model scores across each task category
* Let users filter by model, task, shot-type, and fine-tuning level
* Include real examples of good vs. bad LLM outputs
* Feature traffic-light dashboards, radar charts, and model match suggestions


---

### 🏆 3. **Community Leaderboard + Submission Pipeline**

Later this year, we’ll launch a public leaderboard with:

* A submission portal for models, prompts, or custom evaluations
* An automated CI/CD benchmarking pipeline
* A hall of fame for open LLM fine-tuners in cybersecurity

We want this to become a trusted, community-driven resource—not just our perspective, but a shared ecosystem of insights and data.

---

### 💻 4. **Streamlit-Based Interactive Demo (Optional)**

We’re exploring the idea of a lightweight demo app (possibly built in Streamlit) where users can:

* Try different models on benchmark tasks
* Toggle between zero-shot and few-shot
* View side-by-side outputs from different models
* Test hallucination detection filters

Ideal for workshops, team demos, or just getting a feel for what these models can and can’t do.

---

### 🔄 5. **Expansion Into New Cybersecurity Domains**

The benchmark will expand into:

* **Policy automation**: Turning security standards into natural language summaries or checklists.
* **GRC assistance**: Using LLMs to evaluate risk controls, parse compliance docs.
* **Blue/purple team playbooks**: Testing whether models can generate or improve MITRE ATT\&CK workflows.
* **Explainable security**: Prompting LLMs to explain why something is a threat—in plain English.

---

The vision is simple:

> ✅ A living benchmark.
> ✅ A trusted community resource.
> ✅ A launchpad for smarter, safer, open AI in cybersecurity.

---

## 🤝 Call for Collaboration

Cybersecurity is a team sport—and so is this benchmark.

The Open LLM Benchmark for Cyber Security was never meant to be a closed or solitary effort. We launched it to **ignite a broader conversation**, and we’re building it to grow through community input, open science, and real-world contributions from the field.

If you’re excited about the intersection of AI and cybersecurity, we’d love to work with you.

---

### 👩‍💻 Ways You Can Contribute

#### 📝 1. **Submit Prompts**

Have examples of phishing emails, reverse engineering challenges, or messy log files you use to test analysts or tools?
Anonymize them (or generate synthetic versions), and contribute them to the prompt corpus.

#### 🧪 2. **Test Your Own Models**

Bring your own open-source or fine-tuned LLM and run it through the benchmark. We’ll help you evaluate it, and highlight strong performers on the leaderboard.

#### 🔍 3. **Improve Evaluation Metrics**

Help us build better scoring systems:

* Reduce subjectivity in grading
* Improve hallucination detection
* Explore reward modeling for security reasoning

#### 🌐 4. **Join the Community**

We’re building a small but growing community of security engineers, data scientists, and AI researchers focused on **practical AI for defense**.
That includes forums, Q\&As, monthly check-ins, and an open Slack/Discord space (coming soon).

---

### 🧭 Long-Term Vision

We don’t just want to benchmark models.
We want to help **shape a future** where:

* Security teams have trustworthy AI copilots they understand and control.
* SMEs and nonprofits can access effective AI defenses without paying \$300K/year for enterprise licensing.
* Developers fine-tune open models to meet the needs of **analysts, not algorithms**.

By participating, you're not just improving a benchmark—you’re helping steer the evolution of AI for cyber defense, toward something more equitable, transparent, and powerful.

---

📣 **How to Get Involved**

* ⭐ Star the project on GitHub: \[link]
* 🛠️ Explore the benchmark code and start testing
* 🧑‍💻 Open an issue or discussion with your ideas
* 📬 Reach out on \[email / contact form] to get early access to datasets or demos

---

## 🔚 Final Thoughts

AI is transforming cybersecurity. That’s not hype—it’s happening.

But transformation doesn’t mean disruption for its own sake. It means empowering people: helping analysts make better decisions, enabling SOCs to triage faster, and giving smaller organizations access to powerful defenses they couldn’t afford five years ago.

What it doesn’t mean is blindly trusting black-box tools, outsourcing decision-making to models that hallucinate, or letting marketing slides define operational reality.

That’s why we built the **Open LLM Benchmark for Cyber Security**:
To **cut through the noise**.
To **test models like professionals use them**.
To **give the community real data**, real examples, and real insight into what works—and what doesn’t.

Whether you’re a CISO trying to understand where LLMs fit into your roadmap, a red teamer exploring payload generation, or a data scientist fine-tuning a model for malware classification—this project is here to support you.

We’re not chasing leaderboard glory. We’re building infrastructure for responsible, open, and impactful AI in cybersecurity. And we’d love for you to be part of it.

---

### ✅ Next Steps

* 🔗 Visit the GitHub project: \[Link](https://github.com/FUenal/open-source-llm-cybersecurity-benchmark)
* 📈 Explore the upcoming dashboard and GitHub Pages site
* 💡 Contribute prompts, models, or evaluation feedback
* 🔁 Follow the project for updates, datasets, and leaderboard launches

---

> Let’s build the future of secure, intelligent, and explainable cybersecurity—together.

---





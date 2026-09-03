# Course 1: What is Data Science?

## Key concepts

### The Data Science ecosystem
Data Science sits at the intersection of statistics, programming,
and domain expertise. Unlike a purely technical field, most of its
value comes from framing the right question before touching any
model — a parallel to how physical modeling starts with identifying
which simplifications are valid before solving.

### Roles within the field
The certificate distinguishes several overlapping roles: Data
Analyst (descriptive, reporting-focused), Data Scientist (predictive
modeling, statistical inference), Data Engineer (pipeline and
infrastructure), and ML Engineer (productionizing models). In
practice these boundaries blur significantly at smaller companies.

### Core qualities of a good Data Scientist
The course identifies four traits as central to the role: curiosity,
critical thinking, the ability to take and defend a position, and
storytelling. Soft skills are treated as essential, not secondary —
a data scientist who cannot argue for a conclusion or communicate it
as a coherent narrative fails to deliver value regardless of model
accuracy. This reframes technical output as a means, not an end:
analysis only matters once it converts into a decision someone else
can act on.

### Data Science roadmap — course infographic synthesis
Consolidating the certificate's own summary infographic against what
these notes already cover, to avoid duplication and flag genuinely
new material.

**Personality characteristics**: mostly already covered above
(curiosity, argumentation, storytelling). Two additions worth
noting: familiarity with analytics platforms is treated as a
baseline expectation, not a differentiator — and "know your area of
interest" (e.g. healthcare, IT) suggests domain specialization
matters as much as technical breadth. Given my own trajectory, the
domain is physics/engineering simulation rather than a business
vertical — worth keeping in mind when the certificate's examples
skew toward business analytics.

**Many paths**: data science draws from diverse educational
backgrounds — people typically arrive via exposure to a real data
challenge in their own field, not through a single canonical
pipeline. Directly relevant to my own transition narrative: the
entry point matters less than demonstrated capability.

**Data literacy**: beyond what's covered above (Big Data, Cloud),
the infographic adds structured vs. unstructured data analysis,
file format literacy, and database/SQL skills as baseline
requirements — not yet covered in these notes; will be built out
properly in Course 6 (Databases and SQL for Data Science).

**Tools & techniques (forward preview)**: Python and R as primary
languages; Hadoop (see the earlier note on its declining relevance
in 2026 — the infographic still lists it as current); core Python
libraries NumPy, pandas, scikit-learn; data visualization tools;
machine learning algorithms; data preprocessing techniques. This is
essentially a preview of Courses 4, 7, 8, and 9 — no need to detail
further here, just useful to see the full arc up front.

**Foundational skills**: statistics, calculus, and linear algebra
are listed as prerequisites — already solid from my physics
background, so these will be a review rather than new material when
they resurface. Exploratory data analysis and model
selection/training/testing are the genuinely new technical skills
ahead (Course 7 onward).

**Range of tasks**: concrete outputs a data scientist is expected to
produce — recommendation engines, predictive modeling, pattern
identification, incorporating external data sources, and
communicating findings. Useful as a checklist against my eventual
portfolio projects: a strong portfolio should touch at least
predictive modeling, pattern identification, and communication of
findings explicitly, not just model accuracy metrics.

### Approach to a new project
Before touching any data or model, the recommended sequence is:
1. Clearly delimit the problem the organization wants to solve.
2. Determine what data is needed to solve that problem.
3. Determine where that data can be obtained.

This mirrors a discipline I already practice in physical modeling:
define the problem and its boundary conditions before selecting a
method. Jumping straight to tools before framing the question is a
common failure mode in both fields — and arguably worse in data
science, where the abundance of available data makes it easy to
start analyzing before the problem is even well posed.

### Structuring an analytical report
Report length should match purpose, not arbitrary preference: a
short report (under 5 pages) works for commentary on current
trends; a long, detailed report builds an argument incrementally,
with full methodology, literature review, and intermediate findings.

**Minimum structure, even for short reports:**
1. Cover page — title, authors, affiliation, contact, and
   **publication date** (frequently missing in practice, which
   makes proper citation impossible).
2. Table of contents (mandatory once the document exceeds ~5 pages).
3. Executive summary — the core argument in three paragraphs or
   fewer, regardless of document length.
4. Introduction — frames the problem for an unfamiliar reader.
5. Literature review — length scales with how contested the topic
   is; brief if consensus exists, extensive if nuanced, since its
   job is to expose the knowledge gap the analysis will fill.
6. Methodology — data sources and methods, justified by reference
   back to the literature review.
7. Results — empirical findings only, from descriptive statistics
   to formal hypothesis testing. Interpretation is deliberately
   withheld here.
8. Discussion — where narrative enters: results are tied back to
   the original research question, framed as the missing piece of
   the puzzle. Not every analysis is conclusive, and caveats belong
   here, honestly stated.
9. Conclusion — generalizes findings and frames them for impact,
   without getting stuck on caveats already disclosed. Can point to
   future research directions.
10. References, acknowledgments, appendices.

**Key distinction worth internalizing**: Results presents facts;
Discussion presents interpretation. Conflating the two weakens
credibility — the reader can no longer tell raw finding from
argument built on it. Direct parallel to keeping experimental data
separate from theoretical interpretation in a physics report:
mixing the two invites confirmation bias.

**Self-check before submitting analysis** (adapted from a *Transport
Policy* author checklist, reproduced in the reading): Does the
reader know upfront what they gain from reading this? Is the
objective clear? Is the contribution's importance explained? Is the
work placed in proper context with sufficient references? Is
feasibility/usefulness addressed? Are future developments
identified? Is the structure clear and logical?

This is the operational version of the storytelling/argumentation
qualities already noted above — narrative structure isn't
decoration, it's close to a publication-readiness criterion.

### Big Data: definition and characteristics
Big Data is not simply "a lot of data" — it is a regime where
conventional tools (single-server relational databases, spreadsheet
software) stop being viable. It is commonly defined through the
3 V's, sometimes extended to 5:
- **Volume**: scale beyond conventional storage/processing capacity.
- **Velocity**: rate at which data is generated and must be
  processed (real-time streams vs. comfortable batches).
- **Variety**: heterogeneity of format — unstructured text, images,
  logs, nested JSON, not just clean tabular data.
- **Veracity** (extension): uncertain quality/reliability of data.
- **Value** (extension): raw data is worthless until converted into
  an actionable decision.

Key distinction: Big Data describes a condition of the *data*
(scale, complexity); Data Science is the *discipline* that extracts
value from data regardless of scale. Rigorous data science can be
done on a 500-row dataset — Big Data specifically refers to the
regime requiring distributed infrastructure.

### Big Data processing tools: Hadoop ecosystem
- **Hadoop**: open-source framework for distributed storage and
  batch processing on commodity hardware. Core components: HDFS,
  MapReduce, YARN.
- **HDFS**: the distributed storage layer. Splits large files into
  blocks, replicated across multiple machines for fault tolerance.
- **Hive**: SQL interface layer on top of Hadoop. Translates
  familiar SQL syntax into distributed jobs, removing the need to
  write raw MapReduce code for simple queries.
- **Spark**: in-memory processing engine, successor to MapReduce.
  Keeps intermediate results in RAM instead of writing to disk at
  each step, which dramatically accelerates iterative workloads —
  directly relevant to ML training, which is inherently iterative.

**Current industry status (verified August 2026, since the course
content predates current adoption trends):**
- **Spark**: fully active and growing. Reinforced in 2025–2026 by
  Spark Connect (feature-complete since Spark 4.0), decoupling
  clients from remote clusters via gRPC — usable from notebooks,
  web services, or AI agents.
- **Hadoop (full framework)**: in real decline. Still maintained
  (v3.4.2, August 2025) but the "Hadoop is dead" narrative is
  widespread following Hortonworks/Cloudera's 2019 merger and
  adoption decline.
- **HDFS**: in retreat versus cloud object storage (S3, GCS, Azure
  Blob). The dominant 2026 architecture is the "lakehouse" pattern —
  object storage + open table format (Iceberg, Delta Lake, Hudi) +
  query engine (Spark, Trino, DuckDB) — where HDFS has no place
  except as a legacy mount.
- **Hive**: still in use, but frequently the *starting point*
  organizations are migrating away from (Hive SQL → Spark SQL) in
  new 2026 deployments, not the destination.
- **MapReduce**: effectively obsolete for new development; legacy
  jobs still exist in some organizations, but Spark/Flink are
  preferred for new work.

Takeaway: the certificate presents Hadoop/HDFS/Hive as current
state-of-the-art, but the conceptual foundation remains valid even
as the specific tooling has shifted heavily toward Spark and
cloud-native lakehouse architectures. Practical focus should
prioritize Spark.

### Metadata and metadata management
Metadata is data that describes other data. In the context of data
warehouses and BI systems, it splits into three types:

- **Technical metadata**: defines data structures from a technical
  standpoint — table names, row/column counts, data catalogs (which
  database holds which column, and its data type). In relational
  databases, this typically lives in the **system catalog**.
- **Process metadata**: describes what's happening behind the
  scenes in enterprise systems — process start/end times, disk
  usage, data source/destination, concurrent user counts. Primarily
  used for troubleshooting and workflow optimization, not for
  understanding the data itself.
- **Business metadata**: human-readable context for business users
  doing data discovery — how data was obtained, what it measures,
  how it connects to other data sources. Functions as documentation
  for the entire warehouse system.

**Metadata management** is the set of policies and processes
ensuring data access, integration across sources, and proper
sharing across an organization. Its central artifact is the **data
catalog** — a searchable inventory (usually with a web UI) that lets
both engineers and business users find key attributes without
needing to know the underlying schema by heart.

**Why it matters**: well-managed metadata directly improves data
**discovery**, **repeatability**, and **governance**. It underpins
**data lineage** — tracing where data originated and how it was
transformed — which is what makes root-cause tracing of data errors
possible. This connects to **data governance**: the organizational
capacity to ensure data quality, availability, and security across
its full lifecycle, including accountability for the effects of
poor data quality.

**Tools (recognition-level only)**: IBM's own stack includes
InfoSphere Information Server and Watson Knowledge Catalog — worth
recognizing given this is an IBM certificate. Broader industry
players include Informatica Enterprise Data Catalog, Alation, and
Microsoft Azure Data Catalog. No need to know these deeply at this
stage — just recognize the category (data cataloging/governance
tools) if it comes up in an interview or job posting.

**Relevance to my track**: this reading is more about enterprise
data governance than hands-on technical skill — lower priority for
a scientific/computational data science path than for someone
headed toward a Data Engineer or BI-focused role. Still worth
knowing the vocabulary (data lineage, data catalog, governance)
since it appears in job postings and cross-functional conversations,
even if I won't be implementing a metadata management system myself.

### Cloud Computing
Delivery of on-demand computing resources over the Internet on a
pay-for-use basis. The shift is economic as much as technical
(CapEx → OpEx): infrastructure is rented elastically instead of
owned outright.

**Five essential characteristics**: on-demand self-service, broad
network access, resource pooling (multi-tenancy), rapid elasticity,
measured service (usage-based billing).

**Three deployment models** (who owns/accesses the infrastructure):
- Public: shared, provider-owned (AWS, Azure, GCP).
- Private: dedicated to a single organization.
- Hybrid: combination — critical data private, variable workloads
  public.

**Three service models** (how much of the stack you manage):
- IaaS: you manage apps/data; provider manages runtime, OS,
  virtualization, hardware. Example: Amazon EC2.
- PaaS: you manage only code/data; provider manages everything else.
  Example: Heroku, IBM Cloud Pak for Data.
- SaaS: fully managed; you just use the product. Example: Gmail,
  Watson Studio (managed mode).

Relevant later in the certificate: Course 10 (Capstone) likely uses
IBM Watson Studio, a SaaS/PaaS hybrid on IBM Cloud.

### The Data Mining process (7 steps)
From the prescribed reading (Haider, *Getting Started with Data
Science*, Ch. 1). Describes in prose what CRISP-DM (Course 3) later
formalizes — worth mapping explicitly when that course arrives:

1. **Set objectives**: define key questions, but critically, weigh
   cost-benefit against desired precision. Precision has
   diminishing returns — beyond a certain point, added accuracy
   costs more than it's worth. Direct parallel to mesh refinement
   in numerical methods: stopping refinement once marginal accuracy
   gain no longer justifies computational cost.
2. **Data selection**: assess whether needed data already exists or
   must be newly collected (e.g. surveys). Type, size, and
   collection frequency directly affect cost.
3. **Preprocessing**: remove irrelevant attributes, flag erroneous
   entries, and formally handle missing data. Key distinction:
   missing *randomly* (simple fixes suffice) vs. missing
   *systematically* (introduces real bias — e.g. individuals who
   withhold income data skew any income-based analysis). This maps
   to the formal MCAR vs. MNAR distinction in statistics.
4. **Transformation**: reduce dimensionality (mentions PCA
   explicitly) and convert variable types as needed (e.g. continuous
   income → categorical low/medium/high) to capture non-linear
   behavior.
5. **Storage**: format must allow efficient read/write access for
   the data scientist, while ensuring security and avoiding
   fragmentation across scattered storage locations.
6. **Data mining (extraction)**: apply parametric/non-parametric
   methods and ML algorithms. Visualization recommended as a
   starting point to build preliminary intuition about hidden
   trends.
7. **Evaluation**: test predictive capability via in-sample
   prediction, then incorporate stakeholder feedback. The process
   is explicitly iterative — not a one-pass pipeline.

## Personal reflections — career path analysis

Given my background in Physics Engineering (numerical simulation,
strong differential equations and linear algebra foundation), the
most aligned paths are:

1. **Scientific/Computational Data Scientist** — direct application
   of ML and statistics to physics/engineering problems. Strongest
   fit given existing simulation background.
2. **Quantitative Analyst** — highest earning potential; physics
   backgrounds are historically overrepresented here due to shared
   mathematical tools (stochastic calculus parallels diffusion
   equations). Requires stronger English production and likely
   further credentials.
3. **ML Engineer (simulation/optimization focus)** — production-
   grade ML applied to physical models, digital twins, surrogate
   models.
4. **Research/Data Engineer** — pipeline work for scientific data;
   documentation rigor from prior technical writing experience
   (forestry sector reports) is a transferable asset here.
5. **Independent Simulation Consultant** — longer-term path (Route
   B), contingent on building non-technical skills: pricing, client
   pipeline, proposal writing.

Decision: prioritizing path 1 as the primary 18-month target, given
lowest preparation gap and strongest use of existing quantitative
background.

## Resources referenced
- IBM Data Science Professional Certificate, Course 1: "Discover
  Your Path in Data Science" (Coursera).
- Haider, Murtaza. *Getting Started with Data Science*. IBM Press,
  2015. Chapter 1 (prescribed reading): "Data Science: The Sexiest
  Job of the 21st Century" and the Data Mining process overview.
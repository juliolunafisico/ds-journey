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
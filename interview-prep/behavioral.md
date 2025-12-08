# Behavioral Interviews

## Tell me about a time you had to take initiative without being asked. What was the situation, and what impact did your actions have?

**Situation**:
- Production appliction which uses LLM api went down
- I was on lunch when the fail/loss of service was noticed on the teams channel


**Task**
- The team need to indenfy the root cause of the issue
- Implement a fix and deploy it to the production environment
- Reducing the impact of the issue on the users

**Action**:
- I took initiative by first reviewing the permuthus logs
- I noticed that the error where regrarding the llm services
- I then diagnosed there possible causes, the llm services was down, the llm function that was calling the services that a bug, lastly there was an issue with the credentials
- I quilty setup setup a local verison of the applicaiton, to test the llm service from my computer and the issue did not occur
- The only option left was invalid credentials, so I pinged the DevOps team, and share the error message, and asked if any changes were made to the credentials
- I then worked with Devops team to generate new credentials and deployed the new credentials to the production environment

**Result**:
- We were able to bring the application back online and iminimize the impact on the users
- The team appricated my efforts and I was able to learn more about another part of our application

### What could you have done better in that situation? (follow up)
One area I identified for improvement was our detection and monitoring strategy. The issue was ultimately discovered through human observation, which delayed our response. I could have proactively set up automated alerts tied to LLM latency spikes, IAM role expiration, or STS assume-role failures. That would allow us to react within minutes instead of relying on someone noticing symptoms in the logs.
Second, I realized we didn’t have automated pre-deployment checks validating AWS role health. I could have added a lightweight integration test that uses the AWS API to confirm the credentials and policies were valid before every production deployment. That would prevent similar outages from reaching users.
Overall, we solved the issue quickly, but improving observability and preventive checks would make the system much more resilient going forward


## Tell me about a time you had to collaborate with someone difficult or with conflicting priorities. How did you handle it, and what was the outcome?

**Situation**:
- At PCS Software, I was leading a Hey PCS project which was a voice assistant task answer time critical queries for users.
- We were launch the version 1 of the application in december. At the same time the company was migration the customers from on permise to azure cloud.
- The migration was a high priority project and limted the infrastructure team's bandwidth, creating a conflict around the support that we needed.

**Task**
- My responsiblity was to get Hey PCS realised on time, which required the infrastructure team to support.
- I needed the to provision resource create appropriate policies, setup environments and development pipelines.

**Action**:
- I anticipated the conflict in advance, so I proactivetly prepared good documentation for the Devops realted works. I also create a simple arm template which they could use as a starting point.
- I also stayed flextiy with scheduling and working with their availability. I proived context regration the launch timeline, and showed how early prepration would minimize their workload later. 
- This reduced friction and help align the expectations and goals.

**Result**
- When December did finaly arrive, DevOps team was highly fimilar with the project and expections.
- They are aready setup the infrastrcution script for provisioning the appropriate resources. 
- The realise was on time, both teams felt supported rather than pressured.

## Tell me about a time when you were given a vague or ambiguous project. How did you figure out what to do, and what was the outcome?

**Situation**
- At Veridian, I was assigned to improve a CAT Chat an internal RAG application by the sales team. 
- The existing system worked technically, but users were unhappy with it. 
- There was no User needs, no defined requirements, and no clarity about what “improvement” meant. 
- I was simply told, "Users don't like it — figure out what needs to change."

**Task**
- My task was to capture the needs of the user and define a clear solution for the defined needs.
- The solution had ultimately need to be approved by the stackholders, and implememted by my team and I.

**Action**
- To reduce ambiguity, I schedule user interview with 20 of the most frequent users of the application.
- From the meeting, I identified a list of core user needs, where transfored into a survery to quantify the popularity of the results, and make the process data driven.
- I realize the core issue behind user disatisfaciton was the user wanted to solution to identify which pieces of information where able to lead to a deal
- To achieve this, It require building a Cypher-backed knowledge graph populated with marketing data, event notes, call summaries, and internal reports.
- Layer a hybrid search system combining NLP-based semantic search, keyword search, and graph queries to surface more contextually relevant answers.
- Convert user questions into a pipeline: NLP → query generator → Cypher + vector search → ranked answers.
- I presented the structured findings and solution proposal to my manager and the business team.

**Result**
- The business team approved the new scope immediately because it was grounded in real user research.
- The solution addressed the fundamental gap—semantic relevance—and set the foundation for the next iteration of the chatbot. 
- My manager (Mark) was very impressed with the process and documentation I provided.


## Describe a time when you had to learn something quickly.

**Situation**
- At Draup, I was assigned to build a new workflow simulation engine that could model the impact of AI-driven automation and augmentation on a company’s labor structure.
- I had never worked with labor economics data or simulation methodologies before.
**Task**
- I needed to quickly identify the right technical framework to model these dynamics, validate the approach with leadership, and build an alpha prototype—all within about a week.

**Action**
- I began by surveying existing simulation techniques and discovered agent-based modeling was a strong fit. I read research papers demonstrating similar simulations in automated manufacturing environments, which helped me understand the underlying mechanics.
- Next, I evaluated Python frameworks and selected MESA, an agent-based simulation library that allowed us to represent workers, roles, and automation events as interacting agents.
- I distilled the research, proposed the architectural approach to the team and the CEO, and received immediate approval. With the direction set, I quickly implemented an alpha version that demonstrated core behaviors—labor transitions, automation impact curves, and augmentation effects—so the internal team could review the end-to-end flow.

**Result**
- The alpha was delivered on time, validated the approach, and was later expanded into a full-feature product that was released to users. It became the foundation for how we modeled automation impact going forward.

## Tell me about a time you had to solve a difficult problem

**Situation**
- At Viridien, I was tasked with significantly improving the CAT Chat application used by our sales team. 
- Their biggest complaint was that the system could not answer deep, context-heavy questions because it relied mostly on simple semantic or keyword search.
- Leadership wanted a Text-to-Cypher agentic flow—a much more complex system that could interpret natural language and generate graph queries over a document property graph.

**Task**
My responsibility was to design and implement a robust Text-to-Cypher pipeline, which required: 
- building a document property graph from unstructured content,
- designing a Cypher crawler,
- ensuring high retrieval accuracy,
- and validating the system end-to-end before bringing it to production.
The problem was technically challenging because it required combining NLP, LLM reasoning, and graph-based retrieval.

**Action**
- To approach this systematically, I first created a retrieval evaluation pipeline with a labeled benchmark dataset so I could objectively compare search strategies. I evaluated:
pure semantic search,
- hybrid vector 
- Cypher-based graph traversal.
Next, I built the document property graph and the custom Cypher crawler to extract structured entities and relationships from our internal documents.

To improve Cypher generation quality, I constructed a domain-specific training dataset and fine-tuned a small LLM, which significantly reduced incorrect or unsafe Cypher queries.

Before launch, I deployed the system behind a shadow evaluation framework so we could compare the new agentic flow against production traffic without impacting users. This allowed us to refine the prompt architecture, query generation rules, and ranking logic safely.

**Result**
- The new Text-to-Cypher system outperformed the previous search stack across accuracy, relevance, and depth of answers. 
- After rollout, the sales team reported that CAT Chat could now answer complex, multi-hop queries with far higher reliability. 
- The upgrade became the backbone of the next iteration of the product and enabled new workflows that weren’t previously possible.

## Describe a situation where you had to work with a difficult team member
**Situation**
In a previous role, I was collaborating with a teammate on a high-visibility feature with a tight deadline. Around that time, the teammate was dealing with unrelated issues on another project, and during one of our design discussions, they became unexpectedly short and dismissive in their communication.
**Task**
I needed to keep the project moving forward, maintain a healthy working relationship, and address the communication issue without escalating the situation or damaging trust.
**Action**
Instead of reacting in the moment, I reached out privately to talk. I approached the conversation with curiosity rather than confrontation.
I said something like, “I might be misreading the situation, but I sensed some frustration earlier. I want to make sure we’re aligned — is there anything I can help with?”
This opened the door for them to explain they were overwhelmed by pressure from another project and unintentionally carried that stress into our meeting.
We clarified expectations, divided responsibilities more clearly, and scheduled quick daily check-ins to reduce ambiguity and surface blockers earlier.
**Result**
The tone of our collaboration improved immediately. We ended up delivering the feature on time, and the teammate later thanked me for handling the situation professionally rather than reactively. The experience strengthened our working relationship, and I continued collaborating with them on future projects without issues.


## Give an example of a goal you reached and how you achieved it.
- No sure what to say about this

## Tell me about a time you failed and how you handled it.
- Not sure about this one either

## Describe a time you had to manage multiple priorities.
- At Draup, I was a managing a intern for the summer and I was also working on simulation pipeline at the same time.

## Tell me about a time you had to adapt to a significant change at work.
- Mike leaving

## Describe a time when you had to give constructive feedback.
- Not sure what to say about this 

## Tell me about a time you exceeded expectations on a project.
- Not sure 




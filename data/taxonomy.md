# Research Taxonomy: Manufacturing Digital Gene, DG-VLA, WAM and HRC

## 1. Manufacturing Digital Gene

Manufacturing Digital Gene is a structured representation of manufacturing objects, processes, constraints, affordances, task interfaces, and collaboration context.

It is not only a static knowledge base. It should support object-level representation, task-level activation, execution-level adaptation, and long-term evolution in digital twin and embodied manufacturing systems.

## 2. Digital DNA

Digital DNA describes stable and reusable manufacturing knowledge.

Typical contents include:

- geometry primitives
- object attributes
- material properties
- part hierarchy
- affordances
- assembly relations
- process constraints
- interface definitions
- tool-object compatibility
- manufacturing standards

Example:

A bolt's Digital DNA may include its thread size, length, head geometry, material class, grasp affordance, insertion affordance, tightening constraint, and required coaxial relation with a target hole.

## 3. Digital RNA

Digital RNA describes how Digital DNA is activated and expressed in a specific task context.

Typical contents include:

- task-conditioned gene activation
- context-specific constraint selection
- execution sequence generation
- dynamic topology update
- human intervention response
- adaptive replanning
- state transition under action
- scene-level gene expression

Example:

When a bolt removal task begins, the bolt's Digital DNA is activated into RNA-like task expression: locate bolt, select tool, align tool, rotate counterclockwise, monitor loosening state, update assembly topology after removal.

## 4. Gene-as-Context

Digital Gene can provide structured context for LLM, VLM, VLA, or planning modules.

Possible forms:

- prompt context
- retrieved structured knowledge
- scene graph context
- task ontology context
- CAD / STEP-derived object context
- process document context

Research question:

Can structured manufacturing gene context improve VLA reasoning and manipulation generalization without training a new VLA from scratch?

## 5. Gene-as-Constraint

Digital Gene can constrain perception, planning, and action generation.

Possible constraints:

- geometric constraints
- assembly constraints
- process order constraints
- safety constraints
- tool compatibility constraints
- torque / force / direction constraints
- human-robot shared space constraints

Research question:

Can manufacturing gene constraints reduce logical violations and unsafe actions in embodied manufacturing tasks?

## 6. Gene-as-Memory

Digital Gene can serve as long-term memory for manufacturing systems.

Memory contents:

- object memory
- process memory
- tool memory
- environment memory
- interaction memory
- human preference / intervention memory
- failure and recovery memory

Relation to HRC:

Human-robot collaboration often fails because the human and robot do not share the same memory of task state, environment state, and intent. Digital Gene can support memory alignment and situational resonance.

## 7. Gene-as-Policy Interface

Digital Gene can connect symbolic manufacturing knowledge with robot policies.

Possible interfaces:

- subtask decomposition
- action constraints
- affordance maps
- keyframe proposals
- policy conditioning tokens
- tool-use parameters
- trajectory priors
- success / violation checks

Research question:

Can Digital Gene serve as an intermediate interface between VLA reasoning and low-level action execution?

## 8. DG-VLA

DG-VLA refers to Vision-Language-Action models enhanced by Manufacturing Digital Gene.

Possible integration modes:

- Gene-as-Prompt
- Gene-as-Retrieval Context
- Gene-as-Constraint Layer
- Gene-as-Memory
- Gene-as-Action Interface
- Gene-as-World Model Prior

Current preferred direction:

The user does not aim to train a Digital Gene VLA from scratch at the current stage. The preferred direction is to inject Digital Gene into existing VLA or embodied agents as structured context, constraints, memory, or action interface.

## 9. WAM / World Model

World Action Model or robot world model focuses on learning how the world changes under actions.

Digital Gene may support WAM by providing:

- object state prior
- process constraint prior
- action semantic prior
- state transition constraints
- topology update rules
- cross-view alignment anchors

Relevant user idea:

Third-person continuous dynamics learning + first-person sparse keyframe alignment may reduce the cost of collecting full egocentric robot manipulation videos.

## 10. DG-HRC

DG-HRC refers to Human-Robot Collaboration enhanced by Manufacturing Digital Gene.

Key problems:

- memory mismatch
- task context misalignment
- human intention understanding
- proactive robot adaptation
- explicit command reduction
- safe collaborative execution
- dynamic task replanning

Digital Gene can help HRC by maintaining shared task memory, updating scene topology, interpreting human interventions, and triggering context-aware replanning.

## 11. Industrial Digital Twin Connection

Digital Gene can be embedded in a digital twin as:

- object-level gene units
- scene-level gene expression
- dynamic topology representation
- vectorized multimodal retrieval unit
- simulation and planning prior
- real-time feedback update mechanism

The digital twin is not only a visualization system; it can become the carrier of Digital Gene memory, reasoning, and task adaptation.

# Research Memory

## Current Core Hypothesis

Manufacturing Digital Gene can serve as a structured intermediate representation between perception, language reasoning, world modeling, and robot action. It may improve VLA generalization, reduce data requirements, and support proactive human-robot collaboration in manufacturing scenarios.

## Current Research Focus

The user's personal research focus is:

- Embodied intelligence
- Human-robot collaboration
- Manufacturing Digital Gene
- DG-VLA
- World Action Model / World Model
- Digital twin for industrial robotics
- Robotic disassembly / assembly in manufacturing scenarios

## Current Preferred Direction

The user does not aim to train a large Digital Gene VLA from scratch at the current stage.

The preferred direction is to test whether Manufacturing Digital Gene can enhance existing VLA or embodied agents through:

- structured context
- task constraints
- object affordance representation
- geometry primitive transfer
- process knowledge injection
- memory alignment
- policy interface design

## Current Important Naming Decision

The term **Digital Gene** should be preserved.

Reason:

Digital Gene includes both:

- Digital DNA: stable object-level manufacturing knowledge
- Digital RNA: task-specific activated expression

Using only Digital RNA would ignore the stable knowledge source and weaken the conceptual continuity between object-level gene storage and task-level gene expression.

## Current DG-VLA View

Digital Gene can enhance VLA in several possible ways:

1. Gene-as-Context: provide structured manufacturing context to VLA.
2. Gene-as-Constraint: constrain VLA reasoning and action generation.
3. Gene-as-Memory: store long-term object, process, and collaboration knowledge.
4. Gene-as-Policy Interface: connect high-level reasoning with low-level action execution.
5. Gene-as-World Prior: provide object and process priors for world model or WAM.

The most practical early-stage direction is not end-to-end training, but lightweight injection and module-level validation.

## Current WAM View

A useful training paradigm may be:

> third-person continuous dynamics learning + first-person sparse keyframe alignment

This means:

- Third-person videos are used to learn high-density operation dynamics and state transitions.
- First-person keyframes are used to align latent world state with robot observations.
- This may reduce the need for collecting complete egocentric robot manipulation videos.

Digital Gene may provide object priors, action semantics, and topology constraints for this paradigm.

## Current HRC View

Human-robot collaboration should not only be framed as intention prediction. A central issue is **memory mismatch** between human and robot.

Digital Gene may help align:

- physical state
- task progress
- object topology
- human intention
- process constraints
- robot action plan

This supports situational resonance: when humans act unexpectedly, the robot updates memory, adjusts task sequence, and avoids redundant or unsafe actions.

## Current Application Scenario

The preferred application background is manufacturing, especially robotic assembly/disassembly and power battery disassembly tasks.

Potential task examples:

- bolt removal
- module disassembly
- tool selection
- part localization
- human intervention during disassembly
- adaptive task replanning
- digital twin-guided collaborative execution

## Current Experiment Preference

Good experiments should be small but convincing:

- Use existing VLA or embodied agent as baseline.
- Add Digital Gene context or constraints.
- Compare task success rate, logical violation rate, explicit command ratio, replanning success, and unseen object generalization.
- Prefer manufacturing-like tasks over generic tabletop manipulation.

## Directions to Avoid for Now

Temporarily avoid:

- Training a large VLA from scratch.
- Building a complete industrial digital twin platform before validating the core research idea.
- Treating Digital Gene as only a database or only a prompt.
- Over-expanding into all manufacturing intelligence topics without focusing on VLA/WAM/HRC integration.

## Open Questions

1. What is the minimal Digital Gene representation needed to improve VLA behavior?
2. How should Digital Gene be transformed into action constraints?
3. What is the boundary between Digital DNA and Digital RNA?
4. Can Digital Gene reduce data requirements for world model training?
5. How can memory mismatch in HRC be measured experimentally?
6. Which existing VLA framework is easiest for lightweight Digital Gene injection?

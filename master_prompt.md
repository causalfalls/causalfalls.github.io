Build a complete, standalone, mobile-friendly HTML5 Canvas game in a single "index.html" file.

### Concept & Theme
A physics-based puzzle game themed around Quantum Causality and Directed Acyclic Graphs (DAGs). 
The protagonist refuses indefinite causal orders and must construct valid, acyclic causal graphs from drifting spacetime nodes.

### Gameplay Mechanics
1. Core Objective:
   - Drifted nodes enter the viewport slowly. The player connects existing anchored nodes to falling nodes to incorporate them into a single connected DAG.
   - The player must NEVER create a directed cycle. Connecting an edge that would cause a cycle must trigger a red glitch effect and a warning ("Indefinite Causal Order Detected!").

2. Controls & Snapping (Must feel smooth and forgiving):
   - Touch & Mouse supported: Tap/click an anchored node to start an edge. Drag or tap a nearby falling node.
   - Generous snap radius (at least 45px): When dragging near a candidate node, draw a magnetic highlight around it so it is easy to connect on mobile screens.
   - An edge is directed: Arrow points from parent to child (earlier to later).

3. Physics Engine (Force-Directed Graph):
   - Unconnected nodes fall gently under slow downward gravity.
   - Once a node is connected to the graph, it switches to graph physics:
     * Edges act as spring constraints (Hooke's law, fixed rest length ~70px).
     * All connected nodes repel each other slightly (Coulomb repulsion) to prevent overlapping.
     * Gentle damping/viscosity to keep the graph stable.
     * The initial root node is gently anchored near the bottom/center.

4. Node Types:
   - Standard Observed Nodes (Solid circle, soft blue/white, labeled with variable symbols like X, Y, Z).
   - Latent Confounders (Dashed translucent circles with 'U'). If a Latent node connects to another Latent node, they merge into one combined confounder with a pulse effect.
   - Hazard Node (Process Matrix / Loop Anomaly): Flickering purple node. Connecting to it deducts 1 of 3 "Causal Integrity" lives.

5. Levels:
   - Level 1: "Flat Spacetime" - Nodes drift slowly from top to bottom. Target: DAG of 10 nodes.
   - Level 2: "Radial Singularity" - Nodes spawn from screen edges and drift radially inward toward a center anchor. Target: DAG of 16 nodes.

6. Win State & Gift Reveal:
   - When the target DAG size is reached, freeze the physics and trigger a celebration with confetti (include canvas-confetti via CDN).
   - Present a clean, stylized visual breakdown of their final DAG: show total nodes, edges, and a playful label: "Strict Causal Order Preserved! Indefinite order eradicated."
   - Reveal a stylish, animated birthday card containing:
     * A personalized birthday greeting.
     * A placeholder gift card voucher box with a click-to-copy code button.

### Technical & Aesthetic Requirements
- Responsive full-screen HTML5 Canvas. Optimize for Pixel 7 screen size.
- Dark minimalist aesthetic (deep space blue/slate background, neon/pastel vector graph nodes and glowing edges).
- Synthesize all sound effects via Web Audio API (node click, snap, cycle buzz, win chime) so no external audio files are required.
- Write clean, modular, self-contained vanilla JavaScript with zero external frameworks (other than canvas-confetti CDN).
- Aim for smooth animations (60fps where possible) and intuitive controls.
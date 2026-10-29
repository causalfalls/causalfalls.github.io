# CausalFalls — Features & Roadmap

A physics-based puzzle game themed around Quantum Causality and Directed Acyclic Graphs (DAGs), built as a high-performance, standalone HTML5 Canvas experience.

---

## ✅ Implemented Features

### 1. Quantum Causality & DAG Engine
- [x] **Strict Directed Acyclic Graph (DAG) Enforcement**: Real-time cycle detection using breadth-first/depth-first reachability (`DAGValidator.wouldCauseCycle`).
- [x] **⚡ Instant Game Over on Causal Loops**:
  - Creating any directed cycle ($A \to B \to A$ or deep loops) instantly triggers a **Temporal Paradox Collapse** (Game Over).
  - Red chromatic flash overlay (`#glitch-overlay`) and screen shake.
  - Deep dissonant Web Audio paradox collapse boom (`playParadoxBoom`).
  - Modal Game Over with instant restart button.
- [x] **Directed Causal Edges**:
  - Glowing neon vectors with crisp arrowheads pointing from parent to child (earlier $\to$ later).
  - Animated quantum energy pulses flowing along edges in the direction of causality.
- [x] **Anchor Requirement**: New drifting nodes must connect to an already connected/anchored component to maintain a single unified DAG.

---

### 2. Force-Directed Graph Physics Engine
- [x] **Dual Physics Modes**:
  - **Unconnected State**: Drifts under ambient spacetime currents.
  - **Connected State**: Seamlessly transitions to force-directed graph dynamics.
- [x] **Spring Constraints (Hooke's Law)**: Edges act as harmonic springs with rest length $L_0 \approx 76\text{px}$ and spring stiffness $k \approx 0.042$.
- [x] **Coulomb Repulsion**: All connected graph nodes repel each other with an inverse-square force to prevent overlapping and clustering.
- [x] **Damping & Viscosity**: Linear velocity damping ($0.88$) every frame ensures rapid convergence and stable graphs.
- [x] **Root Anchoring**: The root node ($X_0$) is softly anchored to its designated focal point ($y = 0.76h$ in Level 1, center in Level 2).
- [x] **Soft Boundary Clamping**: Prevents connected components from drifting off-screen.
- [x] **Boundary Culling (Spacetime Loss)**: Unanchored nodes that drift past the viewport or into the singularity are permanently lost to spacetime, reducing the available round pool.

---

### 3. Node Types & Quantum Behaviors
- [x] **Standard Observed Variables ($X, Y, Z, \dots$)**:
  - Solid circular core with radiant vector glow and dynamic causal role coloring.
  - Automatically indexed variable labels ($X_0, X, Y, Z, W, \dots$).
- [x] **Parent ($\text{Amber}$) vs Child ($\text{Cyan}$) Dual-Role Asymmetry**:
  - Eliminates the unilateral connection exploit by giving every falling node an inherent 50/50 causal orientation:
    - **Parent Node ($\text{Amber}$)**: Radiates animated outward chevrons along 6 radial spokes. Must emit outgoing edges into the graph ($Falling \to Graph$).
    - **Child Node ($\text{Cyan}$)**: Streams animated inward chevrons along 6 radial spokes. Must receive incoming edges from the graph ($Graph \to Falling$).
  - Prevents autopilot play and introduces real cycle tension by populating the graph with both ancestors and descendants of earlier nodes.
  - Interactive visual feedback: magnetic tether and candidate snap reticle dynamically reflect role colors and warn of directional mismatches.
- [x] **Entangled Causal Motifs (Subgraph Stitching)**:
  - Spacetime variables drift in pre-connected **Entangled Pairs ($A \to B$)** and **Triads/Forks ($A \to B, A \to C$)**.
  - Anchoring any node of a motif seamlessly incorporates the entire sub-graph into the macroscopic DAG.
  - Pre-fixed arrow directions force players to navigate around pre-existing topological constraints.
  - Entangled unanchored links render with shimmering violet/magenta quantum dash lines.
- [x] **Causal Diamonds Reconvergence**:
  - Closed reconvergences where diverging paths from a common cause recombine into a descendant ($A \to B \to D$ & $A \to C \to D$).
  - Closing a diamond triggers a sparkling crystal chime, golden shockwave, and floating notification.
- [x] **Simplified Scoring (Colliders Removed)**:
  - Collider halo rings and badges removed to keep the scoring system pure, transparent, and focused on node count and causal diamonds.
- [x] **Latent Confounders ($U$)**:
  - Translucent purple circles with dashed orbital rings and glowing label $U$.
  - **Confounder Merge Mechanic**: Connecting two Latent nodes merges them into a unified confounder ($U^+$) at their midpoint.
  - **Acyclic Rewiring**: All incoming/outgoing edges of both nodes are rewired to the merged node while preserving DAG acyclicity.
  - Triggers a deep sci-fi bass sweep and concentric shockwave ripples.
- [x] **Hazard Nodes (Loop Anomaly / Process Matrix $\Omega$ / $\circlearrowleft$)**:
  - Flickering violet/magenta node with a rotating loop symbol.
  - Connecting directly to an indefinite causal order hazard matrix causes instant spacetime collapse.

---

- [x] **Quantum Coherence Gate (Causal Capacity & Diamond Expansion)**:
  - Eliminates the linear chain hoarding exploit by capping initial graph size at **3 nodes** (`initialCapacity = 3`).
  - Closing a **Causal Diamond (💎)** expands node capacity by **+3 nodes** (`capacityPerDiamond = 3`).
  - Organically forces players to weave their first triangle/diamond immediately with their first 3 nodes before they can intake more drifting nodes.
  - **Entangled Excess Evaporation**: If an entangled pair/triad is anchored when only 1 node capacity remains, excess partners are cleanly evaporated with a purple quantum shockwave, audio dissipation zap, and particle burst to prevent capacity overflow.
  - **Simplified, Intuitive HUD**:
    - Node counter displayed as `● current/capacity` (e.g. `● 1/3`). Turns glowing red when capacity is full ($x = y$).
    - Diamond counter displayed simply as `💎 count` (e.g. `💎 0`).
    - Hint banner shows clear goal targets: `Goal: ● ≥20 • 💎 ≥5 | ⚡ Close 💎 to expand ● capacity!`.
- [x] **Self-Contained In-Code `LEVEL_CONFIGS` Array**:
  - Embedded at the very top of `<script>` in `index.html` for instant, seamless zero-CORS play via `file:///` URLs.
  - Highly accessible and documented with inline comments for tuning targets, speeds, probabilities, and capacity parameters.
  - Target: $\infty$ nodes with continuous replenishment for free-form DAG experimentation.

---

### 5. Controls & Mobile-First Snapping
- [x] **Dual Input System**:
  - **Drag-to-Connect**: Click/touch a node, drag towards target, and release.
  - **Tap-to-Select & Tap-to-Connect**: Tap source node (highlights with a pulsing reticle), then tap target node. Tapping empty space deselects.
- [x] **Magnetic Snapping & Progressive Warning System**:
  - Automatically highlights candidate nodes when hovering/dragging nearby ($\ge 55\text{px}$).
  - **Level 1 (Tutorial Mode)**: Displays red reticle and red dashed tether line if a connection would create a causal loop.
  - **Subsequent Levels**: Cycle warning color changes are removed—tether and reticle remain standard cyan. If a cycle is formed, it triggers an instant Temporal Paradox collapse.
- [x] **Touch & Gesture Protection**: Touch events configured with `{ passive: false }` and `e.preventDefault()` to prevent accidental page scrolling or Android swipe-back gestures.

---

### 6. Synthesized Audio Engine (Web Audio API)
*Zero external sound files required — 100% procedurally synthesized in real time.*
- [x] **Node Select**: High-frequency sine chime ($520\text{Hz} \to 740\text{Hz}$).
- [x] **Magnetic Snap**: Crisp triangle ping ($420\text{Hz} \to 560\text{Hz}$).
- [x] **Valid Connection**: Warm harmonic triad chord ($C_5 + E_5 + G_5$).
- [x] **Diamond Reconvergence Chime**: Sparkling crystal harmonic chord ($G_5 + B_5 + D_6 + G_6$) upon closing a causal diamond.
- [x] **Confounder Merge**: Deep resonant saw/lowpass frequency sweep ($220\text{Hz} \to 55\text{Hz}$).
- [x] **Cycle Glitch Buzz**: Dissonant frequency-modulated sawtooth buzz ($85\text{Hz}$).
- [x] **Hazard Hit**: Distorted square wave crunch with rapid pitch drop.
- [x] **Victory Fanfare**: Arpeggiated Lydian chord progression ($C_5 - E_5 - G_5 - B_5 - C_6 - E_6$).
- [x] **Audio Controls**: Top-right HUD sound toggle button (🔊 / 🔇).

---

### 7. UI, HUD & Visual Aesthetics
- [x] **Aesthetic**: Deep space blue/slate palette (`#070B14`, `#0D1527`), glassmorphic overlays (`backdrop-filter: blur(14px)`), and neon accents.
- [x] **Spacetime Coordinate Grid**: Ambient animated coordinate grid with singularity orbit rings in Level 2.
- [x] **Dynamic HUD**:
  - Level title badge.
  - Real-time DAG node counter, **Causal Diamond tracker (💎 D/req)**, and composite progress bar.
  - Causal Integrity gems (3 glowing cyan diamonds that dim upon damage).
  - Quick hint footer banner.
  - Restart, Info, and Mute icon buttons.
- [x] **Responsive Canvas**: Crisp rendering supporting high DPI / Retina displays (Pixel 7 and desktop).
- [x] **Modals**:
  - **How to Play Modal**: Explains rules, Entangled Motifs, Diamond Reconvergence, Colliders, Latent confounders, and Loop hazards.
  - **Level Cleared Modal**: Displays DAG statistics, Causal Diamonds closed, and level advance button.
  - **Causal Collapse Modal**: Game over alert with fast rewind button.

---

### 8. Win State & Animated Birthday Reveal
- [x] **Physics Freeze**: Connected graph locks in place for clear inspection.
- [x] **Celebratory Confetti**: Integrated with `canvas-confetti` via CDN (dual-side fireworks burst).
- [x] **DAG Metrics Breakdown**:
  - Total Nodes in DAG.
  - Total Causal Links (directed edges).
  - Causal Diamonds Closed (💎).
  - Maximum Causal Depth (longest directed path computed via topological sort).
  - Latent Confounders Unified count.
  - Playful status: *"Strict Causal Order Preserved! Indefinite order eradicated."*
- [x] **Holographic Birthday Card**:
  - Shimmering animated gradient border.
  - Personalized birthday greeting message.
  - **Gift Voucher Box**: Pre-configured voucher code (`CAUSAL-BDAY-2026-QUANTUM-DAG`).
  - **Click-to-Copy Button**: Instant clipboard integration with feedback confirmation (`✓ Copied!`).
- [x] **Latent Mediator Reduction ($X \to U \to Y \implies X \to Y$)**:
  - Automatically identifies sequences where an unobserved latent variable $U$ mediates between visible variables $X$ and $Y$.
  - Replaces the indirect path with the direct causal edge $X \to Y$ and eliminates $U$, adhering to fundamental causal graph equivalence.
  - Accompanied by expanding cyan/purple shockwaves, particle bursts, and dedicated audio sweep (`playMediatorReduction`).
- [x] **Dual-Mode Positive & Negative Toast System**:
  - Warning box reserved strictly for negative feedback (cycles, directional errors, capacity full, depleted supply) with red glowing border and `⚠️`.
  - Positive blue toast with sparkling diamond `💎` icon and cyan glow (`#00F0FF`) triggers upon closing Causal Diamonds or reducing latent mediators, retaining identical rounded rectangle geometry (`border-radius: 30px`).
- [x] **Interactive Final DAG Inspector with Fly-In Translation**:
  - When the game is won (Level Cleared / Grand Win) or lost (Paradox Collapse / Singularity Anomaly / Depleted Pool), an interactive mini DAG inspector docks in the modal.
  - Features a smooth cubic-bezier fly-in translation animation that translates and scales the DAG from its exact full-screen game coordinates directly into the mini inspection viewer.
  - Full interactive control: drag to pan, wheel/pinch to zoom, zoom buttons (`+`, `−`, `⛶ Fit`), node hover tooltips showing variable name and degrees, and pulsing hazard red highlight on paradox cycle loops.
- [x] **20% Early Spawn Horizon (Linear & Radial)**:
  - Initial nodes spawn at approximately 20% of the screen height in linear mode and 20% of the journey inward in radial mode (distance $\approx 80\%$ from center), providing ample reaction time at the beginning of each round.

---

## 📋 Planned & Upcoming Features (Backlog)

*Add your future feature requests and ideas in the sections below:*

### Gameplay Mechanics & Causal Logic
- [x] If you have a sequence X -> U -> Y, where U is a latent, and X and Y are visible, you should immediately eliminate the U node and replace it with just X -> Y. This is a known equivalence in causal inference.

### New Levels & Challenges

### Visuals, Particle FX & Audio
- [x] Right now, the warning box is used for all types of information. Reserve it to negative messages. In particular, when a causal diamond is formed, the box should be positive. Make it blue to match the diamond color, remove the warning emoji (replace it with something else?) but keeping the same rounded rectangle shape with the same border style.
- [x] When the game is either won or lost, display the final DAG and allow the player to zoom and pan on it to see the details. Have an animation that translates the final dag to the mini version shown in this screen

### Quality of Life & Sharing
- [x] Right now, the nodes already begin approximately halfway through the screen. This leaves little time in the beginning of the round. You should start the nodes at roughly 20% of the way in (in both vertical and radial modes).
- [ ] If the number of nodes currently connected + remaining nodes < number of required nodes, it is impossible to win, so end the game with a loss screen immediately, explaining what happened. 
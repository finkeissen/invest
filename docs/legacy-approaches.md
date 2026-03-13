# Existing Approaches in Game-Theoretic Modeling of Global Economy, Geopolitics, and Investments

**Invest-GT** builds on – but significantly extends – a rich tradition of game-theoretic and simulation-based modeling in political economy, international finance, and geopolitical strategy. This document provides an overview of the most relevant existing approaches, highlighting key contributions, limitations, and points of differentiation from Invest-GT.

The landscape is grouped into eight main categories:

1. **Classic & Global Games Frameworks**
2. **Game-Theoretic Models in International Trade, Sanctions & Geopolitics**
3. **Agent-Based Modeling (ABM) Combined with Game Theory**
4. **Financial-Market & Investment-Specific Strategic Simulations**
5. **Stochastic Dynamic Games & Markov Perfect Equilibria**
6. **Mean Field Games & Large-Population Strategic Interaction**
7. **Multi-Agent Reinforcement Learning (MARL)**
8. **Network Effects, Contagion Models & Systemic Risk**

Additionally, two cross-cutting methodological frameworks are discussed:
- **Mechanism Design & Information Design**
- **Incomplete Contracts & Political Economy of Agreements**

---

## 1. Classic & Global Games Frameworks

**Global Games** (Carlsson & van Damme 1993; Morris & Shin 2003, 2006)
- **Core idea**: Games of incomplete information where players receive noisy private signals about an underlying state θ (economic fundamentals). Strategic complementarities often lead to unique, dominance-solvable equilibria despite multiplicity in complete-information versions.
- **Applications**: Currency crises, bank runs, liquidity crises, sovereign debt attacks, investment under uncertainty. Explains coordination failures and self-fulfilling crises.
- **Strengths**: Tractable analysis of higher-order beliefs; unique equilibrium selection.
- **Limitations**: Mostly static or two-period; limited agent heterogeneity; no dynamic political feedback loops or LLM-driven adaptive behavior.
- **Relevance to Invest-GT**: Directly inspires the game-theoretic engine (Bayesian games, equilibrium search). Invest-GT extends this with repeated/dynamic interaction, multi-layer feedback (politics ↔ markets), and local LLM agents.

**Coordination Games & Sunspot Equilibria** (Cooper & John 1988; Cass & Shell 1983)
- **Core idea**: Extrinsic uncertainty ("sunspots") can coordinate agents onto Pareto-inferior equilibria even absent fundamental shocks. Multiplicity is a feature, not a bug.
- **Applications**: Business cycles, financial crises, herding in investment.
- **Limitations**: No micro-foundation for sunspot selection; limited policy leverage.
- **Relevance**: Motivates Invest-GT's scenario-injection module, which explicitly models narrative shocks as coordination devices.

---

## 2. Game-Theoretic Models in International Trade, Sanctions & Geopolitics

- **Strategic Trade Policy Models** (Brander & Spencer 1985 onward)
  Oligopolistic competition + government intervention (subsidies, tariffs). Classic prisoner's dilemma structure in trade wars. Extended by Krugman (1987) to increasing-returns economies and by Bagwell & Staiger (1999) to WTO-consistent negotiation frameworks.

- **Sanctions as Stochastic / Evolutionary Games** (Hausken 2025; Zhou & Guo 2025; Malafeyev et al. 2023)
  Continuous-time stochastic games modeling sanctioning vs. sanctioned states (e.g., Russia 2022 SWIFT exclusion, Iran, Libya cases). Nodes: provocation → sanctioning → reinforcement → continuation. Monte Carlo simulations quantify de-escalation probabilities.

- **Bargaining & Repeated Games in Trade Conflicts** (Krapohl 2021; Rytenband 2025)
  Evolutionary game theory applied to deglobalization, tariff escalation, and instability of global trade cooperation. Shows that extreme trade protectionism can emerge as stable equilibria.

- **US–China / Multi-Actor Trade Disputes** (Dong et al. 2018; various 2025 papers)
  Payoff matrices for fossil-energy trade, Belt & Road responses, secondary sanctions.

- **Rubinstein Bargaining & Outside Options** (Rubinstein 1982; Binmore et al. 1986)
  Alternating-offers bargaining with discounting and outside options – foundational for modeling bilateral trade agreements, debt restructurings, and ceasefire negotiations.

- **Geopolitical Risk Indices as Calibration Anchors** (Caldara & Iacoviello 2022)
  The GPR index (Geopolitical Risk Index) provides a text-mining-based monthly measure of geopolitical risk from newspaper coverage. Widely used for calibrating shock processes in DSGE and simulation models. Directly applicable as an exogenous forcing variable in Invest-GT's calibration pipeline.

**Common limitations**: Often analytical/static, few agents, no endogenous investment-layer dynamics, limited local reproducibility.
**Invest-GT differentiation**: Explicit separation of political/investment layers, modular interaction modeling, local runtime + LLM agents for realistic multi-round adaptation, GPR-index calibration.

---

## 3. Agent-Based Modeling (ABM) Combined with Game Theory

- **Strategic ABM in Financial Markets** (Wellman 2017; Axtell et al. 2022/2025 reviews)
  Combines ABM with game-theoretic reasoning to study market impact, clustered volatility, systemic risk, housing bubbles. Agents follow strategic rules or learn.

- **LLM-Augmented ABM** (Hashimoto et al. 2025; Park et al. 2023 "Generative Agents")
  Fundamental-Chartist-LLM agents simulate human-like trading under macro phenomena. Park et al. demonstrate that LLM-powered agents exhibit socially plausible emergent behavior (memory, reflection, planning) in simulated environments.

- **Political Economy ABM** (Tesfatsion ACE framework; various computational political economy models)
  Spatial election models, Tiebout/local public goods, platform convergence – with strategic voting & policy interaction.

- **JASSS-Tradition Models** (Journal of Artificial Societies and Social Simulation)
  A broad literature of validated, open ABM models covering opinion dynamics, tax compliance, financial contagion. Serves as methodological reference for Invest-GT's calibration discipline.

**Strengths**: Emergent macro behavior from micro rules; heterogeneity; relaxation of perfect-rationality assumptions.
**Limitations**: Often finance- or macro-only; rarely deep political-geopolitical layers; cloud-heavy or non-reproducible in many implementations.
**Invest-GT extension**: Local-first (Ollama + LangGraph), hypothesis repository, explicit calibration pipeline against FED/ECB/OFAC data, strong emphasis on political ↔ investment feedback.

---

## 4. Financial-Market & Investment-Specific Strategic Simulations

- **Multi-Player Game-Theoretic Capital Markets** (Singer et al. 2017 System Dynamics paper)
  Sequential dynamic multi-player games modeling central bank QE impact on global asset prices (cooperation + conflict).

- **Behavioral + Evolutionary GT in Investments** (various 2025 reviews)
  Loss aversion, fairness preferences in portfolio rebalancing under geopolitical stress.

- **Geopolitical Investing & Prediction Markets** (2026 practitioner discussions)
  Speculative bets on elections, sanctions, commodity shocks via derivatives / prediction platforms.

- **Strategic Complementarities in Asset Pricing** (Vives 2014; Brunnermeier & Pedersen 2009)
  Models how strategic interactions among investors (liquidity spirals, fire sales, margin constraints) amplify asset price volatility. Brunnermeier & Pedersen's market-liquidity / funding-liquidity spiral is directly relevant to stress-testing investment portfolios in Invest-GT.

**Limitations**: Mostly practitioner-oriented or narrative; limited open-source, modular, reproducible frameworks.
**Invest-GT value-add**: Open, local, reproducible runtime; structured hypothesis tracking; multi-layer separation before integration.

---

## 5. Stochastic Dynamic Games & Markov Perfect Equilibria

**Maskin & Tirole (2001); Ericson & Pakes (1995); Dutta (1995)**
- **Core idea**: Stochastic games (Shapley 1953) generalize repeated games to environments where the state of the world evolves stochastically as a function of players' actions. A **Markov Perfect Equilibrium (MPE)** restricts strategies to depend only on payoff-relevant state variables, ensuring tractability and eliminating non-credible threats.
- **Applications**: Dynamic oligopoly (Ericson & Pakes investment/entry/exit), arms races, environmental treaty compliance, monetary policy credibility.
- **Key papers**:
  - Maskin & Tirole (2001): Characterization of MPE in general stochastic games. *Journal of Economic Theory*, 100(1), 191–219.
  - Ericson & Pakes (1995): Markov-perfect industry dynamics. *Review of Economic Studies*, 62(1), 53–82.
  - Dutta (1995): A folk theorem for stochastic games. *Journal of Economic Theory*, 66(1), 1–32.
- **Strengths**: Handles state-dependent payoffs; credible equilibria; links micro decisions to macro dynamics.
- **Limitations**: Curse of dimensionality; equilibrium computation is NP-hard in high-dimensional state spaces; limited heterogeneity in analytical versions.
- **Relevance to Invest-GT**: The political-macroeconomic state space (sanctions level, trade volumes, asset prices, political stability scores) is naturally modeled as a Markov state. Invest-GT's simulation engine implicitly solves an approximate MPE via LLM-guided best-response iteration, bypassing analytical intractability.

---

## 6. Mean Field Games & Large-Population Strategic Interaction

**Lasry & Lions (2006a, 2006b, 2007); Huang, Malhamé & Caines (2006)**
- **Core idea**: When the number of strategic agents becomes large, individual influence on aggregate outcomes vanishes. The strategic interaction can be approximated by a **mean field**: each agent optimizes against the (endogenous) distribution of all other agents' states. This yields a coupled system of a Hamilton-Jacobi-Bellman (HJB) equation (individual optimization) and a Fokker-Planck equation (population dynamics).
- **Applications**: Systemic risk in interbank lending (Carmona et al. 2015), crowd dynamics, energy markets, epidemiological policy games, cryptocurrency mining competition.
- **Key papers**:
  - Lasry & Lions (2007): Mean field games. *Japanese Journal of Mathematics*, 2(1), 229–260.
  - Carmona & Delarue (2018): *Probabilistic Theory of Mean Field Games with Applications*. Springer.
  - Achdou et al. (2022): Mean field games and applications in economics. *Annual Review of Economics*, 14.
- **Strengths**: Scales to millions of agents; tractable PDE formulation; captures distributional effects of policy shocks.
- **Limitations**: Assumes homogeneous interactions and rational expectations; continuous-time PDEs require specialized numerical methods; political heterogeneity is hard to encode.
- **Relevance to Invest-GT**: MFG provides a theoretical upper-bound framework for Invest-GT's large-population market-participant layer (e.g., retail investors, small exporters). Invest-GT's discrete-agent simulation can be validated against MFG approximations for consistency.

---

## 7. Multi-Agent Reinforcement Learning (MARL)

**Shoham & Leyton-Brown (2009); Lowe et al. (2017); OpenAI Five (2019); AlphaStar (2019)**
- **Core idea**: Multiple agents learn policies simultaneously via trial-and-error interaction with a shared environment. Unlike classical game theory, no closed-form equilibrium is assumed; emergent behavior arises from learning dynamics. Key solution concepts are **Nash equilibria as fixed points of learning**, correlated equilibria (via policy gradient methods), and **no-regret learning**.
- **Subtypes relevant to Invest-GT**:
  - *Cooperative MARL*: Agents share rewards; useful for modeling alliances (e.g., G7 coordination).
  - *Competitive MARL*: Zero-sum or mixed-motive games (e.g., US–China trade war dynamics).
  - *Mean-field MARL* (Yang et al. 2018): Scales RL to thousands of interacting agents.
- **Key papers**:
  - Lowe et al. (2017): Multi-agent actor-critic for mixed cooperative-competitive environments. *NeurIPS 2017*.
  - Vinyals et al. (2019): Grandmaster level in StarCraft II using multi-agent reinforcement learning. *Nature*, 575, 350–354.
  - Peysakhovich & Lerer (2018): Consequentialist conditional cooperation in social dilemmas. *ICLR 2018*.
  - Calvano et al. (2020): Artificial intelligence, algorithmic pricing, and collusion. *American Economic Review*, 110(10), 3267–3297.
- **Strengths**: No equilibrium pre-specification; discovers emergent strategies; scalable with modern deep learning.
- **Limitations**: Non-stationary training environments; convergence not guaranteed to Nash equilibria; computationally intensive; interpretability challenges.
- **Relevance to Invest-GT**: MARL is the natural computational complement to Invest-GT's LLM-agent layer. Where LLM agents bring **semantic reasoning** (narrative-based decision-making), MARL provides **adaptive optimization**. A hybrid architecture – LLM for context framing, RL for parameter tuning – is a promising extension. The Calvano et al. (2020) result (algorithmic agents colluding without explicit communication) is a direct warning for multi-agent investment simulation design.

---

## 8. Network Effects, Contagion Models & Systemic Risk

**Allen & Gale (2000); Acemoglu et al. (2015); Elliott et al. (2014); Eisenberg & Noe (2001)**
- **Core idea**: Financial and political systems are networks. Shocks propagate via balance-sheet linkages (financial contagion), supply chain dependencies (trade networks), or political alliances (geopolitical contagion). Network topology determines whether shocks are absorbed or amplified.
- **Key results**:
  - Allen & Gale (2000): Complete interbank networks are more resilient to small shocks but more fragile to large ones than incomplete networks.
  - Acemoglu et al. (2015): The relationship between network density and systemic risk is non-monotonic – diversification and contagion are two sides of the same coin. *American Economic Review*, 105(2), 564–608.
  - Elliott et al. (2014): Cascades in networks of discontinuous threshold failures (e.g., sovereign defaults, corporate bankruptcy chains). *American Economic Review*, 104(10), 3115–3153.
  - Eisenberg & Noe (2001): Systemic risk in financial systems: clearing vector computation for interbank obligations. *Management Science*, 47(2), 236–249.
- **Geopolitical Network Extensions**:
  - Farrell & Newman (2019): Weaponized interdependence – how states exploit global economic networks for coercion. *International Security*, 44(1), 42–79.
  - Gowa & Mansfield (1993): Power politics and international trade. *American Political Science Review*, 87(2), 408–420.
- **Strengths**: Captures second- and third-order propagation effects; empirically grounded in balance-sheet data.
- **Limitations**: Static network assumptions; limited agent heterogeneity in analytical models; computational scaling issues for large graphs.
- **Relevance to Invest-GT**: Invest-GT's geopolitical module should incorporate a dependency graph layer: trade dependencies, financial exposures, alliance structures, and sanctions-network topology. The Farrell & Newman (2019) weaponized-interdependence framework is particularly relevant for modeling secondary-sanctions dynamics and supply-chain weaponization (e.g., semiconductor export controls).

---

## Cross-Cutting Framework A: Mechanism Design & Information Design

**Hurwicz (1960); Myerson (1981); Maskin (1999); Bergemann & Morris (2016, 2019)**
- **Core idea**:
  - *Mechanism Design* ("reverse game theory"): Designer chooses rules of the game to implement desired outcomes as equilibria (incentive compatibility + participation constraints). Applications: auction design, regulatory frameworks, international treaty design.
  - *Information Design* (Bayesian Persuasion): A sender strategically discloses information to influence receiver behavior. Kamenica & Gentzkow (2011) characterize optimal disclosure policies.
- **Key papers**:
  - Myerson (1981): Optimal auction design. *Mathematics of Operations Research*, 6(1), 58–73.
  - Bergemann & Morris (2016): Bayes correlated equilibrium and the comparison of information structures. *Econometrica*, 84(2), 487–514.
  - Kamenica & Gentzkow (2011): Bayesian persuasion. *American Economic Review*, 101(6), 2590–2615.
- **Applications for Invest-GT**:
  - Regulatory design: How do sanctions regimes, capital controls, or trade rules function as mechanism-design instruments?
  - Central bank communication as information design: Forward guidance as strategic disclosure to coordinate market expectations.
  - LLM agents as information senders: Invest-GT's LLM agents can be modeled as Bayesian persuaders selectively revealing signals.
- **Limitations**: Assumes a designer with full commitment power; political economy constraints (who designs the mechanism?) are often ignored.

---

## Cross-Cutting Framework B: Incomplete Contracts & Political Economy of Agreements

**Grossman & Hart (1986); Hart & Moore (1990); Hart (1995); Acemoglu & Robinson (2006)**
- **Core idea**:
  - *Incomplete Contracts*: Not all contingencies can be specified ex ante. Residual control rights (property rights) determine ex post bargaining power and investment incentives. Applied to firms, joint ventures, alliances, and international agreements.
  - *Political Economy / Power Transitions*: Acemoglu & Robinson model political equilibria where economic and political power interact, leading to endogenous institutional change – highly relevant for modeling autocracy/democracy dynamics in geopolitical risk.
- **Key papers**:
  - Grossman & Hart (1986): The costs and benefits of ownership. *Journal of Political Economy*, 94(4), 691–719.
  - Hart & Moore (1990): Property rights and the nature of the firm. *Journal of Political Economy*, 98(6), 1119–1158.
  - Acemoglu & Robinson (2006): *Economic Origins of Dictatorship and Democracy*. Cambridge University Press.
  - Acemoglu, Johnson & Robinson (2001): The colonial origins of comparative development. *American Economic Review*, 91(5), 1369–1401.
- **Relevance to Invest-GT**:
  - Trade agreements, investment treaties (BITs), and alliance frameworks are inherently incomplete contracts. Their renegotiation dynamics under geopolitical stress (e.g., NATO burden-sharing, WTO dispute mechanisms) are best modeled with incomplete-contract tools.
  - The political power layer in Invest-GT should incorporate Acemoglu-Robinson style transitions: how sanctions or economic crises shift political equilibria and in turn alter investment risk.

---

## Summary Comparison Table

| Approach | Key Strength | Main Limitation | How Invest-GT Improves / Differs |
|---|---|---|---|
| Global Games (Morris/Shin) | Unique equilibrium via higher-order beliefs | Static, low heterogeneity | Adds repeated/dynamic + LLM agents + political layer |
| Sanctions / Trade Games | Captures escalation / de-escalation | Few agents, analytical bias | Multi-agent, modular layers, local simulation |
| Strategic ABM Finance | Emergent macro from micro rules | Finance-heavy, less political depth | Explicit politics–markets feedback, hypothesis repo |
| LLM-ABM Hybrids (2025+) | Human-like adaptive decisions | Early stage, often cloud-dependent | Local-first (Ollama), reproducible, calibrated pipeline |
| Stochastic / Markov Games | State-dependent credible equilibria | Curse of dimensionality | Approximate MPE via LLM best-response iteration |
| Mean Field Games | Scales to large agent populations | Homogeneous interaction assumption | Discrete-agent layer validated against MFG approximations |
| MARL | No equilibrium pre-specification; adaptive | Non-stationary; convergence issues | LLM + RL hybrid: semantic reasoning + adaptive optimization |
| Network / Contagion Models | Second-order propagation; systemic risk | Static topology; scaling limits | Dependency graph layer: trade, finance, alliance, sanctions |
| Mechanism / Information Design | Optimal rule/disclosure design | Commitment power assumptions | Models regulation, central bank communication, LLM persuaders |
| Incomplete Contracts / Pol. Econ. | Renegotiation, power transitions | Abstract; hard to calibrate directly | Models treaty renegotiation, political regime change |
| GPR Index (Caldara/Iacoviello) | Empirical text-based risk measure | Aggregate; no structural model | Direct calibration anchor for shock processes |

---

## Conclusion

Invest-GT is not starting from scratch: it stands on the shoulders of global games, strategic trade/sanctions modeling, strategic ABM, stochastic dynamic games, mean field game theory, MARL, network contagion models, mechanism design, and incomplete-contract theory. Its distinctive contribution lies in the **methodological discipline** (separate modeling → explicit interaction → merged runtime), the **local-first reproducibility**, the **LLM-powered adaptive agents**, the **structured hypothesis repository + calibration pipeline**, and the integration of a **geopolitical network/dependency layer**. These features aim to make the framework more practical for researchers, think tanks, and strategy teams working on political-macro stress-testing in 2026 and beyond.

---

## References

### Foundational Game Theory
- Shapley, L.S. (1953). Stochastic games. *Proceedings of the National Academy of Sciences*, 39(10), 1095–1100.
- Nash, J. (1951). Non-cooperative games. *Annals of Mathematics*, 54(2), 286–295.
- Rubinstein, A. (1982). Perfect equilibrium in a bargaining model. *Econometrica*, 50(1), 97–109.
- Maskin, E., & Tirole, J. (2001). Markov perfect equilibrium. *Journal of Economic Theory*, 100(1), 191–219.

### Global Games & Coordination
- Carlsson, H., & van Damme, E. (1993). Global games and equilibrium selection. *Econometrica*, 61(5), 989–1018.
- Morris, S., & Shin, H.S. (2003). Global games: Theory and applications. In *Advances in Economics and Econometrics* (Dewatripont et al., eds.). Cambridge University Press.
- Morris, S., & Shin, H.S. (2006). Endogenous public signals and coordination. Mimeo, Princeton.

### Dynamic & Stochastic Games
- Ericson, R., & Pakes, A. (1995). Markov-perfect industry dynamics. *Review of Economic Studies*, 62(1), 53–82.
- Dutta, P.K. (1995). A folk theorem for stochastic games. *Journal of Economic Theory*, 66(1), 1–32.

### Mean Field Games
- Lasry, J.M., & Lions, P.L. (2007). Mean field games. *Japanese Journal of Mathematics*, 2(1), 229–260.
- Carmona, R., & Delarue, F. (2018). *Probabilistic Theory of Mean Field Games with Applications*. Springer.

### MARL & Algorithmic Agents
- Lowe, R. et al. (2017). Multi-agent actor-critic for mixed cooperative-competitive environments. *NeurIPS 2017*.
- Calvano, E. et al. (2020). Artificial intelligence, algorithmic pricing, and collusion. *American Economic Review*, 110(10), 3267–3297.
- Vinyals, O. et al. (2019). Grandmaster level in StarCraft II using multi-agent RL. *Nature*, 575, 350–354.

### Network & Systemic Risk
- Allen, F., & Gale, D. (2000). Financial contagion. *Journal of Political Economy*, 108(1), 1–33.
- Acemoglu, D., Ozdaglar, A., & Tahbaz-Salehi, A. (2015). Systemic risk and stability in financial networks. *American Economic Review*, 105(2), 564–608.
- Elliott, M., Golub, B., & Jackson, M.O. (2014). Financial networks and contagion. *American Economic Review*, 104(10), 3115–3153.
- Farrell, H., & Newman, A. (2019). Weaponized interdependence. *International Security*, 44(1), 42–79.

### Mechanism & Information Design
- Myerson, R.B. (1981). Optimal auction design. *Mathematics of Operations Research*, 6(1), 58–73.
- Bergemann, D., & Morris, S. (2016). Bayes correlated equilibrium. *Econometrica*, 84(2), 487–514.
- Kamenica, E., & Gentzkow, M. (2011). Bayesian persuasion. *American Economic Review*, 101(6), 2590–2615.

### Incomplete Contracts & Political Economy
- Grossman, S., & Hart, O. (1986). The costs and benefits of ownership. *Journal of Political Economy*, 94(4), 691–719.
- Hart, O., & Moore, J. (1990). Property rights and the nature of the firm. *Journal of Political Economy*, 98(6), 1119–1158.
- Acemoglu, D., & Robinson, J.A. (2006). *Economic Origins of Dictatorship and Democracy*. Cambridge University Press.

### Trade, Sanctions & Geopolitical Risk
- Brander, J.A., & Spencer, B.J. (1985). Export subsidies and international market share rivalry. *Journal of International Economics*, 18(1–2), 83–100.
- Caldara, D., & Iacoviello, M. (2022). Measuring geopolitical risk. *American Economic Review*, 112(4), 1194–1225.
- Hausken, K. (2025). Sanctions as stochastic games. *(forthcoming)*
- Brunnermeier, M.K., & Pedersen, L.H. (2009). Market liquidity and funding liquidity. *Review of Financial Studies*, 22(6), 2201–2238.

### ABM & LLM-Agent Simulation
- Wellman, M.P. (2017). Putting the agent in agent-based modeling. *Autonomous Agents and Multi-Agent Systems*, 31(6), 1175–1186.
- Park, J.S. et al. (2023). Generative agents: Interactive simulacra of human behavior. *UIST 2023*.
- Hashimoto, T. et al. (2025). LLM-augmented agent-based financial market simulation. *(forthcoming)*

---

*This document will be updated as new relevant work appears. Last revised: 2026.*

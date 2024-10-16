# Reinforcement Learning in Switching Non-Stationary Markov Decision Processes: Algorithms and Convergence Analysis

This project is for the implementation of the paper entitled "Reinforcement Learning in Switching Non-Stationary Markov Decision Processes: Algorithms and Convergence Analysis." It demonstrates the performance of theoretical results in the context of wireless communication systems, which often experience dynamic channel conditions due to factors like fading, interference, and user mobility.

**Adaptive Modulation (AM)** techniques are employed to enhance performance under these fluctuating conditions by dynamically adjusting transmission parameters, such as modulation schemes, to match current channel conditions. This approach aims to maximize data throughput while maintaining reliable communication.

An adaptive communication system is modeled using the **State Non-Stationary Markov Decision Process (SNS-MDP)** framework, capturing the stochastic and time-varying nature of wireless environments. In this model:

- The **agent** (transceiver) selects a frequency band for data transmission based on the current modulation scheme.
- **Actions ($\mathcal{A}$)**: Set of available frequency bands.
- **States ($\mathcal{S}$)**: Different modulation schemes offering trade-offs between data rate and noise tolerance.
- **Environmental States ($\mathcal{E}$)**: Channel conditions categorized as Excellent, Good, Fair, or Poor.

Channel conditions are modeled using predefined Markovian transition probabilities. The **Probability of Successful Transmission** ($ P_{success}(s, e, a) $) is specified for each modulation scheme and channel condition.

A reward function balances data throughput with penalties for unfavorable conditions:

$$
\vec{R}(s, e) = \alpha \cdot \text{Rate}(s) \cdot \text{Decay}(e) - \beta \cdot \text{Decay}(e),
$$

where:

- $\alpha$ and $\beta$ control the importance of data rate and penalties.
- $\text{Rate}(s)$ is the data rate associated with modulation scheme $s$.
- $\text{Decay}(e)$ represents degradation due to channel condition $e$.

 All algorithms start with the same initial policy, recommending frequency band 1 for all modulation schemes.

---

For more details and complete tables, please refer to the code repository and the paper.

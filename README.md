# SNS-MDP

# Adaptive Modulation in Wireless Communication Systems

We **demonstrate** our theoretical results in the context of **wireless communication systems**, which frequently experience dynamic channel conditions due to factors such as fading, interference, and user mobility.

Wireless communication systems are inherently dynamic and complex because of the unpredictable nature of the wireless medium, which causes the quality of the wireless channel to fluctuate over time and across different locations. This variability is influenced by several factors:

- **Fading**: Fluctuations in signal strength caused by the constructive and destructive interference of multiple signal paths.
- **Interference**: Unwanted signals from other transmitters that disrupt communication.
- **User Mobility**: Movement of users alters signal propagation conditions.

To enhance performance under such fluctuating conditions, **Adaptive Modulation (AM)** techniques are employed. Adaptive Modulation involves dynamically adjusting transmission parameters, such as modulation schemes, to match current channel conditions. This approach aims to maximize data throughput while maintaining reliable communication.

To showcase the effectiveness of our proposed framework, we modeled an adaptive communication system using the **State Non-Stationary Markov Decision Process (SNS-MDP)** framework. The SNS-MDP effectively captures the stochastic and time-varying nature of wireless environments.

In our model, the **transceiver functions as an agent** that makes decisions based on observations of the system state. Specifically, the agent selects a frequency band for data transmission after observing the current modulation scheme.

$$
\mathcal{A} = \{ \texttt{FB}_1, \texttt{FB}_2, \ldots, \texttt{FB}_A \},
$$

where $\texttt{FB}_i$ represents the $i$-th frequency band, and $A$ is the total number of available frequency bands.

The **states** in the system correspond to different **Modulation Schemes (MS)**, each offering a unique trade-off between data rate and noise tolerance:

$$
\mathcal{S} = \{ \texttt{MS}_1, \texttt{MS}_2, \ldots, \texttt{MS}_S \},
$$

where $\texttt{MS}_j$ represents the $j$-th modulation scheme, and $S$ is the number of available modulation schemes.

The **environmental states** represent the channel conditions, which are crucial yet typically unobservable factors that influence communication dynamics:

$$
\mathcal{E} = \{ \text{Excellent (E)}, \text{Good (G)}, \text{Fair (F)}, \text{Poor (P)} \}.
$$

## Markovian Dynamics of Channel Conditions

Channel conditions are often modeled using Markovian dynamics, with transitions governed by a probability matrix $q(e'|e)$. This approach captures the temporal dependencies of channel conditions due to factors like fading and mobility. Channel condition transition probabilities can be estimated, but in this work, we use predefined values to show the convergence of the RL algorithms upon the SNS-MDP framework.

The following table shows the channel condition transition probabilities:

| Current State | Excellent | Good  | Fair  | Poor  |
|---------------|-----------|-------|-------|-------|
| **Excellent** | 0.44      | 0.11  | 0.12  | 0.33  |
| **Good**      | 0.20      | 0.10  | 0.30  | 0.40  |
| **Fair**      | 0.66      | 0.11  | 0.09  | 0.14  |
| **Poor**      | 0.18      | 0.22  | 0.40  | 0.20  |

*Table 1: Environment Setting Transition Probabilities*

**Note:** All the probability values in the tables are scaled from 0 to 1.

## Probability of Successful Transmission

In practice, the **Probability of Successful Transmission**, denoted by \( P_{\text{success}}(s, e, a) \), can be estimated through empirical measurements or analytical models. For our simulation, we use predefined values to focus on demonstrating the convergence properties of our algorithms. In Tables 2 and 3, we provide the detailed values for each \( P_{\text{success}}(s, e, a) \). Once a frequency band is selected, the corresponding table is chosen, where each table contains the probability of successful transmission for each pair of modulation schemes and channel conditions.

### Frequency Bands 1 to 5

#### Frequency Band 1

| Modulation Scheme | Excellent | Good  | Fair  | Poor  |
|-------------------|-----------|-------|-------|-------|
| **BPSK**          | 0.83      | 0.84  | 0.89  | 0.86  |
| **QPSK**          | 0.99      | 0.78  | 0.80  | 0.79  |
| **8-PSK**         | 0.91      | 0.81  | 0.87  | 0.81  |
| **16-QAM**        | 0.79      | 0.78  | 0.91  | 0.78  |
| **32-QAM**        | 0.88      | 0.81  | 0.88  | 0.75  |
| **64-QAM**        | 0.92      | 0.85  | 0.84  | 0.72  |
| **128-QAM**       | 0.87      | 0.80  | 0.83  | 0.74  |
| **256-QAM**       | 0.91      | 0.82  | 0.86  | 0.70  |
| **512-QAM**       | 0.93      | 0.86  | 0.90  | 0.68  |
| **1024-QAM**      | 0.85      | 0.79  | 0.81  | 0.71  |
| **2048-QAM**      | 0.89      | 0.83  | 0.84  | 0.69  |

#### Frequency Band 2

| Modulation Scheme | Excellent | Good  | Fair  | Poor  |
|-------------------|-----------|-------|-------|-------|
| **BPSK**          | 0.72      | 0.84  | 0.89  | 0.83  |
| **QPSK**          | 0.94      | 0.87  | 0.67  | 0.66  |
| **8-PSK**         | 0.78      | 0.79  | 0.72  | 0.72  |
| **16-QAM**        | 0.74      | 0.71  | 0.93  | 0.73  |
| **32-QAM**        | 0.79      | 0.75  | 0.87  | 0.71  |
| **64-QAM**        | 0.81      | 0.77  | 0.85  | 0.70  |
| **128-QAM**       | 0.82      | 0.78  | 0.86  | 0.69  |
| **256-QAM**       | 0.85      | 0.80  | 0.88  | 0.68  |
| **512-QAM**       | 0.83      | 0.81  | 0.84  | 0.67  |
| **1024-QAM**      | 0.88      | 0.83  | 0.82  | 0.65  |
| **2048-QAM**      | 0.86      | 0.85  | 0.80  | 0.64  |

*(Tables for Frequency Bands 3 to 5 are structured similarly and can be found in the code repository.)*

### Frequency Bands 6 to 11

*(Tables for Frequency Bands 6 to 11 are structured similarly and can be found in the code repository.)*

## State Transition Probabilities

The **state transition probabilities** \( p_e(s'|s, a) \) are influenced by \( P_{\text{success}}(s, e, a) \) and are defined as:

$$
p_e(s'|s, a) = \begin{cases}
P_{\text{success}}(s, e, a), & \text{if } s' = s, \\\\
\displaystyle \frac{1 - P_{\text{success}}(s, e, a)}{\text{Index}(s') \times \sum_{k=1}^{|\mathcal{S}| - 1}\frac{1}{k}}, & \text{if } s' \neq s,
\end{cases}
$$

where $\text{Index}(s')$ returns the position of modulation scheme $s'$ in the ordered list starting from 1. This formulation ensures that if transmission is successful, the state remains the same; otherwise, it transitions to other states with a probability inversely proportional to their indices.

## Reward Function

The reward function $\vec{R}(s, e)$ measures system performance by balancing data throughput with penalties for unfavorable conditions, expressed as:

$$
\vec{R}(s, e) = \alpha \cdot \text{Rate}(s) \cdot \text{Decay}(e) - \beta \cdot \text{Decay}(e),
$$

where:

- $\alpha$ controls the importance of the data rate (set to 10 in our simulation).
- $\beta$ penalizes the use of higher-order schemes in poor conditions (set to 2 in our simulation).
- $\text{Rate}(s)$ is the data rate linked to modulation scheme $s$.
- $\text{Decay}(e)$ represents degradation due to channel condition $e$.

This formulation promotes modulation schemes that maximize throughput while discouraging risky decisions under poor conditions. Tables 4 and 5 represent the data rate for each modulation scheme and the decay rate for each channel condition.

### Data Rates for Different Modulation Schemes

| Modulation Scheme | Data Rate |
|-------------------|-----------|
| **BPSK**          | 10        |
| **QPSK**          | 20        |
| **8-PSK**         | 30        |
| **16-QAM**        | 40        |
| **32-QAM**        | 50        |
| **64-QAM**        | 60        |
| **128-QAM**       | 70        |
| **256-QAM**       | 80        |
| **512-QAM**       | 90        |
| **1024-QAM**      | 100       |
| **2048-QAM**      | 110       |

*Table 4: Data Rates for Different Modulation Schemes*

### Decay Rates for Different Channel Conditions

| Channel Condition | Decay Rate |
|-------------------|------------|
| **Excellent**     | 0.99       |
| **Good**          | 0.70       |
| **Fair**          | 0.50       |
| **Poor**          | 0.30       |

*Table 5: Decay Rates for Different Channel Conditions*

## Simulation Code

The simulations are implemented in Python, and the code is available in the following repository:

[Simulation Code Repository](https://anonymous.4open.science/r/SNS-MDP-EB4F/README.md)

All the algorithms start with the same initial policy that recommends frequency band 1 for all the modulation schemes. The results are shown in the Experimental Results section of the paper.

---

*For detailed tables and additional information, please refer to the code repository and accompanying documentation.*

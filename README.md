# SIR-
# Dynamics of COVID-19: A SIR Model Analysis

**Author:** Peerapat Phatpanichot  
**Date:** [Today's Date]

## Introduction

Here is the walkthrough of constructing and studying the dynamics of the SIR model using a real-world dataset. The dynamics of COVID-19 and the calibrated parameters we've derived from the Canadian COVID-19 original dataset of the original virus variant.

## Calibrated Parameters

First, we begin with the assumption of the total population being 38 million individuals. During the initial growth phase of the epidemic, we estimated the basic reproduction number, denoted by β. This parameter is critical as it reflects the transmission rate—indicating the probability of an infected individual transmitting the virus to those susceptible in their vicinity.

Our findings indicated that the estimated β stands at 0.119, which means, on average, each infected individual has a chance to infect 11.9% of the susceptible individuals they come into contact with, per day.

We then calculated γ, the recovery rate, the daily recovery percentage within the infected population. Our estimated γ was 0.058, meaning for every 100 infected individuals, approximately 5.8 are expected to recover each day.

Moreover, μ, the natural birth and death rate, was factored into our model, representing an average lifespan of 75 years, which translates to a rate of 1/75 per individual. Lastly, α, the disease-induced death rate, was calculated at 0.002, indicating a daily mortality risk of 0.2% for the infected individuals due to the disease.

By inputting these calibrated parameters into the SIR model's differential equations and performing numerical integration over the dataset's time span, we were able to simulate the epidemic's progression.

## Simulation Results

The simulation, spanning 340 days, demonstrates a classic epidemic curve. The susceptible proportion of the population (`S(t)`), depicted in blue, decreases over time as individuals contract the virus and move into the infected category (`I(t)`). This category, shown in red, initially rises sharply, reflecting the outbreak's growth phase, before declining as individuals recover or succumb to the disease. The recovered population (`R(t)`), colored green, increases over time as individuals recover from the virus, with a gradual plateau indicating the epidemic's slowdown.

The model includes the effects of natural birth and death rates (`μ`) as well as disease-induced mortality (`α`), providing a more realistic scenario where the total population size remains constant, but the dynamics of disease spread and recovery are influenced by these additional factors.

These dynamics are crucial for understanding the potential impact of public health interventions and can be used to inform policy decisions. The model suggests that without any interventions, the epidemic will eventually reach a steady state, where the number of new infections is balanced by the number of recoveries and deaths.

![SIR Model Simulation showing the proportion of Susceptible (blue), Infected (red), and Recovered (green) individuals over time.](output/SIM.png)

## SIR Model Dynamics

## Nullclines and Fixed Points

In this segment of the paper, we delve deeper into the dynamics of our SIR model for the dataset. We analyze the nullclines, fixed points, and perform a stability analysis to comprehend the potential long-term behavior of the epidemic within the population.

We begin by plotting the nullclines for our system. These are the curves along which the rate of change of our susceptible and infected populations is zero, essentially where the system is in a state of equilibrium. The red dashed line represents the nullcline where the rate of change of the susceptible population is zero, and the blue dashed line represents the nullcline for the infected population.

The fixed points, where these nullclines intersect, give us critical insights:
- The Disease-Free Equilibrium occurs at full susceptibility with no infections, depicted by the green marker. Here, s* = 1, meaning the entire population is susceptible, and i* = 0, indicating no current infections.
- The Endemic Equilibrium, shown by the magenta marker, is where the disease persists in the population at stable levels. The values s* = 0.601 and i* = 0.0744 suggest that 60.1% of the population remains susceptible while 7.44% is infected in the long term.

The nullclines, which represent the points where the rate of change of susceptible (s) and infected (i) individuals is zero, are depicted in the following figure. These curves are critical for understanding the system's behavior at equilibrium.

[Embed images of the equations here]

The fixed points (s*, i*) are where these nullclines intersect, indicating the system's potential long-term behavior:
- Disease-free equilibrium: (s*, i*) = (1, 0), where the population is fully susceptible and there are no infections.
- Endemic equilibrium: (s*, i*) = (δ / β, (μ (1 - δ / β)) / δ), where the disease persists at stable levels within the population.

For the given parameters, the endemic equilibrium is approximately (0.6009, 0.0744), as shown by the magenta dot in the phase portrait.

![SIR Model Nullclines and Fixed Points. The dashed red and blue lines represent the nullclines for the susceptible and infected populations, respectively. The green and purple dots indicate the disease-free and endemic equilibria.](output/FIX_NULL.png)

### Stability Analysis

Our stability analysis revolves around the eigenvalues of the Jacobian matrix at each equilibrium point. The eigenvalues tell us about the nature of these points:
- At the Disease-Free Equilibrium, we have mixed eigenvalues: one negative, indicating attraction, and one positive, suggesting that any introduction of the infection could lead to an epidemic since this point is unstable.
- Conversely, the Endemic Equilibrium has complex eigenvalues with negative real parts, confirming stability. This implies a tendency towards a steady state where the disease coexists with the population without leading to an outbreak or eradication.

Our model predicts that in the context of the parameters derived from the Canadian COVID-19 data, complete eradication of the disease is unlikely without intervention. Instead, the population tends toward an equilibrium where the disease persists at manageable levels.

#### Eigenvalues Analysis

The stability at the fixed points is analyzed by computing the eigenvalues of the Jacobian matrix at each equilibrium:

- For the disease-free equilibrium, the Jacobian matrix is:

  $$ J = \begin{bmatrix} -\mu & -\beta \\ 0 & \beta - \delta \end{bmatrix} $$

  The eigenvalues at the disease-free equilibrium are: `[-0.01333333, 0.04749398]`.

- For the endemic equilibrium, the Jacobian matrix is:

  $$ J = \begin{bmatrix} -\beta i^* - \mu & -\beta s^* \\ \beta i^* & \beta s^* - \delta \end{bmatrix} $$

  The eigenvalues at the endemic equilibrium are approximately: `[-0.01109474+0.02258672i, -0.01109474-0.02258672i]`.

The presence of a positive eigenvalue at the disease-free equilibrium indicates instability, suggesting that if an infection is introduced into the population, it will grow. The complex eigenvalues with negative real parts at the endemic equilibrium suggest a stable spiral point.

## Phase Portrait

Moving forward in our exploration of the SIR model, we now focus on the phase portrait which encapsulates the flow of the epidemic through the susceptible and infected populations.

![Phase portrait of the SIR model.](output/PHASE_PORTRAIT.png)

As illustrated in the phase portrait, the dynamic interplay between susceptible and infected populations is captured.

Key Points of the Phase Portrait:
- Unstable Disease-Free Equilibrium: The green dot at the bottom right corner, where 100% of the population is susceptible and none are infected, is an equilibrium point. However, the flow lines diverge from this point, indicating instability. This suggests that any introduction of the disease into the population is likely to grow rather than die out, necessitating active measures to control the spread.
- Stable Endemic Equilibrium: The magenta dot represents a point where the disease persists in the population at a stable level. The inward spiraling of flow lines towards this point highlights its stability. This means that once the disease spreads in the population, it's likely to settle at a constant level without overwhelming the healthcare system.
- Inevitable Endemic State: The trajectories in the phase portrait all lead towards the endemic equilibrium. This indicates that, given the current parameters, the disease is expected to become a constant feature of the population's health landscape.

The phase portrait thus offers a valuable visual aid in understanding the potential outcomes of the epidemic's spread. By mapping the possible trajectories of the disease, we can better anticipate and prepare for its impact on the population.


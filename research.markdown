---
layout: page
title: Research
permalink: /Research/
---

<center><strong><em>My research uses modeling and simulation to improve complex engineering systems, with a growing focus on integrating sensing and autonomy-enhancing technologies into engineering system operations and their decision-making processes.</em></strong></center>
<center><strong><em>This page lists and discusses contributions in selected research areas.</em></strong></center>

<br>

<div style="background-color: #d4d4d4; padding: 20px; border-radius: 8px;">
<h1 style="text-align: center; font-weight: bold; text-decoration: underline;">Research Activities</h1>
</div>

<br>


<style>
  details summary {
    list-style: none;
  }
  details summary::-webkit-details-marker {
    display: none;
  }
  details > summary::after {
    content: '▶';
    font-size: 1rem;
    margin-left: 10px;
    color: darkblue;
  }
  details[open] > summary::after {
    content: '▼';
  }
</style>



<details>
  <summary style="display: flex; align-items: center;">
    <h1 style="display: block; border-bottom: 1px solid darkblue; margin: 0; flex: 1;">Modeling and Simulation of Production Systems and Condition-based Maintenance</h1>
  </summary>
    <div style="background-color: #e4e4f7; margin-top: 10px; padding: 4px; border-radius: 8px; width:96%;">
         <p>Manufacturing maintenance can be viewed as a support system that increases the availability of factory floor equipment (e.g., machines, workstations, material handling devices), and its importance is highlighted by the fact that it accounts for 15-70% of the cost of produced goods. The adoption of condition-based maintenance, via digital technologies that enable and expand condition monitoring, can vastly benefit manufacturing performance. As depicted below (with manufacturing image from <a href="https://www.pesmedia.com/nissan-sunderland-new-juke-upgrading-manufacturing-final-assembly">https://www.pesmedia.com/nissan-sunderland-new-juke-upgrading-manufacturing-final-assembly</a>), these condition monitoring technologies (also known as condition monitoring systems, or CMSs) can perform anomaly detection, fault diagnosis, or failure prognosis to mitigate the risk of production process failures and product defects.</p>
        <center><img src="/assets/images/cms_manufacturing_example_V2.png" alt="Condition monitoring in a manufacturing system" style="width: 500px; margin-bottom: 13px;"/></center>
        <p> However, the adoption of these technologies requires strict investment justification, as their value derives from failures and risks that do not occur and often their AI/ML-based internal logic is obfuscated and does not result in easily predictable impacts. This research effort identified discrete-event simulation as a testbed for condition monitoring-enabled maintenance policies on manufacturing performance, with the aim that evaluation procedures can be developed to leverage simulation towards increasing confidence in condition monitoring tool investments. Simulation can rapidly model manufacturing system configurations, maintenance policies, and monitoring algorithms without disrupting actual factory floor operations. Furthermore, simulation can be used to compare manufacturing scenarios by various performance measures, from algorithm-level metrics such as detection true positive rates to manufacutring-level metrics such as production throughput.</p>
        <center><img src="/assets/images/simprocesd_entities.png" alt="SimPROCESD model entities" style="width: 500px; margin-bottom: 13px;"/></center>
        <p>This reseach developed <a href="https://github.com/usnistgov/simprocesd">SimPROCESD</a>, or Simulated-Production Resource for Operations & Conditions Evaluations to Support Decision-making, an open-source and python-based manufacturing discrete-event simulator. This software models the interactions between production system assets, maintenance personnel and policies, and condition monitoring tools and algorithms. Each simulation captures the event history log of the modeled manufacturing and maintenance operations. Model entities include devices that can handle parts such as machines and buffers, as well as the parts themselves. Other entities include sensor probes and condition monitoring systems that collect and process manufacturing data in simulation time, as well as maintenance personnel and resource managers that handle maintenance decision-making and operational logistics. All model entities in this simulator are customizable. </p>   
        <center><img src="/assets/images/expanded_sim_study.png" alt="Expanded simulation study of manufacturing configurations and maintenance policies" style="width: 500px; margin-bottom: 13px;"/></center>
        <p>To showcase SimPROCESD's capabilities, an expanded simulation study considered 25 combinations of 5 possible manufacturing configurations of 6 machines and 5 possible maintenance policies, 3 of which used some variation of automated condition monitoring algorithms to detect severe machine degradation. Each machine has an independent health degradation model that follows a stochastic-timed state automata (with finite, discrete health states) that generates a generalized sem-Markov process. Each machine contributes to an incoming part's quality indicator, but this contribution is proportional to the machine's current health status. Furthermore, maintenance model parameters such as time-to-repair, inspection frequency, and condition monitoring alert thresholds are specified. Given these modeling decisions, the expanded study selects key performance indicators to compare the 25 scenarios on manufacturing outcomes, maintenance results, and, when applicable, condition monitoring detection metrics. </p>
        <center><img src="/assets/images/expanded_sim_results.png" alt="Expanded simulation study's sample results" style="width: 500px; margin-bottom: 13px;"/></center>
    </div>
    <div style="background-color: #e4e4f7; margin-top: 10px; padding: 4px; border-radius: 8px; width:96%;">
        <h4 style="text-align: center; font-weight: bold; text-decoration: underline;">Key References</h4>
        <p style="font-size: 0.75em;">Dadfarnia, Mehdi. "Approaches to Evaluate Condition Monitoring-Based Technologies for Manufacturing Maintenance and Risk Management." PhD diss., University of Maryland, College Park, 2025.</p>
        <p style="font-size: 0.75em;"> Dadfarnia, Mehdi, Michael E. Sharp, Serghei Drozdov, and Jeffrey W. Herrmann. "A simulation-based approach to assess condition monitoring-enabled maintenance in manufacturing." In 2023 7th International Conference on System Reliability and Safety (ICSRS), pp. 413-422. IEEE, 2023.</p>
        <p style="font-size: 0.75em;">Dadfarnia, Mehdi, Michael Sharp, and Timothy Sprock. "Understanding and evaluating naive diagnostics algorithms applicable in multistage manufacturing from a risk management perspective." In International Manufacturing Science and Engineering Conference, vol. 84263, p. V002T07A042. American Society of Mechanical Engineers, 2020.</p>
    </div>
</details>

<br>


<details>
  <summary style="display: flex; align-items: center;">
    <h1 style="display: block; border-bottom: 1px solid darkblue; margin: 0; flex: 1;">Analytically-based Methods for Evaluating Condition Monitoring Impact on Manufacturing</h1>
  </summary>
    <div style="background-color: #e4e4f7; margin-top: 10px; padding: 4px; border-radius: 8px; width:96%;">
        <p> For certain manufacturing systems that operate under condition monitoring-enabled maintenance policies, analytically-based mathematical methods for evaluating their performance can serve as an alternative to simulation-based approaches. Analytical models, once set up, can much more quickly estimate performance measures than simulation, but are limited to performance metrics for which mathematical derivations exist. Furthermore, analytical models comprise of derived equation sets that characterize a state space, and instances with larger state spaces require approximations to calculate performance metric derivations. This research effort modified existing analytical methods for manufacturing performance estimation to account for condition monitoring impacts of condition monitoring-enabled maintenance.</p>
        <p>This research proposed two analytical models for deriving five performance metrics (production rate or throughput, scrap rate, total work-in-process, machine blockage probabilities, and machine starvation probabilities): a condition monitoring-augmented Bernoulli model and a condition monitoring-augmented exponential model. The Bernoulli model characterizes each machine by one of eight independent machine states, each defined by a combination of one of four machine health states (perfect, heavily deteriorated, slightly deteriorated, or down) and one of two condition monitoring states (alert or no alert). Buffer states are characterized by a discrete number of parts. These machine and buffer states are determined at the end of each time slot &tau;. Additionally, part quality is taken into account with probabilities that each machine produces a non-defective part, dependent on the machine health state. Steady-state analysis of this model can be accomplished to derive performance metrics for: (a) serial two-machine systems, (b) serial manufacturing lines with more than two machines, and (c) converging three-machine systems. Steady-state analysis of (b) and (c) each requires their own special recursive algorithms that approximate these production systems to a set of coupled two-machine lines. </p>
        <center><img src="/assets/images/bernoulli_systems.png" alt="Manufacturing system configuration (a), (b) and (c) under analysis with the condition monitoring-augmented Bernoulli model" style="width: 350px; margin-bottom: 13px;"/></center>
        <p>The condition monitoring-augmented exponential model likewise characterizes each machine by one of eight independent machine states from combinations of four machine health states and two condition monitoring alert states. However, the transition rates between the machine states are exponentially distributed (see figure below). Along with the continuous buffer state space, the machine and buffer states form an ergodic, continuous-time mixed-state Markov process. Part quality is also taken into account in a similar manner as the Bernoulli model. Analogous to the Bernoulli model, steady-state analysis of the exponential model can be accomplished to derive performance metrics for: (a) serial two-machine systems, (b) serial manufacturing lines with more than two machines, and (c) converging three-machine systems.</p>
        <center><img src="/assets/images/exponential_systems.png" alt="Exponential model machine states and transition rates" style="width: 600px; margin-bottom: 13px;"/></center>
        <p>Computational implementation of the exponential model requires solving a system of equations that is only feasible with simplifications that involve discretizing the continuous-flow buffer states. In an empirical study, this research estimated performance metrics for the same set of manufacturing systems using exponential model implementations, discrete-event simulation (SimPROCESD) implementations that mimic exponential model parameters, and Bernoulli model implementations. Insights from this comparative study include: the Bernoulli model suffers from not taking into account time-to-repair, discretization may have caused loss of probability information in the exponential model, and simulator implementations of the exponential model require careful selection of exponential transition rates to match intended machine availabilities. Moreover, while the Bernoulli model required the least modeling effort and quickly produced rough performance estimates, the exponential model implementation required by far the most computational power, modeling effort, and mathematical acumen. </p>
    </div>
    <div style="background-color: #e4e4f7; margin-top: 10px; padding: 4px; border-radius: 8px; width:96%;">
        <h4 style="text-align: center; font-weight: bold; text-decoration: underline;">Key References</h4>
        <p style="font-size: 0.75em;">Dadfarnia, Mehdi. "Approaches to Evaluate Condition Monitoring-Based Technologies for Manufacturing Maintenance and Risk Management." PhD diss., University of Maryland, College Park, 2025.</p>
        <p style="font-size: 0.75em;">Dadfarnia, Mehdi, Michael E. Sharp, and Jeffrey W. Herrmann. "Comprehensive evaluations of condition monitoring-based technologies in industrial maintenance: A systematic review." Journal of Manufacturing Systems 82 (2025): 449-477.</p>
    </div>
</details>


<br>

<details>
  <summary style="display: flex; align-items: center;">
    <h1 style="display: block; border-bottom: 1px solid darkblue; margin: 0; flex: 1;">Evaluation Process and Investment Analysis for Adopting Condition Monitoring Technologies</h1>
  </summary>
    <div style="background-color: #e4e4f7; margin-top: 10px; padding: 4px; border-radius: 8px; width:96%;">
        <p> The adoption of condition monitoring technologies for manufacturing maintenance requires strict investment justification, as their value derives from defective products and machine downtime that do not occur, and the impact of these technologies on a manufacturing system is not easily predictable prior to their adoption. Investment justification can result from a comprehensive evaluation process or framework that takes into account the interplay between a manufacturing system's operations, maintenance, and condition monitoring integration. This research effort included a literature survey of condition monitoring-enabled maintenance evaluation processes to better understand the evaluation techniques, performance measures, and investment analyses that could justify the use of monitoring-based technologies in industrial maintenance. Key findings from the survey include insufficient sensitivity analyses of evaluation parameters, misleading use of performance metrics, a lack of uncertainty quantification in cost-benefit calculations, and a failure to frame investment outcomes in terms of the time value of money.
        <center><img src="/assets/images/evaluation_data_items.png" alt="Conceptual model for condition monitoring-enabled maintenance evaluation, and relevant data items" style="width: 600px; margin-bottom: 13px;"/></center>
        Alongside the findings from the literature survey, this research effort also facilitated the development of a systematic evaluation process that aligns the monitoring, maintenance, and manufacturing performance analyses to condition monitoring system (CMS) investment analysis. A conceptual process was developed to contextualize the impact of a CMS within the maintenance and manufacturing operations that it is being deployed in. Each configuration of a manufacturing system, maintenance policy, and CMS model can form a scenario for which both various performance metrics can be generated and a CMS investment analysis can be conducted. This evaluation process allows for the use of cost-benefit analysis as a basis to compare different condition monitoring tools within the same CMS-enabled maintenance policy as well as to compare different maintenance policies.
        <center><img src="/assets/images/conceptualEvaluationProcess.png" alt="Conceptual CMS evaluation process" style="width: 500px; margin-bottom: 13px;"/></center> 
        This research effort also prescribed a five-step procedure for the economic analysis of CMS investments. This procedure combines risk analysis of maintenance in a manufacturing system, performance analysis of condition monitoring capabilities, and investment analysis that captures the time-value of the costs and benefits of CMS integration. This work also applied the prescribed procedure to several case studies to demonstrate the value that CMS-enabled maintenance can bring to a manufacturing system.
        </p>
        <center><img src="/assets/images/evaluation_procedure_example.png" alt="Evaluation procedure example" style="width: 500px; margin-bottom: 13px;"/></center> 
    </div>
    <div style="background-color: #e4e4f7; margin-top: 10px; padding: 4px; border-radius: 8px; width:96%;">
        <h4 style="text-align: center; font-weight: bold; text-decoration: underline;">Key References</h4>
        <p style="font-size: 0.75em;">Dadfarnia, Mehdi. "Approaches to Evaluate Condition Monitoring-Based Technologies for Manufacturing Maintenance and Risk Management." PhD diss., University of Maryland, College Park, 2025.</p>
        <p style="font-size: 0.75em;">Dadfarnia, Mehdi, Michael E. Sharp, and Jeffrey W. Herrmann. "Comprehensive evaluations of condition monitoring-based technologies in industrial maintenance: A systematic review." Journal of Manufacturing Systems 82 (2025): 449-477.</p>
        <p style="font-size: 0.75em;">Dadfarnia, Mehdi, and Michael Sharp. "Key elements to contextualize ai-driven condition monitoring systems towards their risk-based evaluation." In 2022 5th International Conference on Artificial Intelligence for Industries (AI4I), pp. 38-41. IEEE, 2022.</p>
        <p style="font-size: 0.75em;">Sharp, Michael, Mehdi Dadfarnia, Timothy Sprock, and Douglas Thomas. "Procedural guide for system-level impact evaluation of industrial artificial intelligence-driven technologies: Application to risk-based investment analysis for condition monitoring systems in manufacturing." Journal of manufacturing science and engineering 144, no. 7 (2022): 071008.</p>
    </div>
</details>


<br>

<details>
  <summary style="display: flex; align-items: center;">
    <h1 style="display: block; border-bottom: 1px solid darkblue; margin: 0; flex: 1;">Physics-based Simulation from Systems Models</h1>
  </summary>
    <div style="background-color: #e4e4f7; margin-top: 10px; padding: 4px; border-radius: 8px; width:96%;">
        <p> Systems modeling languages are capable of capturing requirements, functional behaviors, and physical architecture relationships of a complex engineering system. In contrast, engineering simulation languages and numeric computing environments allow for equation-based execution of engineering system dynamics. This work focused on developing solutions to conduct seamless model interoperability between systems engineers or project managers using systems modeling languages and domain-specialized engineers focused on developing equation-based simulation models.</p>
        <center><img src="/assets/images/sysml_simulation_v2.png" alt="Translating from SysML model to simulation language" style="width: 500px; margin-bottom: 13px;"/></center>
        <p> This work developed SysPhS, the systems modeling language (SysML) extension for physical interactions and signal flow simulation. SysPhS exploited the overlaps and gaps of the modeling constructs between SysML and commonly-used simulation languages. Allowing for the modeling of physical interactions and signal flows in SysML, SysPhS directly translates SysML models to executable simulation models. As part of this team effort, my contributions focused on developing methods to trace and verify mathematical model constructs in SysML as well as creating a corpus of use cases and tutorials for SysPhS across various domains.</p>
        <center><img src="/assets/images/extended_sysml.png" alt="Extended SysML constructs in SysPhS" style="width: 420px; margin-bottom: 13px;"/></center>
    </div>
    <div style="background-color: #e4e4f7; margin-top: 10px; padding: 4px; border-radius: 8px; width:96%;">
        <h4 style="text-align: center; font-weight: bold; text-decoration: underline;">Key References</h4>
        <p style="font-size: 0.75em;">Dadfarnia, Mehdi, and Raphael Barbau. "Platform-Independent Debugging of Physical Interaction and Signal Flow Models." In SysCon, pp. 1-8. 2019.</p>
        <p style="font-size: 0.75em;">Barbau, Raphael, Conrad Bock, and Mehdi Dadfarnia. "Translator from extended SysML to physical interaction and signal flow simulation platforms." Journal of Research of the National Institute of Standards and Technology 124 (2019): 1.</p>
        <p style="font-size: 0.75em;">Bock, Conrad, Raphael Barbau, Ion Matei, and Mehdi Dadfarnia. "An extension of the systems modeling language for physical interaction and signal flow simulation." Systems Engineering 20, no. 5 (2017): 395-431.</p>
        <p style="font-size: 0.75em;">Dadfarnia, Mehdi, Conrad Bock, and Raphael Barbau. "An improved method of physical interaction and signal flow modeling for systems engineering." In Conference on Systems Engineering Research (CSER 2016). Available at https://www. nist. gov/publications/improved-method-physical-interaction-and-signal-flow-modeling-systems-engineering. 2016.
        </p>
    </div>
</details>

<br>

<details>
  <summary style="display: flex; align-items: center;">
    <h1 style="display: block; border-bottom: 1px solid darkblue; margin: 0; flex: 1;">Modeling and Simulation of Energy-harvesting Microgenerators</h1>
  </summary>
    <div style="background-color: #e4e4f7; margin-top: 10px; padding: 4px; border-radius: 8px; width:96%;">
        <p>Wearable wireless sensors are attractive monitoring solutions in healthcare settings, as they allow clinicians to capture a patient's vitals for more accurate diagnosis and prognosis. However, such sensors are often powered by small batteries that may require frequent recharging. To address this limitation, this research explored energy harvesting methods that draw energy from the ambient environment to prolong the battery lifetime of these sensors. In particular, this work focused on modeling and characterizing kinetic energy harvested from human body motion.</p> 
        <p>Harvesting kinetic energy requires a motion-driven microgenerator to convert mechanical work into raw electrical energy, which is then conditioned into a steady DC output for the sensor load via power-processing circuitry. The following, from <a href="https://doi.org/10.1016/j.sna.2004.04.026">doi.org/10.1016/j.sna.2004.04.026</a>, portrays a generic model of a motion-driven microgenerator:</p>        
        <center><img src="/assets/images/generic_msd.png" alt="Generic motion-driven microgenerator" style="width: 350px; margin-bottom: 13px;"/></center>
        <p>where the mass, spring stiffness, energy-extracting damping force, and internal displacement are represented by <em>m</em>, <em>k</em>, <em>f</em>, and <em>z</em>, respectively. To best suit highly variable and infrequent motion of sensors and energy harvesters attached to arms and legs, the energy-extracting damping mechanism uses electrostatic transduction via a Coulomb-force parametric generator (CFPG) architecture. The damping force in electrostatic transduction is set by the electric field between the two capacitor plates on each side of the mass <em>m</em>, and this force can be optimized by controlling the input voltage source to the capacitor. With the CFPG architecture, the damping force <em>f</em> is constant and the spring constant <em>k</em> is zero. </p> 
        <p>Typically, the mass is attached to a moving capacitor plate that moves with respect to a fixed capacitor plate. When the gap between the two plates is at the minimum, the plates are pre-charged with low voltage from the input source, resulting in high capacitance (see '1-2' in the diagram below, from <a href="doi.org/10.1177/002029400804100404">doi.org/10.1177/002029400804100404</a>). As the external kinetic force from human motion exceeds the electrostatic damping force, the moving plate (and mass) breaks away and increases the gap between the capacitor plates. During this phase, the voltage source is disconnected, keeping the charge on the plates constant while increasing voltage and decreasing capacitance (2-3). At the maximum possible gap, the voltage is at its highest and the capacitor discharges into the power-processing circuity (3-1). </p>
        <center><img src="/assets/images/qv_diagram.png" alt="QV diagram of energy generation" style="width: 350px; margin-bottom: 13px;"/></center>
        <p>The electrostatic damping force must be less than the external kinetic force from human motion for the mass to break away from the capacitor plate. Optimal energy capture therefore occurs when the mass moves during the peak of the kinetic force. To study the optimality of the damping force, we developed a Simulink model that captures the mass-spring-damper dynamics of the CFPG architecture as well as its resulting instantaneous generated power.</p>
        <center><img src="/assets/images/simulink_CFPG.png" alt="Simulink model of CFPG microgenerator" style="width: 350px; margin-bottom: 13px;"/></center>
        <p>Using the Simulink model, we analyzed optimal damping forces that maximize energy output for distinct sinusoidal acceleration inputs, each characterized by a different combination of amplitude and frequency. Having established that an optimal damping force exists based on the input's characteristics, we studied the potential harvested power from an extensive database of human arm and leg movement acceleration traces. We then devised an optimization procedure to identify the optimal damping force across the acceleration trace dataset for several fixed-time intervals over which the damping force is assumed constant. This procedure enabled a preliminary study of near-real-time tuning of the damping force.</p>
        <center><img src="/assets/images/cfpg_sine_outputs.png" alt="Optimal value of electrostatic force and maximized harvested power for artificially-generated sinusoidal acceleration inputs." style="width: 500px; margin-bottom: 13px;"/></center>
    </div>
    <div style="background-color: #e4e4f7; margin-top: 10px; padding: 4px; border-radius: 8px; width:96%;">
        <h4 style="text-align: center; font-weight: bold; text-decoration: underline;">Key References</h4>
        <p style="font-size: 0.75em;"> Dadfarnia, Mehdi. "Energy harvesting microgenerators for body sensor networks." Master's thesis, University of Maryland, College Park, 2014.</p>
        <p style="font-size: 0.75em;">Dadfarnia, Mehdi, Kamran Sayrafian, Paul Mitcheson, and John S. Baras. "Maximizing output power of a CFPG micro energy-harvester for wearable medical sensors." In 2014 4th International Conference on Wireless Mobile Communication and Healthcare-Transforming Healthcare Through Innovations in Mobile and Wireless Technologies (MOBIHEALTH), pp. 218-221. IEEE, 2014.</p>
    </div>
</details>





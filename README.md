# Multisensory-Integration
A minimal spiking LIF neuron model demonstrating super-additive, additive, and sub-additive responses emerging from threshold and refractory period dynamics alone.


## Background
Multisensory integration is a phenomenon where a neural circuit receives input from more than one modality and integrates 
them in a way that the resultant response differs from the linear combination of the modalities. For example, the superior colliculus receives input from visual and auditory modalities. The neurons present in the superior colliculus integrate the incoming input in such a way that it results in super-additivity (when the response is more than the linear sum), additivity (when the response is somewhat equal to the linear sum) or sub-additivity (when the response is less than the linear sum). 
The project demonstrates that a single LIF neuron can show the three different regimes as intensity of the input varies without hardcoding an integration mechanism. That is, threshold nonlinearity and refractory period alone are sufficient to produce super-additive, additive, and sub-additive responses.

## Model
The equation, `dv/dt = (-(v-V_rest))/tau` was used.
the enhancement index is calculated as `(AV - (A+V))/(A+V))`

parameters used in the model: 
- tau = 10ms, V_rest = -75mV, V_thresh = -40mV, V_reset = -75mV
- Refractory period: 5ms
- 50 independent Poisson inputs per modality, synaptic weight = 3mV per spike
- N = 20 neurons per condition, spike rates averaged across neurons
  
Each neuron receives two kinds of Poisson inputs (auditory and visual), with 50 independent poisson sources per modality. After each spike v is set back to V_reset and the neuron is not able to fire another spike until the refractory period is up. Each incoming spike adds 3mV directly to v. There are three conditions - A only (no visual input), V only (no auditory input), and AV (both auditory and visual inputs are present). Each run at matched input rates across a sweep of 5-30Hz.

## Results
- The first plot shows the input rate of the Poisson input as the X-axis and the output firing rate of the neurons as the Y-axis. Three different results are plotted (A only, V only and AV) along with linear sum of A and V. AV output increases with input rate, but grows more slowly than the linear sum (A+V) at high rates, eventually falling below it.
- The second plot shows the computed enhancement index (which measures how much the output is enhanced as opposed to the inputs) as the Y-axis and the input rates as the X-axis. The enhancement index starts as positive, demonstrating super-additivity, crosses zero demonstrating additivity and finally becomes negative showing sub-additivity.
  
Note: the enhancement index plot uses a symlog scale to show both the large super-additive values at low rates and the small sub-additive values at high rates on the same axis without either dominating.  

## Limitations
- Parameter dependence. The crossover point between regimes (where the enhancement index crosses zero) is parameter-dependent, therefore, changing tau, weight, V_thresh, or N_sources will shift where each regime appears.
- The model uses one neuron to explain the multisensory integration instead of a whole circuit, simplifying the phenomenon.
- The total number of neurons N = 20 is averaged to present results of one neuron over 20 trials.
- The A and V inputs are assumed to come from a poisson distribution. Real auditory and visual spike trains are not purely Poisson. They have temporal structure that is not captured here.

## Requirements
pip install brian2 numpy matplotlib

## How to Run
The script was written in Google Colab. Open `multisensory_snn.ipynb` in Google Colab or Jupyter and run all cells in order.

License: MIT

## Background
Multisensory integration is a phenomenon where a neural circuit receives input from more than one modality and integrates 
them in a way that the resultant response differs from the linear combination of the modalities. For example, the superior colliculus recieves input from visual and auditory modalities. The neurons present 
in the superior colliculus integrates the incoming input in such a way that it results in super-additivity(when the response is 
more than the linear sum), additivity (when the response is somewhat equal to the linear sum) or sub-additivity (when the
response is less than the linear sum).
The model is a minimal spiking LIF neuron which receives two poisson inputs- A and V. The neuron integrates the inputs and 
produces a response. for each response an enhancement index is computed. the output is then plotted against input firing rates. 
the model shows three kinds of responses by the neuron- super-additivity, additivity and subadditivity, which can be seen by decresing
enhancement index as firing rates increase.

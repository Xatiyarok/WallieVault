### Trade-offs
Rail to rail op amps - nmosfet to pmosfet transition generates noise due to the switch when going from V- to V+. This is due to offset voltage coming from inputs (Vos).

This make output to be V = G[((V+)-(V-))Vos]

Vcm = voltage on the inputs can't go over or below V- to V+ for single input. Rail to rail input

Same behaviour  goes for output voltage.

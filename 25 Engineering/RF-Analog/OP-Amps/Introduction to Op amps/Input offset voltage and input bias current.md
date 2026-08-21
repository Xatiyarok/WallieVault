### Vos and Ib - Specifications


Input Offset Voltage (Vos) - FET
Input Bias Current (Ib) - BJT and FET

Vos = diffferential input voltage that have to be applied to force op amps output to zero volts. 

- Offset is made by mismatch of the transistors in the differential input pair. 

why laser trimming Ros helps to reduce Vos?
R. 

Drift slope Vosi- changes with temperature - important for calibrated systems  (slope) (dVos/dT)

- Vosi = Vosi_room + Vosi_drift(T-25C) <- this the complete offset expected on op amp


Input bias current - current flowing into the inputs of the op-amp. In reality this currents are not equal
Input bias offset - difference between inputs currents. If its low, it's possible to match the impedances connected to each input and cancel the offset developed from Ib
Input bias drift - changes with temperature (slope) (dIb/dT)

Overall input error
Verror (T) = Vos(T) + Vib (T)


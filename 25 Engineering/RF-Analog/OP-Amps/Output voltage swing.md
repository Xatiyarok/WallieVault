This parameter defines how close the op-amp output can be driven rail to rail. This is related to [[Op amp voltage ranges & rail to rail inputs]]

The key to comparing voltage output swing specifications is to determine the amount of current that the amplifier is sinking or sourcing. *The smaller the output short circuit current, the closer the amplifier will swing to rail* - Output is dependent on the op output stage design and the load current.

![[Pasted image 20260820214430.png]]

The [[Input Voltage Range]] restrictions are critical in op-amp circuit applications. In a [[Closed Loop Gain]] configuration, using a voltage beyond the input voltage range sometimes looks like an output limit problem, but it's in fact an input range problem
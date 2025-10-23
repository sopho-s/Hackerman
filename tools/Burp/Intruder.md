Intruder is a built in fuzzing tool that is used for automated request modification and repetitive testing with variations in input values
# Positions
Positions inform intruder about the location where the payload will be introduced, which can be indicated by the `§` symbol
# Attack Types
## Sniper
the sniper attack is the default and most common attack type, it is particularly effective for single-position attacks, such as password brute-force or fuzzing API endpoints
## Battering ram
battering ram attack places the same payload into every position simultaneously rather than substituting each payload into each position in turn
## Pitchfork
pitchfork attack is an attack that is similar to having multiple snipers running simultaneously. Pitchfork utilises one payload set per position and iterates through them all simultaneously
## Cluster bomb
Cluster bomb is similar to pitch fork but it will go through every combination of each payload

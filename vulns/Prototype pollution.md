Prototypes are just parts of objects that used to define what functions and attributes the object has, this can be manipulated by overwriting stuff in the prototype to run malicious code
it seems rather confusing but essentially its just trying to define your own values and overwrite defined values of an object kinda, but because its done on prototype its done across all entities of that type
# How to find
- Input fuzzing and manipulation can help look for scenarios where entrusted data can lead to prototype pollution
- Context analysis and payload injection can help find areas where pollution is possible
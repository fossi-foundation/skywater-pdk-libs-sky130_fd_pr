These files have been automatically generated using [SpiceArmyKnife.jl](https://github.com/NyanCAD/Cadnip.jl/tree/main/SpiceArmyKnife.jl)

```
spak-convert combined_models/sky130.lib.spice vacask/combined_models/sky130.lib.spice --input-simulator ngspice --output-simulator vacask
```

and smoke tested using
```
test

load "spice/resistor.osdi"
load "spice/capacitor.osdi"
load "spice/diode.osdi"
load "spice/bsim4v8.osdi"

model vsource vsource

include "/path/to/skywater-pdk-libs-sky130_fd_pr/vacask/combined_models/sky130.lib.spice" section=tt

ground 0 
v1 (1 0) vsource dc=1.0
M1 (1 1 0 0) sky130_fd_pr__nfet_01v8 l=0.16 w=0.9

control
    options scale=1e-6
   analysis op1 op
endc

```

resulting in
```
Simulating: test
Running analysis 'op1'.
  |============ 100% ============| 0.000222s
```

It's extremely lightly tested so far

# Validation of 'steam_plant'

## Variables
Weighted-root-mean-square norm with RelTol = 1e-3 and AbsTol = 1e-3, where
AbsTol is based on max. magnitude of reference values.

```
WRMS(tempc@tpf_st_chamber) = 10.7936719373
WRMS(press@tpf_st_chamber) = 16.8507792622
WRMS(out2@division) = 1.71476352752
WRMS(tau@tpf_st_chamber) = 1.65351537626
WRMS(dm2@tpf_pump) = 7.94772603419
WRMS(torque@expseu_) = 17.8508032688
```

## MasterSim project file

Below is the project file that was used to successfully simulation the test case.
Mind: project file is copied from working directory, hence relative path to fmu file.

```

tStart                   0.000000 s
tEnd                     100.000000 s
hMax                     30 min
hMin                     1e-6 s
hFallBackLimit           0.001 s
hStart                   1.000000 s
hOutputMin               1.000000 s
adjustStepSize           no
absTol                   1e-06
relTol                   0.000010
MasterMode               GAUSS_JACOBI
ErrorControlMode         NONE
maxIterations            1
writeInternalVariables   yes

simulator 0 0 slave1 #ffff8c00 "../../fmi-cross-check/fmus/1.0/cs/linux64/AMESim/13SL3/steam_plant/steam_plant.fmu"
simulator 0 0 in_csv #ff0000ff "steam_plant_in.csv"

graph in_csv.heat@expseu_ slave1.heat@expseu_
graph in_csv.speed@expseu_ slave1.speed@expseu_

```


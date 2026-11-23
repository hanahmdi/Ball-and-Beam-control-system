# Validation and Reproducibility Notes

## What has been directly inspected

- All seven `.slx` archives are present and contain Simulink model data.
- The original MATLAB script contains arrays `A`, `B`, `C`, and `D`.
- Screenshots depict linear, nonlinear, and Multibody simulation experiments, as well as PID variants.
- Six videos were supplied: three physical-hardware recordings and three simulation recordings.
- The source report and screenshots show sensitivity to tuning in the linear and nonlinear PID trials and a more favorable qualitative Multibody response.

## Recommended validation before quantitative closed-loop claims

- [ ] Confirm the MATLAB/Simulink version and all required toolboxes.
- [ ] Resolve `D = [0 0 1 0]`: with `C` of size 1×4 and `B` of size 4×1, feedthrough `D` must be 1×1 in the basic state-space form.
- [ ] Verify that the linear dynamics and nonlinear equations use consistent physical parameters.
- [ ] Confirm the beam length; the supplied reporting uses inconsistent values.
- [ ] Identify model-local or base-workspace dependencies and bundle permitted files.
- [ ] Run each original model and record initial conditions, solver and run duration.
- [ ] Compare outputs using matched inputs and units and compute numerical performance metrics.
- [ ] Confirm the servo/sensor wiring and actual hardware pin assignments against the assembly.
- [ ] Add source Arduino firmware only after retrieving and verifying its original implementation.
- [ ] Quantify sensor errors and actuator limits; never claim reliable balancing from video alone.
- [ ] Credit any collaborators and reused third-party material, if applicable.

## Interpretation of observed behavior

A representative screenshot or short video establishes that an experiment was recorded. It does **not** establish reliable tracking, repeatability, or validation across varying initial ball positions. A control strategy should be evaluated using measured trajectories, position setpoints, settling time, overshoot, failure rate and hardware safety conditions.

## Hardware precautions

An unsecured rolling ball, high-torque servo or moving linkage can create a pinch or projectile hazard. Supervise testing, limit servo commands and secure the mechanism before enabling a controller.

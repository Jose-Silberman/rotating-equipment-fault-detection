# Industrial Asset Context

## Asset Description
The selected asset is a **water injection centrifugal pump** operating in upstream oil & gas water injection plants. These pumps inject treated formation water into injection wells in order to maintain reservoir pressure and support production.

Typical operating ranges are:
- **Discharge pressure:** 80 to 350 kg/cm²  
- **Flow rate:** 400 to 2400 m³/day  

A typical equipment train consists of:
- Electric motor (from ~400–500 hp up to >2000 hp)
- Speed increaser (gearbox), when required
- Centrifugal pump

Depending on the pump model and application, the equipment may include:
- Mechanical seal system (according to API seal plans)
- Lubrication system
- Independent seal flush or seal water system, subject to availability and design

---

## Instrumentation and Measurements

The typical instrumentation and sensing configuration includes:

### Process Instrumentation
- Suction pressure
- Discharge pressure
- Individual flow meters per pump
- Temperature sensors on:
  - Cooling circuits
  - Pump casing and/or bearings, depending on design

### Vibration and Mechanical Condition Monitoring
- For smaller units, vibration protection may rely on vibration switches
- For critical or larger units, **accelerometers are preferred**

Measured vibration directions:
- Axial
- Radial

A recommended accelerometer configuration includes:
- One longitudinal and one transverse sensor on the non-drive end of the motor
- Transverse sensors on each bearing of the pump–motor assembly

If the equipment uses **journal bearings (sleeve bearings)** instead of rolling bearings:
- **Proximity probes (proximitors)** should be used
- One probe per bearing to be monitored

For trains composed of pump, gearbox, and motor:
- Dual axial sensors are recommended, one per shaft train

---

## Operating Environment

Water injection pumps typically operate under demanding industrial conditions, including:

- Continuous or semi-continuous operation
- Significant **seasonal thermal amplitude** between winter and summer
- Automatic trips initiated by the control system, such as:
  - High discharge pressure
  - Low recirculation flow
  - Other protective interlocks

Flow and pressure are not purely driven by production variability, but by:
- Injection pressure setpoints
- Hydraulic conditions between the pump and the injection wells
- Automatic control loops, typically including:
  - Pressure and/or flow control loops
  - Control valves
  - Variable frequency drives (VFDs) acting on the motor, when applicable

Future integration of ML-based condition monitoring outputs as advisory or protective signals is considered conceptually, but remains out of scope for the initial implementation.

---

## Operational Criticality

Water injection pumps are **critical assets** in upstream operations. Failures may lead to:
- Loss of injection capacity
- Reservoir pressure decline
- Production impact
- Increased maintenance costs
- Potential safety and environmental risks

Early detection of abnormal operating conditions is therefore essential.

---

## Assumptions

The following assumptions apply to this project:
- The asset is instrumented with **standard industrial instruments and sensors**
- Signals are acquired and managed by a control system (typically PLC-based)
- Historical time series data is available at fixed sampling intervals
- Maintenance events and failures are not perfectly labeled
- The focus is on condition monitoring and early fault detection rather than precise fault classification

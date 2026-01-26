# Process Variables and Instrumentation Signals

## System Overview

Water injection pump systems typically present heterogeneous instrumentation depending on several design and operational factors, including:

- Control strategy (fixed speed vs VFD)
- Active control loops (pressure and/or flow control)
- Number of parallel pumps in operation
- Process configuration (minimum flow recirculation, common headers, etc.)
- Company engineering standards and instrumentation philosophy

For this project, the reference equipment configuration is:

Motor → Speed increaser gearbox → Centrifugal pump

The system includes:
- Minimum flow recirculation line (discharge to suction)
- Auxiliary subsystems (e.g., lubrication skid, seal systems)
- Standard process and protection instrumentation

Not all available signals will necessarily be used for condition monitoring. Signal selection will be refined iteratively during the anomaly detection design phase.

---

## Signal Categories

To keep the architecture realistic and aligned with industrial practice, signals are grouped into the following categories:

### 1. Process Variables (low frequency, continuous)
Used to characterize operating conditions and provide context for equipment behavior.

Typical sampling: 1–10 s

Examples:
- Suction pressure
- Discharge pressure
- Injection flow rate
- Recirculation flow rate (if available)
- Differential pressure (derived)
- Pump casing temperature
- Cooling circuit temperatures

---

### 2. Mechanical Condition Monitoring (high frequency, snapshots)
Used for vibration-based diagnostics and early fault detection.

Primary measurement: acceleration (IEPE accelerometers)

Sampling strategy (project assumption):
- Sampling rate: ~20 kHz
- Bandwidth of interest: up to ~10 kHz
- Snapshot duration: 5–10 s
- Acquisition frequency: periodic or event-triggered

Typical sensor locations:
- Motor non-drive end (radial + axial)
- Motor drive end (radial)
- Gearbox interfaces (radial)
- Pump drive end (radial)
- Pump non-drive end (radial + axial)

Total expected sensors: ~8 accelerometers

Waveforms will be stored for offline processing in the cloud. Feature extraction (FFT, RMS, band energy, kurtosis, etc.) will be performed within the data pipeline rather than at the edge.

---

### 3. Electrical Variables
Provide load and operating state information.

Typical sampling: 1–10 s

Examples:
- Motor current
- Motor power
- Motor speed (VFD frequency)
- Motor status

---

### 4. Control and Operational Signals
Used to identify operating modes and transient events.

Examples:
- Pump running status (on/off)
- Start/stop events
- Trips and interlocks
- Active control mode (pressure/flow/manual)
- Alarm states

---

## Assumptions

- Signals originate from standard industrial instruments and sensors connected to the control system (PLC-based), not directly from SCADA.
- Low-frequency variables are continuously available through the historian.
- High-frequency vibration signals are acquired as periodic snapshots.
- The initial implementation is cloud-first (no edge processing), prioritizing MLOps architecture simplicity over real-time diagnostics.
- Signal selection may evolve as modeling and anomaly detection logic are refined.

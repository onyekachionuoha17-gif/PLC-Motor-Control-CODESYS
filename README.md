# PLC Motor Start/Stop Control — CODESYS Ladder Logic

## Project Overview
This project demonstrates a PLC-based motor start/stop control system built in **CODESYS V3.5** using **Ladder Diagram (LD)**. The control logic includes a standard motor seal-in circuit, stop control, emergency-stop permissive logic, overload protection, and live runtime validation using **CODESYS Control Win V3 x64**.

## Key Features
- Start pushbutton control
- Stop pushbutton control
- Motor seal-in / holding circuit
- Emergency-stop permissive
- Overload permissive
- Motor run coil
- Online monitoring and live testing
- Soft-PLC runtime validation

## Software / Technologies
- CODESYS V3.5 SP22
- CODESYS Control Win V3 x64
- IEC 61131-3 Ladder Diagram (LD)
- Boolean PLC logic
- Online variable monitoring

## PLC Variables

| Variable | Type | Initial Value | Purpose |
|---|---|---:|---|
| `Start_PB` | BOOL | FALSE | Motor start pushbutton |
| `Stop_PB` | BOOL | FALSE | Motor stop pushbutton |
| `E_Stop_OK` | BOOL | TRUE | Emergency-stop permissive |
| `Overload_OK` | BOOL | TRUE | Overload permissive |
| `Motor_Run` | BOOL | FALSE | Motor run command/output |

## Ladder Logic

```text
 E_Stop_OK    Overload_OK     Stop_PB
----| |----------| |-----------|/|---------+----| | Start_PB ----+----( Motor_Run )
                                           |                    |
                                           +----| | Motor_Run ---+
```

Pressing `Start_PB` energizes `Motor_Run`. The parallel `Motor_Run` contact creates the seal-in path so the motor stays energized after Start is released. Pressing Stop, removing `E_Stop_OK`, or removing `Overload_OK` de-energizes the motor.

## Functional Test Results

| Test | Expected Result | Result |
|---|---|---|
| Idle state | `Motor_Run = FALSE` | PASS |
| Start command | `Motor_Run = TRUE` | PASS |
| Release Start | `Motor_Run` stays TRUE | PASS |
| Stop command | `Motor_Run = FALSE` | PASS |
| E-stop permissive removed | `Motor_Run = FALSE` | PASS |
| Overload permissive removed | `Motor_Run = FALSE` | PASS |

## Screenshots

### 1. Complete Ladder Logic
![Complete Ladder Logic](images/01-complete-ladder-logic.png)

### 2. Project / Task Configuration
![Task Configuration](images/02-task-configuration.png)

### 3. Successful Build
![Successful Build](images/03-build-zero-errors.png)

### 4. PLC Runtime Connected
![PLC Runtime Connected](images/04-plc-runtime-connected.png)

### 5. Motor Running Online
![Motor Running](images/05-motor-running.png)

### 6. Seal-In / Latch Test
![Seal-In Test](images/06-seal-in-latch.png)

### 7. E-Stop Safety Test
![E-Stop Safety Test](images/07-estop-safety-test.png)

### 8. Overload Safety Test
![Overload Safety Test](images/08-overload-safety-test.png)

## What I Learned
- PLC scan-cycle based control logic
- Ladder Diagram programming
- Normally open vs. normally closed logic
- Motor starter seal-in circuits
- Safety permissives and overload logic
- PLC task configuration
- CODESYS device communication
- Soft-PLC runtime setup
- Online monitoring and troubleshooting
- Functional verification of control logic

## Troubleshooting Performed
- Configured the Ladder Diagram editor and Toolbox
- Corrected Ladder contact operand errors
- Built a proper parallel seal-in branch
- Assigned `Motor_Control` to `MainTask`
- Resolved Gateway vs. Control Win runtime connectivity
- Started and connected the CODESYS Control Win x64 soft PLC
- Established the active device path
- Configured device-user access
- Verified live variables and wrote test values online

## Possible Future Enhancements
- Motor-running indicator
- Fault indicator
- Fault reset pushbutton
- TON start delay
- Runtime counter
- HMI start/stop interface
- VFD run command and speed reference
- Simulated field I/O
- Auto/manual modes

## Resume Project Entry
**PLC Motor Start/Stop Control — CODESYS**
- Developed and tested a PLC-based motor control application using IEC 61131-3 Ladder Logic in CODESYS.
- Implemented start/stop control, motor seal-in logic, emergency-stop permissive, and overload protection.
- Configured the application task and CODESYS Control Win x64 soft PLC for online simulation and testing.
- Validated normal operation, stop conditions, E-stop response, overload response, and motor latch behavior through live variable monitoring.

## Repository Structure

```text
PLC-Motor-Control-CODESYS/
├── README.md
├── project/
│   └── Motor_Control_Project.project
├── images/
│   ├── 01-complete-ladder-logic.png
│   ├── 02-task-configuration.png
│   ├── 03-build-zero-errors.png
│   ├── 04-plc-runtime-connected.png
│   ├── 05-motor-running.png
│   ├── 06-seal-in-latch.png
│   ├── 07-estop-safety-test.png
│   └── 08-overload-safety-test.png
└── docs/
    └── test-results.md
```

## Author
**Onyekachi Onuoha**

Industrial Automation / Controls / Networking Portfolio

# Functional Test Results

| Test | Inputs / Condition | Expected Output | Result |
|---|---|---|---|
| Idle | E_Stop_OK=TRUE, Overload_OK=TRUE, Stop_PB=FALSE, Start_PB=FALSE | Motor_Run=FALSE | PASS |
| Start | Start_PB=TRUE | Motor_Run=TRUE | PASS |
| Seal-In | Start_PB returned to FALSE after motor starts | Motor_Run remains TRUE | PASS |
| Stop | Stop_PB=TRUE | Motor_Run=FALSE | PASS |
| E-Stop | E_Stop_OK=FALSE | Motor_Run=FALSE | PASS |
| Overload | Overload_OK=FALSE | Motor_Run=FALSE | PASS |

## Validation Summary
All required motor control behaviors were validated online in CODESYS Control Win V3 x64. The seal-in circuit held the motor command after the Start pushbutton was released, and each stop/safety condition de-energized the motor output as expected.

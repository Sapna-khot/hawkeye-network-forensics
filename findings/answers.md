# HawkEye Lab – Question Answers

This file records answers obtained during the investigation. Answers are documented together with the method used to obtain them.

---

## Q1. How many packets does the capture have?

**Answer:** `4003`

### Method

Wireshark → Statistics → Capture File Properties.

### Evidence

The Capture File Properties window showed:

- Captured packets: 4003
- Displayed packets: 4003

![Capture Statistics](../screenshots/01_capture_statistics.png)

---

## Q2. At what time was the first packet captured (UTC)?

**Answer:** `2019-04-10 20:37`

### Method

The first packet timestamp was obtained from Wireshark Capture File Properties. The displayed timestamp was converted from the local timezone to UTC before submitting the answer in CyberDefenders.

### Evidence

Wireshark showed the first captured packet timestamp as:

`2019-04-11 02:07:07`

The corresponding UTC time was calculated and verified through the CyberDefenders lab.

**Status:** Solved

![Capture Statistics](../screenshots/01_capture_statistics.png)

## Q3. What is the duration of the capture?

**Answer:** `01:03:41`

### Method

Wireshark → Statistics → Capture File Properties.

### Evidence

The capture properties showed an elapsed time of:

`01:03:41`

![Capture Statistics](../screenshots/01_capture_statistics.png)

---

## Investigation Status

- Q1 – Solved
- Q2 – Pending verification
- Q3 – Solved

Further questions will be added as they are investigated and verified.

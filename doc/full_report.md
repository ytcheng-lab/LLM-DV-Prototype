# LLM-DV-Prototype: Applying Large Language Models to Digital Design Verification
# 1. Introduction

Hardware verification is one of the most resource-demanding tasks in digital design.
This project explores the use of Large Language Models (LLMs) to assist in RTL verification by automatically generating and refining testbenches in a closed-loop workflow.

- **Prototype DUT**: a simple 1-bit full adder, used purely as a concept demonstration for integrating LLMs with a simulation flow.
- **Case Study DUT**: an actual RV32IM+Zfinx FPU integration task, where I applied the same methodology to address real verification bottlenecks (refer to [case study](case-study-rv32imzfinx.md)).

# 2. System Architecture

<img width="1810" height="1032" alt="LLM_DV_concept" src="https://github.com/user-attachments/assets/3fec5d13-27fc-4305-a02a-dcf104265530" />

Workflow:
1. Use prompt to describe DUT interface, specified pattern format to LLM and request pattern in csv form {input a, input b, input c..., golden output a, ...}
2. Python script read csv file, send input signals to cocotb
3. cocotb run with Icarus Verilog
4. cocotb generate output signal(s)
5. Python script compare output signals with golden
6. Feed back Pass/Fail and coverage to LLM as a prompt
7. LLM generate next pattern with specified format
8. Iterate until coverage reach 100%

# 3. Environment Setup

|Tool/Library|Version|
|------|------|
|Python3|	3.10.12|
|cocotb|	1.9.2|
|google-generativeai	|0.8.4|
|Icarus Verilog	|11.0|

# 4. Prototype Implementation

<img width="1813" height="875" alt="system_structure_demo" src="https://github.com/user-attachments/assets/fb5cd31d-ddfa-4e6f-97c4-e4f1f798e1bb" />

Minimal RTL design used to validate the concept.
Allows fast turnaround for testbench generation and simulation.

Workflow(Demo):
1. Use prompt to describe DUT interface, specified pattern format to LLM and request pattern in csv form {input a, input b, input c, golden output}
2. Python script read csv file, send input signals to cocotb
3. cocotb run with Icarus Verilog
4. cocotb generate output signal(s)
5. Python script compare output signals with golden
6. Print Pass/Fail

# 5. Observations & Analysis

- Rapid boilerplate generation
- Assists in brainstorming corner cases
- Useful for junior engineer onboarding.

# 6. Conclusion

This prototype demonstrates how LLMs can accelerate testbench creation and complement hardware verification workflows.
By validating the flow on a simple full adder, and showing applicability in a real RV32IM+Zfinx case study, the project highlights both conceptual feasibility and practical impact.

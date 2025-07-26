# LLM-DV-Prototype: A Closed-Loop LLM-Driven Verification Flow

## 📌 Summary
**This project explores how Large Language Models (LLMs) can directly participate in digital design verification by generating stimuli, interfacing with Python/Cocotb, and evaluating DUT responses in a closed-loop system.**

## Overview
This repository demonstrates a proof-of-concept for using an LLM (Google Gemini) as part of an automated chip verification loop. A Python script sends a prompt to the Gemini API to generate signal input values, which are fed to a Device Under Test (DUT, e.g., full adder) via the cocotb framework. The simulation results are then collected and compared to expected outcomes.
(overview image tbd)

## Motivation
In traditional RTL verification, creating meaningful test vectors and golden outputs often requires significant manual effort. By embedding an LLM in the loop, this project aims to:
- Reduce test authoring effort.
- Explore the feasibility of AI as a stimulus generator.
- Prototype the future of "AI-assisted digital design flow".

## Technologies Used
- **Google Gemini API** (via `google-generativeai`)
- **Python** scripting (data handling, prompt wrapping)
- **Cocotb** for Python-based HDL simulation
- **Icarus Verilog** as simulation backend

## Repo Structure
- LLM-DV-Prototype/
  - README.md # You are here
- doc/
  - full-report.md # Full flow explanation
  - case-study-rv32imzfinx.md
- run/
  - Makefile # Sim + Gemini driver entry
- src/
  - (tbd: example prompts, source code)

## More Documentation
- [`doc/full-report.md`](doc/full-report.md): Design architecture and how prompts are constructed
- [`doc/case-study-rv32imzfinx.md`](doc/case-study-rv32imzfinx.md): Origin of LLM use during Zfinx verification

## Future Work
- Generalize LLM prompts for more complex instruction sets
- Connect with assertion-based verification frameworks
- Explore alternative LLMs and multi-turn prompting

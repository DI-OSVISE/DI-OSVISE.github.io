---
layout: post
title:  "Intro Chosys project"
date:   2025-08-28
---

In this post, we explore [Chosys](https://github.com/hm-aemy/chosys). A project
which brings together two important tools in the chip design ecosystem.


## Motivation

When you want to create a chip, you have to design it. There are various
languages available in order to describe or generate the design.

One of the most common description language is SystemVerilog.
And a widely used generator language is [Chisel](https://www.chisel-lang.org/).
Chisel is a generator, because the output of it is SystemVerilog, the de facto
standard for all the steps after the design phase.

In the open-source ecosystem, [Yosys](https://github.com/YosysHQ/yosys) is the
tool for synthesis.
When targeting an FPGA or ASIC, the first step is to use Yosys to synthesis your
design.

But now the question is, why do we have to use SystemVerilog as the exchange
format?
This is where we have to look at [CIRCT](https://circt.llvm.org/).


## Chisel and CIRCT

Chisel is a Scala based domain specific language.
It gives the chip designer the required specific hardware additions.
But how does this Scala system produce SystemVerilog?
It uses CIRCT in the backend.

CIRCT is a compiler for the hardware world. It is based on the MLIR framework.
Internally, it uses an Intermediate Representation (IR) to store our design.
The Chisel input is processed by Scala and converted to a specific CIRCT
dialect. Now CIRCT as the compiler, is doing all the transformations and
optimizations required to create an optimal hardware based representation of the
design. In a final stage, the IR is exported to SystemVerilog.

Yosys is also using an Intermediate Representation, called
[RTLIL](https://yosyshq.readthedocs.io/projects/yosys/en/latest/yosys_internals/formats/rtlil_rep.html).

What if we connect CIRCT IR and Yosys IR? Then we could skip SystemVerilog as an
exchange format.


## Connecting CIRCT and Yosys

CIRCT and Yosys use different formats and structures in their IR.
But we can create a dialect in CIRCT to closely match the way Yosys is
representing it.

This is the goal of [Chosys](https://github.com/hm-aemy/chosys).
Here we see a new dialect conveniently named RTLIL.
The challenge now is to convert the CIRCT dialects to the RTLIL dialect.

The advantage we now have with CIRCT is that there is a subset of dialects,
referred to as _core dialects_, which is all that is needed to represent the
hardware of our design.
Those include a dialect for sequential parts, and a dialect for the
combinational parts.
Now we have to create conversion passes for the operations of those dialects in
order to transform the design to the RTLIL dialect.

Once the design is completely represented in the RTLIL dialect, we can go to
Yosys. Here we need to have a new frontend, which takes the MLIR wrapped RTLIL
and converts it to the internal IR.

In the repository you can see a demonstration of this. A CIRCT IR is converted
to RTLIL, exported in the MLIR format, and then imported and processed in Yosys.
To make the demonstration complete, the design is exported to Verilog and
together with a testbench simulated with iverilog.

## Outlook

The first goal is to bring the new RTLIL dialect upstream.
Then the conversion passes need to be extended to fully support the operations
of the core dialects.
Following that, there are a lot of possibilities to explore.
The obvious thing to do is enable the reverse path, from RTLIL back to the core
dialects. This will allow a seamless back and forth, widening the possibilities
of the different frontends and backends of the two tools.

But there is also the task of verification. In CIRCT the verification operations
are not part of the core dialects, but we can extend the flow to transport the
information around. This can then be used for elaborating verification
statements or in a formal verification flow.

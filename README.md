# Python SDK

Python software development kit (SDK) and Jupyter notebooks for working with
OPENQASM and the IBM Quantum Experience (QE).

Related external projects:

- [Python API](https://github.com/IBM/qiskit-api-py)
- [OPENQASM](https://github.com/IBM/qiskit-openqasm)

## Organization

The *scripts* directory contains Jupyter notebooks showing how to use the
[Python API](https://github.com/IBM/qiskit-api-py) with [OPENQASM](https://github.com/IBM/qiskit-openqasm).

*Under development*; There are Jupyter notebooks demonstrating components of
the SDK.

*Under development*; Ismael has refactored the parser on a branch of qx-sdk
but not committed yet. We want to reorganize the SDK so that is has a
comfortable and intuitive interface for developers.

Here is the current organization. The *qiskit_sdk* directory is a Python
module. It contains a *Qasm* module for parsing OPENQASM circuits,
a *QasmInterpreters* module for unrolling to a backend, and a *QasmBackends*
module implementing collections of backend methods. A *CircuitGraph* module
represents, transforms, and computes properties of OPENQASM circuits as
directed acyclic graphs.

Quantum circuits flow through the components as follows. **OPENQASM** source,
as a file or string, is passed into a *QasmParser*, which produces an abstract
syntax tree (**AST**). The **AST** is passed to a *QasmInterpreter* that is
attached to a *QasmBackend*. The *QasmInterpreter* makes calls into the
*QasmBackend* and does whatever that backend is defined to do. The
*BaseBackend* simply prints calls into itself and is useful for debugging
**QASM** circuits. The *CircuitBackend* creates a *CircuitGraph* object that
represents the **OPENQASM** circuit as a directed acyclic graph (**DAG**). The *CircuitGraph* provides methods for working with circuits.

## Setup Python Virtual Enviroment

### Anaconda
To create a new Virtual Enviroment:
> conda create -n QISKitenv python=3 pip

use it:

> source activate QISKitenv

### Install Dependencies

> pip install -r requires.txt

### Dependencies problems.

When you try to install the dependencies "pip install --upgrade IBMQuantumExperience", if you have the next error:

* Cannot remove entries from nonexistent file [PATH]/easy-install.pth

You can fix it using:

> curl https://bootstrap.pypa.io/ez_setup.py -o - | python

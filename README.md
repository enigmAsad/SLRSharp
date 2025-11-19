# SLRSharp

A versatile C# Windows Forms compiler construction tool that implements an SLR (Simple LR) Parser, visualizing the entire compilation process from grammar input to intermediate code generation.

![Build Status](https://img.shields.io/badge/build-passing-brightgreen)
![Platform](https://img.shields.io/badge/platform-windows-blue)
![Framework](https://img.shields.io/badge/.NET-4.7.2-purple)
![License](https://img.shields.io/badge/license-MIT-green)

## Table of Contents

- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Architecture](#architecture)
- [Example Grammars](#example-grammars)
- [Contributing](#contributing)
- [License](#license)

## Features

SLRSharp provides a comprehensive suite of tools for understanding and implementing compiler phases:

- **Grammar Processing**: Accepts custom context-free grammars as input.
- **Automated Set Calculation**: Computes and displays **FIRST** and **FOLLOW** sets for all non-terminals.
- **DFA Visualization**: Generates the SLR Deterministic Finite Automaton (DFA) states and transitions (GOTO).
- **Parse Table Generation**: Automatically constructs the SLR Parsing Table based on the DFA.
- **Lexical Analysis**: Tokenizes input strings based on the provided grammar rules.
- **Step-by-Step Parsing**: Visualizes the parsing process with a detailed trace of the **Stack**, **Input**, and **Action** (Shift/Reduce).
- **Semantic Analysis**: Generates semantic rules (Syntax Directed Definitions).
- **Syntax Tree**: Constructs and displays an annotated syntax tree for the parsed input.
- **Intermediate Code Generation**: Generates Three Address Code (TAC) from the syntax tree.

## Installation

### Prerequisites
- Windows OS
- [Visual Studio](https://visualstudio.microsoft.com/) (2019 or later recommended)
- .NET Framework 4.7.2

### Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/SLRSharp.git
   cd SLRSharp
   ```

2. **Open the Solution**
   - Navigate to the `SLRSharp` directory.
   - Open `SLR_parser.sln` in Visual Studio.

3. **Build and Run**
   - Set the build configuration to `Debug` or `Release`.
   - Press `F5` or click **Start** to build and run the application.

## Usage

1. **Input Grammar**: Enter your context-free grammar in the main input box.
   - Format: `NonTerminal -> Production`
   - Example: `E -> E + T`
2. **Initialize**: Click the initialization button (e.g., "Generate Table") to process the grammar.
   - The application will calculate FIRST/FOLLOW sets, generate the DFA, and populate the Parse Table.
3. **Input String**: Enter the string you want to parse in the input string box.
4. **Parse**: Click the "Parse" button.
   - The application will perform lexical analysis, parse the string, and generate the syntax tree and intermediate code.
5. **Inspect Results**:
   - **Tabs/Panels**: Switch between different views to see the DFA states, Parse Table, Token List, Parse Trace, and Syntax Tree.

## Architecture

The project is structured as a modular Windows Forms application:

```
SLRSharp/
├── SLR_parser/              # Main Source Code
│   ├── Form1.cs             # Main GUI and Event Handling
│   ├── Preprocess.cs        # Grammar processing, FIRST/FOLLOW sets
│   ├── SLR_DFA.cs           # DFA construction and Parse Table generation
│   ├── Lexer.cs             # Lexical Analyzer (Tokenizer)
│   ├── InputParsing.cs      # Core Parsing Logic (Stack operations)
│   ├── SemanticAnalyzer.cs  # Semantic Analysis and SDD generation
│   ├── SyntaxTree.cs        # Annotated Syntax Tree construction
│   ├── ThreeAddrCode.cs     # Intermediate Code Generation (TAC)
│   └── Program.cs           # Application Entry Point
├── Inputs.txt               # Sample grammars and inputs
└── SLR_parser.sln           # Visual Studio Solution File
```

## Example Grammars

You can find sample grammars in `Inputs.txt`. Here is a classic arithmetic expression grammar:

```text
E -> E + T
E -> E - T
E -> T
T -> T * F
T -> T / F
T -> F
F -> ( E )
F -> NUM
NUM -> 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
```

**Input String:** `(5 + 3) * (2 + 1)`

## Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature/AmazingFeature`).
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`).
4. Push to the branch (`git push origin feature/AmazingFeature`).
5. Open a Pull Request.

## License

Distributed under the MIT License. See `LICENSE` for more information.

# Pokedex Persistence & Exception Architecture (Java)

A comprehensive Java OOP application introducing domain-specific exception handling and dual persistence mechanisms (native binary serialization and formatted text I/O persistence) for the Pokedex registry.

## Core Architectural Enhancements
- Custom Exception Framework: Defines `PokemonException` to handle edge cases, state violations, duplicate insertions, missing lookups, and parameter boundaries with specific diagnostic messaging (`bad name: <name>`, `bad name: Empty`, `bad parameter: <parameter>`).
- Binary Serialization (`Serializable`): Integrates standard Java object serialization to serialize entire `Pokedex` graph snapshots to disk and restore runtime state reliably.
- Formatted Text I/O Persistence: Adds dedicated file-based serialization and deserialization routines to `SpecialPokemon`, parsing and writing human-readable key-value formats while managing `IOException` gracefully.
- Boundary & Priority Logic: Resolves validation conflicts deterministically (e.g., prioritizing null names over numeric parameter anomalies during constructor validation).

## Text File Schema Example
Name: Charizard
Type: Fire
Attack: 20
Defense: 30
Health: 40
Special Attack: 50

## File Structure
- PokemonException.java: Domain exception representing name and state parameter validation errors.
- Type.java: Element categorization implementing Comparable and Serializable.
- Pokemon.java: Base Pokemon domain entity with strict exception propagation.
- SpecialPokemon.java: Derived entity supporting constructor-based file ingestion and structured text file export.
- Pokedex.java: Iterable and Serializable container coordinating entities, map storage, and persistence operations.

## Requirements
- Java Development Kit (JDK 8 or higher).

## Build & Run
Compile all Java source files:
javac *.java

Run main execution driver:
java Main

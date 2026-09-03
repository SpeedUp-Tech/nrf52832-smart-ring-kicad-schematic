# Excluded Source-Bundle Assets

The following files were present in the supplied SpeedUp source bundle but are not redistributed in this public repository or Release ZIP because their exact upstream source and redistribution terms were not established from the supplied evidence:

- `Smart_Ring/symbols/*.kicad_sym` — 10 standalone project-local symbol libraries.
- `Smart_Ring/libs/ProjectFootprints.pretty/*.kicad_mod` — 13 standalone project-local footprint files.
- `Smart_Ring/sym-lib-table` — project-local symbol-library table.
- `Smart_Ring/fp-lib-table` — project-local footprint-library table.

The editable `.kicad_sch` files retain embedded symbol definitions and footprint assignment strings as part of the schematic design. Anyone taking the project toward PCB layout must independently verify every symbol, pin mapping, package, land pattern, and applicable upstream license before fabrication.

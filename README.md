# HILForge

A hardware-in-the-loop runner that builds and flashes firmware, controls fixtures, injects failures, captures evidence, and publishes machine-readable results.

## Languages

- Python 3.12+ for orchestration, adapters, fixtures, and reports.
- Shell/PowerShell only for small platform entry points.
- YAML for test manifests and CI workflows.

## Suggested structure

```text
hilforge/
├── hilforge/
│   ├── adapters/        # Serial, SWD, GPIO, CAN, HTTP
│   ├── fixtures/        # DUT and rig descriptions
│   ├── orchestration/   # Flash/reset/stimulate/observe lifecycle
│   ├── reporting/       # JUnit, logs, metrics, artifacts
│   └── simulation/      # Fake adapters for CI
├── schemas/             # Versioned test-manifest schemas
├── tests/
├── examples/
├── .gitignore
├── ARCHITECTURE.md
├── pyproject.toml
└── README.md
```

## Potential libraries and packages

- pytest and pytest-xdist
- pyserial
- python-can and cantools
- pyOCD and/or OpenOCD command integration
- Pydantic for validated manifests
- Typer for the CLI
- Rich for readable local output
- Hypothesis for generated protocol inputs
- Jinja2 for reports/configuration generation
- Prometheus client as an optional rig-metrics exporter
- Ruff, mypy, and coverage.py for quality checks

## Independent demonstration

Use simulated serial/CAN adapters in ordinary CI, then run real flashing and GPIO/UART tests on a self-hosted runner when hardware is attached.

## Integration

Adapters consume public contracts only. ControlBench is one supported DUT, CANWorks provides CAN traffic semantics, LinuxEdge can be another DUT, and SecureFleet can be tested through its public API.


# HILForge Architecture

## Execution pipeline

```text
manifest -> reserve rig -> build -> flash -> reset -> stimulate
         -> observe -> assert -> collect artifacts -> publish result
```

## Adapter interfaces

- `Flasher`: program, erase, and verify firmware.
- `ResetController`: reset, power-cycle, and interrupt boot.
- `SerialChannel`: send commands and capture logs.
- `GpioController`: stimulate and observe digital signals.
- `CanChannel`: publish, capture, corrupt, delay, and replay frames.
- `ApiClient`: validate LinuxEdge or SecureFleet behavior.

Every adapter requires a fake implementation so the orchestration engine remains testable without hardware.


# OpenVINO RISC-V FloorMod JIT Emitter

## Summary of Implementation

### Implemented jit_floor_mod_emitter:
- Created the `jit_floor_mod_emitter` class in `jit_eltwise_emitters.hpp`.
- Implemented the FloorMod algorithm in `jit_eltwise_emitters.cpp` using RVV1.0 instructions.

### Integrated the emitter with the JIT executor:
- Added FloorMod support in `jit_uni_eltwise_generic.cpp` in the functions:
  - `create_eltwise_emitter`
  - `get_supported_precisions`

### Modified RISCV64 kernel:
- Updated RISCV64 kernel code to enable usage of the new emitter during runtime.

### Testing:
- Added unit tests within the CPU functional tests (`ov_cpu_func_tests`).
- Tested using QEMU RISCV64 emulator with tests enabled (`-DENABLE_TESTS=ON`) and filtered GoogleTest for `"*smoke*Eltwise*FloorMod*"`.

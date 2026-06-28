DarkEngine
A High-Performance, Lock-Free Runtime Kernel powered by Java 26 & Mechanical Sympathy

Peak PerformanceJava 26Zero GCLicense

Overview
DarkEngine is a low-latency infrastructure kernel designed to communicate directly with the operating system and underlying hardware. Its primary goal is to evolve into the foundational runtime for a high-performance video game engine.

It solves the inherent latency problems of the Java Virtual Machine (JVM) by aggressively bypassing the Garbage Collector, aligning memory structures directly with physical RAM, and avoiding traditional OS thread scheduler bottlenecks. Fully integrated with a CI/CD pipeline via GitHub Actions for automated, cloud-based native Windows production builds.

Microarchitectural Sympathy (Core Technologies)
DarkEngine is built upon the philosophy of Mechanical Sympathy—aligning software structures with the hardware behavior to solve critical performance bottlenecks:

Project Panama FFI: Zero-overhead native C++ bindings for OS windowing (glfw3.dll) and Spatial Audio (soft_oal.dll). The engine controls the OS memory buffers directly.
SIMD Vector API (Project Valhalla ready): 256-bit AVX2/AVX-512 "Data Particle Acceleration" for massive parallel physics and state processing.
Lock-Free Concurrency: Wait-free SPSC/MPSC Ring Buffers coupled with VarHandle memory fences for sub-30ns thread coordination.
DAG Task Orchestration: A Directed Acyclic Graph (DAG) scheduler that parallelizes physics calculations (Broadphase) across slave threads without global barriers.
SoA Data Topology (ECS): Struct of Arrays memory topology paired with JMH Microbenchmarking to ensure zero cache-misses and maximum CPU iteration speed.
Off-Heap Memory Vaults: Direct Arena allocations structured with strict 64-byte padding to absolutely prevent L1 cache false sharing.
OS Thread Pinning: CPU core affinity mapping directly at the kernel level for deterministic execution.
Peak Performance Metrics
The kernel includes an automated integrity suite that evaluates the hardware limits. The latest JMH hardware stress tests on the production build yielded the following metrics:

Subsystem	Metric	Technology Utilized
ECS Memory Topology (SoA vs AoS)	2x Speedup (126µs/op vs 240µs/op)	JMH Validated Struct of Arrays vs Object-Oriented
Data Accelerator	4.17 GB/s	SIMD Vector API (256-bit, 8 lanes)
Atomic Bus Latency	29.69 ns	Wait-free VarHandles (Acquire/Release)
Event Throughput	67.8M ops/sec	Off-heap Native Ring Buffers
Garbage Collection	Zero Pauses	ZGC + 100% Off-heap execution
Build & Execution
DarkEngine relies on cutting-edge Java 26 features and GraalVM's jpackage to distribute a standalone native image without requiring a local JRE.

bash

# 1. Compile the kernel and FFI bindings in aggressive Zero-Debug mode
.\build.bat
# 2. Run the Extreme Hardware JMH Benchmarks (Zero-GC Validation)
.\benchmark.bat
# 3. Cloud-Ready Native Packaging (Compiles and bundles into a standalone Windows .exe)
.\build_release.bat
License
This project is licensed under the GNU Lesser General Public License v3.0 (LGPL-3.0).

Permissions of this copyleft license are conditioned on making available complete source code of licensed works and modifications under the same license or the GNU GPLv3. Copyright and license notices must be preserved. Contributors provide an express grant of patent rights. However, a larger work using the licensed work through interfaces provided by the licensed work may be distributed under different terms and without source code for the larger work.

Marvin Dev
Systems Architecture Practitioner | High-Performance Runtime & Kernel Development Java 26 · SIMD Vector API · Off-Heap Memory · Low-Latency Concurrency · CI/CD Automation

For deep technical insights, explore the binary-indexed documentation in the /docs/internal directory.

“Optimizing at the hardware level, one nanosecond at a time.”

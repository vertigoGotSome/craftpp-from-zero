# Performance goals

Aim for high, stable frame rates, consistent frame times, bounded RAM and VRAM, and fewer stalls during loading. Use profiling to identify avoidable CPU overhead, GPU work, resource transfers and synchronization costs before changing architecture or adding parallelism.

Minecraft already uses the GPU without additional shader packs. C++ and GPU utilization alone do not demonstrate a performance improvement.

When a comparable workload exists, document hardware, driver, resolution, scene, settings and capture procedure. Compare CPU and GPU frame times, frame-time percentiles, memory peaks and loading stalls under controlled conditions. There are no benchmarks or measured claims at setup.

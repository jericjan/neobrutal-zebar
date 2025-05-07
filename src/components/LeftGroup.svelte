<script lang="ts">
  import type { CpuOutput, MemoryOutput } from "zebar";

  import Button from "./Button.svelte";
  import Meter from "./Meter.svelte";

  type LeftGroupProps = {
    cpu: CpuOutput;
    memory: MemoryOutput;
  };

  let { cpu, memory }: LeftGroupProps = $props();
</script>

<div class="flex flex-row gap-3 items-center">
  <Button class="text-zb-icon" iconClass="bolt-filled" />
  <div class="flex gap-1 items-center">
    <i class="ti ti-ruler-2"></i>
    <Meter class="bg-zb-memory" percent={Math.round(memory?.usage ?? 0)} />
  </div>
  <div class="flex gap-1 items-center">
    <i class="ti ti-cpu"></i>
    <Meter class="bg-zb-cpu" percent={Math.round(cpu?.usage ?? 0)} />
  </div>
</div>

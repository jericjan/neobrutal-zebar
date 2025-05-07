<script lang="ts">
  import type { CpuOutput, MemoryOutput, DiskOutput } from "zebar";

  import Button from "./Button.svelte";
  import Meter from "./Meter.svelte";

  type LeftGroupProps = {
    cpu: CpuOutput;
    memory: MemoryOutput;
    disk: DiskOutput
  };

  let { cpu, memory, disk }: LeftGroupProps = $props();
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
  <i class="ti ti-point-filled"></i>
  {disk?.disks[0].availableSpace.iecValue.toFixed(2)} {disk?.disks[0].availableSpace.iecUnit} free
</div>
